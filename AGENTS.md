# epochop — Unix Epoch Timestamp Converter

> Convert between Unix epoch timestamps and human-readable dates. Browser-side only.

## What it does

epochop converts Unix epoch timestamps (integers representing seconds or milliseconds since 1970-01-01 00:00:00 UTC) to human-readable dates — and back. It auto-detects whether a timestamp is in seconds or milliseconds.

**Conversions provided:**
- Epoch (seconds or ms) → UTC date, local date, ISO 8601, relative time
- Date/time picker → epoch seconds and milliseconds
- Live current epoch ticker

## Input / output

**Epoch → Date (URL deep-link):**

```
GET https://epochop.radicchio.page/#1741730648
```

The page loads with `1741730648` pre-filled in the epoch input and shows:
- UTC: `2025-03-11 21:44:08 UTC`
- ISO 8601: `2025-03-11T21:44:08.000Z`
- Relative: `1y ago`
- Milliseconds: `1741730648000`

**Epoch → Date (browser-side JavaScript — no fetch required):**

```javascript
const epoch = 1741730648; // seconds
const ms = epoch > 1e12 ? epoch : epoch * 1000; // auto-detect
const date = new Date(ms);
// date.toISOString() → "2025-03-11T21:44:08.000Z"
```

**Date → Epoch:**
Use the datetime-local picker on the right panel. Results shown: epoch seconds, epoch milliseconds.

## Agent usage

epochop is a pure browser-side utility. Agents can:

1. **Deep-link to a decoded timestamp:** send users to `https://epochop.radicchio.page/#<epoch>` to show them a timestamp in human-readable form.
2. **Compute inline (recommended for agents):** epoch conversion is trivial in any language. The JavaScript above is the canonical pattern.

**Common JWT claims (epoch seconds):**
- `exp` — token expiry
- `iat` — issued at
- `nbf` — not before

To decode the full JWT and see these claims labeled, use [jwtchop](https://jwtchop.radicchio.page).

## Pricing

Free. No API key. No account. No server.

## Related tools

- [jwtchop](https://jwtchop.radicchio.page) — decode JWT tokens (exp/iat/nbf are epoch timestamps)
- [cronfig](https://cronfig.radicchio.page) — cron expression builder
- [hashchop](https://hashchop.radicchio.page) — SHA hash generator

## Contact / support

[bitterdesk.com/s/epochop/](https://bitterdesk.com/s/epochop/)
