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

## Next

- Fork `pesu-dev/discord_bot`, run `.githooks/install.sh`, set up a test Discord server, a bot token and a MongoDB instance (Linux or WSL).
- Read the `mod` cog, then build `/mod cleanup` with tests.
- Open the PR to `dev`, record the maintainers' replies here, and update the portfolio card with the PR link and a reflection.
