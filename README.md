# ICS 635 — Homework 2: Fine-Tuning an LLM with LoRA

Shea Stevens

Fine-tunes Qwen3-1.7B with LoRA to label the sentiment (outlook) of finance
tweets, and compares it with zero-shot and few-shot prompting and two TF-IDF
baselines. All code, results and analysis are in `hw2.ipynb`.

## Files

| File | Contents |
|---|---|
| `hw2.ipynb` | All code, outputs and written analysis (Sections 1–7) |
| `test_predictions.csv` | One row per test tweet: text, true label, and every method's prediction (and raw LLM output) |
| `pyproject.toml`, `uv.lock` | Pinned Python environment |
| `ai-use.md` | AI tools used, requests, and how the output was checked |

## Hardware used

| Sections | Machine |
|---|---|
| 1–7 (final run with the reported results) | GPU Gateway system with **20 GB of GPU memory** |
| 1, 2 and 7 (drafting and the Section 7 analysis) | Laptop, CPU only (no GPU needed) |

Measured on the 20 GB GPU: LoRA training peaked at **16.4 GB** of GPU memory
(r = 64) and 12.9–13.1 GB for the smaller ranks, so a 10 GB system will not fit
the Section 4–5 training as configured. The model runs in float32 as the
assignment requires.

## Setup

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), then in
this folder run:

```sh
uv sync --locked
```

This installs Python 3.13 and creates `.venv` with the exact package versions
in `uv.lock` (PyTorch 2.15, Transformers 5.14.1, PEFT 0.20.0, TRL 1.9.2,
scikit-learn 1.9). Open `hw2.ipynb` in VS Code or JupyterLab and select the
`.venv` interpreter as the kernel. The results were produced on Linux (the GPU
Gateway). Check that `torch.cuda.is_available()` is `True` before running
Sections 3–6.

The first run downloads the dataset and about 4 GB of model weights into the
Hugging Face cache.

## Running

Run `hw2.ipynb` from top to bottom on a 20 GB GPU (**Run All**). Keep
`DEV_RUN = False` in Section 4. Approximate times measured on the 20 GB system:

| Section | What runs | Time |
|---|---|---|
| Setup, 1, 2 | Data, splits, TF-IDF baselines | under 1 min |
| 3 | 6 prompts × 600 selection tweets | about 2–3 min |
| 4 | One LoRA training run (r = 64) + reload and score | about 11 min |
| 5 | Four more LoRA runs + scoring | about 42 min |
| 6 | Six methods on 1,788 test tweets | about 4 min |
| 7 | Slices (bootstrap) and error reading | about 1 min |

Total: roughly **1 hour** of GPU time, plus the model download.

The notebook writes these files as it runs: `adapters/lora_r*_a*/` (the five
LoRA adapters, not submitted), `selection_*.csv` (per-prompt and per-adapter
selection outputs), `lora_runs.csv`, and in Section 6 `test_predictions.csv`,
`test_results.csv` and `section6_state.json`.

### Running Section 7 without a GPU

Section 6 saves everything Section 7 needs. After a full GPU run, Section 7 can
be rerun on any machine: run the three Setup cells, then the first cell of
Section 7 ("Resume here on a laptop…"), then the Section 7 cells. Do **not**
run the cell at the end of Section 6 that saves the state, since it would
overwrite the saved test timings.

## Sources

- Dataset: [`zeroshot/twitter-financial-news-sentiment`](https://huggingface.co/datasets/zeroshot/twitter-financial-news-sentiment). License: MIT.
- Model: [`Qwen/Qwen3-1.7B`](https://huggingface.co/Qwen/Qwen3-1.7B). License: Apache-2.0.
- Course materials (ICS 635): the Ch3, Ch6 and Ch12 reading notebooks, cited in
  the notebook where they were used.
