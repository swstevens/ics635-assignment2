# ICS 635 — Homework 2 student materials

1. Read **ASSIGNMENT.pdf** for the requirements and grading.
2. Open **hw2.ipynb** and implement your workflow. Its setup cells load the data,
   create the fixed splits, and define the shared prompt and scoring helpers.
3. Write your analysis in Markdown cells beside the relevant notebook results.
   **record.md** is optional scratch space and does not need to be submitted.
4. Follow **Files to submit** in the assignment when creating your final archive.

## Set up Python with uv

Install [uv](https://docs.astral.sh/uv/getting-started/installation/), then open
a terminal in the extracted `hw2` folder and run:

```sh
uv sync --locked
```

This installs Python 3.13 if needed and creates a local `.venv` using the
package versions pinned in `uv.lock`. Dependencies are listed in `pyproject.toml`.
Open `hw2.ipynb` in VS Code and select the `.venv` interpreter as its kernel.

Run this on the 10 GB or 20 GB VRAM systems you reach through the GPU Gateway,
whichever is available; see Compute in the assignment for memory use. The first
run downloads the dataset and about 4 GB of model weights into your Hugging Face
cache.

## Sources

- Dataset: [`zeroshot/twitter-financial-news-sentiment`](https://huggingface.co/datasets/zeroshot/twitter-financial-news-sentiment).
  License: MIT.
- Model: [`Qwen/Qwen3-1.7B`](https://huggingface.co/Qwen/Qwen3-1.7B).
  License: Apache-2.0.
