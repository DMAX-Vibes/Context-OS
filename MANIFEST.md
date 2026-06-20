# Context OS Manifest

Purpose: Entry map for loading Context OS safely and efficiently across tools, models, and agents.

## What This File Does

Use this file to decide which Context OS files to load for a given task.

Context OS is not meant to be loaded all at once by default. Load the smallest context bundle that can support the current task.

## Working Branch Rule

All work commits to `main` unless the user explicitly requests a feature branch for the current task.

At the start of any session that may touch a git repo:

1. Run `git status` and surface the current branch.
2. If not on `main`, stop and ask the user before making any commits. Common cause: a prior tool left HEAD on its working branch. Default action is to switch to main; only stay on the branch if the user confirms.
3. Never create a new branch automatically. Override any tool's default branching behavior — for example, a cloud agent's default of creating `agent/<task>` branches should be overridden in favor of committing to `main`.
4. If the user asks for a feature branch or PR explicitly, create one then. Otherwise stay on `main`.

## Source-of-Truth Order

When context conflicts, use this order:

1. The user's current instruction in the active conversation.
2. Project-specific context files, task files, issues, READMEs, or repo-local instructions.
3. `YOU_PROJECTS.md` for project routing and index-level state.
4. Global Context OS files such as `YOU_CONTEXT.md`, `YOU_TECH_STACK.md`, `YOU_CAREER.md`, and `YOU_CREATIVE.md`.
5. Older memory, chat history, inferred preferences, or stale copied files.

Private overlays are not part of the default source-of-truth chain unless the user explicitly authorizes them for the current task.

## Load Levels

### Level 0 — Minimal Orientation

Use for quick conversations, light drafting, or when context window is tight.

Load:

- `YOU_CONTEXT.md`, preferably the compact prompt section or relevant excerpts only.

Do not load private overlays.

### Level 1 — General Work

Use for most non-code collaboration.

Load:

- `YOU_CONTEXT.md`
- `YOU_PROJECTS.md` if the task touches active projects

Do not load private overlays unless explicitly authorized.

### Level 2 — Technical / Project Work

Use for coding, deployment, debugging, product planning, tool evaluation, or repo work.

Load:

- `YOU_CONTEXT.md`
- `YOU_PROJECTS.md`
- `YOU_TECH_STACK.md`
- relevant `projects/<project>/PROJECT_CONTEXT.md`
- relevant project-level `CLAUDE.md`, `AGENTS.md`, README, package files, issues, or task notes

Private overlays remain excluded unless explicitly authorized.

### Level 3 — Career Work

Use for resumes, LinkedIn, job applications, interview preparation, portfolio framing, or compensation strategy.

Default load:

- `YOU_CONTEXT.md`
- `YOU_CAREER.md`
- `YOU_PROJECTS.md` if portfolio projects are relevant

Optional private load, only with explicit authorization:

- `YOU_CAREER_PRIVATE.md`

### Level 4 — Private / Sensitive Work

Use only when the user explicitly authorizes sensitive context.

Potential private overlays:

- `YOU_CAREER_PRIVATE.md` for sensitive career strategy, salary, relocation, and candidacy material.
- `YOU_PRIVATE.md` for non-career private context.

Do not infer, request, or load private overlays automatically.

## Privacy Rule

The default Context OS context should be safe for trusted AI collaboration but should not include unnecessary personal, family, health, salary, or sensitive employment details.

Private overlays may exist, but they are opt-in per task. If a task can be completed without private overlays, do not load them. By convention the real `*_PRIVATE.md` files are git-ignored so they are never committed or pushed.

## Verification Rule

Some facts are durable. Others are operational and should be verified before action.

Durable facts may remain useful for long periods:

- identity and professional background
- stable working preferences
- project purpose
- positioning rules
- recurring technical preferences

Operational facts should be treated as last-known state until checked:

- open PRs
- deployment state
- current blockers
- next actions
- source availability
- payment/auth settings
- production data
- live URLs or service status

Before taking consequential action based on operational facts, verify against the canonical project file or live source when available.

## Duplication Rule

Intentional repetition is allowed for durable, high-priority constraints, especially privacy rules, positioning rules, safety cautions, and working-style preferences.

Volatile operational details should have one canonical home, usually the relevant project-specific context file. Index files may summarize them, but should point to the project file for details.

If duplicated operational details conflict, do not average them and do not guess. Use the source-of-truth order and verify before acting.

## Unknown Tool Rule

If a tool-specific adapter does not exist, read `TOOL_ADAPTERS.md` and create a temporary self-adapter before beginning work.

Classify your capabilities, choose the smallest useful context bundle, and proceed without asking for the entire repo unless necessary.

## End-of-Session Rule

At the end of meaningful work, identify whether the session created durable context updates.

If yes, propose a concise patch to the appropriate file. Do not silently rewrite Context OS unless the user explicitly authorizes the change.
