# cal — calorie tracker

A tiny Python command-line calorie tracker. Standard library only, single file.

- `./cal add "food" 450` — log a food and its calories for today
- `./cal today` — list today's foods and the total

## Files
- `cal` — the whole program (executable Python script)
- `calories.json` — data, created on first add; keyed by date (`YYYY-MM-DD`) → list of `{food, calories}`
- `LOG.md` — change log

## Guidelines
- Keep it as simple as possible: one file, no dependencies.
- After every change, add a dated entry to `LOG.md` describing what changed.
- Note: macOS has a built-in `cal` (calendar), so run with `./cal` or alias it.
