# Source-to-claim index

Every number in `main.tex` is transcribed from one capture session:
`base_qwen35_a3b_base_safety_smoke_20260429T1925Z` (base Qwen3.5-35B-A3B-Q8_0,
`qwen35moe`, 40 layers / 256 experts / top-8, greedy `--temp 0 --top-k 1 --seed 0`,
bare `</think>`, all-40-router-layer capture). The consolidated evidence is under
`data/`. Paths below are relative to `data/`.

Primary write-ups:
- `RESULTS.md` — the run's full results document (definitions, run inventory, all tables).
- `JOURNAL-SAFETY-EXPERTS.md` — the experiment-history journal, with held/partly-held/did-not-hold verdicts.

| # | Claim in paper | Value | Source (under `data/`) | Status |
|---|----------------|-------|------------------------|--------|
| 1 | Model / routing config | base Qwen3.5-35B-A3B Q8_0; 40 layers, 256 experts, top-8; greedy | `RESULTS.md` "Scope"; `JOURNAL-SAFETY-EXPERTS.md` "Local Routing Convention" | verified |
| 2 | Metric W=S·Q (softmax→top8→renorm); A−B delta_W | definitions | `RESULTS.md` "Metric definitions", "Per-Token W/S/Q Decomposition" | verified |
| 3 | Exp 1: 3 token-matched A/B pairs, tokens 50/50, 37/37, 74/74 | prompt token counts | `RESULTS.md` "Primary 3-Pair Safety Smoke"; `prompts/safety_smoke_3pair.tsv` | verified |
| 4 | Gen leader L25 E173 ΔW=0.124; A W=0.192 S=0.81; B W=0.068 S=0.43 | 0.124037 / 0.191791 (0.809) / 0.067754 (0.426) | `RESULTS.md` "Generation A-minus-B Leaders" row 1; `analysis/3pair_all_router/all_layer_a_minus_b_delta.tsv` | verified |
| 5 | Gen Q rises 0.16→0.24 for E173 | Q^B 0.159128 → Q^A 0.236972 | `RESULTS.md` per-token sanity table (L25/173 generation_clean) | verified |
| 6 | Table 1 supporting leaders (E45 L19/L31, E25 L20, E173 L13, E216 L27, E189 L17) | 0.082/0.073/0.072/0.067/0.063/0.061 | `RESULTS.md` "Generation A-minus-B Leaders" rows 2–7 | verified |
| 7 | Prefill L1 E173 aggregate 0.068 → 0.0004 after removing ` layer` filler | 0.067911 → 0.000369 | `RESULTS.md` "Focused Per-Token Readout" filler table; `analysis/3pair_all_router/per_token_candidate_wsq.tsv` | verified |
| 8 | Prefill survivors after filler removal: L14 E218 0.025→0.022; L25 E173 0.037→0.046; L19 E45 0.030→0.034 | as stated | `RESULTS.md` filler table | verified |
| 9 | Exp 2: 12 prompts, 2×2 finance×consequence buckets | bucket design | `RESULTS.md` "Finance vs Consequence Theory Test"; `prompts/financial_vs_consequence_theory.tsv` | verified |
| 10 | Finance-domain experts E62 L20 0.180 (B_S 0.000), E95 L30 0.177, E223 L19 0.167, E214 L16 | as stated | `RESULTS.md` "Finance-Domain Signals"; `analysis/finance_vs_consequence/bucket_comparison_delta.tsv` | verified |
| 11 | Consequence/duty experts E189 L17 0.073, E122 L23 0.065, E157 L14 0.058, E171 L15 0.053, E45 L19, E122 L11 | as stated | `RESULTS.md` "Broad Consequence / Duty Signals" | verified |
| 12 | Exp 3: E173 router bias −0.25/−0.5/−1/−2 | `--expert-bias 173:-x` | `RESULTS.md` "E173 Suppression" / "Run Inventory" | verified |
| 13 | E173 dose-response (L25 gen A−B): 0.124→0.093→0.056→0.041→0.004; A_S 0.809→0.046; A_W →0.005 | 0.124037/0.093495/0.056305/0.041212/0.004024; S 0.809→0.046; W^A 0.191791→0.004564 | `RESULTS.md` "Generation L25 E173" table; `analysis/e173_suppression/e173_by_layer.tsv` | verified |
| 14 | No jailbreak at any level; oxycodone refusal more explicit at −2; 500% "impossible and dangerous"→"trap"; benign stays professional | behavioral | `RESULTS.md` "Behavioral Effect Of E173 Suppression"; `analysis/e173_suppression/generated_openings.tsv` | verified |
| 15 | Reallocation to E45, E185, E157, E189, E216, E133 (generation) | as stated | `RESULTS.md` "Routing Reallocation Under E173 Suppression" | verified |
| 16 | Layer 39 excluded from prefill (distinct row count) | 257 rows/prompt | `RESULTS.md` "Capture surface"; `JOURNAL` "Local Routing Convention" | verified |

## Figures and tables in the paper
- Table 1 (generation leaders) — claims #4, #6 → `all_layer_a_minus_b_delta.tsv`.
- Table 2 (finance vs consequence) — claims #10, #11 → `bucket_comparison_delta.tsv`.
- Table 3 + Figure 1 (E173 dose-response) — claim #13 → `e173_by_layer.tsv`.

## Excluded / not used as result
- `per_token_top8_wsq_long.tsv` (~92 MB, 510,704 rows): the full per-token export. Not
  load-bearing for the claims; the summaries and delta tables are derived from it.
  Excluded from this repo for size; available from the author.
- Earlier L13/L14/L15-only exploratory suppressions (E218/E185/E157): superseded by the
  all-router captures; not cited as final intervention evidence (`RESULTS.md` Limitations).
- Raw `.npy` router tensors: kept out of version control by project policy.

## Caveats carried into the paper (from the journal's verdict vocabulary)
- Generation result "held up"; aggregate prefill leaders "partly held" (filler artifact).
- All headline numbers are single greedy trajectories (point estimates); n = 6 and 12.
- Scope: base Qwen3.5-35B-A3B Q8_0, bare `</think>`, greedy. Only E173 was suppressed in
  the final all-router setup.
