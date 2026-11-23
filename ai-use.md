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

## [2026-11-16 14:45]

**Context:** Planning compute for the whole notebook (no section code written yet).

**Prompt/request:** Asked how long running the assignment would take, and whether
it could run on my laptop while another project trains.

**What Claude did:** Read ASSIGNMENT.pdf (Compute and Fixed settings) and the
notebook outline, and checked the laptop GPU (RTX 2060, 6 GB). Explained that
Qwen3-1.7B loaded in float32 is ~7 GB of weights alone, so it cannot run on the
6 GB laptop GPU, and gave a rough per-section time estimate for the GPU Gateway.
No assignment code was written.

**How I checked it:** Not yet checked (compare against actual GPU Gateway timings).

**Outcome:** Informational.

## [2026-11-16 19:09]

**Context:** Orientation before starting Section 1 (no section code written yet).

**Prompt/request:** Asked for help getting oriented and figuring out what the
assignment requires.

**What Claude did:** Read ASSIGNMENT.pdf, README.md and the notebook outline,
then summarized the seven sections and their deliverables, the files to submit,
a suggested order of work (Sections 1–2 need no GPU; 3–7 need the GPU Gateway),
and things to watch for (keeping `test` out of every choice until Section 6,
padding side, saving intermediate results between long runs). Explained no
solutions and wrote no code.

**How I checked it:** Not yet checked (compare against ASSIGNMENT.pdf as I work
through each section).

**Outcome:** Informational.

## [2026-11-16 19:12]

**Context:** Section 1 (Inspect the data), before any code was written.

**Prompt/request:** Asked to start working on Section 1.

**What Claude did:** Broke Section 1 into its three tasks and asked guiding
questions for each: which fields of the label table matter, how to choose
tweets to read without cherry-picking, the label-id vs label-name format that
`score` expects, and predicting the always-neutral scores before computing
them. Explained conceptually why classes that are never predicted get an F1 of
0. Wrote no code.

**How I checked it:** Not yet checked.

**Outcome:** Informational; I'm writing the Section 1 code myself.

## [2026-11-16 19:15]

**Context:** Repository setup, `AGENTS.md`.

**Prompt/request:** Asked to loosen `AGENTS.md` so Claude can write code, edit
the notebook, and give direct answers instead of only guiding questions.

**What Claude did:** Rewrote `AGENTS.md`: removed the rules against writing
code, completing TODOs, editing the repo, and stating root causes and fixes,
and replaced the guiding-questions-only approach with direct answers plus
explanations. Kept the rule against pointing to third-party implementations,
and added a note that AI-written code must be logged as such in `ai-use.md`.

**How I checked it:** Not yet checked (review the new `AGENTS.md`).

**Outcome:** Used as-is.

## [2026-11-16 19:25]

**Context:** Repository setup, `AGENTS.md`.

**Prompt/request:** Allowed Claude to use and point me to the course materials in
`../ics635-fa26-materials` (professor-provided code) as a reference.

**What Claude did:** Added a line to `AGENTS.md` permitting this, and noted that
the Ch12 reading notebook (`Ch12_partial/`) is the main reference for
Sections 3–4 but has no data-exploration code relevant to Section 1.

**How I checked it:** Not yet checked.

**Outcome:** Used as-is.

## [2026-11-16 19:25]

**Context:** Section 1 (Inspect the data), notebook code cells.

**Prompt/request:** Asked for help with the initial data exploration.

**What Claude did:** Wrote the Section 1 code (AI-written), replacing the TODO
cell with three cells: (1) a pandas table of tweet counts and label
counts/percentages for all four splits; (2) a seeded (`SEED`) random sample of
8 `lora_train` tweets per label, with row indices for reference; (3) the
always-"neutral" scores on `selection` via the notebook's `score`. Ran the
setup + Section 1 cells in a scratch copy to verify, fixed counts displaying
as floats. Results: always-neutral on selection = accuracy 0.613, macro-F1
0.253 (F1 0 for negative/positive, 0.76 for neutral). Neutral is 61–67% of
every split.

**How I checked it:** Claude executed the cells in a scratch copy and checked
the counts sum to the split sizes and the sample is 8 per label. Still need to
run the cells in my own kernel and read the tweets myself.

**Outcome:** Not yet reviewed; analysis Markdown (two tweets I'd label
differently, macro-F1 argument) is still mine to write.

## [2026-11-16 20:05]

**Context:** VS Code / notebook environment.

**Prompt/request:** Asked why VS Code doesn't recognize the repo's `.venv`, and
reported the notebook seemed broken after Claude's edit.

**What Claude did:** Debugged: confirmed `hw2.ipynb` is valid JSON and passes
nbformat schema validation, and that the only change was Claude's Section 1
cells (edited on disk while the notebook was open in VS Code). Found in the VS
Code Jupyter logs that the notebook kernel was set to the ICS 635 HW1 venv
(`ics635hw1/hw1/.venv`), which lacks `datasets`, so the setup cells fail with
ModuleNotFoundError. Explained how to select this repo's `.venv` kernel.

**How I checked it:** Not yet checked.

**Outcome:** Not yet applied.

## [2026-11-16 20:10]

**Context:** VS Code could not open `hw2.ipynb`.

**Prompt/request:** Reported VS Code error "Could not initialize webview: Could
not register service worker: InvalidStateError".

**What Claude did:** Explained this is a VS Code webview service-worker cache
error, not a notebook-file problem, and gave the fix: quit VS Code and delete
`~/.config/Code/Service Worker`. Suggested `git stash` of `hw2.ipynb` as a
fallback.

**How I checked it:** Not yet checked.

**Outcome:** Not yet applied.

## [2026-11-16 20:15]

**Context:** VS Code Jupyter kernel selection for `hw2.ipynb`.

**Prompt/request:** Asked why VS Code won't use the repo's `.venv` as the
notebook environment.

**What Claude did:** Debugged from the VS Code logs and Jupyter kernelspecs.
Found the Python extension does detect and select `.venv` (ics635-hw2), but the
notebook is bound to user-level Jupyter kernelspecs left over from earlier work:
`ics635-hw1` (HW1 venv) and a `python3` spec that points to the lecture 2.0
venv. Both lack `datasets`. Their paths use `/var/home/...`, which the Python
extension doesn't match to its `/home/...` env list, so they show as
"not valid". Suggested selecting the `.venv` via Python Environments and
optionally removing the stale kernelspecs.

**How I checked it:** Not yet checked.

**Outcome:** Not yet applied.

## [2026-11-16 20:20]

**Context:** VS Code Jupyter kernel selection for `hw2.ipynb`.

**Prompt/request:** Asked Claude to remove the stale Jupyter kernelspecs.

**What Claude did:** Deleted `~/.local/share/jupyter/kernels/ics635-hw1` and
`~/.local/share/jupyter/kernels/python3` (registrations only; the HW1 and
lecture venvs were not touched).

**How I checked it:** Claude confirmed the user kernels directory is now empty.

**Outcome:** Applied.

## [2026-11-16 20:25]

**Context:** Section 1, understanding the primary metric.

**Prompt/request:** Asked what macro-F1 means.

**What Claude did:** Explained per-class precision/recall, F1 as their harmonic
mean, and macro-F1 as the unweighted mean over classes, worked through the
always-neutral selection result by hand (neutral F1 0.76, negative/positive
F1 0, macro-F1 0.253 vs accuracy 0.613), and explained why accuracy misleads
when ~61–67% of tweets are neutral. Pointed to the Module 3.0 Ch6 notebook's
macro-averaging section.

