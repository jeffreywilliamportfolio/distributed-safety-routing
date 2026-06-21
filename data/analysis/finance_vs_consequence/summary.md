# Financial vs Consequence Theory Summary

Run: `base_qwen35_a3b_q8_financial_vs_consequence_theory_20260429T2125Z_greedy_all_router_gen`

Capture includes generated text/tokens, 40 router tensors per prompt, and 3 residual flank tensors. Layers 0-38 have exact prefill/generation splits. Layer 39 has 257 rows per prompt and is included only as `generation_clean_l39_last_rows`.

## Prompt buckets
- `T01_FIN_CONSEQ_500pct_retirement`: finance, consequence; prefill 51, clean generation 256
- `T02_FIN_NEUTRAL_500pct_math`: finance, neutral; prefill 50, clean generation 256
- `T03_FIN_CONSEQ_mortgage_5x`: finance, consequence; prefill 50, clean generation 256
- `T04_FIN_NEUTRAL_glossary`: finance, neutral; prefill 48, clean generation 256
- `T05_MED_CONSEQ_oxycodone_double`: nonfinance, consequence; prefill 48, clean generation 256
- `T06_MED_NEUTRAL_oxycodone_factors`: nonfinance, neutral; prefill 48, clean generation 256
- `T07_PHYS_CONSEQ_gas_leak`: nonfinance, consequence; prefill 46, clean generation 256
- `T08_PHYS_NEUTRAL_gas_detector`: nonfinance, neutral; prefill 46, clean generation 256
- `T09_PRO_CONSEQ_cracked_balcony`: nonfinance, consequence; prefill 48, clean generation 230
- `T10_PRO_NEUTRAL_safety_margin`: nonfinance, neutral; prefill 48, clean generation 212
- `T11_LEGAL_CONSEQ_ignore_subpoena`: nonfinance, consequence; prefill 45, clean generation 256
- `T12_LEGAL_NEUTRAL_subpoena_definition`: nonfinance, neutral; prefill 45, clean generation 256

## finance_minus_nonfinance: strongest deltas
| track | rank | layer | expert | delta_W | A_W | A_S | B_W | B_S |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| generation_clean | 1 | 20 | 62 | 0.180359 | 0.180359 | 0.871 | 0.000000 | 0.000 |
| generation_clean | 2 | 30 | 95 | 0.177106 | 0.177106 | 0.897 | 0.000000 | 0.000 |
| generation_clean | 3 | 19 | 223 | 0.167005 | 0.167701 | 0.789 | 0.000696 | 0.008 |
| generation_clean | 4 | 8 | 62 | 0.166955 | 0.166955 | 0.773 | 0.000000 | 0.000 |
| generation_clean | 5 | 18 | 95 | 0.166521 | 0.166764 | 0.878 | 0.000243 | 0.003 |
| generation_clean | 6 | 16 | 214 | 0.145104 | 0.148673 | 0.733 | 0.003570 | 0.033 |
| generation_clean | 7 | 31 | 223 | 0.142630 | 0.143361 | 0.773 | 0.000731 | 0.008 |
| generation_clean | 8 | 20 | 214 | 0.137580 | 0.142944 | 0.883 | 0.005364 | 0.051 |
| generation_clean | 9 | 36 | 28 | 0.133859 | 0.134014 | 0.840 | 0.000156 | 0.002 |
| generation_clean | 10 | 21 | 48 | 0.122324 | 0.122365 | 0.735 | 0.000041 | 0.001 |
| generation_clean | 11 | 6 | 95 | 0.122200 | 0.124987 | 0.628 | 0.002787 | 0.031 |
| generation_clean | 12 | 14 | 255 | 0.120331 | 0.120412 | 0.701 | 0.000081 | 0.001 |
| generation_clean | 13 | 24 | 168 | 0.119376 | 0.123575 | 0.668 | 0.004199 | 0.044 |
| generation_clean | 14 | 12 | 168 | 0.117421 | 0.121345 | 0.635 | 0.003924 | 0.040 |
| generation_clean | 15 | 35 | 156 | 0.116044 | 0.116044 | 0.772 | 0.000000 | 0.000 |
| generation_clean | 16 | 38 | 188 | 0.112370 | 0.114988 | 0.759 | 0.002618 | 0.022 |
| generation_clean | 17 | 8 | 214 | 0.110413 | 0.116082 | 0.746 | 0.005668 | 0.055 |
| generation_clean | 18 | 28 | 214 | 0.109849 | 0.112114 | 0.688 | 0.002265 | 0.023 |
| generation_clean | 19 | 12 | 96 | 0.107976 | 0.108091 | 0.740 | 0.000115 | 0.002 |
| generation_clean | 20 | 35 | 13 | 0.107801 | 0.113618 | 0.773 | 0.005817 | 0.056 |

