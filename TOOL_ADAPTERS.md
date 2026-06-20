# Context OS Tool Adapters

Purpose: Guidance for adapting Context OS to different AI tools, coding agents, builders, and workflow systems.

## Core Principle

Context OS is the portable control plane. Individual tools are execution environments.

Do not assume every tool can read repo files, honor local instruction files, preserve memory, run commands, or write patches. First determine what the current tool can actually do, then load the smallest useful context bundle.

## Universal Adapter Rules

1. Current instructions from the user override all stored context.
2. Project-specific context overrides global context.
3. Private overlays are opt-in and must not be loaded unless the user explicitly authorizes them for the current task.
4. Prefer patches, PRs, or clearly marked replacement sections over silent context rewrites.
5. For technical work, provide exact commands, file paths, patches, and verification steps.
6. For operational project state, verify before taking consequential action.
7. At session end, propose durable context updates if needed.

## Unknown or Unsupported Tool

If your tool is not listed below, create a temporary self-adapter. Classify your capabilities across these dimensions: file read, file write, terminal/command execution, code inspection, web access, memory persistence, external API access, ability to honor local instruction files, trust level, and private-overlay policy.

Then choose a temporary mode:

- Read/write repo agent
- Read-only repo reviewer
- Conversational assistant
- UI / code generator
- Research assistant
- Automation / workflow runner
- Local / offline model
- Unknown / limited tool

Pick the smallest useful context bundle for that mode and proceed without asking for the entire repo unless necessary.

## Tool-Specific Adapters

**Claude Code** — entry point `CLAUDE.md`. Load: `CLAUDE.md`, `MANIFEST.md`, `YOU_CONTEXT.md`, `YOU_PROJECTS.md`, `YOU_TECH_STACK.md` for technical work, and the relevant project folder. Use for: repo-aware coding, patches, command sequences, project context updates, local troubleshooting.

**Codex / AGENTS.md-Compatible Coding Agents** — entry point `AGENTS.md`. Load: `AGENTS.md`, `MANIFEST.md`, and relevant project files before global context when doing project work. Use for: code review, implementation passes, PR review, repo-level patching. Do not assume another agent's earlier decisions are final.

**Cursor / IDE Assistants** — point at this folder as context. Load: `MANIFEST.md`, `YOU_CONTEXT.md`, `YOU_TECH_STACK.md`, and the relevant project file. Use repo-local instruction files if the IDE honors them.

**ChatGPT / Conversational Mode** — if a GitHub/file connector is available, fetch: `README.md`, `MANIFEST.md`, the relevant project file, and `YOU_CONTEXT.md` as needed. If not, ask the user for the smallest relevant pasted file or export bundle. Use for: strategy, drafting, analysis, review.

**Gemini or Other General Chat Models** — use pasted or connected context. Good for: critique, alternate framing, simplification, cross-model review, patch proposals.

**Perplexity / Web-Forward Research Tools** — use for: public URL verification, market/current-state research, public documentation checks, external source comparison. Do not let these tools rewrite private identity or career context unless the user explicitly asks.

**UI Builders (v0, Lovable, Bolt.new, etc.)** — paste a short bootloader prompt; include only relevant project context. After using: export or sync code to GitHub, reconcile generated output against project context, and update Context OS only with durable decisions.

**Local Models / Ollama / Offline Tools** — use a minimal bootloader, relevant project context, and compact global context only if needed.

**Automation Tools (n8n, cron agents, etc.)** — may read Context OS and propose updates. Should not silently commit or rewrite Context OS. Good uses: scheduled project status checks, PR summaries, deployment/watch notifications, proposed context update drafts, weekly digests.

**Hosted Knowledge Agents (Chatbase, custom GPTs, etc.)** — should consume curated exports from Context OS. Flow: `Context OS -> sanitized export bundle -> knowledge base`. Do not upload private overlays unless explicitly authorized.

**Stack-Specific Tools Not Yet Adopted** — add a temporary adapter or project note. Promote to durable context only after the user adopts it or repeatedly uses it.
