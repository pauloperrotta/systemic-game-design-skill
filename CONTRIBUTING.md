# Contributing

Thanks for helping. Short rules:

1. **Do not paste text from the book.** Paraphrase in your own words. Pull requests that copy passages will be asked to change.
2. **Keep `SKILL.md` lean.** It is read on every activation. Detail goes in `skills/systemic-game-design/references/` with an index at the top.
3. **Say why, not just what.** Instructions to the model should explain the reason; avoid shouting rules.
4. **Mark invented numbers.** Any weight, exponent or threshold not given by the method must be labeled as a starting point.
5. **Evidence for behavior changes.** If you change how the skill answers, add or update a prompt in `evals/evals.json` with objective assertions and report with/without results.
6. **Triggering changes** (the `description` field) need before/after results on a balanced set of should-trigger and should-not-trigger prompts.

Validate the skill folder before opening a pull request: the `SKILL.md` header must have `name` and `description`, and every section name cited in `SKILL.md` must exist in the references.
