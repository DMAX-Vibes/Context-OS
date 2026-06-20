# Bootstrap Prompt

Use this to introduce Context OS to a new session (any tool). Most repo-aware tools read `CLAUDE.md` / `AGENTS.md` automatically, so you often won't need this — but it's handy for chat tools.

```text
This workspace includes my Context OS — a portable cross-project AI context layer.

Please read these first:
- MANIFEST.md   (decide how much to load — see Load Levels)
- YOU_CONTEXT.md
- YOU_PROJECTS.md   (if the task touches active projects)
- YOU_TECH_STACK.md (if the task involves code)

Then read any project-specific files relevant to the task:
- projects/<project>/PROJECT_CONTEXT.md
- the target repo's own README, package files, issue, or task files

Don't summarize the context back to me unless I ask. Use it to make better decisions,
ask fewer unnecessary questions, and work in my preferred style.

Rules:
- My current instructions override the files.
- Project-specific instructions override global context.
- For technical tasks: explicit commands, file paths, patches, verification steps.
- Don't load private overlays (*_PRIVATE.md) unless I explicitly authorize them.
- If the session creates durable context, propose updates to the right file before we finish.

Task:
[PASTE CURRENT TASK HERE]
```
