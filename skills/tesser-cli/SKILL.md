---
name: tesser-cli
description: Run dev servers, tests, typechecks, and builds on persistent cloud boxes while the code stays local. Use when the user wants a dev server running off the laptop with localhost as the window into it, several worktrees running at once, a box for tests or heavy commands, putting a repo on tesser for the first time, or when the repo has a tesser (or older devboxes) skill under .agents/skills or .claude/skills.
---

First look for the repo's own skill: a SKILL.md and *.toml manifests in any of
.agents/skills/tesser, .claude/skills/tesser, .agents/skills/devboxes,
.claude/skills/devboxes at the repo root. Check all four; what you find there wins.

With a repo skill, these are most of what you need. Without one, read
`tesser --help` once: it has the rules.

    tesser exec -- pnpm test     tests, typechecks, builds on the workbench
    BOX=$(tesser dev web)        a dev server; give the human the URL it prints
    tesser wait <box|job_id>     after dev or exec --detach; never nohup, tmux or &
    tesser sync "$BOX"           ship edits; --restart for a new dependency
    tesser browser "$BOX" <<'JS' screenshots, page checks: JS on stdin next to the box's Chrome

Errors name the next command to run. Trust them over anything you remember.
Stuck on a command: `tesser <cmd> --help`. `use`, `keep` and `cloud` are the
human's.

Hit a sharp edge (a misleading error, a missing command, a workaround)? Run
`tesser feedback "<what you ran, what happened, what you expected>"`, then
keep going.

No `tesser` command? Install it first: https://tesser.sh/docs/install.md

Not logged in? Run `tesser login` yourself. It prints a link and exits: send
it to the user, and once they say they have authorized it, run
`tesser login --wait`, then tell them the account and org it logged in as.

Putting a repo on tesser for the first time, or fixing a setup that keeps
failing: `tesser help setup` is the guide; read all of it first.
