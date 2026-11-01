# Artifact 4 Log

A running log of what I planned and what changed for TCSS 490 Artifact 4, and the AI prompts I used. Newest entries go at the bottom.

## Template

### Step N: short title
- **Date:**
- **Tool / model:**
- **Prompt:**
- **What it produced:**
- **What I changed and why:**

---

### Step 1: Read the assignment and choose a kind of project
- **Date:** 2026-10-30 to 2026-11-01
- **Tool / model:** Claude Code
- **Prompt:** "for the next artifact what are some suggestion", then "what is something that i could do alone for now" and "how do i go about number 6".
- **What it produced:** A summary of the Artifact 4 requirements (two or three people, someone outside the team, ask what they need, plan and log in the repository, a handover before Nov 8, a card with a reflection) and a list of project ideas. The idea I chose was a contribution to an open-source Discord bot.
- **What I changed and why:** The assignment asks for a pair or trio. I asked my professor whether I can do this submission alone and find a partner for the next one. *Answer: pending.* I chose a pull request because the handover (opening it) does not depend on someone replying in time.

### Step 2: Find a project and pick an issue
- **Date:** 2026-11-01
- **Tool / model:** Claude Code (Claude Opus 5.5 / Sonnet 5.5)
- **Prompt:** "okay how do i go about number 6" and "i want a project to be picked. is it possible without someone responding?"
- **What it produced:** A GitHub search of Discord bot libraries and bots for "good first issue" and "help wanted" issues, with checks on how active each repository is. Most of the big libraries had issues that had not been touched for months. `pesu-dev/discord_bot` had recent commits, outside pull requests merged in October, and open beginner issues with no assignee.
- **What I changed and why:** I picked issue #92 ("Clean up access help", a `/mod cleanup` slash command) because it is clearly specified, labeled "good first issue", unclaimed and a good size for about a week. Issue #96 is the backup if #92 turns out too hard. I have not yet read the code, so I do not know how hard it really is.

### Step 3: Ask the maintainers
- **Date:** 2026-11-01
- **Tool / model:** Claude Code with the in-app browser
- **Prompt:** "i signed in on claude browser and imported cookies. you can post the comment"
- **What it produced:** It read the project's `CONTRIBUTING.md` first (PRs must target `dev`, branch name `<discord-username>/feature`, Linux or WSL supported, needs MongoDB and a bot token), then posted my comment on issue #92 from my account asking the maintainers if it is still wanted and how they would like it done.
- **What I changed and why:** I changed the wording of my draft so it no longer asked which branch to use, because the contributing guide already says `dev`. *Maintainer reply: none yet.*

### Step 4: Set up this repository
- **Date:** 2026-11-01
- **Tool / model:** Claude Code
- **Prompt:** "Yes, do both" (update the card and create the notes repo).
- **What it produced:** This repository with `README.md` (what, who for, ownership, how collisions are avoided), `CLAUDE.md` (the plan for agents, including no Claude co-author line in commits) and this log, plus an "in progress" Artifact 4 card on my portfolio.
- **What I changed and why:** The README says plainly that I am the only team member so far and that the professor's answer is pending, so it does not claim anything that has not happened.

### Step 5: Fork the project and read the code
- **Date:** 2026-11-01
- **Tool / model:** Claude Code
- **Prompt:** "Yes, set it up" (fork `pesu-dev/discord_bot`, read the `mod` cog, and tell me how hard `/mod cleanup` is and what setup I need on my Mac).
- **What it produced:** My fork `IbrahimCart/discord_bot`, cloned to `~/IdeaProjects/discord_bot` on the `dev` branch. It read the project's `AGENTS.md`, `CONTRIBUTING.md`, the `mod` cog and the tests. The issue is rated "Low": one new command in `src/cogs/mod/commands.py`, modelled on the existing `/mod purge`, with the two message texts kept as constants, and unit tests in `tests/unit/cogs/mod/commands_test.py`. No code has been written yet, and no other open pull request touches this issue.
- **What I changed and why:** I learned the project needs Python 3.13 or newer, `uv`, and a unit-test coverage of at least 95% in CI. My Mac has none of `uv`, Docker or MongoDB. The unit tests mock Discord, so I only need `uv` to build and test the command. Running the real bot needs MongoDB, a bot token and a test server, so I will treat that as optional. *Maintainer reply on issue #92: none yet.*