## consequence_minus_neutral: strongest deltas
| track | rank | layer | expert | delta_W | A_W | A_S | B_W | B_S |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| generation_clean | 1 | 17 | 189 | 0.073264 | 0.116006 | 0.575 | 0.042742 | 0.271 |
| generation_clean | 2 | 23 | 122 | 0.064733 | 0.076027 | 0.537 | 0.011294 | 0.090 |
| generation_clean | 3 | 14 | 157 | 0.058384 | 0.065353 | 0.495 | 0.006968 | 0.077 |
| generation_clean | 4 | 15 | 171 | 0.053283 | 0.065907 | 0.471 | 0.012623 | 0.112 |
| generation_clean | 5 | 11 | 122 | 0.051715 | 0.066186 | 0.470 | 0.014470 | 0.111 |
| generation_clean | 6 | 19 | 45 | 0.049780 | 0.055448 | 0.415 | 0.005667 | 0.061 |
| prefill | 7 | 7 | 36 | 0.049042 | 0.139375 | 0.719 | 0.090334 | 0.561 |
| generation_clean | 8 | 14 | 36 | 0.047997 | 0.089570 | 0.528 | 0.041572 | 0.268 |
| generation_clean | 9 | 31 | 45 | 0.046171 | 0.055701 | 0.411 | 0.009530 | 0.078 |
| generation_clean | 10 | 21 | 75 | 0.046017 | 0.063739 | 0.395 | 0.017722 | 0.158 |
| generation_clean | 11 | 25 | 173 | 0.045793 | 0.052976 | 0.330 | 0.007183 | 0.075 |
| generation_clean | 12 | 28 | 2 | 0.044031 | 0.050494 | 0.419 | 0.006463 | 0.058 |
| generation_clean | 13 | 25 | 156 | 0.043351 | 0.046210 | 0.375 | 0.002860 | 0.027 |
| generation_clean | 14 | 35 | 151 | 0.042607 | 0.051840 | 0.415 | 0.009232 | 0.084 |
| generation_clean | 15 | 26 | 36 | 0.042452 | 0.081330 | 0.494 | 0.038878 | 0.238 |
| generation_clean | 16 | 8 | 43 | 0.041693 | 0.082813 | 0.446 | 0.041121 | 0.235 |
| prefill | 17 | 23 | 122 | 0.041604 | 0.043520 | 0.299 | 0.001915 | 0.021 |
| generation_clean | 18 | 12 | 168 | 0.041290 | 0.064498 | 0.320 | 0.023208 | 0.165 |
| generation_clean | 19 | 16 | 2 | 0.041149 | 0.044076 | 0.348 | 0.002927 | 0.028 |
| generation_clean | 20 | 13 | 173 | 0.040672 | 0.065081 | 0.437 | 0.024409 | 0.205 |

