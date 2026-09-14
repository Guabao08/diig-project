## 1. NC Hotel Group | F26 DIIG
Joshua Wu · jw1059
A booking-time risk lens for a reversible pilot

## 2. The decision
Which reservations create the largest avoidable cancellation/no-show exposure—and what should NCHG test?

20,000 reservation rows | Jul 2015–Aug 2017 | 2 properties

## 3. Audit before action
37.69% cancellation/no-show label rate
3,486 exact duplicate rows beyond first (1,338 groups)
Status and label are perfectly consistent

Duplicates are not silently deleted: they change the answer.

## 4. Headline: a material sensitivity
Raw rows: 37.69% label rate | $2.815m gross exposure proxy
Exact-deduplicated: 31.00% | $2.219m

ADR × stay nights is a gross exposure proxy—not lost revenue.

## 5. Where risk sits
City Hotel: 42.73% vs Resort: 27.91%
Groups: 63.05% cancellation/no-show label rate
City × Groups: 72.09%

Property mix and segment composition matter.

## 6. Lead time is the clearest gradient
0 days: 6.70%
31–90 days: 37.86%
181+ days: 58.45%

Long-lead bookings are a natural early-confirmation experiment population—not a reason to reject demand.

## 7. Signals, with causal caution
Non Refund: 99.49% (n=2,554)
Returning guest: 14.85% vs 38.47% non-returning

These are associations. Deposit/channel changes may alter conversion, mix, fees, and service.

## 8. Can we target risk?
Chronological logistic model
Test AUC 0.733 | Brier 0.197 vs 0.239 baseline
Frozen Non Refund rule: 100% test label rate; 18.6% of test labels

Monitor calibration drift; verify history timing.

## 9. Limitation: what this file cannot answer
No room count or inventory/capacity
No commissions, replacement demand, walk costs, or fee recovery
No causal policy assignment or experiment

Therefore: no safe overbooking multiplier, profit lift, or channel-shift claim.

## 10. Recommendation | targeted pilot
1. Audit duplicate identity and field timing
2. Randomize confirmation/deposit offer for eligible long-lead/high-risk bookings
3. Block by property, channel, lead band, arrival month
4. Measure conversion, kept nights, refunds, contacts, net contribution
5. Add inventory + economics before capacity decisions