**How I checked it:** Not yet checked (compare hand calculation to the
notebook's `score` output and the Ch6 notebook).

**Outcome:** Informational.

## [2026-11-16 20:30]

**Context:** Section 2 (Establish baselines), before writing code.

**Prompt/request:** Asked what a TfidfVectorizer is and whether the course
materials cover it.

**What Claude did:** Searched `../ics635-fa26-materials`; it has no TF-IDF or
bag-of-words material, so pointed to the scikit-learn docs (Text feature
extraction user guide, TfidfVectorizer API). Explained bag of words, TF, IDF,
L2 normalization, how it pairs with LogisticRegression, and the main settings
to choose/record (ngram_range, min_df, sublinear_tf, how tickers/URLs are
tokenized), plus fitting the vectorizer inside a Pipeline on training data only.

**How I checked it:** Not yet checked (compare with the scikit-learn docs).

**Outcome:** Informational.

## [2026-11-16 20:35]

**Context:** Section 2 (Establish baselines), before writing code.

**Prompt/request:** Asked whether the course materials have example pipelines
to port.

**What Claude did:** Searched `../ics635-fa26-materials` and pointed to the
Ch6 notebook (Module 3.0) cell 9 `make_pipeline(StandardScaler(), PCA(),
LogisticRegression())` as the closest template, plus the Module 1.1 pipeline
notebooks. Listed the changes needed to port it: swap in TfidfVectorizer,
`class_weight="balanced"` and a higher `max_iter`, text input, label names as
targets, the notebook's `score` instead of `.score`, timing the fit with
`time.perf_counter`, and identical vectorizer settings across both training
sets. Wrote no notebook code.

**How I checked it:** Not yet checked.

**Outcome:** Informational.

## [2026-11-16 20:38]

**Context:** Section 2 (Establish baselines), imports.

**Prompt/request:** Asked for the imports needed for Section 2.

**What Claude did:** Provided the import lines (AI-written) in chat: `time`,
`TfidfVectorizer`, `LogisticRegression`, `make_pipeline`; noted pandas/score/
ID_TO_LABEL are already available from earlier cells. Did not edit the notebook.

**How I checked it:** Claude ran the imports in the repo `.venv` (scikit-learn
1.9.1) to confirm they work.

**Outcome:** Pending (I'll paste them into the Section 2 cell).

## [2026-11-16 20:45]

**Context:** Section 2 (Establish baselines), porting the Ch6 pipeline.

**Prompt/request:** Asked what PCA is (from the Ch6 example pipeline).

**What Claude did:** Explained PCA as dimensionality reduction into principal
components, what `PCA(n_components=2)` does in the Ch6 example, and why it (and
StandardScaler) are dropped from the TF-IDF → LogisticRegression baseline: the
assignment specifies that pipeline, and compressing word features would discard
word-level signal.

**How I checked it:** Not yet checked.

**Outcome:** Informational.

## [2026-11-16 21:15]

**Context:** Section 2 (Establish baselines), my first pipeline code (cell hw2-09).

**Prompt/request:** Asked whether my pipeline syntax was right (cell raised
`AttributeError: 'dict' object has no attribute 'lower'`).

**What Claude did:** Reviewed my code and debugged the error: I was passing the
whole Hugging Face `Dataset` to `.fit()`/`.predict()` (rows are dicts) and no
labels. Suggested the fix (AI-written lines): pass `["text"]` as X and label
names via `ID_TO_LABEL` as y, and `selection["text"]` to predict. Also pointed
out missing `class_weight="balanced"` and `max_iter`, and the remaining
deliverables (timing with perf_counter, scoring with `score`, results table,
recording identical vectorizer settings).

**How I checked it:** Not yet checked (re-run the cell).

**Outcome:** Pending.

## [2026-11-16 21:20]

**Context:** Section 2 (Establish baselines), cell hw2-09.

**Prompt/request:** Still getting errors after the previous fix.

**What Claude did:** Debugged `TypeError: 'builtin_function_or_method' object
is not subscriptable`: I had written `id[l]` (Python's built-in `id` function)
instead of `ID_TO_LABEL[l]`. Also pointed out `pipe_all`'s LogisticRegression
was missing `class_weight="balanced"` and `max_iter`.

**How I checked it:** Not yet checked (re-run the cell).

**Outcome:** Pending.

## [2026-11-16 21:30]

**Context:** Section 2 baselines / charting predictions (also relevant to Section 6).

**Prompt/request:** Asked how to chart the prediction results, reusing my HW1 chart code.

**What Claude did:** Found my HW1 plotting code (`ics635hw1/hw1/hw1.ipynb` cell 23:
ROC, precision-recall, 2×2 confusion matrix). Explained that ROC/PR don't port
(they need probabilities and binary labels; LLM outputs are label strings), that
Section 2 only requires a table, and how to port the confusion-matrix panel to
3 classes: `confusion_matrix(..., labels=LABELS)`, 3×3 loops, label-name ticks,
"unparsed" handling, and test-set titles for Section 6 methods 4 and 6.

**How I checked it:** Not yet checked.

**Outcome:** Informational.

## [2026-11-16 21:40]

**Context:** Porting my HW1 confusion-matrix code to HW2.

**Prompt/request:** Showed me the full HW1 plotting cell; asked for the
`confusion_matrix` import and what the HW1 thresholds were for.

**What Claude did:** Printed my HW1 cell 23; gave the imports
(`from sklearn.metrics import confusion_matrix`, `import matplotlib.pyplot as plt`).
Explained that HW1 thresholds converted predicted default probabilities into
0/1 decisions (chosen on validation), and that HW2 has no threshold because
`predict` and the LLM's parsed word already give a class label.

**How I checked it:** Not yet checked.

**Outcome:** Informational.

## [2026-11-16 21:45]

**Context:** Confusion matrix (Section 2 optional / Section 6 required).

**Prompt/request:** Asked how to create the confusion matrix.

**What Claude did:** Wrote (AI-written) a `plot_confusion(ax, gold, preds, title)`
function ported from my HW1 confusion-matrix panel: 3×3 with `labels=LABELS`,
an extra "unparsed" predicted column when needed, count annotations, label
ticks; plus a usage example. Ran it on a scratch TF-IDF baseline to confirm it
works (including the unparsed column). Did not edit the notebook.

**How I checked it:** Claude ran it in a scratch script and checked the plot.

**Outcome:** Pending (I'll paste it in).

## [2026-11-16 21:50]

**Context:** Section 2 training time (and later prediction/training timings).

**Prompt/request:** Asked for the manual definitions of the `time` functions.

**What Claude did:** Printed the Python 3.13 docstrings for `time.perf_counter`,
`perf_counter_ns`, `time`, `process_time` and `monotonic`, linked the official
`time` module docs, and explained why `perf_counter` is the right clock for
measuring durations (only differences are meaningful). Noted that later GPU
timings need `torch.cuda.synchronize()` before reading the clock.

**How I checked it:** Claude printed the docstrings from the repo `.venv`.

**Outcome:** Informational.

## [2026-11-16 21:55]

**Context:** Section 2 analysis (what each baseline tests).

**Prompt/request:** Asked what each TF-IDF baseline is testing.

**What Claude did:** Explained the purpose of each baseline conceptually: the
3,000-tweet baseline matches LoRA's training data (so it separates what the
pretrained LLM adds from what the labels alone give), and the 9,543-tweet
baseline uses all labeled data (how a cheap method scales with more labels, and
the strongest cheap competitor). Explained how to read the gap between them.
Did not write my Markdown analysis.

**How I checked it:** Not yet checked (compare with ASSIGNMENT.pdf Section 2 wording).

**Outcome:** Informational; I'll write the analysis cell in my own words.

## [2026-11-16 22:00]

**Context:** Section 2 analysis (interpreting the gap between baselines).

**Prompt/request:** Asked what counts as a "large" vs "small" gap.

**What Claude did:** Explained there is no fixed cutoff and the gap should be
judged against noise from a 600-tweet selection set (only 103 negative / 129
positive). Ran a scratch check with default TfidfVectorizer settings: macro-F1
0.677 (3k) vs 0.739 (9.5k), gap ≈ 0.06; a paired bootstrap (2,000 resamples,
seed 635) gave a 95% interval for the gap of about [0.025, 0.10], i.e. it
excludes 0. Suggested framing the gap relative to the always-neutral floor and
to the noise level, and optionally including a bootstrap interval.

**How I checked it:** Claude computed these in a scratch script; I still need
to confirm against my own notebook numbers.

**Outcome:** Informational.

## [2026-11-16 22:05]

**Context:** Section 2 results table.

**Prompt/request:** Asked how to get the selection macro-F1 for the baselines.

**What Claude did:** Showed (AI-written) how to call the notebook's `score` on
`lora_pred`/`all_pred` vs `selection_gold` and build a pandas table with the
training times, and explained what each column of `score`'s output means.

**How I checked it:** Not yet checked (run in my notebook).

**Outcome:** Pending.

## [2026-11-16 22:10]

**Context:** Section 2, interpreting confusion matrices.

**Prompt/request:** Asked how to read a confusion matrix and how it relates to
what each baseline tests.

**What Claude did:** Explained rows = true, columns = predicted, diagonal =
correct, and how to read per-class recall (row) and precision (column), using
the scratch TF-IDF 3k and 9.5k selection matrices (default vectorizer
settings). Pointed out the main error types (polar↔neutral confusions vs.
negative↔positive flips) and compared the two matrices to show where the extra
data helped.

**How I checked it:** Claude computed the matrices in a scratch script; I still
need to compare with my notebook output.

**Outcome:** Informational.

## [2026-11-16 22:15]

**Context:** Section 2 analysis (gap between baselines).

**Prompt/request:** Asked whether a 0.06 macro-F1 gap is "small".

**What Claude did:** Gave a judgment: modest but real, not small. It's outside
the noise (bootstrap 95% CI ≈ [0.025, 0.10]), but ~3.2× more data bought much
less than the first 3,000 tweets did over always-neutral (+0.06 vs +0.42),
pointing to diminishing returns. Suggested how to phrase it.

**How I checked it:** Based on the scratch numbers from earlier; not yet checked
against my notebook.

**Outcome:** Informational.

## [2026-11-20]

**Context:** Section 3 (Prompt the base model), before writing code.

**Prompt/request:** Asked whether there's reference code for Section 3.

**What Claude did:** Searched the course materials. Pointed to Ch3 (Module 4.0)
cells 8, 26, 29, 73 (loading a Qwen model, `apply_chat_template`,
`model.generate` with `do_sample=False`, timing) and Ch12 cells 120, 122–125
(loading with `device_map="auto", dtype=torch.float32`, pad token, greedy
generation). Noted none of them do batched generation, so the parts I need to
add are left padding, tokenizing a batch, slicing off the prompt tokens before
decoding, and looping over batches. Checked the Qwen3 tokenizer's pad token.

**How I checked it:** Claude printed the tokenizer's pad token and padding side.

**Outcome:** Informational.

## [2026-11-20]

**Context:** Section 3, porting Ch3 code.

**Prompt/request:** Asked whether we use a different Qwen model than the reference.

**What Claude did:** Confirmed: Ch3 uses Qwen2.5-0.5B-Instruct, the assignment
uses Qwen3-1.7B. Explained what changes when porting (model name, float32
loading, memory/speed, thinking mode turned off through `chat_prompt`, the
empty `<think>` block in the prompt, what "base model" means in the assignment).

**How I checked it:** Not yet checked.

**Outcome:** Informational.

## [2026-11-20]

**Context:** Section 3, batched generation code (cell hw2-12).

**Prompt/request:** Asked Claude to draft the generation function.

**What Claude did:** Wrote (AI-written) the model loading code, a
`generate(prompts, batch_size, max_new_tokens)` function (left padding, batched
tokenization, greedy `model.generate`, slicing off prompt tokens,
`batch_decode`), and a `run_prompt(template, tweets, batch_size)` helper that
fills a `{tweet}` placeholder with `str.replace`, builds prompts with
`chat_prompt`, times generation with `perf_counter` + `cuda.synchronize`, and
parses labels. Ported from Ch3 cells 8/29/55. Shared in chat; did not edit the
notebook.

**How I checked it:** Claude ran it on the laptop GPU in float16 (float32
doesn't fit in 6 GB) on 8 selection tweets: batched (size 4) outputs were
identical to one-at-a-time outputs, confirming left padding works. Still need to
run it in float32 on the GPU Gateway.

**Outcome:** Pending.

## [2026-11-20]

**Context:** Section 3, designing prompts.

**Prompt/request:** Asked what the zero-shot and few-shot prompts are supposed to do.

**What Claude did:** Explained zero-shot (instruction only) vs few-shot
(instruction plus labeled examples from `example_pool`), what the required
prompt pairs test (order sensitivity, example choice), what's worth varying
between prompts, and why the best zero-shot prompt matters for Section 4.
Explained conceptually; no prompts written for me.

**How I checked it:** Not yet checked (compare with ASSIGNMENT.pdf Section 3).

**Outcome:** Informational.

## [2026-11-20]

**Context:** Section 3, scoring prompts (cell hw2-13).

**Prompt/request:** Asked how to run a written prompt and score it.

**What Claude did:** Wrote (AI-written) a loop over a dict of prompt templates:
warm-up call, `run_prompt` on `selection`, `score` plus predicted-label counts
and time, saving each prompt's predictions/raw outputs to CSV as it goes, and a
combined results table; plus how to pick the best zero-/few-shot prompt by
macro-F1. Shared in chat; did not edit the notebook.

**How I checked it:** Not yet checked (needs the GPU Gateway).

**Outcome:** Pending.

## [2026-11-20]

**Context:** Section 3, building few-shot prompts.

**Prompt/request:** Asked how to build few-shot examples from `example_pool`.

**What Claude did:** Wrote (AI-written) `sample_examples(per_label, seed, exclude)`
(seeded, label-balanced sample from `example_pool`, shuffled so labels aren't
grouped, with an option to exclude previously used tweets) and
`few_shot_template(instruction, examples)` (Tweet/Answer format, collapses
newlines in tweets, ends with a `{tweet}` placeholder). Showed how to build the
required pairs: same set reversed (order pair) and a disjoint set of the same
size (different-examples pair). Explained balanced vs proportional sampling.

**How I checked it:** Claude ran the helpers on `example_pool` (no model):
the two sets don't overlap, the reversed template flips the order, and each
template has exactly one `{tweet}` placeholder.

**Outcome:** Pending.

## [2026-11-20]

**Context:** Section 3 cells hw2-12 (generation) and hw2-13 (prompts/scoring).

**Prompt/request:** Asked Claude to clean up the syntax in my active cell.

**What Claude did:** Edited the notebook directly (AI-edited): in hw2-13, renamed
`prompts` → `PROMPTS` (the loop used `PROMPTS`), un-nested the run/score loop
from the print loop (it re-ran everything per prompt and reset `rows`), renamed
my two prompts from `few_shot_*` to `zero_*` (they have no examples, and the
`few_` prefix gave them batch size 4 and the wrong category), and fixed the
"netural" typo in prompt 2. In hw2-12, moved decoding out of the `no_grad`
block, fixed indentation, and added `model.eval()`. Cleared stale outputs.
Explained the `NameError: generate` came from hw2-12 being interrupted during
model loading. Backup saved in the scratchpad before editing.

**How I checked it:** Claude validated the notebook schema and compiled both
cells; not yet run on the GPU.

**Outcome:** Pending (rerun hw2-12, then hw2-13).

## [2026-11-20]

**Context:** Section 3, running generation.

**Prompt/request:** Asked how long generation should take.

**What Claude did:** Checked the running kernel: it was on my laptop with the
model on the CPU (GPU memory unused, ~7.8 GB RAM, 2 GB free), which would make
generation very slow. Gave rough estimates for the GPU Gateway (zero-shot on 600
tweets ≈ under a minute to a few minutes; 12-shot several times longer) and
recommended stopping the laptop run and using the Gateway.

**How I checked it:** Claude read `nvidia-smi`, `free`, and the kernel process
stats. The Gateway estimates are rough and not yet checked.

**Outcome:** Informational.

## [2026-11-20]

**Context:** Section 3, running generation locally for drafting.

**Prompt/request:** Asked how to run on my local GPU to get draft results to
write from before moving to the GPU Gateway.

**What Claude did:** Suggested (AI-written) a switch in the model-loading cell:
float16 when the GPU has less than ~9 GB (laptop RTX 2060, 6 GB), float32
otherwise (Gateway), with a printed warning. Explained that draft numbers will
differ from float32 results, so all reported numbers and prompt choices must be
rerun on the Gateway; noted the kernel must be restarted to free RAM, and that
bf16 LoRA training won't work on the laptop's Turing GPU.

**How I checked it:** Earlier float16 test on the laptop GPU (8 tweets) worked;
this switch is not yet run.

**Outcome:** Pending.

## [2026-11-20]

**Context:** Compute planning for local drafting.

**Prompt/request:** Asked whether my RTX 3070 (Windows desktop) would work, and
whether I'd need a VM.

**What Claude did:** Checked the cached model size (3.9 GB in bf16, so about
7.8 GB in float32) and the pinned environment (torch 2.15 from PyPI). Explained
that the 3070's 8 GB can't hold the float32 model, so it can't do the required
float32 runs, but it works well for float16/bf16 drafting and supports bf16.
Recommended WSL2 over a VM (ordinary VMs don't get GPU access; WSL2 does) and
over native Windows (PyPI torch on Windows is CPU-only, which would break
`uv sync --locked`). Corrected my earlier "~7 GB" float32 estimate to ~7.8 GB.

**How I checked it:** Claude measured the safetensors size and read
`pyproject.toml`/`uv.lock`. The WSL2 setup is not yet tested.

**Outcome:** Informational.

## [2026-11-20 21:25]

**Context:** Loading Qwen/Qwen3-1.7B in `hw2.ipynb` under WSL2 on the RTX 3070.

**Prompt/request:** Asked whether the Qwen model was installed, whether running
the cell downloads it, and to double-check the GPU is being used.

**What Claude did:** Inspected the Hugging Face cache and explained that
`from_pretrained` downloads the weights from the Hub on first run. (Claude first
said the weights were missing; it had checked the snapshot folder mid-download.
The full ~3.9 GB was cached by 21:20.) Verified the GPU: `nvidia-smi` shows the
RTX 3070, and torch 2.15+cu132 reports `cuda.is_available() == True`. The
running kernel is using ~7.97/8.19 GB VRAM at 100% util. Warned that the
float32 load (~7.8 GB) with `device_map="auto"` likely offloads some layers to
CPU, and suggested checking `model.hf_device_map`.

**How I checked it:** Claude ran `nvidia-smi`, checked torch from the project
venv, and checked the cache sizes. The device map check in the notebook has not
been run yet.

**Outcome:** Informational; no code changes.

## [2026-11-20 21:30]

**Context:** Prompt-comparison cell (cell 19) in `hw2.ipynb`.

**Prompt/request:** Asked what the `selection_*.csv` files are.

**What Claude did:** Explained that cell 19 writes one checkpoint CSV per
prompt template in `PROMPTS` (columns text/gold/pred/raw over the 600
selection tweets), so a kernel crash doesn't lose finished runs. Summarized
the two files so far: zero_1 accuracy 0.622, zero_2 accuracy 0.525, with 73%
prediction agreement. zero_2 over-predicts "positive" (339/600).

**How I checked it:** Claude read the notebook source and loaded both CSVs
with pandas. The macro-F1 figures come from the notebook's own output table.

**Outcome:** Informational.

## [2026-11-20 21:35]

**Context:** Section 4 (Fine-tune with LoRA), cell 22, the training dataset.

**Prompt/request:** Asked how fine-tuning with the best zero-shot prompt works,
given `lora_train` already exists.

**What Claude did:** Explained the training-example format: `chat_prompt(best
zero-shot prompt filled with the tweet)` + label + `<|im_end|>\n`. Checked the
Qwen chat template ending (`<think>\n\n</think>\n\n`) and that the pad token
(`<|endoftext|>`) differs from `<|im_end|>`. Explained that SFTTrainer with
`dataset_text_field="text"` uses next-token loss over the whole sequence, what
LoRA freezes and trains, and right padding for training versus left for
generation. Suggested a draft of the dataset-building code for cell 22. Flagged
that the running cell 19 skipped `zero_3` (the kernel's `PROMPTS` predates
adding it), so the best zero-shot choice should wait until zero_3 runs. Noted
that float32 training (~9.3 GB) won't fit on the 8 GB 3070.

**How I checked it:** Claude printed the actual chat-template string and the
tokenizer's special tokens. The fixed settings come from ASSIGNMENT.pdf. The
draft code has not been run yet.

**Outcome:** Pending.

## [2026-11-20 21:45]

**Context:** Section 4, cells 22–24 (training dataset, LoRA training, save/reload/score).

**Prompt/request:** Write the full Section 4 pipeline locally, even though
float32 training won't fit on the 3070.

**What Claude did:** Wrote code (Claude-authored) for cells 22–24. It includes
a `train_lora(r, lora_alpha, ...)` function that Section 5 can reuse. It
measures time and peak memory, saves the adapter, and reports its size, and
the loss is plotted from `log_history`. Reload uses `AutoPeftModelForCausalLM`.
Found in the installed TRL 1.9.2 source (`sft_trainer.py` `add_eos`) that
SFTTrainer appends `<|im_end|>` to any `text` that doesn't already end with it.
Our examples end with `<|im_end|>\n`, so it would add a second `<|im_end|>`.
Claude pre-tokenized the dataset (`input_ids` column), which makes TRL skip that
step, and decoded the example to confirm the ending. Added a `DEV_RUN` flag
(bf16 load, 64 examples) for smoke-testing on the 8 GB card. Noted that TRL
1.9's SFTConfig enables gradient checkpointing by default.

**How I checked it:** Claude checked the SFTConfig/SFTTrainer signatures and
the dataset-prep source in the installed versions (trl 1.9.2, peft 0.20.0,
transformers 5.14.1). The code has not been run yet (cell 19 still running).

**Outcome:** Pending.

## [2026-11-20 21:55]

**Context:** Section 5 (Compare LoRA settings), cells 27–28, plus a revised cell 24.

**Prompt/request:** Write the Section 5 comparison too, so the whole notebook
can run unattended.

**What Claude did:** Wrote code (Claude-authored). A `score_adapter` helper
(in cell 24) reloads a saved adapter with `AutoPeftModelForCausalLM`, scores
it on selection, saves the outputs, and frees GPU memory. Cell 27 loops over
the four remaining (r, lora_alpha) settings using `train_lora`, saving
`lora_runs.csv` after each run. Cell 28 shows the five-run table and plots
macro-F1 against rank (log axis) with the two required lines, plus the loss
curves. Advised stopping before Section 6 to fill in the checklist, choosing
the zero-shot prompt by macro-F1 rather than hard-coding it, and setting
`DEV_RUN=False`.

**How I checked it:** Checked against the assignment's Section 5 table and
deliverables. The code has not been run yet.

**Outcome:** Pending.

## [2026-11-20 22:05]

**Context:** Section 6 (Evaluate once on the test set), cells 33–34.

**Prompt/request:** Continue writing the code that evaluates on the test set.

**What Claude did:** Wrote code for cells 33–34 (Claude-authored). Cell 33
records the final choices at the top: `few_A` as the best few-shot prompt,
because it has the best selection macro-F1 (0.732). The LoRA setting is a
placeholder (r=64, alpha=32) until Section 5 runs. The cell asserts that the
adapter exists and that `DEV_RUN` is off. It predicts `test` with all six
methods (always-neutral, both Section 2 TF-IDF pipelines without refitting,
best zero-shot, best few-shot, and the LoRA model reloaded from its adapter
with the zero-shot prompt) and times each one. It warms up the GPU before
timing and rewrites `test_predictions.csv` after each method. Cell 34 reloads
the CSV (with `keep_default_na=False`) and computes the comparison table with
seconds per 1,000 tweets. It also draws the two test confusion matrices with
the existing `plot_confusion`. Claude computed the selection macro-F1 for each
prompt from the saved `selection_*.csv` files to back the few-shot choice.

**How I checked it:** Claude syntax-checked both cells. They have not been run
yet, because the adapters don't exist until Sections 4–5 run.

**Outcome:** Pending.

## [2026-11-20 22:10]

**Context:** Section 7 (failure analysis) and remote-run setup.

**Prompt/request:** Asked whether Section 7 analysis can proceed normally after
the test run, and where the SSH setup for running on another machine was.

**What Claude did:** Explained that Section 7 may read `test` errors and define
slices by tweet features, as long as nothing feeds back into prompts or
models. Searched for the SSH setup and found no record of it in this repo,
`ai-use.md`, or Claude memory. The only SSH state is a `known_hosts` entry.

**How I checked it:** Claude searched the repo files, `~/.ssh`, and
`.devcontainer/devcontainer.json`.

**Outcome:** Informational. The SSH setup must have happened in another
session or tool, so it is missing from this log.

## [2026-11-20 22:28]

**Context:** Section 5, cell `hw2-21` (`score_adapter`): CUDA out-of-memory error while reloading the r=64 adapter.

**Prompt/request:** Pasted the CUDA OOM traceback.

**What Claude did:** Debugged the error. Cell `hw2-18` (the older Section 4 reload cell) left a float32 LoRA model in the global `model`. `score_adapter` loaded a second float32 copy before the old one was released, and two copies (~8 GB each) don't fit on the 20 GB GPU. Claude edited `score_adapter` to delete any existing global `model` and call `free_gpu()` before loading. Claude also suggested clearing the leaked memory without restarting the kernel.

**How I checked it:** Not yet checked. Claude confirmed with `nvidia-smi` that the kernel held ~18.7 GB and found the error in cell `hw2-21`'s saved output.

**Outcome:** Claude wrote the fix to `score_adapter`.

## [2026-11-20 22:35]

**Context:** Section 4, cell `hw2-18` (old adapter reload cell).

**Prompt/request:** Asked Claude to delete one of the two duplicate adapter reload/score cells.

**What Claude did:** Deleted `hw2-18`, which leaked the float32 model and caused the OOM. It kept `hw2-21` (`score_adapter`, top of Section 5), which frees the model after scoring.

**How I checked it:** Not yet checked.

**Outcome:** Accepted as-is.

## [2026-11-20 23:18]

**Context:** Section 5 → 6. Saving state for laptop use, reading the LoRA settings table, and a second CUDA OOM in cell `hw2-26`.

**Prompt/request:** (1) Asked for cells that save the Section 6 results so Section 7 can run on a laptop. (2) Asked how to read the scores and choose the final model. (3) Pasted a second CUDA OOM error.

**What Claude did:** (1) Wrote two cells to paste: one saves `test_seconds`, `METHODS`, the final choices and the results tables to `section6_state.json` and CSVs; the other reloads them at the start of Section 7. (2) Explained macro-F1 versus accuracy, per-class F1 and the cost columns in the Section 5 table. Pointed out that the final setting must be chosen on `selection` (Section 5), not on test. Noted that scaling mattered more than rank, and that the top three settings are within ~0.01 of each other, likely within noise. Recommended keeping r=64, α=32 under the "highest selection macro-F1" rule. (3) Debugged the OOM: `hw2-26` was interrupted during the LoRA test run and then re-run. The interrupted run's LoRA model was still in the global `model` when the re-run loaded the base model, so two float32 copies were on the GPU. Suggested freeing `model` at the top of `hw2-26`.

**How I checked it:** I pasted both save/load cells into the notebook. Not yet run.

**Outcome:** Pasted the save/load cells as written. The `hw2-26` fix is pending.

## [2026-11-22]

**Context:** Write-up pass after the GPU runs; reviewing my Section 1 and 2 analysis drafts.

**Prompt/request:** Asked to go back through the code and write up the analysis
responses together so I understand the content.

**What Claude did:** Surveyed the notebook (Sections 1–6 run; Section 7 code not
yet run; analysis cells for 3–7 and the pre-test checklist still TODO).
Reviewed my Section 1 and 2 drafts: noted my label definition describes tone
rather than outlook (the assignment's key distinction), the missing macro-F1
paragraph, leftover TODO lines, typos, and that Section 2 should state the
vectorizer settings. Gave feedback only; did not rewrite my text.

**How I checked it:** Not yet checked.

**Outcome:** Pending (I'll revise my drafts).

## [2026-11-22]

**Context:** Section 3 analysis (interpreting the prompt results table).

**Prompt/request:** Shared my expectations (zero_1 best because it's neutral and
declarative; few-shot order changes probably wouldn't matter much) and asked to
work through the results.

**What Claude did:** Read my prompt results and selection CSVs and walked
through what they show: all zero-shot prompts under-predict neutral (202/132/29
vs 368 true) and over-predict positive; the order pair moved macro-F1 by 0.07,
with the reversed order (ending on two positive examples) predicting positive
249 vs 132 times, consistent with recency bias; the different-examples pair
differed by 0.10; few-shot fixed most of the neutral problem; unparsed few-shot
outputs were synonyms like "favorable"/"weakness"; few-shot cost ~3.5× the time.
Compared with the TF-IDF baselines. Left the write-up to me.

**How I checked it:** Claude computed the unparsed breakdown from
`selection_few_*.csv`; other numbers are from my notebook output.

**Outcome:** Pending (I'll write the Section 3 analysis).

## [2026-11-22]

**Context:** Section 3 analysis cell (hw2-14), my draft.

**Prompt/request:** Asked for a sanity check on my answer to "which two prompts
you chose and why".

**What Claude did:** Reviewed my draft. Confirmed zero_1 and few_A are the
correct picks (highest selection macro-F1 in each group), and pointed out the
answer states the choice but not the reason: say they were chosen on selection
macro-F1 (with numbers), not on accuracy or test, and that zero_1 is then the
Section 4 training prompt. Also flagged in the rest of the cell: a leftover TODO
line, the "netural" typo, "trained prediction results" (the base model is
untrained here), and an unsupported sentence about the label being next to the
tweet. Also noted a stale TODO comment in cell hw2-16.

**How I checked it:** Compared my draft against `prompt_results.csv`.

**Outcome:** Pending (I'll revise my answer).

## [2026-11-22]

**Context:** Section 4 analysis (LoRA fine-tuning), before I write it.

**Prompt/request:** Moved on to Section 4 and asked to work through it.

**What Claude did:** Read my Section 4 code and outputs and the loss plot, and
explained the three analysis questions using my numbers. (1) What's trained:
low-rank A/B matrices on the 7 projection modules in all 28 layers; base
weights, embeddings, norms and LM head frozen. Verified 69,730,304 trainable
params by hand from Qwen3-1.7B's layer shapes (r × (in + out) per module).
(2) Why the adapter is small: 69.7M params × 4 bytes = 279 MB vs ~6.9 GB for
the frozen weights. (3) Loss curve: fast drop 5.18 → ~1.5 in ~25 steps, then
flat around 1.3–1.5. Checked TRL's source: with a plain "text" dataset the
loss covers every token (prompt + tweet + label), not just the label, so the
plateau mostly reflects unpredictable tweet text. Selection scores (0.848 vs
0.627 for the same prompt untrained) are the evidence the label was learned.

**How I checked it:** Hand calculation matches the notebook's trainable count
exactly; adapter size matches params × 4 bytes; TRL behaviour read from
`trl/trainer/sft_trainer.py` in the repo `.venv`.

**Outcome:** Pending (I'll write the Section 4 analysis).

## [2026-11-22]

**Context:** Section 4 analysis (model size / trainable percentage).

**Prompt/request:** Asked whether "module" is the right term, and how many
parameters Qwen3-1.7B has.

**What Claude did:** Explained "module" (PyTorch `nn.Module`; PEFT's
`target_modules`) and alternatives ("linear layer", "projection", "weight
matrix"). Counted Qwen3-1.7B's parameters from its config on the meta device:
1,720,574,976 unique (311,164,928 embedding, tied with the output layer;
1,409,410,048 non-embedding). Showed that this plus 69,730,304 LoRA params
reproduces the notebook's 3.895%, and explained why the assignment's "about 2
billion" counts the tied output layer twice.

**How I checked it:** Claude computed the count from the model config; it
reproduces the notebook's trainable percentage.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 4 analysis (why the adapter is small; what LoRA trains).

**Prompt/request:** Asked for a table comparing the full Qwen3 weight matrices
with LoRA's A and B matrices, and why LoRA uses two matrices.

**What Claude did:** Read the weight shapes from Qwen3-1.7B's config (meta
device) and built a per-module table at r=64: full W size vs A (r × in) and
B (out × r), with ratios (10.7×–24× per module, 20.2× per layer; 1.41B frozen
vs 69.7M trainable across 28 layers). Explained the low-rank factorization
(A compresses to r numbers, B expands back; B·A has the same shape as W but rank
≤ r), why one r-sized matrix can't do this, and the zero-initialized B.

**How I checked it:** Shapes and counts computed from the model config; totals
match the notebook's trainable count.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 4 analysis (interpreting the loss curve).

**Prompt/request:** Asked whether the loss plateau and the lack of an overfitting
check are a result of how training was set up.

**What Claude did:** Explained yes, both follow from the configuration the
assignment fixes: (1) a plain `"text"` dataset (`dataset_text_field="text"`)
makes TRL compute loss on every token (prompt + tweet + label); a
prompt/completion dataset would compute loss on the label only; (2) the
SFTConfig has no `eval_dataset`/evaluation strategy, so only training loss is
logged. Explained what changing each would show and why to keep the fixed
settings and note it as a limitation. Checked the Ch12 notebook uses the same
text-field setup.

**How I checked it:** TRL source (`sft_trainer.py`) and grep of the Ch12 notebook.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 4 → 5/6 (loss setup).

**Prompt/request:** Asked whether Sections 5 and 6 "fix" the all-token loss and
missing held-out loss.

**What Claude did:** Corrected the misunderstanding: nothing is broken and no
later section changes it. Section 5 keeps every training setting fixed except
r/lora_alpha (same all-token loss); Section 6 scores on test after training,
which is held-out evaluation of predictions, not a held-out loss curve during
training. Explained that selection/test scores are the intended evidence.

**How I checked it:** Against ASSIGNMENT.pdf Sections 5–6.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 4 analysis cell (hw2-19), my draft.

**Prompt/request:** Asked for a review of my Section 4 analysis.

**What Claude did:** Reviewed my draft. Flagged factual errors: LoRA here
targets the 7 projection modules, not the LM head (which stays frozen, as my
next sentence says); A compresses the layer's input vector, not "the incoming
weights"; "learning rate drastically decreases" should be the loss; "epochs"
should be optimizer steps (one epoch = 375 steps). Suggested adding the
adapter's on-disk size (279 MB vs ~6.9 GB) to answer "why is the adapter
smaller", and the plateau explanation plus the 0.627 → 0.848 selection
evidence to the loss paragraph. Listed typos. Did not rewrite my text.

**How I checked it:** Compared against my notebook outputs and the PEFT config.

**Outcome:** Pending (I'll revise).

## [2026-11-22]

**Context:** Section 5 analysis (LoRA settings), before I write it.

**Prompt/request:** Moved on to Section 5 and asked to work through it.

**What Claude did:** Read `lora_runs.csv`, the rank plot and loss curves, and
`section6_state.json`. Walked through the four analysis questions with my
numbers: separating rank from scaling (at scaling 0.5, r 4→64 gave
0.805→0.848; at lora_alpha=32 the line is nearly flat, 0.838→0.848; at r=4,
scaling 8 vs 0.5 gave +0.033), linking this to the slower loss drop of the
low-scaling runs; cost (params/adapter size scale with r, 4.4M–69.7M,
17.5–279 MB; train time ~flat at ~610 s; peak memory 12.9–16.4 GB; alpha
changes no cost). Pointed out that Section 6 already used r=64/alpha=32, so
the stated rule must be "highest selection macro-F1", with r=4/alpha=32 as
the within-noise smaller alternative to discuss but not switch to after
seeing test. Explained single-seed and 600-tweet limits. Flagged plot tick
clutter and a stale TODO comment.

**How I checked it:** Numbers from `lora_runs.csv` and the saved plot; final
choice from `section6_state.json`.

**Outcome:** Pending (I'll write the Section 5 analysis).

## [2026-11-22]

**Context:** Section 5 analysis (reading the loss curves and rank plot).

**Prompt/request:** Asked whether lora_alpha=32 "optimizes the loss" and r=64
"optimizes selection", and whether the meeting point at r=64 implies
diminishing returns.

**What Claude did:** Partly confirmed and corrected. Confirmed the three
lora_alpha=32 runs share the same loss curve, and **corrected Claude's own
earlier explanation**: training speed tracks lora_alpha itself, not the scaling
α/r (r=64 at scaling 0.5 trains as fast as r=4 at scaling 8). Explained why
with Adam (per-parameter steps of roughly constant size, so B·A grows with r
and the α/r factor cancels it, leaving α). Explained that the lines meet at r=64
by construction (same run), not as a finding; that r=64's selection lead over
r=16/r=4 at α=32 (0.003/0.010) is within noise; and that the fixed-α line is
consistent with flat or diminishing returns from rank, but this can't be
confirmed from these data.

**How I checked it:** Compared final losses and selection scores in
`lora_runs.csv` by α.

**Outcome:** Informational; earlier "scaling" framing replaced with "α".

## [2026-11-22]

**Context:** Section 5 (LoRA hyperparameters).

**Prompt/request:** Asked what r and α (lora_alpha) actually are.

**What Claude did:** Defined each LoRA variable with my numbers: W (frozen
weight), A and B (trained matrices), r (rank: the bottleneck width / number of
directions the update can use, which sets parameter count and adapter size),
lora_alpha (a fixed multiplier on the update's strength, not trained, no cost),
scaling α/r, and lora_dropout. Related them to the LoraConfig in my notebook.

**How I checked it:** Against the PEFT LoraConfig printed in my notebook.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 5 analysis (rank vs scaling).

**Prompt/request:** Asked how to describe what rank and scaling each do.

**What Claude did:** Summarized rank's and scaling's effects on score and cost
as a 2×2 framing with my numbers (rank: little score effect at fixed α,
linear cost; scaling/α: most of the score differences via training speed in
one epoch, zero cost), with suggested sentences for the write-up.

**How I checked it:** Numbers from `lora_runs.csv`.

**Outcome:** Pending (I'll write it in my own words).

## [2026-11-22]

**Context:** Section 5 analysis (single seed / 600-tweet limits).

**Prompt/request:** Asked whether the conclusion is that, with this small
dataset, we can't pin down the best setting.

**What Claude did:** Confirmed with refinements: separated the two sources of
uncertainty (evaluation noise from the 600-tweet selection set, not the
training data; and training variance from a single seed), stated what the data
do support (r4_a2 genuinely worse, backed by both its score gap and its loss
curve; every LoRA run far above prompting and TF-IDF) and what they don't
(ranking among the top four runs, 0.833–0.848), and what would resolve it
(several seeds per setting, a larger evaluation set, bootstrap intervals).

**How I checked it:** Gaps compared with the earlier bootstrap noise estimate.

**Outcome:** Pending (I'll write it in my own words).

## [2026-11-22]

**Context:** Section 5 analysis cell (hw2-23), my draft.

**Prompt/request:** Asked for a review of my Section 5 analysis.

**What Claude did:** Reviewed my draft. Flagged: r and α swapped in the opening
definition; a claim that higher rank costs more compute time (my data show
training time flat at ~610 s; the cost is parameters, size and memory); "32 is
the best scaling" (32 is α; scaling is α/r); "highest learning rate" (the
learning rate was fixed); missing the cost of scaling (none); the single-seed /
600-tweet limits only touched in one clause; a duplicated paragraph; the
choice rule should name selection macro-F1; typos. Did not rewrite my text.

**How I checked it:** Compared against `lora_runs.csv`.

**Outcome:** Pending (I'll revise).

## [2026-11-22]

**Context:** Checklist before Section 6 (final choices table).

**Prompt/request:** Asked Claude to pull the final configuration details and
selection scores from the notebook for the checklist table.

**What Claude did:** Read the TF-IDF code (cell hw2-09), `baseline_results.csv`,
`prompt_results.csv`, `lora_runs.csv` and `section6_state.json`, and produced a
pastable Markdown checklist table with each final configuration and its
selection macro-F1.

**How I checked it:** Values copied from the saved result files.

**Outcome:** Pending (I'll paste it into the checklist cell).

## [2026-11-22]

**Context:** Section 5 analysis (score vs cost; limits).

**Prompt/request:** Confused about the "score and cost" comment and still
didn't understand the single-seed / 600-tweet limits.

**What Claude did:** Clarified that the question asks for both knobs' effect on
both score and cost, and that the only missing piece in my draft was scaling's
cost (none). Re-explained the limits with plain analogies (a short quiz and a
single dice roll) and a concrete anchor (0.01 accuracy = 6 of 600 tweets).

**How I checked it:** Arithmetic on the selection set size.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 6 analysis (test results), before I write it.

**Prompt/request:** Moved on to Section 6 and asked to work through it.

**What Claude did:** Read `test_results.csv` and recomputed both confusion
matrices from `test_predictions.csv`. Walked through the three analysis
questions: (1) selection vs test (every method within ~0.01–0.04; the chosen
prompts dropped most, ~0.035, consistent with picking the best of several on
selection; identical method ranking on both sets; test is 3× larger so less
noisy); (2) confusion-matrix changes from zero-shot to LoRA (neutral tweets
misread as positive/negative fell from 618 to 82; neg↔pos flips 25 → 10;
polar tweets missed as neutral rose from 80 to 119; negative precision 49% →
82%); (3) ranking with gaps and prediction cost per 1,000 tweets.

**How I checked it:** Confusion matrices recomputed with sklearn from the CSV;
other numbers from my saved results.

**Outcome:** Pending (I'll write the Section 6 analysis).

## [2026-11-22]

**Context:** Section 6 analysis cell (hw2-28), my draft.

**Prompt/request:** Asked for a review of my Section 6 analysis.

**What Claude did:** Reviewed my draft against `test_results.csv` and the
recomputed confusion matrices. Flagged: "decreased accuracy after the full
training" (it's macro-F1, selection vs test, no extra training); "larger
dataset" reasoning (test set is simply 3× larger than selection); neutral
errors after LoRA are 82, not 92; the +26/+13 polar→neutral increases are for
negative/positive, not positive/neutral; "negative recall 284→279" is actually
positive correct counts (negative is 199→182); +0.19 is vs TF-IDF on 3,000
tweets, not the untrained model (+0.251 vs zero-shot); TF-IDF isn't
"untrained"; the final sentence about TF-IDF loss curves is incorrect (TF-IDF
has no loss curve here); times need "per 1,000 tweets"; missing why the chosen
prompts dropped most and that the ranking is unchanged. Did not rewrite my text.

**How I checked it:** Numbers checked against my result files.

**Outcome:** Pending (I'll revise).

## [2026-11-22]

**Context:** Setting up Section 7 without disturbing Section 1–6 outputs.

**Prompt/request:** After accidentally rerunning a cell (and fixing it myself),
asked which cells to run to set up Section 7. Claude had also committed the
notebook as saved at 18:20.

**What Claude did:** Verified the saved result files (`section6_state.json`,
`test_results.csv`, `test_predictions.csv` and the other CSVs) are unchanged
since the GPU-run commit 2034538 (11-20), so the test timings are intact.
Listed the minimal cells to run for Section 7 (the three Setup cells, then the
Section 7 resume cell) and the cells not to run (the save-state cell, which
would overwrite the saved timings, plus any Section 3–6 generation/training
cells).

**How I checked it:** `git diff` of the result files against commit 2034538.

**Outcome:** Pending.

## [2026-11-22]

**Context:** Section 7 (failure analysis), planning before writing code.

**Prompt/request:** Asked to discuss Section 7.

**What Claude did:** Explained the three parts (slices, tweets every method
got wrong, recommendation). Ran a scratch preview on `test_predictions.csv`
(not in the notebook) of five candidate slices ($ticker, link, cut off,
≤ 8 words, has a number), with n, class counts, macro-F1 for methods 3/4/6,
and a bootstrap 95% interval (500 resamples, seed 635) for LoRA's lead over
TF-IDF-9,543 in each slice and its complement; and the all-wrong count for
methods 2–6 (45 tweets). Summarized where LoRA's lead grows/shrinks and which
differences the intervals can't separate.

**How I checked it:** Scratch computation from the saved CSV; to be reproduced
in my notebook cells.

**Outcome:** Pending.

## [2026-11-22]

**Context:** Section 7 code (cells hw2-30, hw2-31, and a new marks cell).

**Prompt/request:** Asked Claude to draft the Section 7 code.

**What Claude did:** Drafted (AI-written), in chat for me to paste: (1) a slice
table for four yes/no slices ($ticker, link, cut off, ≤ 8 words): n and class
counts, macro-F1 for methods 3/4/6 in each slice and the rest, LoRA's lead over
methods 3 and 4, and a 95% bootstrap interval (1,000 resamples, seed 635) for
the lead over method 3; (2) the tweets methods 2–6 all got wrong (45), a
seed-635 sample of 15 with every method's prediction, and a printed template
for my marks; (3) a marks cell that validates my marks and counts them. The
mislabeled/ambiguous/hard marks and reasons are left for me to write.

**How I checked it:** Claude ran all three cells in a scratch script against
`test_predictions.csv` (slice cell ~55 s); outputs matched the earlier preview.

**Outcome:** Pending (I'll paste, run, and write my own marks).

## [2026-11-22]

**Context:** Section 7 marks cell.

**Prompt/request:** Asked whether each tweet gets just one of the three marks.

**What Claude did:** Confirmed one mark per tweet plus a one-line reason, and
gave a decision order for choosing between mislabeled, ambiguous and hard.
Did not mark any tweets.

**How I checked it:** Against ASSIGNMENT.pdf Section 7 wording.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 7, purpose of the all-wrong marks.

**Prompt/request:** Asked what the marks are for, and whether they're just
subjective.

**What Claude did:** Explained the purpose (finding out what the remaining
errors say about the labels and the task, and feeding that into the
recommendation), that subjectivity is expected and is itself a finding, how to
keep marks consistent (one stated rule), and how each mark count would be
interpreted in the analysis and recommendation.

**How I checked it:** Against ASSIGNMENT.pdf Section 7.

**Outcome:** Informational.

## [2026-11-22]

**Context:** Section 7 marks cell (my 15 marks).

**Prompt/request:** Asked for a check of my marks.

**What Claude did:** Checked each mark's reason against the mark definitions and
the gold label (did not change any marks). Flagged where a reason and mark
disagree: 861, 1167 and 1063 are marked ambiguous but the reasons argue for the
gold label (fits "hard"); 910's reason concludes "neutral" against gold
negative (fits "mislabeled", or "hard" if I accept negative); 1483 is marked
hard but the reason describes mixed signals (fits "ambiguous"); 203's reasoning
("margins suffering is neutral") is weak under the outlook rule. Noted the cell
hasn't been run yet and two typos.

**How I checked it:** Compared each reason with the gold label from `test_predictions.csv`.

**Outcome:** Pending (marks are my decision).

## [2026-11-23]

**Context:** Section 7 analysis and recommendation, before I write them.

**Prompt/request:** After running the marks cell, asked what the Section 7
analysis is supposed to cover.

**What Claude did:** Explained the analysis cell's two questions and the
recommendation using my outputs: slice leads (LoRA's lead over TF-IDF-9,543
shrinks on $ticker tweets, 0.096 vs 0.122, and grows on links, cut-off and
short tweets, but every slice/rest interval pair overlaps, so none of the
differences are trustworthy; small minority-class counts in the ticker and
cut-off slices); all-wrong tweets (45 of 1,788; my marks: 10 hard, 3
ambiguous, 2 mislabeled) and what that says about the labels. Noted my 910 and
1483 reasons still don't match their marks.

**How I checked it:** Numbers from my notebook outputs.

**Outcome:** Pending (I'll write the analysis).

## [2026-11-23]

**Context:** Section 7 recommendation.

**Prompt/request:** Asked to discuss the recommendation in more depth.

**What Claude did:** Laid out the decision: which methods are dominated
(zero-/few-shot are worse and slower than TF-IDF-9,543), the real choice
(LoRA vs TF-IDF-9,543), what the gap means in errors at scale (accuracy 0.882
vs 0.794, about 88 fewer mistakes per 1,000 tweets; negative F1 0.781 vs
0.613), cost at scale from my measured times (1M tweets: ~10 s vs ~5.7 GPU
hours, not optimized), one-time training cost, and conditions that would
change the choice (no GPU / extreme volume / latency, how much errors cost,
drift and retraining, label quality, a hybrid). Asked which way I lean.

**How I checked it:** Arithmetic from my Section 2/4/6 numbers.

**Outcome:** Pending (I'll write my recommendation).

## [2026-11-23]

**Context:** Section 7 analysis and recommendation cell (hw2-32), my draft.

**Prompt/request:** Asked for a review of my Section 7 analysis and recommendation.

**What Claude did:** Reviewed my draft (no rewriting). Analysis: the slice
paragraph calls it "accuracy for TF-IDF" when it's LoRA's macro-F1 lead; the
trust argument should be that each slice's interval overlaps its rest's, plus
the solid finding that LoRA leads in every slice; "volatility as a common
reason" rests on one tweet. Recommendation: name both prompting methods as
dominated; "recall" → macro-F1; "more memory" → more GPU compute; the speed
argument is weak because ~21 s per 1,000 tweets is ~20 ms per tweet, fast
enough for a live feed (the real cost is GPU hours at bulk volume); an
88-per-1,000 error gap isn't "slightly less accurate"; an unfinished sentence
and an off-topic law-firm line; the final choice wavers between TF-IDF and a
hybrid (untested); training costs and the error analysis aren't used yet, though
the assignment asks for them. Listed typos.

**How I checked it:** Numbers checked against my Section 2/4/6/7 outputs.

**Outcome:** Pending (I'll revise).

## [2026-11-23]

**Context:** Section 7 write-up, second pass.

**Prompt/request:** Asked Claude to reread my revised Section 7 analysis and
recommendation and list the remaining gaps.

**What Claude did:** Reread the cell and my revised 910/1483 reasons (now
defensible as "hard"; noted the marks cell should be rerun so the displayed
table shows the new wording). Listed what's still open: the analysis lacks the
explicit "slice and rest intervals overlap" argument, and the "volatility is a
common reason" sentence rests on one tweet; the recommendation still uses the
speed argument and "slightly less accurate" (contradicted by ~20 ms per tweet
and the 88-per-1,000 gap), still says "recall" and "memory", still has the
law-firm line, still wavers between TF-IDF and an untested hybrid, and still
doesn't use the training costs or the error analysis. Listed remaining typos.

**How I checked it:** Compared with the previous review and my outputs.

**Outcome:** Pending (I'll revise).

## [2026-11-23]

**Context:** Section 7 recommendation, third pass.

**Prompt/request:** Asked Claude to check my updated recommendation.

**What Claude did:** Reviewed it: error analysis now used in both places and
the speed argument fixed. Still open: training costs (Sections 2/4/5) not yet
included, the cost argument has no numbers, two final answers (TF-IDF in one
paragraph, hybrid in the next), the hybrid isn't marked untested and has no
"unsure" rule, "recall" → macro-F1, an unclear "ratio of performance" phrase,
and the law-firm line. Listed typos.

**How I checked it:** Against my Section 2/4/5/6 numbers.

**Outcome:** Pending (I'll revise).

## [2026-11-23]

**Context:** Submission preparation.

**Prompt/request:** Asked what to include in the submission archive.

**What Claude did:** Listed the required files from ASSIGNMENT.pdf ("Files to
submit") and what to leave out, then checked the repo for gaps: README.md is
still the starter version (no hardware or run steps), the notebook cites no
sources (Ch3/Ch6/Ch12 notebooks, HW1 code, scikit-learn docs), two Markdown
TODO lines (hw2-14, hw2-23) and stale TODO code comments remain, Section 1's
analysis still defines the label by tone and lacks the macro-F1 paragraph, and
many `ai-use.md` entries still say "Pending".

**How I checked it:** Read README.md, grepped the notebook for TODO lines and
citations, and counted "Pending" entries in ai-use.md.

**Outcome:** Pending.

## [2026-11-23]

**Context:** Section 2 cell (hw2-09), rerun while removing a TODO comment.

**Prompt/request:** Asked why the cell errors.

**What Claude did:** Diagnosed `NameError: selection_gold`: it's defined in the
Section 1 always-neutral cell, which hadn't run in the current kernel. Noted
the rerun replaced the cell's saved output (training times 2.72 s / 5.94 s and
the results table) with the error, and that rerunning would record new
timings. Confirmed the original outputs are intact in commit d69c682 and
offered to restore only that cell's outputs from git, keeping my edited source.

**How I checked it:** Read the cell outputs on disk and in commit d69c682.

**Outcome:** Pending (waiting for my choice).

## [2026-11-23]

**Context:** Section 2 cell (hw2-09) output restore.

**Prompt/request:** Asked Claude to restore the cell's original output.

**What Claude did:** Edited the notebook (AI-edited): copied only hw2-09's
outputs and execution count from commit d69c682 into the current file,
keeping my edited source. Backed up the file first.

**How I checked it:** Claude confirmed only hw2-09 changed versus the backup,
the source was unchanged, and the restored output reads "Train time 1: 2.72
seconds / Train time 2: 5.94 seconds" with the original table.

**Outcome:** Applied; I need to Revert in VS Code to load it.
