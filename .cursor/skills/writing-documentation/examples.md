# Documentation format examples

Each example keeps `title` + `short description` ≤ 120 characters (plain text).

## Example 1 — feature

**Count:** 20 + 46 = 66

```markdown
# Auth session refresh
Keeps users signed in without a full re-login.

## TLDR
Access tokens expire quickly. A stored refresh token silently requests a new access token. Logout revokes both. Failed refresh sends the user to login.

## Dummy Section
Think of a visitor badge that dies every 15 minutes. Instead of walking back to the front desk, you also hold a longer-lived pass that quietly gets you a new badge. Hand both in at logout and neither works.

## Deep Dive
Refresh lives in `src/auth/session.ts`. Access tokens last 15 minutes; refresh tokens last 14 days in httpOnly cookies (`refresh_token`). `POST /auth/refresh` rotates the refresh token and returns a new access token. Concurrent refresh is single-flighted via `refreshInFlight`. On `invalid_grant` or HTTP 401 from refresh, clear cookies and redirect to `/login?reason=session`. Do not refresh on 403. Logout: `POST /auth/logout` then delete both cookies.
```

## Example 2 — bugfix

**Count:** 24 + 44 = 68

```markdown
# Invoice PDF timezone fix
PDF dates now use the org timezone, not UTC.

## TLDR
Invoice PDFs were rendering due dates in UTC. They now use the organization timezone stored on the tenant. Existing PDFs are not regenerated.

## Dummy Section
The PDF was printing the due date as if everyone lived in UTC. If you are in Eastern Time, a due date of Jan 15 could show up as Jan 14. It now uses the company's timezone so the printed date matches what people expect.

## Deep Dive
Cause: `InvoicePdfRenderer` called `dueDate.toISOString().slice(0, 10)` (UTC date). Fix: `formatInTimeZone(dueDate, org.timezone, 'yyyy-MM-dd')` via `date-fns-tz` in `src/invoices/pdf/renderer.ts`. `org.timezone` is IANA (required on tenant; default `America/Toronto` for legacy rows). Applies to new PDFs only; do not backfill. Tests: `renderer.test.ts` covers UTC-midnight and US/Eastern DST.
```

## Example 3 — over budget, then trimmed

**Too long (135):** `Background job retry policy for billing exports` (47) + `Explains how failed billing export jobs retry, back off, give up, and alert the on-call.` (88)

**Trimmed (70):** `Billing export retries` (22) + `How failed export jobs retry, back off, and stop` (48)

Cut the title first when it is a sentence. Keep the description as the scan payload.

