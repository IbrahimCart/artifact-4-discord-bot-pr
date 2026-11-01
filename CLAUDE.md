# CLAUDE.md

Team plan for Artifact 4 (TCSS 490). Agents do not share memory, so anything an agent needs to know about the plan is written here. Read `README.md` for the full plan.

## Goal

Implement `/mod cleanup <channel>` for `pesu-dev/discord_bot` (issue #92) as a pull request to their `dev` branch.

## Rules

- Work only in the fork's `mod` cog (`src/cogs/mod/`: `groups.py`, `commands.py`, optional `helpers.py`) unless the feature truly needs more. Follow the cog layout and code style in the project's `CONTRIBUTING.md`.
- Branch name: `<discord-username>/mod-cleanup`. Pull requests go to **`dev`**, not `main`. Use the project's PR template.
- Run `.githooks/install.sh` and the project's linter and tests (see its `CONTRIBUTING.md`) before committing.
- Never commit bot tokens, database credentials or a `.env` file.
- Commit messages are plain, short and describe the change. **Do not add a `Co-Authored-By: Claude` line or a "Generated with Claude Code" line** to commits or pull requests.
- Do not post comments, open pull requests or push to anyone else's repository without the user saying so.

## Logging

- Add an entry to `LOG.md` in this repository for each meaningful step: the date, tool, the prompt, what it produced, and what I changed or checked. Do not invent entries or results.
- Keep a record of anything the maintainers say (screenshots or quotes) and what changed because of it.

## Before calling it done

- The pull request is open against `dev` and linked in `README.md`.
- The command was tested on a Discord server and there is a screenshot.
- `LOG.md` is current and the portfolio card has the PR link and a reflection.