### Step 6: Install uv and build `/mod cleanup`
- **Date:** 2026-11-01
- **Tool / model:** Claude Code (Claude Opus 5.5 / Sonnet 5.5)
- **Prompt:** "Yes, install uv" (install `uv`, run the existing tests, then build the command).
- **What it produced:** `uv` installed with Homebrew, then the project's pinned `uv` 0.11.x installed as a tool because the project refuses other versions. The existing suite passed before any change (393 unit tests, 99.6% coverage). It then wrote `/mod cleanup` in `src/cogs/mod/commands.py`, modelled on `/mod purge`: it only accepts `#access-help`, purges the channel, posts and pins the two onboarding messages, deletes Discord's "pinned a message" notices and sends an audit embed to the mod-logs channel. The two message texts are constants in `src/cogs/mod/helpers.py` (the second is 1783 characters, under Discord's 2000 limit), and the command is listed in the `/help` mod menu. Five new unit tests cover a wrong channel, a user without a moderator role, the purge/post/pin/audit flow, the message length and the notice cleanup.
- **What I changed and why:** The linter flagged one line over the project's 120-character limit, which was fixed. I checked that the "no moderator role" test really tests the role check by running the same call as a moderator and seeing the purge run. After the change, lint, format, compile, the cog import check and the full unit suite all pass (398 tests, 99.6% coverage). I have **not** run the command in a real Discord server, which needs MongoDB, a bot token and a test server, so the tests use mocks. Nothing is committed in my fork yet: the project's `AGENTS.md` says not to commit until asked, and the branch name must use my Discord username.

### Step 7: Open the pull request (the handover)
- **Date:** 2026-11-01
- **Tool / model:** Claude Code (Claude Opus 5.5 / Sonnet 5.5)
- **Prompt:** "yes" (push the branch and open the PR), after I chose `llokri` for the branch prefix and my GitHub noreply address for the commit.
- **What it produced:** Branch `llokri/mod-cleanup` pushed to my fork, and [pull request #103](https://github.com/pesu-dev/discord_bot/pull/103) opened against `pesu-dev/discord_bot`'s `dev` branch with the project's PR template: 5 files, +199 -2, one commit (`feat(mod): add /mod cleanup command to reset #access-help`, closes #92). GitHub reports it as mergeable. No CI checks had started yet.
- **What I changed and why:** I changed the commit's author email to my GitHub noreply address before pushing so my school email would not be public on someone else's repository. In the PR template I only ticked what I actually did (unit tests, lint, format) and wrote plainly that I have not tested the command in a live Discord server and that my local tests ran on Python 3.15, not the project's 3.13. *Maintainer reply: none yet. Professor's reply about working alone: pending.*

### Step 8: The maintainers closed the pull request
- **Date:** 2026-11-01
- **Tool / model:** Claude Code
- **Prompt:** "they responded"
- **What it produced:** A check of the PR and the issue on GitHub. About 35 minutes after I opened it, a maintainer (`achyu-dev`) commented on both: *"were you even assigned the issue? are you part of PES university? Closing your PR as you were not even assigned"*, and closed PR #103. There was no review of the code itself, and nobody replied to my first comment on issue #92 before that.
- **What I changed and why:** I had told myself a reply was not needed and opened the PR within an hour of asking, even though my comment said "within a few days". That was a mistake: I never waited to be assigned, which is what the maintainers expect. The project is also run by and for PES University students, which I am not, so it may not take outside contributions the way I assumed. I corrected my portfolio card and this README so they no longer say the handover is complete. Next step: decide whether to reply politely and ask to be assigned, or build the same kind of work for a different project or group. *Professor's reply about working alone: pending.*

## Next

- Decide with the maintainers (or a new project) how to get a handover that is accepted, and record it here.
- Add a reflection and the final status to my portfolio card before Nov 8.
