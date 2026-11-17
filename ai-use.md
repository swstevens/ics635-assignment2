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
