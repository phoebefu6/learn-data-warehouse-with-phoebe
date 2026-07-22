# Presenter notes · b5 - Slowly changing dimensions (45 min)

## Run of show
- 0-3 · Recap: staging + star are live; tonight adds dim_customer_scd. Point at the Part 0 build-state paragraph.
- 3-10 · Part 1: tell the Liam Ford story BEFORE showing the SVG, then let the before/after report land the punch. Key line: "history that rewrites itself is a lie."
- 10-18 · Part 2: the SCD menu SVG. Spend the time on Type 2 and the surrogate-key card; Types 0/3 get one sentence each.
- 18-24 · Part 3: run both small playgrounds live (current view, version counts). Say the coalesce 9999-12-31 idiom out loud twice.
- 24-36 · Demo 1: the three moves by hand, then the point-in-time report. Have the room run the "try the lie" tip - the contrast is the lesson.
- 36-42 · Demo 2: MERGE version live; Zoe Tan your-turn is the room's solo work. Self-study card is homework fodder.
- 42-45 · Q&A + homework pointer (the overlap-bug exercise is the one to plug).

## Preflight
- Open the page, press Run once on the first Part 3 playground before class - caches the 8 MB DuckDB engine so nobody waits live.
- Toolbar: Projector zoom ON, Expand all ON for the demo sections.
- Have b1 open in a second tab in case someone asks "what is DuckDB again."
- Sanity-run Demo 1 box 1: expect two rows for customer 2 (Basic sealed Jun 30, Pro open from Jul 01).

## Never cut
- The overwrite lie story + SVG (Part 1) - the whole session hangs on it.
- Demo 1 box 1 (the three moves) and the timeline read-back.
- The surrogate vs durable key card - the quiz and b6 both depend on it.

## Cut if long
- Type 3 discussion (leave it at "one step of history, rare").
- The "try the lie for contrast" tip - assign as homework instead.
- Demo 2 self-study card (point-in-time per order) - it is written to be read alone.

## Likely questions
- "Why not just snapshot the whole dimension daily?" - You can (that is a Type 2 cousin); it trades storage for simplicity. At scale, versioned rows win.
- "Who decides the effective date?" - The business event, not the load time. If the source only tells you when it noticed, document that honestly.
- "Does MERGE handle the new version row too?" - Not in one statement: MERGE routes changed vs new; one INSERT opens the new versions. Two statements, one script.
- "What about deletes - a customer leaves?" - Close the row out (valid_to stamped, is_current FALSE) and insert nothing. History keeps them; the current view drops them.
