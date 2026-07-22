# Presenter notes · b6 - Loading patterns (45 min)

## Run of show
- 0-3 · Recap: the warehouse has shape (b2-b5); tonight it gets a heartbeat. Frame the night around the 2am crash question.
- 3-11 · Part 1: ETL vs ELT SVG, then the reveal: "you have been doing ELT since b2." Run the monthly_revenue playground as proof. dbt stays one card - resist the tangent.
- 11-19 · Part 2: full vs incremental SVG. Tell the 6am-cliff story from the Real world callout; define watermark, late arrival, batch window on the card.
- 19-24 · Part 3: idempotency. Set up the 2am scenario verbally - "can I just run it again?" - and promise the proof in Demo 2.
- 24-35 · Demo 1: walk the three batch rows' fates (insert, insert, update) BEFORE running, then run. Point at rows_before 53 / rows_after 55 in the result.
- 35-42 · Demo 2: idempotency proof (55 = 55, copies 1), then the room breaks it with plain INSERT (copies 2). The broken version is the memorable one.
- 42-45 · Q&A + homework pointer (the event-table merge-key exercise sparks the best discussion).

## Preflight
- Open the page, press Run once on the Part 1 playground before class - caches the 8 MB DuckDB engine so nobody waits live.
- Projector zoom ON; Expand all for Demos 1-2 (the MERGE boxes are long - scroll practice helps).
- Sanity-run Demo 1: expect three result rows (1032 refunded, 1034, 1035) with rows_before 53, rows_after 55.
- Sanity-run Demo 2 box 1: expect 55 / 55 / copies_of_1034 = 1.

## Never cut
- The "you have been doing ELT all along" reveal - it converts theory into recognition.
- Demo 1's row-fate walkthrough (the ON clause IS the session).
- Demo 2 run-twice proof AND the deliberate break - the pair is the lesson.

## Cut if long
- The dbt card (self-study by design).
- The late-arrival bonus callout after Demo 1 - mention, do not demo.
- The watermark self-study box - it returns as homework anyway.

## Likely questions
- "Is ELT always better?" - No: strict PII regimes that forbid landing raw data, or weak targets, still argue for ETL. Say "default ELT, justify ETL."
- "Why does the fact MERGE key on (order_id, product_key) and not order_id?" - The fact grain is the order LINE; one order holds many products. Key = grain.
- "What if the same batch row appears twice in one batch?" - MERGE requires one source row per target row; dedupe the batch first (row_number by key).
- "Delete-then-insert vs MERGE?" - Both idempotent. Partition replace is coarser and often cheaper at scale; MERGE is surgical. Engines and bills decide.