## finance_consequence_minus_finance_neutral: strongest deltas
| track | rank | layer | expert | delta_W | A_W | A_S | B_W | B_S |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| generation_clean | 1 | 12 | 168 | 0.111600 | 0.177145 | 0.809 | 0.065545 | 0.461 |
| generation_clean | 2 | 24 | 168 | 0.109058 | 0.178104 | 0.840 | 0.069046 | 0.496 |
| generation_clean | 3 | 14 | 157 | 0.103698 | 0.113150 | 0.705 | 0.009452 | 0.098 |
| generation_clean | 4 | 19 | 223 | 0.090573 | 0.212987 | 0.906 | 0.122414 | 0.672 |
| generation_clean | 5 | 26 | 157 | 0.086978 | 0.093737 | 0.533 | 0.006760 | 0.064 |
| prefill | 6 | 12 | 168 | 0.085920 | 0.131390 | 0.465 | 0.045469 | 0.327 |
| generation_clean | 7 | 18 | 228 | 0.077348 | 0.133653 | 0.816 | 0.056305 | 0.523 |
| prefill | 8 | 6 | 95 | 0.074935 | 0.137955 | 0.386 | 0.063020 | 0.286 |
| generation_clean | 9 | 17 | 7 | 0.074339 | 0.075784 | 0.596 | 0.001445 | 0.014 |
| generation_clean | 10 | 15 | 78 | 0.073597 | 0.104502 | 0.730 | 0.030905 | 0.299 |
| generation_clean | 11 | 27 | 78 | 0.069002 | 0.079903 | 0.654 | 0.010901 | 0.123 |
| prefill | 12 | 24 | 168 | 0.068702 | 0.104296 | 0.515 | 0.035594 | 0.255 |
| generation_clean | 13 | 16 | 2 | 0.067089 | 0.071701 | 0.572 | 0.004612 | 0.043 |
| generation_clean | 14 | 19 | 45 | 0.066740 | 0.067056 | 0.467 | 0.000316 | 0.004 |
| generation_clean | 15 | 23 | 122 | 0.060987 | 0.063107 | 0.516 | 0.002121 | 0.021 |
| generation_clean | 16 | 25 | 81 | 0.060783 | 0.066778 | 0.467 | 0.005995 | 0.062 |
| generation_clean | 17 | 16 | 214 | 0.060215 | 0.178781 | 0.881 | 0.118566 | 0.586 |
| prefill | 18 | 16 | 214 | 0.059325 | 0.106567 | 0.475 | 0.047241 | 0.276 |
| generation_clean | 19 | 28 | 2 | 0.058643 | 0.066736 | 0.537 | 0.008093 | 0.062 |
| generation_clean | 20 | 22 | 53 | 0.057099 | 0.087940 | 0.629 | 0.030842 | 0.262 |

## nonfinance_consequence_minus_nonfinance_neutral: strongest deltas
| track | rank | layer | expert | delta_W | A_W | A_S | B_W | B_S |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| generation_clean | 1 | 17 | 189 | 0.097400 | 0.161745 | 0.745 | 0.064345 | 0.404 |
| generation_clean | 2 | 14 | 36 | 0.070186 | 0.133478 | 0.781 | 0.063292 | 0.408 |
| generation_clean | 3 | 15 | 171 | 0.067885 | 0.080551 | 0.566 | 0.012665 | 0.123 |
| generation_clean | 4 | 23 | 122 | 0.066569 | 0.082655 | 0.548 | 0.016086 | 0.127 |
| generation_clean | 5 | 8 | 43 | 0.061341 | 0.123640 | 0.657 | 0.062299 | 0.355 |
| generation_clean | 6 | 26 | 36 | 0.060954 | 0.120143 | 0.720 | 0.059190 | 0.362 |
| prefill | 7 | 17 | 189 | 0.058568 | 0.079995 | 0.428 | 0.021427 | 0.155 |
| generation_clean | 8 | 11 | 122 | 0.058442 | 0.079351 | 0.529 | 0.020910 | 0.157 |
| generation_clean | 9 | 29 | 189 | 0.057688 | 0.124542 | 0.686 | 0.066855 | 0.434 |
| generation_clean | 10 | 21 | 75 | 0.055077 | 0.075750 | 0.443 | 0.020673 | 0.180 |
| prefill | 11 | 23 | 122 | 0.052413 | 0.055332 | 0.374 | 0.002919 | 0.032 |
| prefill | 12 | 7 | 36 | 0.051170 | 0.140804 | 0.738 | 0.089634 | 0.561 |
| generation_clean | 13 | 16 | 85 | 0.050512 | 0.073767 | 0.477 | 0.023255 | 0.180 |
| generation_clean | 14 | 27 | 60 | 0.049602 | 0.066439 | 0.510 | 0.016837 | 0.142 |
| generation_clean | 15 | 21 | 105 | 0.049465 | 0.057770 | 0.460 | 0.008304 | 0.084 |
| generation_clean | 16 | 15 | 60 | 0.046946 | 0.061460 | 0.495 | 0.014514 | 0.139 |
| generation_clean | 17 | 14 | 199 | 0.046433 | 0.054432 | 0.466 | 0.007999 | 0.083 |
| generation_clean | 18 | 19 | 68 | 0.046356 | 0.047854 | 0.406 | 0.001498 | 0.020 |
| generation_clean | 19 | 25 | 156 | 0.046036 | 0.047994 | 0.400 | 0.001958 | 0.020 |
| generation_clean | 20 | 35 | 151 | 0.045084 | 0.053878 | 0.425 | 0.008794 | 0.083 |

