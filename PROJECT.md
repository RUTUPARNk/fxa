# fxa — the story

This is the one where he walked into the big leagues.

`fxa` is **Mozilla's Firefox Accounts** — the identity and login system behind
Firefox, sync, and subscriptions, used by hundreds of millions of people. A
35,000-commit monorepo maintained by a full Mozilla engineering org. He forked it,
learned his way around it, and **fixed a real, open issue in it (#18859).**

The bug was a humane little thing: when Firefox shows you the devices connected to
your account, it lists *where* each one is — the city and country. But that
location was rendering in the wrong language. His fix made it **localized
properly** — refactored the formatter to be locale-agnostic and return a country
code, then used `Intl.DisplayNames` so a user in any language sees their own
city and country in *their* language, not hardcoded English.

Two things make it more than a drive-by:
- He **wrote tests** for it — added coverage to the geodb module, the `Account`
  model, and the shared formatters (hundreds of lines of new test code), the way a
  real contributor to a codebase that size has to.
- His last commit before finalizing was *"remove unprofessional comments and
  cleanup geodb tests"* — he went back and **cleaned up after himself**, polishing
  his own work to meet the bar of the project he was contributing to. That instinct
  — to make it presentable for someone else's standards — is the whole point.

There's a quiet symmetry to it, too. The kid who broke past his school's identity
lockdown grew up to make a small, careful fix to the identity system that logs in
the world — not breaking it this time, improving it.

## What I did

- `fix: explicit country code handling for client-side localization` (Dec 2025) —
  refactored `ClientFormatter` to be locale-agnostic and return `countryCode`,
  switched `DeviceInfoBlock` to `Intl.DisplayNames`.
- `Fix #18859: Correct City/Country language display in sync flow` (Feb 2026) —
  the issue fix across `geodb`, `geo-locate`, the `Account` model, and formatters,
  with tests.
- `Refactor: remove unprofessional comments and cleanup geodb tests` — the polish
  pass.
- Prepared on the `fix/issue-18859` branch and kept in sync with `mozilla:main`.

## Note

This repo is upstream Mozilla fxa with my commits on top — left untouched (the
committed `.env` files are Mozilla's dev placeholders, e.g. `STRIPE_API_KEY=11233`,
not real secrets). Whether #18859 was merged upstream isn't visible from the fork
— it was built, tested, and prepared against the issue.
