# Presenter notes · b2 - Architecture and the staging layer

## Run of show (45 min)
- 0-3 · Recap b1 in one breath: OLTP vs OLAP, columnar, DuckDB in the tab. Then the hook: "the warehouse is still an empty lot - tonight we pour the foundation."
- 3-11 · Part 1: three layers on the SVG. Walk left to right, land hard on "each layer only reads the layer before it" and "never model on raw."
- 11-18 · Part 2: CREATE TABLE AS + CAST live (stg_orders + typeof proof), then TRY_CAST vs CAST on the junk-values box.
- 18-25 · Part 3: the four gates. Run the PASS/PASS/PASS/PASS script, then break gate 1 live (DELETE one row from stg_orders) and re-run - the FAIL gets a laugh and sticks.
- 25-37 · Demo 1: everyone builds the full staging layer. Do the four steps slowly; step 4 (add a WHERE, then undo it) is the teaching moment: staging copies, it does not filter.
- 37-42 · Demo 2: Q1 and Q2 live, Q3 assigned as self-study.
- 42-45 · Q&A + point at homework.

## Preflight
- Open the page and press Run once BEFORE class so the 8 MB DuckDB-WASM engine is cached - first Run on a cold cache takes several seconds and kills the demo rhythm.
- Check the venue network anyway: the engine download is the only network dependency; after that everything is local.
- Projector zoom: on. Expand all: off (open cards as you reach them).
- Have b1's page in a second tab in case someone asks for the typeof(order_date) VARCHAR proof from last week.

## Never cut
- The "never model on raw" rule and the four promises (typed, renamed, quality-gated, replayable).
- Breaking a quality gate live in Part 3 - PASS lists are forgettable, a FAIL you caused is not.
- Demo 1 step 4: staging copies, filtering is a core-layer decision made in daylight.

## Cut if long
- Part 1 self-study card (dbt / medallion mapping) - it is written to be read at home.
- The Real-world callout in Part 2 (CAST vs TRY_CAST choice) - compress to one spoken sentence.
- Demo 2 Q2 can move to homework; keep Q1 (it completes the staging layer).

## Likely questions
- "Why copy instead of a view over source?" - Views still hit the source with every dashboard query (b1's frozen checkout again) and cannot be gated; a materialized copy is inspected once and read forever.
- "Who decides the allowed status values in Q2?" - The source team + analytics together: that agreement IS a data contract; the query just enforces it.
- "TRY_CAST hides errors, is that safe?" - It defers them: the NULLs land, gate 3 counts them, a human decides. The unsafe option is CAST failing at 3am with nobody deciding anything.
- "Do real teams really re-run the whole layer?" - Small tables, yes (this is that case); big tables load incrementally - that is b6, promise it.
