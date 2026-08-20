---
name: writing-documentation
description: Creates documentation only after full completion as the last step with human intervention, using title, short description, TLDR, Dummy Section, and Deep Dive. Use when finishing work, when asked to write docs, README, or documentation, or when considering adding markdown documentation. Never write documentation mid-task.
---

# Writing Documentation

We only create documentation upon full completion as the last step with human intervention.

## Hard rule

Do not write, update, or scaffold documentation while work is in progress. Do not document as you go. Do not assume docs are wanted.

Documentation is allowed only when **all** of these are true:

1. The requested work is fully complete (implemented and verified)
2. Documentation is the last remaining step
3. The human has explicitly confirmed they want documentation written now

If work is complete and docs may be needed, stop and ask:

> Work is complete. Write documentation now in the standard format?

Wait for a yes. Then write.

**Override:** If the human explicitly asks to write documentation *now*, that *is* the human intervention. Write it in this format. Do not wait for a second confirmation.

This skill covers documentation files (markdown, README sections that follow this format, docs pages). It does not block ordinary code comments.

## Format

```markdown
# [title]
[short description]

## TLDR
[TLDR]

## Dummy Section
[Dummy Section]

## Deep Dive
[Deep Dive]
```

### Title + short description (scan budget)

`title` + `short description` together must be **≤ 120 characters**.

Count plain text only: the title text plus the short-description text. Do not count `#`, the space after `#`, or the newline between them.

These two lines are the scan layer. A reader should get the idea from those 120 characters before opening TLDR, Dummy Section, or Deep Dive.

- Title: specific topic name, not a sentence
- Short description: one line that states what this doc is about
- If over 120, cut the description first, then the title
- Verify the count before saving

### Sections

| Section | Audience | Content |
| --- | --- | --- |
| **TLDR** | Human reading | Short factual summary. What it is, what changed, what to do. No tutorial tone. |
| **Dummy Section** | Easy understanding | Dumbed-down explanation. Analogies, plain language, no required jargon. A newcomer should get it. |
| **Deep Dive** | Agentic usage | Full context: behavior, files, APIs, constraints, edge cases, commands, and anything an agent needs to act without rereading the repo. |

Do not merge sections. Do not omit a section. If a section is genuinely empty, write `None.` rather than deleting the heading.

## Write workflow

1. Confirm the three gates above (complete, last step, human said yes)
2. Draft title + short description; count characters; trim to ≤ 120
3. Write **TLDR** for a human who will not read further
4. Write **Dummy Section** as the dumbed-down explanation
5. Write **Deep Dive** with full agentic context
6. Re-count title + short description; save only if ≤ 120

One topic per file. Derive the filename from the title (kebab-case). Prefer an existing `docs/` location; do not create a new docs tree unless the human asked for one.

For filled-out samples, see [examples.md](examples.md).
