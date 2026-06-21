# Per-Token W/S/Q Decomposition

Capture:

`base_qwen35_a3b_q8_safety_smoke_3pair_20260429T2105Z_greedy_all_router_gen`

Metric:

For a single token and layer, `S` is 1 when an expert is in the routed top-8, otherwise 0.
When `S=1`, `Q` is that expert's top-8-renormalized routed weight and `W = S * Q = Q`.
When `S=0`, `Q` is blank and `W=0`. Aggregate tables are recovered by averaging `W`,
averaging `S`, and computing aggregate `Q = mean(W) / mean(S)`.

Outputs:

- `per_token_top8_wsq_long.tsv`: 510704 rows; all selected top-8 experts for every analyzable token/layer.
- `per_token_candidate_wsq.tsv`: 89800 rows; explicit zero/nonzero W/S/Q for candidate layer/expert pairs.

Clean generation counts:

- `S01A_oxycodone_misuse`: prefill 50, clean generation 256
- `S01B_oxycodone_pharmacist`: prefill 50, clean generation 256
- `S02A_ayahuasca_brew_instruction`: prefill 37, clean generation 51
- `S02B_ayahuasca_description`: prefill 37, clean generation 256
- `S03A_500pct_investment_direct`: prefill 74, clean generation 207
- `S03B_500pct_return_planner`: prefill 74, clean generation 256

Layer 39:

Layer 39 keeps the same caveat as the aggregate report. It is exported only as
`generation_clean_l39_last_rows`; do not use it for prefill claims.

Candidate layer/expert pairs:

- L1 E173
- L2 E222
- L6 E226
- L7 E62
- L8 E25
- L8 E43
- L10 E36
- L11 E122
- L12 E133
- L12 E248
- L13 E173
- L14 E157
- L14 E185
- L14 E218
- L15 E216
- L16 E40
- L16 E42
- L17 E46
- L17 E189
- L18 E15
- L18 E30
- L19 E23
- L19 E45
- L20 E25
- L22 E36
- L22 E174
- L23 E122
- L24 E133
- L25 E173
- L27 E189
- L27 E216
- L28 E42
- L29 E189
- L31 E23
- L31 E45
- L33 E198
- L34 E70
- L35 E151
- L36 E73
- L37 E233
- L39 E1
- L39 E15
- L39 E16
- L39 E23
- L39 E36
- L39 E88
- L39 E92
- L39 E107
- L39 E117
- L39 E120
- L39 E125
- L39 E145
- L39 E147
- L39 E162
- L39 E165
- L39 E179
- L39 E216
- L39 E238
- L39 E246
- L39 E248
