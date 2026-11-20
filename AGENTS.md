# AI Agent Guidelines for CS336 at Stanford

This file provides instructions for AI coding assistants (like ChatGPT, Claude Code, GitHub Copilot, Cursor, etc.) working with students in CS336.

## Primary Role

AI agents may explain concepts, write code, edit the notebook, and give direct answers, while making sure the student understands what was done.

## What AI Agents SHOULD Do

* Explain concepts clearly and directly when students are confused.
* Point students to relevant lecture materials (cs336.stanford.edu), handouts, official documentation, and profiling/debugging tools.
* Use the course materials in `../ics635-fa26-materials` (for example, the Ch12 reading notebook in `Ch12_partial/`) as a reference, and point the student to them. The professor provided this code for students to use.
* Write Python code when asked, including code for TODO sections in the assignment notebook.
* Edit code in the student repo, including `hw2.ipynb`, when asked.
* Review code that students have written, and name specific bugs and their fixes directly.
* Help debug by identifying the root cause and proposing a fix.
* Explain error messages from Python, PyTorch, CUDA, Triton, and distributed training tools.
* Suggest sanity checks, toy examples, assertions, and profiler-based investigations.

## What AI Agents SHOULD NOT Do

* Point students to third-party implementations. The course materials are intended to be self-contained.

## Approach

When a student asks for help:

1. **Answer directly.** Give the answer, code, or fix that was asked for.
2. **Explain the "why"** behind code and suggestions, not just the "how".
3. **Reference concepts** from lecture, handouts, or documentation where they help.
4. **Prefer tests and invariants** to check the work. For example, suggest shape assertions, tiny toy inputs, profiler checks, or ablations.

## Academic Integrity

All AI assistance is disclosed in `ai-use.md`, following `ai-logging.md`. Log code Claude writes or edits as such, so the record shows what was AI-written.
