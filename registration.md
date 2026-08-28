# Silicon Sample Benchmark — method registration form (completed)

Team: team_5 · Disclosure class: A (all items public)

**0.1** — Team 5 — solo: Jamie Cummins, University of Bern. Contact: jamie.cummins@unibe.ch.

**0.2** — Cell-level statistics derived from the same generator as the team's Tier-1 cohort: control-cell means are reference-survey-calibrated baselines; treatment cells add the Tier-3 crowd-forecast ATEs; demographic-moderator cells carry real group-level baseline differences (reference-calibrated) plus headroom-proportional effect moderation (groups far from ceiling move more); behavioral outcomes get level differences but flat effects.

**0.3** — Tier 2, primary. Family: measurement-calibrated statistical synthesis; LLM ensemble for effects; reference-survey-conditioned.

**0.4** — (1) same generator as Tier-1 (see that form) -> (2) main cells: full-cohort baseline means + ATE vector -> (3) moderator cells: group baseline means from the full 18,000-profile cohort render + ATE x group mean headroom factor (flat for donation/signup) -> (4) verify ranges, completeness, no NAs, no exact zeros.

**0.5** — Full coverage: 221 main cells (17 conditions x 13 outcomes) + 5,967 moderator cells (x 27 demographic levels), complete, no NA.

**A.1** — LLMs only in the Tier-3 effect-forecast stage feeding step (4) (see the team's T3 primary registration; same crowd, same logs, deposited here too). Profile construction, baselines, rendering: deterministic statistical code, no LLM.

**A.2** — Fully automated at prediction time; no human edited, selected, or overrode any model output or predicted value. Human decisions were limited to pre-specified pipeline design and literature-derived prior values, all fixed before the target elicitation runs.

**B.1** — See metadata.json models list; exact API identifiers: gpt-5.6-terra, gpt-5.6-luna (OpenAI); openai/gpt-oss-120b (Groq); deepseek/deepseek-v3.2, meta-llama/llama-4-maverick (OpenRouter).

**B.2** — Provider HTTP APIs (OpenAI-compatible chat completions), stateless single-turn calls, 2026-08-18 (retrodiction runs 2026-08-17/18).

**B.3** — Provider-default sampling (no temperature/top-p passed); max output tokens 8192; one completion per (model x variant x intervention) cell, one resample retry on parse failure; no seeds (hosted APIs).

**B.4** — No fine-tuning, retrieval, tools, or web access. Literature conditioning occurs only through fixed reference-class anchor text in prompts and the prior blend in aggregation.

**B.5** — None; every call independent.

**B.6** — N/A (all hosted APIs).

**B.7** — Ensemble = 5 models x 12 prompt variants (6 for gpt-5.6-terra), pooled per cell by 20%-per-side trimmed mean, then the aggregation rule in G.3/F.2.

**C.1** — Verbatim prompt templates and variant generator deposited in the code repo (src/silicon/prompts_t3.py); design pre-specified, refined only during retrodiction pilots, frozen before target elicitation.

**C.2** — Three system framings (forecaster / methodologist / meta-analyst), verbatim in the deposited code.

**C.3** — Multi-prompt variation implements the measurement view of silicon sampling (prompt-specific bias cancels across variants; Cummins & Wulff): framings, anchor placement, and outcome order are deliberately varied and averaged.

**D.1** — Profiles: weighted draw from ACS 2023 1-year PUMS (18+, n=2.77M records), banded to the benchmark's exact levels; documented opt-in-panel education skew; benchmark quotas (gender x age, gender x race) hold by construction of the weighted draw; party from a CCAM-microdata x NPORS-margin raked table; condition assignment random, exactly 1,000/arm and 2,000 control. (Moderator cells use the full cohort as the group baseline population for smoothness.)

**D.2** — No verbalization — respondents are never shown to an LLM.

**D.3** — 18,000 profiles, no reuse, no weighting beyond the sampling design.

**E.1** — N/A at respondent level. State-adaptive arm: each treated profile's ACS state maps to its preregistered case; effects applied uniformly across cases.

**E.2** — N/A (no survey walk-through; response structure comes from the calibrated generative model).

**E.3** — N/A.

**F.1** — Fully deterministic given documented numpy seeds (in deposited code); regeneration reproduces the file bit-for-bit.

**F.2** — N/A at respondent level; Tier-3 aggregation rule as in the T3 primary form.

**G.1** — None.

**G.2** — All cells verified in range with exact level strings; moderation profile example: near-ceiling groups receive proportionally smaller effects (headroom mechanism), never exact zeros.

**G.3** — Baseline levels/shapes calibrated to ANES/TISP/CCAM/GSS/Pew (public); effect vector calibrated as per the T3 primary form (retrodiction).

**H.1** — None.

**H.2** — In-context: only the benchmark's own public materials (verbatim) and the fixed anchor paragraph. No retrieval.

**I.1** — No funding or in-kind support from LLM-interested entities. API usage paid personally at standard public rates (OpenAI, Groq, OpenRouter). No relationships with model providers beyond ordinary paid API access.

**I.2** — Reference surveys used for calibration: TISP (OSF), ANES 2016/2020 (public Dataverse replication copy), CCAM (OSF), GSS 2024, ACS 2023 PUMS, Pew/NPORS published toplines; plus the two retrodiction corpora (see T3 form). None from the target study.

**I.3** — I attest that no team member accessed, solicited, or was shown any human outcome data from this study, including pilots and the three disclosed talks, before the prediction lock. A signed declaration accompanies the deposit email.

**I.4** — Model training cutoffs (2025 for most roster members; gpt-5.6 family 2026) predate any release of this benchmark's results (unreleased). The benchmark's public materials (call, template) appeared mid-2026 and could in principle be in the newest models' training data; they contain no outcome information. The target study's preliminary-results talks were never searched for or accessed; web access was disabled for all prediction calls (plain chat completions).

**J.1** — Design space was explored exclusively by retrodiction on public studies (never on the target): a 72-combination grid over three aggregation hyperparameters (prior weight x shrinkage x trim) scored on two grounds — the Vlasceanu et al. 2024 US arm (11 interventions x 4 outcomes; effects computed from public Zenodo microdata) and a 129-contrast slice of the Hewitt et al. 2026 archive (Code Ocean, CC0). Selection criterion: mean RMSE rank across BOTH grounds (pre-registered internally before ground-2 elicitation; frozen-parameter confirmation run first). Model roster and prompt-variant count were fixed from leave-one-model-out and split-half reliability on ground 1. Approximately 2 small pilots (~30 calls) preceded each elicitation run.

**K.1** — Full pipeline code deposited (code_repository in metadata.json); seeds and deterministic aggregation documented; API keys excluded.

**K.2** — Raw logs of every LLM call feeding the effect vector (JSONL) in raw_data_deposit/, plus the deterministic generator code; public.

**K.3** — Whole project (all four entries + retrodiction tuning): ~5,500 API calls, ~30M tokens, ~$14 total, on laptop + public APIs; no GPUs.

**L** — Class A — every item public.
