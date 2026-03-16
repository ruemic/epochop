## epochop — Standing Directive

A browser-side Unix epoch timestamp converter. Paste a timestamp,
see the date. Pick a date, get the epoch. Auto-detects seconds
vs milliseconds. Nothing leaves the browser.

### Current state

Single `index.html` (842 lines) with inlined CSS and JS. Dark
monospace theme with gold accent. Live ticker, quick offsets,
bidirectional conversion. Functional but has room for polish.

### Priority: Improve the tool

Work through these in order. Each one is a single commit.

1. **Batch conversion.** Add a textarea below the main input that
   accepts one timestamp per line and converts all of them at once.
   Show results as a simple two-column table (input → UTC date).
   Useful for log analysis where you have many timestamps to decode.

2. **Copy all results.** Add a "Copy All" button that copies every
   output field (epoch seconds, ms, UTC, ISO 8601, relative) as a
   formatted block of text. Show brief "Copied!" feedback.

3. **Timezone selector.** Add a dropdown next to the output that lets
   the user pick a timezone (e.g. US/Eastern, Europe/London, Asia/Tokyo).
   Convert and display the date in that timezone alongside UTC.
   Use `Intl.DateTimeFormat` — no libraries.

4. **Shareable URL.** When a timestamp is entered, update the URL hash
   (e.g. `#1741730648`). On page load, if a hash is present, parse it
   and populate the converter automatically. This lets users share
   specific timestamps via URL.

5. **Diff calculator.** Add a small section below the main converter:
   two epoch inputs side by side with a "Diff" result showing the
   difference in days, hours, minutes, seconds. Useful for computing
   TTLs or measuring durations between events.

6. **Keyboard shortcuts.** Cmd/Ctrl+Enter to copy the current epoch
   seconds. Cmd/Ctrl+K to clear all inputs. Cmd/Ctrl+B to focus
   batch input. Show shortcuts in a small help tooltip triggered by
   a `?` button.

### Verification

After making changes, verify with the page inspector:

    bin/page-inspect https://epochop.radicchio.page

This renders the page in headless Chromium and prints the accessibility
tree. Use it to confirm changes are live and structurally correct.
Add `--screenshot /tmp/out.png` for human review.

### Rules

- Everything stays in one `index.html`. No build step, no npm.
- Preserve the existing design language (dark theme, monospace,
  gold accent).
- Test each change by entering real timestamps before committing.
- Do not break existing functionality.
- Commit after each feature. Small, focused commits.
