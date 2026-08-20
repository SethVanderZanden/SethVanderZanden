---
name: reading-documentation
description: Reads documentation in the title, short description, TLDR, Dummy Section, Deep Dive format. Use when reading project docs, markdown documentation, README sections in this format, or when asked to review, summarize, or consult documentation.
---

# Reading Documentation

Documentation follows a fixed scan-then-depth format. Understand this format when wanting to read documentation. Do not ingest a whole doc by default.

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

`title` + `short description` are a **120-character scan budget** (plain text only; do not count `#` or the newline). Those two lines are enough to decide whether the file is relevant before opening another section.

## What each part is for

| Part | Who it is for | What you get |
| --- | --- | --- |
| **Title + short description** | Everyone (scan) | Topic + one-line idea, ≤ 120 characters combined |
| **TLDR** | Human reading | Short factual summary |
| **Dummy Section** | Easy understanding | Dumbed-down explanation |
| **Deep Dive** | Agentic usage | Full context to act on |

## How to read

1. **Scan only the title and short description.** Stop there if the doc is irrelevant.
2. **Open exactly the section that matches the need:**
   - Human-facing summary, status, or "what is this?" → **TLDR**
   - Plain-language explanation, onboarding, "explain it simply" → **Dummy Section**
   - Implementing, debugging, or answering with full context → **Deep Dive**
3. **Do not read remaining sections** unless the chosen section is missing detail you still need.
4. If you must go deeper, climb one step: Dummy Section → TLDR is the wrong direction; Dummy Section → Deep Dive is the right one when accuracy matters.

## Matching the question to a section

- "What changed?" / "Give me the gist" / "Summarize for me" → TLDR
- "Explain this like I'm new" / "What's the simple version?" → Dummy Section
- "How does this work in the code?" / "What should an agent know?" → Deep Dive
- Listing or searching many docs → titles + short descriptions only

## When quoting or answering

Cite the section you used. Do not mix Dummy Section analogies into Deep Dive answers, and do not treat TLDR as complete technical context.

If a file is missing a heading, read what exists and say which section was absent.
