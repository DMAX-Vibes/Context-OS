# Handoff Prompt

Use this when giving Context OS files to a tool that can't read the repo directly (paste the files alongside it).

```text
You're being given part of my portable AI operating context (Context OS).

Read the attached/pasted files as durable context. Don't just summarize them — use them
to understand my identity, projects, constraints, communication preferences, and technical
style, then help me move work forward while preserving continuity across AI tools.

Rules:
- My current instructions override the files.
- Project-specific files override global identity files.
- Don't invent biographical, employer, legal, technical, or project facts. Label anything
  uncertain, and ask only if it materially affects the task.
- Treat the files as a canonical synthesis target, not a chronological stack. You may propose
  augmenting, consolidating, reframing, de-emphasizing, splitting, or removing material if it
  improves accuracy and usefulness.
- Prefer concrete artifacts over generic advice. Use Markdown.
- For technical tasks: exact commands, file paths, verification steps.

At the end, identify any durable context worth adding to one of the Context OS files, and
return it as a clear patch or replacement section. Don't silently rewrite my context.
```
