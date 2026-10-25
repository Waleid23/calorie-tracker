# Change log

## 2026-10-16
- Created `cal` with `add` and `today` commands, saving data to `calories.json`.
- Added `CLAUDE.md` (project overview) and this `LOG.md`.
- Added `.gitignore` to keep `calories.json` (personal food data) out of git.
- The first request got cut off at "Keep it a"; Claude guessed "keep it a single file with no dependencies", which matched the intent ("keep it as simple as possible").
- User tested `add` and `today` by hand and got the correct total (555).

## 2026-10-25
- Plan (Artifact 3): make `./cal add "food"` with no number ask `claude -p` for a
  calorie estimate. The model replies with only a number; our code checks it is a
  whole number from 1 to 5000 before saving, otherwise shows an error and saves
  nothing. Giving a number skips the model. Documented the split of
  responsibilities in `CLAUDE.md` before writing code.
- Implemented the plan: added `estimate()` to `cal`, which runs `claude -p` (60s
  timeout), requires a digits-only reply, and requires 1–5000. Entries from the
  model print "estimated by Claude".
- Tested with a fake `claude` script: "320" was saved; "about 300", "300-400",
  "12.5", "-50", "9000", "0", a failing `claude`, and a missing `claude` were all
  rejected with an error and nothing saved. With the real `claude`, "a banana" was
  estimated at 105 cal. A manual `add "manual" 100` skipped the model. Test entries
  were removed from `calories.json` afterward.
