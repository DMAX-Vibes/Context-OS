# Claude Code Instructions for Context OS

This repository/folder is the user's portable Context OS — a cross-project AI context layer.

Treat this as a working context system, not as a normal software repository and not as a static biography.

> **First-time setup:** If the `YOU_*.md` files are still mostly empty/template text, read `SETUP.md` and run the setup flow — pre-fill from what you already know about the user, then confirm. Don't make them fill in blank files by hand.

## Start Here

At the beginning of a session involving the user's work, read these files in order:

1. `YOU_CONTEXT.md` — stable identity, collaboration style, global operating instructions.
2. `YOU_PROJECTS.md` — active project index and project-level routing.
3. `YOU_TECH_STACK.md` — technical preferences, stack, debugging style, repo conventions.
4. The relevant project folder under `projects/`, especially `PROJECT_CONTEXT.md` and `CLAUDE.md`.
5. Any current task, issue, README, ticket, or user-provided instruction.

Consult `MANIFEST.md` to decide *how much* of the above to load (see Load Levels). Current user instructions override all files. Project-specific files override global files.

## How to Work With the User

Default working style (override with whatever the user puts in `YOU_CONTEXT.md`):

- Give exact terminal commands, with file paths.
- Say what each command should do, and how to verify it.
- Prefer small, understandable patches.
- Don't give architecture lectures unless asked.
- If something fails, give the next diagnostic command and likely fix.
- Mark uncertainty. Do not invent personal, professional, legal, institutional, or project facts.

## Agentic OS Rule

Context OS is a canonical synthesis target. Do not treat any previous model's version as primary merely because it came first.

When improving context, you may augment, consolidate, reframe, de-emphasize, split, remove, or move material into a more appropriate module. The goal is order-independent convergence: the same useful context system should emerge regardless of which agent touched the files first.

## Current-State Truth Model

Context OS is meant to become the maintained current state, not a permanent set of competing observations.

During onboarding or cross-agent reconciliation, treat each source as partial evidence. Use provenance while reconciling uncertainty. Once the user confirms a fact or enough evidence supports it, promote it into current-state language. In normal operation, the current files are the working truth; the user's direct corrections override them. New evidence should update the files rather than force future agents to re-litigate settled facts.

## Context Update Loop

At the end of significant work, ask internally:

> Did this session reveal durable context that should be added to Context OS?

If yes, propose a patch to the correct file:

- `YOU_CONTEXT.md` — stable identity and global operating context.
- `YOU_PROJECTS.md` — active project index, status, and next actions.
- `YOU_TECH_STACK.md` — recurring stack, command, deployment, or debugging patterns.
- `YOU_CAREER.md` — job strategy, portfolio positioning, résumé/LinkedIn language.
- `YOU_CREATIVE.md` — writing voice, submissions, editorial preferences.
- `YOU_PRIVATE.md` / `YOU_CAREER_PRIVATE.md` — sensitive context that should not be broadly shared (git-ignored).
- project-specific `PROJECT_CONTEXT.md` or `CLAUDE.md` — project details.

Do not silently update sensitive context. Propose the patch clearly and let the user decide.

### Always do these two things when capturing durable context

1. **Cross-project generalization sweep.** When a durable fact emerges inside one project, ask: "Is a generalized version of this useful outside this project?" If yes, record the project-specific version in the project file AND a generalized version in the right cross-project file (usually `YOU_TECH_STACK.md` for technical patterns/gotchas, `YOU_CONTEXT.md` for working-style/identity). A reusable lesson should never stay trapped in one project's notes.
2. **Keep any mirrored memory in sync.** If your tool also keeps its own always-loaded memory (e.g. an auto-memory store), don't let it drift from Context OS. When you update one, reflect it in the other. Context OS is the canonical, version-controlled truth; if they conflict, Context OS wins.

## When Working Inside Another Project Repo

If the user brings this context into a separate project repo:

1. Use `YOU_CONTEXT.md` and relevant modules as background.
2. Use the project repo's own `CLAUDE.md`, README, package files, and code as the immediate implementation source of truth.
3. If durable project context emerges, propose updates to that repo's project-level `CLAUDE.md` or `PROJECT_CONTEXT.md`.
4. If global durable context emerges, propose updates back to the main Context OS files.

Keep the distinction clear: repo instructions tell you how to work on that project; Context OS tells you how to work with this user across projects.

## Output Style

Default to concise, practical Markdown.

For implementation tasks, include: what changed, files modified, commands run or recommended, verification steps, and remaining risks or open questions.

For planning tasks, include: objective, assumptions, recommended path, next concrete action, and context updates if any.