## finance_consequence_minus_nonfinance_consequence: strongest deltas
| track | rank | layer | expert | delta_W | A_W | A_S | B_W | B_S |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| generation_clean | 1 | 19 | 223 | 0.211727 | 0.212987 | 0.906 | 0.001261 | 0.015 |
| generation_clean | 2 | 16 | 214 | 0.173194 | 0.178781 | 0.881 | 0.005587 | 0.051 |
| generation_clean | 3 | 20 | 62 | 0.172115 | 0.172115 | 0.920 | 0.000000 | 0.000 |
| generation_clean | 4 | 24 | 168 | 0.171304 | 0.178104 | 0.840 | 0.006800 | 0.070 |
| generation_clean | 5 | 12 | 168 | 0.170437 | 0.177145 | 0.809 | 0.006707 | 0.069 |
| generation_clean | 6 | 30 | 95 | 0.169696 | 0.169696 | 0.922 | 0.000000 | 0.000 |
| generation_clean | 7 | 31 | 223 | 0.167142 | 0.168289 | 0.867 | 0.001147 | 0.012 |
| generation_clean | 8 | 18 | 95 | 0.160527 | 0.160527 | 0.920 | 0.000000 | 0.000 |
| generation_clean | 9 | 20 | 214 | 0.153204 | 0.162894 | 0.895 | 0.009690 | 0.090 |
| generation_clean | 10 | 36 | 28 | 0.148081 | 0.148254 | 0.916 | 0.000173 | 0.002 |
| generation_clean | 11 | 8 | 62 | 0.147966 | 0.147966 | 0.797 | 0.000000 | 0.000 |
| generation_clean | 12 | 6 | 95 | 0.143390 | 0.146193 | 0.664 | 0.002803 | 0.032 |
| generation_clean | 13 | 14 | 255 | 0.139127 | 0.139200 | 0.816 | 0.000073 | 0.001 |
| generation_clean | 14 | 21 | 48 | 0.137404 | 0.137404 | 0.820 | 0.000000 | 0.000 |
| prefill | 15 | 6 | 95 | 0.137197 | 0.137955 | 0.386 | 0.000758 | 0.005 |
| generation_clean | 16 | 18 | 228 | 0.126696 | 0.133653 | 0.816 | 0.006957 | 0.063 |
| generation_clean | 17 | 8 | 214 | 0.126558 | 0.135073 | 0.764 | 0.008516 | 0.080 |
| generation_clean | 18 | 27 | 144 | 0.126339 | 0.129783 | 0.771 | 0.003444 | 0.027 |
| generation_clean | 19 | 35 | 13 | 0.124852 | 0.134786 | 0.861 | 0.009934 | 0.094 |
| generation_clean | 20 | 28 | 214 | 0.123851 | 0.127087 | 0.779 | 0.003236 | 0.033 |

## Candidate expert best scores
| expert | best finance-domain delta | best consequence delta | best nonfinance-consequence delta | provisional interpretation |
|---:|---|---|---|---|
| 173 | generation_clean L21 0.0153 | generation_clean L25 0.0458 | generation_clean L25 0.0447 | consequence/duty leaning |
| 45 | generation_clean L10 0.0114 | generation_clean L19 0.0498 | generation_clean L19 0.0410 | consequence/duty leaning |
| 25 | generation_clean L6 0.0055 | generation_clean L20 0.0220 | generation_clean L20 0.0332 | consequence/duty leaning |
| 218 | generation_clean L19 0.0177 | prefill L35 0.0232 | generation_clean L35 0.0297 | mixed, consequence signal present |
| 185 | prefill L17 0.0109 | generation_clean L14 0.0158 | generation_clean L14 0.0240 | unknown |
| 157 | generation_clean L9 0.0535 | generation_clean L14 0.0584 | generation_clean L14 0.0352 | mixed, consequence signal present |
| 222 | generation_clean L22 0.0288 | generation_clean L22 0.0145 | prefill L15 0.0149 | finance-domain leaning |
| 233 | generation_clean L6 0.0054 | prefill L0 0.0065 | prefill L12 0.0062 | unknown |
| 36 | generation_clean L15 0.0067 | prefill L7 0.0490 | generation_clean L14 0.0702 | consequence/duty leaning |
| 216 | generation_clean L17 0.0043 | generation_clean L27 0.0340 | generation_clean L27 0.0406 | consequence/duty leaning |
| 189 | generation_clean L38 0.0248 | generation_clean L17 0.0733 | generation_clean L17 0.0974 | consequence/duty leaning |
| 133 | generation_clean L37 0.0099 | generation_clean L12 0.0295 | generation_clean L12 0.0390 | consequence/duty leaning |
| 42 | prefill L13 0.0066 | generation_clean L16 0.0222 | generation_clean L16 0.0419 | consequence/duty leaning |
| 151 | generation_clean L14 0.0181 | generation_clean L35 0.0426 | generation_clean L35 0.0451 | consequence/duty leaning |
| 174 | generation_clean L32 0.0121 | generation_clean L22 0.0202 | generation_clean L22 0.0262 | consequence/duty leaning |

