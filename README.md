# ULAK public forecast ledger

**CDLI** ([cdli.ai](https://cdli.ai)) publishes every ULAK forecast here *before* the event it
is about, then scores it once the outcome is known. Misses are published alongside hits.

Each file under `forecasts/` holds one batch of probabilities, for example "Will this TBMM
bill be adopted by the Genel Kurul by date D?" or "Will the CBRT cut rates at the next MPC
meeting?".

## How to verify

1. The **git commit time** of a file shows it existed publicly before the event.
2. Its **SHA-256** in [HASHES.md](HASHES.md) proves the content never changed:
   `sha256sum forecasts/<file>`.
3. Published forecast files are never edited. Withdrawn files stay public under
   `withdrawn/`, with the reason.

## Status (updated 2026-10-19 06:55 UTC)

- Forecasts registered: **1068** (official files only)
- Resolved so far: **0**

| File | Forecasts | Resolved | Brier (resolved) |
|---|---|---|---|
| prereg_bench_20261018T093507Z.jsonl | 252 | 0 | — |
| prereg_bills_20261017T112200Z.jsonl | 203 | 0 | — |
| prereg_bills_20261017T113200Z.jsonl | 203 | 0 | — |
| prereg_bills_20261018T043003Z.jsonl | 203 | 0 | — |
| prereg_bills_20261019T043003Z.jsonl | 203 | 0 | — |
| prereg_cpi_20261018T085936Z.jsonl | 2 | 0 | — |
| prereg_tcmb_20261017T113447Z.jsonl | 2 | 0 | — |

## Record format

Each line of a `forecasts/*.jsonl` file is one forecast, with these fields:

- `qid`, `statement_tr` (the question);
- `as_of` (when it was made) and `deadline`;
- `p` (the probability of "yes");
- `model_id`;
- bill fields (`esas`, `title`, `page_url`, `stage`) or TCMB inputs.

Scores in `scores/` are recomputed daily from public TBMM and CBRT outcomes.

*Event probabilities for research and information. Not investment, legal or financial
advice.*
