# Presenter notes - Builder session 8: Performance and cost

## Run-of-show (45 min)

| Min | Beat |
|-----|------|
| 0-3 | Welcome. Frame: "every slow dashboard and every scary bill traces to one thing - scanning data you did not need." |
| 3-18 | Part 1-2: the three prunings (column, partition, clustering), how cloud engines implement them (micropartitions, partitioned+clustered tables), the storage-pennies vs compute-dollars cost model. |
| 18-30 | Part 3 + Demo 1: EXPLAIN a filtered query on big_orders; then time three variants (filtered 2-col, unfiltered 2-col, SELECT *) and read the ms deltas out loud. |
| 30-42 | Demo 2: pre-aggregation - build daily_summary, query it vs raw, the 40x/day dashboard decision; self-study index card. |
| 42-45 | Quiz + cheat sheet. Tie forward: b9 makes the data portable, b10 assembles everything. |

## Preflight
- Open the page and press Run on one big_orders box BEFORE class - caches the 8 MB engine so the first live timing is not dominated by download.
- Run all three Demo 1 variants once yourself so you know tonight's actual ms numbers (they vary by machine; the RATIO is the lesson, not the absolute).

## Never cut
- The live ms comparison in Demo 1. Feeling SELECT * cost real milliseconds is the whole session.
- "Storage is pennies, compute is the bill" - the one line execs and engineers both need.

## Cut if long
- The EXPLAIN plan reading (Part 3) - mention it exists, show one, move on.
- The b-tree-index self-study card - it is genuinely self-study.

## Likely questions
- "So indexes are useless in a warehouse?" - Not useless, just rarely worth it: zonemaps + full-column scans beat b-trees for the all-rows-few-columns workload. Point lookups still like an index.
- "How do I see this on Snowflake/BigQuery?" - Query history + bytes-scanned per query. Same lesson, their console.
- "Is pre-aggregation always worth it?" - No. Worth it when a query runs far more often than the underlying data changes. A once-a-day report does not need a materialized view.
