# Set up Context OS — start here

**New here? You don't fill these files in by hand.** Point your AI tool at this folder and say:

> **"Read SETUP.md and set up Context OS for me."**

That's it. The instructions below tell the AI how to interview you *briefly* and pre-fill everything from what it already knows about you, so you never start from a blank page.

Works with Claude Code, Codex, Cursor, ChatGPT, Gemini, or any agent that can read these files.

---

## Instructions for the AI assistant

You are setting up **Context OS** for this user: a portable Markdown context layer they'll reuse across every AI tool. Your job is to get them from an empty template to a filled-in, usable context system in one short conversation. **Do the work for them. Don't hand them homework.**

Read `README.md` and `MANIFEST.md` first so you understand the structure, the Load Levels, and the privacy model. Then follow this flow.

### Core principle: never start them blank

The whole point of Context OS is that the user should *not* type their life story into a blank file. **Pre-fill first, confirm second.** Before asking the user anything, gather what you already know about them from every source available to you, then draft the files and show your work. Only then ask about real gaps.

### Step 1 — Gather what you already know (don't ask yet)

Silently pull from whatever sources you have access to. Depending on your tool, that may include:

- **This conversation + any memory/personalization** you carry about the user.
- **Prior chats / saved memory** if your tool exposes them.
- **The current git repo** — run `git config user.name` / `user.email`, look at the README, recent commits, languages, and folder structure to infer their stack and active projects.
- **Connected accounts** — email, calendar, GitHub, docs, etc., *only* if already connected and clearly appropriate. Don't connect anything new without asking.
- **Anything the user pasted or pointed you at.**

Make a short internal list of what you found. Mark each fact as **known** (you're confident) or **inferred** (a guess to confirm).

### Step 2 — Draft the files from what you found

Create the `YOU_*.md` files and fill them in using the section structure already in each template. For every field:

- Write what you know.
- Tag guesses inline as `[inferred — confirm]`.
- Leave a clear `[unknown]` where you have nothing rather than inventing.

**Never fabricate** identity, employer, project, legal, financial, or biographical facts. An honest `[unknown]` is always better than a confident wrong guess.

Priority order — get `YOU_CONTEXT.md` solid first (it's the only required file), then `YOU_PROJECTS.md` and `YOU_TECH_STACK.md`. Treat `YOU_CAREER.md` / `YOU_CREATIVE.md` as optional.

**Per project:** for each active project the user has, copy `projects/example-project/` to `projects/<their-project>/` and fill in its `PROJECT_CONTEXT.md` and `CLAUDE.md`. Every project gets its own folder — that's how project context stays separated and doesn't bleed between unrelated work.

### Step 2b — clean up the scaffolding

A filled-in Context OS should not look like a half-finished template. After drafting:

- **Strip template furniture** from every file you filled in: the `> blockquote` setup notes at the top and the `<!-- HTML comments -->`. Leave only real content (and honest `[unknown]` markers for genuine gaps).
- **Delete `projects/example-project/`** once you've created at least one real project folder from it.
- **Delete optional modules the user doesn't need.** If they have no career or creative material, remove `YOU_CAREER.md` / `YOU_CREATIVE.md` rather than leaving placeholder files lying around.
- Leave the `*.example.md` private templates in place (they're the privacy scaffolding and stay tracked).

### Step 3 — Show your draft and ask only about gaps

Show the user the drafted `YOU_CONTEXT.md` (at minimum) and say something like: *"Here's what I already knew about you — does this look right?"*

Then ask a **small, targeted** set of questions — aim for 3–6, not an interrogation — covering only:

- the `[inferred — confirm]` items you're least sure about, and
- the `[unknown]` gaps that actually matter for how you'll work with them.

Do **not** ask about things you can already answer. Do **not** make them fill in every blank before the system is usable.

### Step 4 — Set up privacy correctly

- If anything sensitive came up (salary, family, health, sensitive career/employer strategy), put it in `YOU_PRIVATE.md` or `YOU_CAREER_PRIVATE.md` — **never** in the default files.
- Create those by copying the `*.example.md` versions to the real filename (e.g. `cp YOU_PRIVATE.example.md YOU_PRIVATE.md`).
- Confirm `.gitignore` already excludes the real `*_PRIVATE.md` files so they're never committed. Tell the user this is handled.
- If you have no sensitive material, skip this — don't manufacture private content.

### Step 5 — Wire up their tools and hand off

Briefly tell the user:

- **Claude Code** reads `CLAUDE.md` automatically; **Codex / coding agents** read `AGENTS.md`. No setup needed.
- For **other tools** (ChatGPT, Gemini, etc.), paste `prompts/handoff.md` plus the relevant `YOU_*.md` file at the start of a session.
- **End meaningful sessions** by pasting `prompts/session-end.md` ("did we learn anything durable?") so the context keeps itself current. Offer to do this for them at the end of *this* session as the first example.

### Step 6 — Confirm and stop

Summarize what you created, which files are still thin, and the one or two highest-value things they could add later. Keep it short. The system is meant to grow over time — they do **not** need a "complete" profile to start using it today.

---

### Setup checklist (for the AI)

- [ ] Read `README.md` + `MANIFEST.md`
- [ ] Gathered known/inferred facts from available sources (Step 1)
- [ ] Drafted `YOU_CONTEXT.md` (required) + others where possible (Step 2)
- [ ] Made a `projects/<name>/` folder per active project; stripped template furniture; deleted `example-project/` + unused optional modules (Step 2b)
- [ ] Showed the draft, asked only 3–6 gap questions (Step 3)
- [ ] Routed anything sensitive to `*_PRIVATE.md`, confirmed git-ignored (Step 4)
- [ ] Explained tool wiring + the session-end loop (Step 5)
- [ ] Summarized + stopped without demanding a "complete" profile (Step 6)
