# CLAUDE.md

Repo of Claude skills (`skills/`) and agents (`agents/`).

## Git workflow

- **Never merge or push directly to `main`.** All changes go through a branch and a pull request.
- Commit and push only when asked.
- Branch protection on `main` should enforce this; the rule applies even if protection isn't configured yet.

## Content rules

- Third-party material needs a compatible license (MIT, Apache-2.0 or similar). Never copy AGPL or unlicensed code.
  Record each source and its license text in `THIRD_PARTY_NOTICES.md`.
- Don't state facts about the user's shop, tools or preferences that the user hasn't told you. Ask.
