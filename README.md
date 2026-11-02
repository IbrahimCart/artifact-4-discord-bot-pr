# Artifact 4: `/mod cleanup` for the PESU Discord Bot

> **Update, 2026-11-01:** this was my first attempt. The maintainers closed the pull request, so Artifact 4 is now **[Doses](https://github.com/IbrahimCart/dose-reminder)**, a reminder app for my mom. This repository stays as the record of the first attempt.

TCSS 490 (Generative AI and Software Development, UW Autumn 2026), Artifact 4: *For Someone Else*, by Ibrahim Cartan.

This repository holds the **plan, the team notes and the log** for my Artifact 4 work. The code itself is a pull request to someone else's project, so it lives in my fork of that project and in the pull request linked below.

## What I am building and for whom

- **For:** the maintainers of [`pesu-dev/discord_bot`](https://github.com/pesu-dev/discord_bot), the Discord bot of the PESU Developer Group, a student group that builds open-source tools for the PES University community. Their moderators are the people who would use the feature.
- **What:** the feature requested in [issue #92, "Clean up access help"](https://github.com/pesu-dev/discord_bot/issues/92). A new moderation slash command, `/mod cleanup <channel>`, that purges all messages in a designated channel (at first only `#access-help`), then posts two predefined onboarding and troubleshooting messages and pins them.
- **Why they want it:** during admission and onboarding seasons `#access-help` fills with outdated questions and clutter, and moderators need a quick way to reset it with the official checklist pinned.
- **How I found out what they need:** I read the issue and the project's `CONTRIBUTING.md`, and I commented on the issue on 2026-11-01 to ask the maintainers whether it is still wanted and how they would like it done. Their answers, and what I changed because of them, are in [`LOG.md`](LOG.md).

## Team and who owns what

- **Team:** Ibrahim Cartan only, so far. The course asks for a pair or trio; I asked my professor whether I may do this submission alone and find a partner for the next one. That answer is recorded in `LOG.md` when I have it.
- **Owner of all work:** Ibrahim.
- **Reviewers and mergers:** the `pesu-dev` maintainers (they merge, I do not).

## How collisions are avoided

- All work happens on one branch in my fork, named `<my-discord-username>/mod-cleanup` as the project's `CONTRIBUTING.md` requires.
- The pull request targets the project's **`dev`** branch, never `main`.
- I do not touch files outside the `mod` cog (`src/cogs/mod/`) unless the feature needs it.
- Before starting I check the issue and open pull requests so I do not duplicate someone else's work.
- If a partner joins, we split the work by file or sub-task first, each on their own branch, and the maintainers merge.

## How the AI is used

I use Claude Code for reading the unfamiliar codebase, drafting the command and its tests, and keeping `LOG.md`. The agent follows [`CLAUDE.md`](CLAUDE.md). I run the project's own checks (lint, format and the unit tests with their 95% coverage gate) before opening the pull request. I have not run the command in a live Discord server, because the project is only supported on Linux (or WSL) and needs a database, a bot token and a test server that I have not set up.

## Definition of done

1. A pull request to `pesu-dev/discord_bot` (`dev` branch) that implements `/mod cleanup` as described in issue #92, using their PR template. *PR #103 was opened on 2026-11-01 but the maintainers closed it the same day because I had not been assigned the issue. See `LOG.md`, Step 8.*
2. *Not done:* the command tested on a test Discord server, with a screenshot of it working. Unit tests and lint pass; a live test is optional and would need MongoDB, a bot token and a test server.
3. This repository's `LOG.md` is up to date, and my portfolio card has the PR link and a short reflection.

## Links

- Issue: https://github.com/pesu-dev/discord_bot/issues/92
- Pull request: https://github.com/pesu-dev/discord_bot/pull/103 (opened 2026-11-01, branch `llokri/mod-cleanup` into `dev`; **closed by the maintainers** because I was not assigned the issue)
- My fork: https://github.com/IbrahimCart/discord_bot
- Portfolio: https://ibrahimcart.github.io
