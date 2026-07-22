# Presenter notes · b3 - Facts and dimensions

## Run of show (45 min)
- 0-3 · Recap: staging is live and gated. Hook: "trusted copies are still OLTP-shaped - tonight we reshape."
- 3-12 · Part 1: say the grain sentence out loud and make the room repeat it ("one row = one order line"). Star SVG: amber row = measures, arms = context. Run the orders-vs-lines count box - the gap IS the grain.
- 12-18 · Part 2: Inmon vs Kimball, one card each, then the SVG side panel: "we walk Kimball's road because Daybreak needs answers this quarter." Name One Big Table, park it for b9.
- 18-23 · Part 3: the mapping table. Do NOT read every row - pick three (a measure, an attribute, order_id as degenerate) and let the table document the rest.
- 23-35 · Demo 1: build the star. Call out each of the four moves by name before running. After the counts land, ask "what if the fact had MORE rows than stg_order_items?" - fan-out check.
- 35-42 · Demo 2: Q1 and Q2 live (the payoff moment - keep energy high, this is why they came), Q3 self-study.
- 42-45 · Q&A + homework.

## Preflight
- Open the page and press Run once BEFORE class so the 8 MB engine is cached; also pre-run the Demo 1 box once so you know the timing.
- The Demo 2 boxes use data-setup="star" - remind the room these start from the FINISHED star; their Demo 1 build does not carry over (fresh database per Run).
- Have the b2 page reachable: the staging schema columns come up when someone asks where line_amount was born.
- Projector zoom: on.

## Never cut
- The grain sentence, said aloud, before any SQL. It is the session's title in disguise.
- The "can I SUM it?" vs "do I GROUP BY it?" test - fastest fact/dim classifier that exists.
- Demo 2 Q1: revenue by month with zero date functions - the payoff of the whole architecture so far.

## Cut if long
- Part 1 self-study card (grain disasters) - written for home reading.
- Inmon card details: compress to "normalized enterprise core first, months to first answer" and move on.
- Demo 2 Q3 (top products) - it is already marked self-study; skip the walkthrough entirely if under 8 minutes remain at 35.

## Likely questions
- "Why one row per LINE and not per order?" - Order 1001 holds two products; order-level rows make "revenue by product" impossible. Roll up any time, drill below the grain never.
- "Isn't denormalizing what the SQL course said not to do?" - Yes, deliberately: apps optimize safe writes (normalize), analytics optimizes wide reads (denormalize). Opposite pressures, both correct.
- "Why is status on the fact, not a dimension?" - Three values, no attributes of their own: a dim would be ceremony. Judgment call, documented in the mapping table - that documentation habit is the real lesson.
- "Which school does dbt / our stack follow?" - Most modern ELT teams are Kimball-ish (staging then marts on shared dims), often without saying the name.
- "Where did dim_date come from in Demo 2?" - The star setup ships it pre-built; b4 opens by building it properly with generate_series.
