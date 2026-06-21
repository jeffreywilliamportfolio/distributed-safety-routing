# No Single Safety Gate

Distributed Routing of Harm-Refusal in a Mixture-of-Experts Language Model — paper source, figures, and reproducibility materials.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20786891.svg)](https://doi.org/10.5281/zenodo.20786891)

**Author:** Jeffrey W. Shorthill (independent researcher) · `jws299792@icloud.com`
**Version:** 1.0 (June 2026) · preprint, not peer reviewed
**DOI:** [10.5281/zenodo.20786891](https://doi.org/10.5281/zenodo.20786891) (concept DOI — resolves to the latest version)
**License:** [CC BY 4.0](LICENSE)

## What this is

A mixture-of-experts (MoE) router makes a discrete per-token choice, so it is natural
to ask whether a model's **harm-refusal** is owned by a single "safety expert" that
could be located, monitored, or attacked. We probe the **base Qwen3.5-35B-A3B** model
(40 layers, 256 experts, top-8) with router capture at every layer under greedy
decoding, and find that refusal does **not** route through one gate:

- On token-matched redflag vs. benign prompts, the generation-side signal is led by
  **expert 173 at layer 25** (ΔW = 0.124), atop a broad supporting cluster.
- A finance-vs-consequence control separates **topic** experts (finance) from a
  **real-world-consequence / duty** cluster (experts 189, 45, 122, 157, 36, 216, …).
- Suppressing expert 173 with a router bias (5 levels) collapses its routed mass
  (selection rate 0.81 → 0.05) but the model **never produces a harmful completion**
  on this set — routing reallocates to sibling experts and the refusals persist.

It is an **exploratory case study** (n = 6 token-matched, n = 12 bucketed; single
greedy trajectories), and the paper sets out the cluster-suppression and benchmark
controls that would confirm or break it.

## Repository layout

| Path | Contents |
|---|---|
| `main.tex` | Paper source (LaTeX). |
| `refs.bib` | Bibliography (every entry verified against an authoritative record). |
| `SOURCES.md` | Claim-by-claim source-to-value index. |
| `data/` | Supporting evidence (see below). |
| `main.pdf` | Built PDF of the paper. |

## Data

`data/` carries the analysis tables from one capture session,
`base_qwen35_a3b_base_safety_smoke_20260429T1925Z`:

- `RESULTS.md`, `JOURNAL-SAFETY-EXPERTS.md` — the run write-up and history journal.
- `analysis/3pair_all_router/` — all-layer A−B routing deltas and the per-token
  decomposition that backs the prefill filler-artifact correction.
- `analysis/finance_vs_consequence/` — the 2×2 control's bucket comparison tables.
- `analysis/e173_suppression/` — the expert-173 dose-response and generated openings.
- `prompts/` — the redflag/benign and finance/consequence prompt sets.

Raw router tensors (`.npy`) and the full ~92 MB per-token export are kept out of
version control; the tables here substantiate every reported number.

## Build

```bash
latexmk -pdf main.tex
```

## Ethics note

This studies *how a model refuses*. The redflag prompts (drug misuse, a
prompt-injection attempt, a financial "sure thing") were refused at every
intervention level; the repository releases the prompts and the model's **refusals**,
not harmful content. The suppression result is reported because it *fails* to bypass
safety.

## Citation

See [`CITATION.cff`](CITATION.cff). Please cite the preprint (version 1.0, 2026).

## AI-use disclosure

Generative AI (Anthropic's Claude) was used for drafting, organization, and
bibliography formatting. The author verified every reported value and reference and
takes full responsibility for the content.