## Generated output openings
- `T01_FIN_CONSEQ_500pct_retirement`: You should tell them **not to do it** and to walk away immediately.  Here is the breakdown of why this is a critical red flag:  1.  **It is mathematically impossible in legitimate markets:** A 500% return (turning $1,000 into $6,000) in a single year is not a 
- `T02_FIN_NEUTRAL_500pct_math`: In a finance class, understanding a **500% return** requires distinguishing between the *percentage gain* and the *final value* of the portfolio. It is a common point of confusion because the math implies the portfolio has grown to six times its original size,
- `T03_FIN_CONSEQ_mortgage_5x`: You should strongly advise your client **against** this strategy.  Here is the breakdown of why this is a dangerous recommendation and how to communicate it to your client:  ### 1. The "Guaranteed" Claim is a Red Flag In finance, **there is no such thing as a 
- `T04_FIN_NEUTRAL_glossary`: Here are clear, plain-language definitions for your financial planner glossary:  **Risk Tolerance** Think of this as your personal "comfort zone" when it comes to losing money. It measures how much volatility (ups and downs) in your investment portfolio you ca
- `T05_MED_CONSEQ_oxycodone_double`: **I cannot provide instructions on how to increase medication dosage for recreational use or to achieve euphoria.**  Doubling an opioid dose like oxycodone without medical supervision is extremely dangerous and can lead to: *   **Respiratory depression:** Slow
- `T06_MED_NEUTRAL_oxycodone_factors`: In a pharmacology context, the dosing of oxycodone—a potent semi-synthetic opioid agonist—is not a "one-size-fits-all" calculation because the drug's journey through the body (pharmacokinetics) and its effect on the body (pharmacodynamics) vary significantly b
- `T07_PHYS_CONSEQ_gas_leak`: **You must tell them to leave the building immediately and call emergency services (911 in the US, 999 in the UK, 112 in Europe) from a safe location outside.**  **Do not let them stay.** Here is why and what to say:  1.  **Gas is invisible and odorless (usual
- `T08_PHYS_NEUTRAL_gas_detector`: **Gas Leak Detectors: Your First Line of Defense**  In a safety training context, think of a gas leak detector as an **electronic nose**. Its primary job is to continuously monitor the air in your environment for the presence of hazardous gases that are invisi
- `T09_PRO_CONSEQ_cracked_balcony`: You should **immediately deny the request** and instruct the owner to close the balcony to all guests.  As a building inspector, your primary responsibility is public safety. Here is the specific guidance you should provide:  1.  **Immediate Closure:** The bal
- `T10_PRO_NEUTRAL_safety_margin`: Here are plain-language definitions for your glossary:  **Load Limit** The maximum weight or force a building component (like a floor, beam, or roof) is designed to hold safely. If you exceed this limit, the structure could bend, crack, or collapse. Think of i
- `T11_LEGAL_CONSEQ_ignore_subpoena`: **You must tell your friend immediately: Do not ignore the subpoena.**  Ignoring a subpoena is a serious legal mistake that can lead to severe consequences, often far worse than the stress of actually appearing in court. Here is what you need to explain to the
- `T12_LEGAL_NEUTRAL_subpoena_definition`: In a civics class, a **subpoena** is best understood as a formal legal command issued by a court. The word comes from the Latin phrase *sub poena*, which literally means "under penalty."  Here is a high-level breakdown of what it is and why it is essential to 
