# Change log

## 2026-10-16
- Created `cal` with `add` and `today` commands, saving data to `calories.json`.
- Added `CLAUDE.md` (project overview) and this `LOG.md`.
- Added `.gitignore` to keep `calories.json` (personal food data) out of git.
- The first request got cut off at "Keep it a"; Claude guessed "keep it a single file with no dependencies", which matched the intent ("keep it as simple as possible").
- User tested `add` and `today` by hand and got the correct total (555).
