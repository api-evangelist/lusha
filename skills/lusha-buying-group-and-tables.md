---
name: Map a buying group and persist it to a Lusha table
description: Identify the buying committee across up to 25 named accounts, then keep the working set in a Lusha table with enrichment columns instead of re-querying.
api: openapi/lusha-buying-group-api-openapi.yml
operations: [getContactsBuyingGroup, enrichContacts, createContactsTable, listContactsTables, getContactsTable, addContactsTableEntities, getContactsTableEntities, listContactsTableColumns, runContactsTableColumn, removeContactsTableEntities, deleteContactsTable]
generated: '2026-08-13'
method: generated
source: openapi/lusha-buying-group-api-openapi.yml + openapi/lusha-contacts-tables-api-openapi.yml + changelog/lusha-changelog.yml
---

# Map a buying group, then keep it in a table

Buying Group replaced the retired Decision Makers endpoint on 2026-08-12. It is persona classification
over a **fixed set of named accounts** — not filter-based search and not similarity search.

The Tables API is in **beta** as of the 2.9.x release line.

## Steps

1. **Classify the committee.** `getContactsBuyingGroup` (`POST /v3/contacts/buying-group`) with a
   `companies` array of up to 25 entries, each identified by `domain` or Lusha company `id`, plus an
   optional `clientReferenceId` that is echoed back on the matching result.
   - `personas` (optional) filters to `decision_maker`, `potential_champion` and/or `end_user`; omit it to
     get all three.
   - `contactsLimit` (optional, default 60) caps contacts per company.
   - `pagination.page` / `pagination.size` (10-100, default 100) page the flattened result.
   Results are grouped by company; each contact is a non-PII preview (`has`, `canReveal`) plus a `roles`
   array and a relevance `score` between 0 and 1. Billing is per contact returned, via the
   `buyingGroupContact` action.
2. **Rank, then reveal.** Sort by `score` within each company, keep the contacts you will actually
   contact, and call `enrichContacts` on just those ids with a narrow `reveal` list.
3. **Create a table.** `createContactsTable` (`POST /v3/contacts/tables`) with `name`, `visibility` and
   `owner`. A duplicate name returns `409 TABLE_NAME_CONFLICT`. Table error bodies use
   `{ "message", "code" }`, not the `{ "statusCode", "message" }` shape the rest of the API uses.
4. **Load it.** `addContactsTableEntities` (`POST /v3/contacts/tables/{table_id}/entities`) with up to
   **500 entity ids per call**. Limits: 50,000 entities per table, 500 tables per account.
5. **Work it.** `listContactsTableColumns` (`GET .../columns`) shows the columns and their per-column
   row counts (`rowsNotRun`, `rowsProcessing`, `rowsSuccess`, `rowsNoData`, `rowsFailed`);
   `runContactsTableColumn` (`POST .../columns/{column_id}/run`) runs a column over a `runScope` or an
   explicit `entityIds` list. `getContactsTableEntities` (`GET .../entities`) reads rows back with
   `page` (0-100) and `size` (default 100).
6. **Clean up.** `removeContactsTableEntities` (`DELETE .../entities`), `deleteContactsTable`
   (`DELETE /v3/contacts/tables/{table_id}`).

The companies-side operations are identical in shape: `createCompaniesTable`, `listCompaniesTables`,
`getCompaniesTable`, `updateCompaniesTable`, `deleteCompaniesTable`, `getCompaniesTableEntities`,
`addCompaniesTableEntities`, `removeCompaniesTableEntities`, `listCompaniesTableColumns`,
`removeCompaniesTableColumn`, `runCompaniesTableColumn`.

## Rules

- Every table-writing response carries a `billing` block and, on search/signal calls that pass `tableId`,
  a `tableWrite` block with `added`, `alreadyPresent`, `rowsProcessed`, `rowsCharged` and
  `rowsAlreadyPaidInTable` — rows already paid for in that table are not re-charged.
- Running a column costs credits. Scope the run (`entityIds`) rather than re-running the whole table.
- No idempotency key: a retried `addContactsTableEntities` is a second call. `alreadyPresent` in the
  response is your reconciliation signal.
