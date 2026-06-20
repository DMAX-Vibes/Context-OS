# Context Merge Prompt

Use this when two AI tools produced competing versions of a Context OS file and you need to reconcile them.

```text
I have two (or more) versions of the same Context OS file from different AI tools.

Merge them into one canonical version. Don't treat any version as primary just because it
came first or came from a particular model. Synthesize toward the clearest, most accurate,
most useful result.

You may add, remove, consolidate, reframe, or de-emphasize material. The outcome should be
substantially independent of the order the versions were created in (order-independent
convergence).

For anything that genuinely conflicts (not just wording):
- list the conflict
- say which version you kept and why
- flag it for me if you can't resolve it from the text alone

Return the merged file plus a short list of conflicts and decisions.
```
