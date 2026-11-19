---
name: tesser-cli
description: Run dev servers, tests, typechecks, and builds on persistent cloud boxes while the code stays local. Use when the user wants a dev server running off the laptop with localhost as the window into it, several worktrees running at once, a box for tests or heavy commands, putting a repo on tesser for the first time, or when the repo has a tesser (or older devboxes) skill under .agents/skills or .claude/skills.
---

First look for the repo's own skill: a SKILL.md and *.toml manifests in any of
.agents/skills/tesser, .claude/skills/tesser, .agents/skills/devboxes,
.claude/skills/devboxes at the repo root. Check all four; what you find there wins.

tesser explains itself. Before your first command:

    tesser --help          how it works, and the rules
    tesser <cmd> --help    what that command actually does

Errors name the next command to run. Trust them over anything you remember.

Hit a sharp edge (a misleading error, a missing command, a workaround)? Run
`tesser feedback "<what you ran, what happened, what you expected>"`, then
keep going.

No `tesser` command? `curl -fsSL https://tesser.sh/install | sh` installs it
and prints the path to call it by in this shell.

Not logged in? Run `tesser login` yourself. It prints a link and exits: send
it to the user, and once they say they have authorized it, run
`tesser login --wait`, then tell them the account and org it logged in as.

Putting a repo on tesser for the first time, or fixing a setup that keeps
failing: `tesser help setup` is the guide; read all of it first.
