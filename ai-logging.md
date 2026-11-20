# AI-Use Logging (ICS 635 Homework 2)

This assignment requires an `ai-use.md` file describing the tools used,
important prompts or requests, and how I checked their output. Follow this
logging protocol throughout the session.

## When to log

After any exchange where you (Claude) provide meaningful help — explaining a
concept, suggesting code, debugging an error, reviewing my implementation or
analysis — append an entry to `ai-use.md` in the repo root. Do this
proactively, without waiting for me to ask. Create `ai-use.md` if it doesn't
exist yet.

## Entry format

Keep a short **Tools used** section at the top of `ai-use.md` (tool name and
model, e.g. Claude Code / Claude Opus 5.5). Append entries in this format,
newest at the bottom:

```markdown
## [YYYY-MM-DD HH:MM]

**Context:** What notebook section/cell/problem we were working on.

**Prompt/request:** A short paraphrase of what I asked.

**What Claude did:** Explained a concept / suggested code / debugged an
error / reviewed logic or analysis — be specific about which.

**How I checked it:** How the output was verified (ran it, compared against
docs or lecture, sanity-checked numbers, etc.), or "Not yet checked."

**Outcome:** Did I use the suggestion as-is, adapt it, or reject it and
write my own version? Note any significant edits I made afterward.
```

## Reminders

- Log design discussions and debugging help, not just finished code
  Claude wrote — the assignment cares about *how* AI was used, not just
  final output.
- If I explicitly rewrite or diverge from a suggestion, note that in the
  Outcome field rather than leaving the entry looking like the suggestion
  was adopted unchanged.
- Keep entries honest and specific (e.g. "explained why the LoRA target
  modules affect trainable parameter count" is better than "helped with
  LoRA").
- This log only covers this Claude Code session. If I also used a separate
  chat tool (claude.ai, ChatGPT, etc.) for parts of the assignment, I'll
  paste those exchanges in manually — remind me if a gap seems likely.
