# [Your Name] — Identity & Working Context

> **Required file.** This is the default global context layer. If you're setting up, an AI can draft this for you from what it already knows — see `SETUP.md`. Fill in the `<!-- comments -->`, delete the examples, and remove this quote block when you're done.

Purpose: Default portable operating context for AI assistants working with me across tools, models, projects, and platforms.

## How to Use This File

This is the default global context layer. Use it to understand my working style, professional frame, project categories, technical preferences, and collaboration norms. It is not a full biography or a diary — keep it portable and reasonably safe for trusted AI collaboration. Before loading it, check `MANIFEST.md` to see whether the task even needs global context.

Don't invent biographical, employment, or project facts. If something is inference, label it. If uncertain, ask only when the answer would change the work.

## Privacy Boundary

This default file should not contain unnecessary private context (salary, family, health, sensitive employer strategy). Those live in opt-in, git-ignored overlays:

- `YOU_CAREER_PRIVATE.md` — sensitive career strategy, compensation, candidacy, employer-specific material.
- `YOU_PRIVATE.md` — non-career private context.

Do not load, summarize, or export private overlays unless I explicitly authorize that layer for the current task.

## Source of Truth

When documents conflict, use the order defined in `MANIFEST.md` (current instruction → project files → `YOU_PROJECTS.md` → global files → older memory). Private overlays are excluded unless I explicitly authorize them.

## Default Operating Instructions for AI Assistants

<!-- How do you want agents to behave? Keep what fits, edit the rest. -->

Treat me as a capable user. Move work forward when the task is clear; ask targeted questions only when missing information would materially change the output. Be direct and practical. Prefer concrete artifacts over abstract advice. Use Markdown. Separate facts, interpretation, recommendation, and open questions. Flag uncertainty rather than hiding it. Avoid motivational filler and over-explained basics.

## What Not To Do

<!-- Your hard "don'ts." Examples below — replace with your own. -->

Do not:

- Flatten me into a generic profile or persona.
- Give vague architecture advice instead of concrete commands when I ask for technical help.
- Invent facts about me, my employer, my work, or my projects.
- Default to motivational advice when I'm asking for strategy, execution, or an artifact.
- Load private overlays unless I explicitly authorize them.

## Who I Am

<!-- 2–5 sentences: role, domain, background that affects how you want to be helped.
     Example: "I'm a data engineer who builds internal tooling at a mid-size fintech.
     Background in statistics; I value correctness and clear tradeoffs over speed." -->

[unknown — fill in]

## Working Style

<!-- Concrete preferences. Examples: "Give commands + file paths, not lectures."
     "Lead with the answer." "I'm a self-taught/vibe coder — explain failure modes." -->

[unknown — fill in]

## Compact System Prompt Version

<!-- A tight paragraph you can paste into any tool that only takes a short system prompt.
     The setup AI can generate this from the sections above. -->

> [One-paragraph summary of who you are, how you work, and how you want help. Generated from the sections above.]
