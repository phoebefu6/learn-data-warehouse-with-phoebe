# Presenter notes - Builder session 10: Capstone (the whole warehouse)

## Run-of-show (60 min - note the longer budget)

| Min | Beat |
|-----|------|
| 0-3 | The brief: Friday board pack (monthly revenue, refund rate by channel, weekend share, top products). "Tonight you build the whole thing that makes these easy." |
| 3-6 | Part 1: the one-strip pipeline recap. Keep it fast - this is a doing session. |
| 6-18 | Demo 1 Stage it: staging + three quality gates. Emphasize the boring summary row is the pro move. |
| 18-36 | Demo 2 Model it: the long star-build script. Narrate that every line is a prior session. Do the SCD self-study card only if the room is fast. |
| 36-52 | Demo 3 Serve it: four board answers + the Parquet export. Let them feel how short each query is now. |
| 52-60 | Part 3 wrap: what they can do, where to go next, the honest gap list. Send them off with a next course chosen. |

## Preflight
- Budget the full 60 min - the Model-it script is long and people type at different speeds. Do not start Demo 2 after minute 20 or you will run over.
- Press Run once on a Demo 3 (star) box before class to cache the engine.
- Pre-run the whole Demo 2 script yourself; if a learner's box errors, the usual cause is a missing semicolon between statements when they edited.

## Never cut
- Demo 3. The payoff of the entire course is watching board questions become five-line queries. Protect this slot even if Demo 2 runs long.
- The "define the metric once" point on Answer 1 (completed-only revenue) - it closes the loop back to leader session a3.

## Cut if long
- The SCD self-study card in Demo 2 (it is already marked self-study).
- Part 3's gap-list card - assign as reading rather than presenting.

## Likely questions
- "Why rebuild staging in Demo 2 instead of reusing Demo 1's tables?" - Fresh database per Run. It is the idempotency lesson made physical: self-contained scripts.
- "In production would I really rebuild the whole star every night?" - Small warehouses, yes (full rebuild is simple and correct). At scale you switch to the incremental MERGE pattern from b6.
- "Where does this run for real?" - Same SQL on DuckDB locally, or Snowflake/BigQuery/Redshift in the cloud. The modeling does not change; only the engine and the orchestration around it.
- "What is not in this course?" - Orchestration, permissions, BI tools. Name the sibling courses that own each.
