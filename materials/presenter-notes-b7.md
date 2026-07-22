# Presenter notes · b7 - Marts and serving (45 min)

## Run of show
- 0-3 · Recap: the core is complete (staging, star, SCD, loads) - "and nobody outside the data team has touched it." Tonight it becomes a product.
- 3-11 · Part 1: the three-marts SVG, then the triangle card (view / matview / table). The one-liner to repeat: "the refund rule lives in ONE place."
- 11-18 · Part 2: ROLLUP. Show the shape SVG first so eyes know what to hunt for, then run the playground and have the room find the grand-total row.
- 18-23 · Part 3: serving surfaces + the semantic contract. Tell the renamed-column horror story from the Real world callout - it always lands.
- 23-35 · Demo 1: build both marts. Emphasize the OPPOSITE policy calls: finance drops refunds, marketing features them. Same star, two truths, both governed.
- 35-42 · Demo 2: Q1 and Q2 are the room's solo work (answers in the boxes - push them to try blind first). Q3 PII card: read the two column calls aloud even if short on time.
- 42-45 · Q&A + homework pointer (the break-a-contract exercise is the sticky one).

## Preflight
- Open the page, press Run once on the Part 2 playground before class - caches the 8 MB DuckDB engine so nobody waits live.
- Projector zoom ON; Expand all for Demos 1-2.
- Sanity-run Demo 1 box 1: expect six monthly rows, Jan-Jun 2026, completed revenue only.
- Sanity-run the ROLLUP playground: the top row should be the both-NULL grand total (sorted by revenue DESC).

## Never cut
- The marts SVG + "policy written once" framing - it is the session's thesis.
- Demo 1's two opposite policy calls (finance vs marketing).
- The semantic-contract card - b8 and every real deployment depend on it.

## Cut if long
- Part 2 self-study (when to pre-aggregate) - it reads fine alone.
- The four serving surfaces card - name the four, skip the detail.
- Demo 2 Q2 (ROLLUP mart) - the playground already taught ROLLUP; keep Q1 and Q3.

## Likely questions
- "Does DuckDB have materialized views?" - Plain views yes; scheduled materialization is a cloud-engine feature (Snowflake, BigQuery, Redshift). Here we simulate with CTAS + the b6 load.
- "Why is NULL the subtotal marker - is that not confusing with real NULLs?" - It can be; engines offer GROUPING() to tell them apart. For teaching, the ORDER BY trick makes the totals obvious.
- "Marts vs data mesh domains?" - Same instinct (team-shaped, owned slices); mesh formalizes ownership and contracts org-wide. Out of scope tonight, fair dinner conversation.
- "Who owns a mart's definition?" - The consuming team owns the POLICY, the data team owns the implementation. Write both names into the contract doc.
