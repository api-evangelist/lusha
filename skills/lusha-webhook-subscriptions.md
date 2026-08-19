---
name: Receive Lusha signals over webhooks
description: Create the account webhook secret, subscribe entities to signal types in bulk, verify the HMAC signature on delivery, and watch the audit log for blocked subscriptions.
api: openapi/lusha-webhooks-api-openapi.yml
operations: [getAccountSecret, regenerateAccountSecret, createSubscription, listSubscriptions, getSubscriptionById, updateSubscription, testSubscription, deleteSubscriptions, createOptOutSubscription, getAuditLogs, getAuditLogStats]
generated: '2026-08-13'
method: generated
source: openapi/lusha-webhooks-api-openapi.yml + asyncapi/lusha-webhooks.yml
---

# Receive signals over webhooks

Push beats polling for signals. Subscriptions are per entity (one contact or company id) and per signal
type, and one account-level secret signs every delivery.

## Steps

1. **Ensure a secret exists.** `getAccountSecret` (`GET /api/account/secret`) returns the current account
   webhook secret; `404` means none exists yet. `regenerateAccountSecret`
   (`POST /api/account/secret/regenerate`) creates or replaces it — it is an upsert and always succeeds.
   **The secret is shown once.** Store it immediately. Regenerating invalidates the old secret for every
   subscription on the account, so rotate deliberately.
2. **Subscribe.** `createSubscription` (`POST /api/subscriptions`) takes a `defaults` block (`url`,
   `entityType`, `signalTypes`, name prefix) plus a `subscriptions` array of 1-25 items, each with an
   `entityId` and optional overrides. The response reports `total` / `successful` / `failed` with a
   per-index result, so a partial success is normal — read the results array, not just the status code.
   The `url` must be HTTPS in production.
3. **Verify delivery works.** `testSubscription` (`POST /api/subscriptions/{id}/test`) sends a test
   payload and returns `flowCheck`, `testPayload` and `isSuccess`.
4. **Verify every real delivery.** Each callback carries `X-Lusha-Signature` and `X-Lusha-Timestamp`.
   Compute `HMAC-SHA256(secret, timestamp + "." + JSON.stringify(payload))` and compare in constant time
   (`crypto.timingSafeEqual`). Reject anything that does not match. Then acknowledge in the response shape
   documented on `createSubscription` — Lusha requires an acknowledgment.
5. **Manage the set.** `listSubscriptions` (`GET /api/subscriptions`), `getSubscriptionById`
   (`GET /api/subscriptions/{id}`), `updateSubscription` (`PATCH /api/subscriptions/{id}`, which can also
   `regenerateSecret`), and `deleteSubscriptions` (`POST /api/subscriptions/delete`, up to 25 per call).
6. **Watch for silence.** `getAuditLogs` (`GET /api/audit-logs`) returns per-delivery status, HTTP status,
   duration and error; `getAuditLogStats` (`GET /api/audit-logs/stats`) returns total / success / failed /
   successRate. A subscription that exceeds max retries is **disabled** and comes back with
   `isActive: false`, `blockReason` and `blockedAt` — poll the list or the stats to notice.
7. **Handle opt-outs.** `createOptOutSubscription` (`POST /api/subscriptions/opt-out`, contacts only)
   delivers an `OptOutWebhookPayload` when a contact requests removal from data processing. Wire it to
   your CRM suppression list — this is a compliance obligation, not an optional feed.

## Rules

- Webhook management endpoints are limited to **100 requests/minute per account**; bulk create and delete
  take at most 25 items each.
- Credits are charged once per delivered signal (`creditsCharged` is in the payload). Retried deliveries
  are not re-charged.
- Audit-log retention: 90 days for successful deliveries, 180 days for failed/DLQ.
- No AsyncAPI document exists for this surface; the event catalogue is captured in
  `asyncapi/lusha-webhooks.yml`.
