# AI Use — ICS 635 Homework 2

## Tools used

- Claude Code (Claude Opus 5.5)

## Log

## [2026-11-15]

**Context:** Repository and environment setup.

**Prompt/request:** Set up the repo from the provided `ics635-hw2-student.zip`
and copy over my usual AI-guideline/logging markdown files.

**What Claude did:** Extracted the zip into the repo root, removed a duplicate
copy of the assignment PDF, added a `.gitignore`, ran `uv sync --locked` to
create the environment, and copied `AGENTS.md`/`CLAUDE.md` from a previous
course repo, adapting `ai-logging.md` to log to `ai-use.md`. No assignment
code or analysis was written.

**How I checked it:** Confirmed the environment imports torch/transformers and
sees the GPU.

**Outcome:** Used as-is.

## [2026-11-15]

**Context:** Repository setup, `CLAUDE.md`.

**Prompt/request:** Use plain `@` imports in `CLAUDE.md`.

**What Claude did:** Changed `CLAUDE.md` from HTML-commented imports to plain
`@AGENTS.md` / `@ai-logging.md` lines.

**How I checked it:** Not yet checked (will confirm the files load in the next session).

**Outcome:** Used as-is.

## [2026-11-15]

**Context:** Repository setup, `AGENTS.md`.

**Prompt/request:** Allow the AI to run terminal commands in this repo (class
policy permits it).

**What Claude did:** Removed the "Run bash commands" line from this repo's
`AGENTS.md`. The ICS 483 copies were left unchanged.

**How I checked it:** Confirmed with grep that the line is gone.

**Outcome:** Used as-is.

## [2026-11-15]

**Context:** Notebook setup cells (data, tokenizer, helpers).

**Prompt/request:** Asked whether running all cells downloaded everything
needed, or whether other prep cells must be run.

**What Claude did:** Inspected the notebook outputs and the Hugging Face cache.
Confirmed the dataset and tokenizer were downloaded but the Qwen3-1.7B weights
were not yet, since the model is loaded in my own Section 3 code. No
assignment code was written.

**How I checked it:** Claude listed the cached files for the model and dataset.

**Outcome:** Informational.
