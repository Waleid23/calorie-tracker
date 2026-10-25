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

## Model estimation (`./cal add "food"` with no number)
If calories are given, the model is never called. If they are omitted, `cal` runs
`claude -p` once to estimate them.

**The model is responsible for:** reading the food description and replying with
its best estimate of the calories as a single whole number, and nothing else.
That is its only job — it does not read or write `calories.json`.

**Our code is responsible for (and checks):**
- Running `claude -p` with a fixed prompt; if `claude` isn't installed, exits
  non-zero, or takes longer than 60 seconds, show an error and save nothing.
- Stripping surrounding whitespace from the reply, then requiring it to be only
  digits (no words, units, decimals, signs, or ranges like "300-400").
- Requiring the number to be in a reasonable range: 1 to 5000 inclusive.
- If any check fails, print an error that includes the model's raw reply and save
  nothing. If all pass, save the entry and print it marked as an estimate.
- Manually given numbers keep the existing rule (must be a whole number).
