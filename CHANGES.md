# Changes made to Customer-Segmentation-Recommendation

Re-run notebooks 01 -> 15 in order after importing these files (data generation changed).

| Notebook | Change |
|---|---|
| 01 | Each customer attribute now has its own hash (gender was fully determined by acquisition channel) |
| 03 | Orders dated on/after signup; data runs to 2026-11-29 so the 30-day outcome window has orders |
| 05 | Events dated on/after signup, up to 2026-11-29 |
| 06 | Support cases dated on/after signup, up to 2026-10-30 |
| 07 | RFM uses only delivered orders up to the analysis date (2026-10-30) |
| 08 | Fixed inverted recency score (r_score = ntile(5)); segment_rule table is now saved |
| 09 | SUPPORT_FOLLOWUP is one row (target ALL); added NO_MARKETING_ACTION; removed duplicate cells |
| 10 | One recommendation per customer; deterministic recommendation_id; added 1-per-customer check |
| 11 | Deterministic outcome_id |
| 12 | Future-order check moved to 2026-11-29; new checks: activity before signup, 1 recommendation per customer, consent checked against consent table |
| 14 | gold_customer_spending uses the same cut-off as RFM |
| 13 | Rewritten: tests the real pipeline tables (not hand-made rows). Each of the 4 issue types has a real check (must find 0) and a control check with one injected bad row (must find >=1). Results saved to `edge_case_test_results`; the old `test_*` tables are no longer created |
| README | Removed "Bronze/Silver" claim, added run order and data timeline |

Not changed: 15 (dashboard). Segment rules in 08 are still hard-coded.
