# F26 DIIG NC Hotel Group Data Challenge

**Joshua Wu · NetID: jw1059**

A reproducible analysis of reservation cancellation/no-show exposure for NC Hotel Group. The central question is: **which reservations create the largest avoidable exposure, and what reversible pilot should the group test?**

## Headline findings

- The cancellation/no-show label rate is 37.69% across 20,000 rows; exact deduplication changes it to 31.00% (duplicate sensitivity is material).
- City Hotel (42.73%) and Groups (63.05%) have higher observed label rates; City × Groups is 72.09%.
- Risk rises with lead time: 6.70% at 0 days versus 58.45% at 181+ days.
- A chronological logistic model reaches test AUC 0.733 and Brier score 0.197 versus a 0.239 baseline.

ADR × stay nights is a **gross exposure proxy**, not realized lost revenue. The data cannot establish causal lift, safe overbooking, profit impact, or channel-shift economics.

## Repository contents

- `nchg_submission.ipynb` — executed analysis notebook
- `nchg_submission_deck.pdf` — final 10-page presentation
- `nchg_submission_deck.pptx` — editable 10-slide deck
- `TALK_TRACK.md` — presentation talk track
- `data/nc_hotel_group.csv` — anonymized challenge dataset
- `data/evidence/` — reproducibility tables used by the analysis
- `requirements.txt` — Python dependencies

## Reproduce

From the repository root, create a clean Python 3.11+ environment and run:

```bash
python -m venv .venv
. .venv/bin/activate                 # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace nchg_submission.ipynb
```

The notebook reads only `data/nc_hotel_group.csv` and `data/evidence/` via repository-relative paths. Do not commit `.venv`, notebook checkpoints, or other generated output.

## Method and limitations

The workflow audits schema, missingness, status consistency, duplicates, and outcome rates; compares segments and lead-time bands; and fits a chronological logistic model with frozen-rule evaluation and calibration checks. Duplicate records are retained for the primary row-level view and assessed separately because they change the answer. Historical timing and label leakage require review before deployment.

The recommended next step is a randomized, blocked pilot for eligible long-lead/high-risk bookings, measuring conversion, kept nights, refunds, contacts, and net contribution. Inventory, capacity, commissions, replacement demand, walk costs, and fee recovery are absent, so capacity decisions require additional data.
