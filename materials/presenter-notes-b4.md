# Presenter notes · b4 - Building dimensions

## Run of show (45 min)
- 0-3 · Recap: star stands, but the arms were built on faith. Hook: "facts are boring, dimensions carry the judgment - tonight is craft night."
- 3-10 · Part 1: the surrogate-key SVG. Walk the collision story (two customer_id 7s) slowly, then point at the grey row: "two versions of Ava, side by side - hold that for b5." Land the three escapes as a chant: change, collide, history.
- 10-16 · Part 2: build dim_date live with generate_series, then the "why not strftime everywhere" card - consistency, logic-lives-once, pruning (promise b8 for proof).
- 16-21 · Part 3: conformed dimensions SVG. The one-liner that lands with practitioners: "two private customer tables = two revenue numbers in the same board meeting."
- 21-33 · Demo 1: dim_date + dim_customer + the weekend-by-plan payoff. Run it, then do one bend (swap plan for city) so they see the one-line-change ease.
- 33-42 · Demo 2: Q1 and Q2 live; introduce Q3's acquisition scenario verbally (30 seconds, it hooks) and assign the card as self-study.
- 42-45 · Q&A + homework + tee up b5: "next week Ava moves to Denver and history gets interesting."

## Preflight
- Open the page and press Run once BEFORE class so the 8 MB engine is cached - cold-cache first Runs stall the room.
- Pre-run Demo 1 once; the three-statement script is the longest of the night and you want its timing in your hands.
- Remember state never carries between boxes: Q1 and Q2 each rebuild their own dimension - say this before Demo 2 or someone will ask why their Demo 1 tables "disappeared".
- Projector zoom: on. Keep b3's star SVG one tab away for the recap.

## Never cut
- The three escapes (keys change, keys collide, history needs room) - the whole session hangs on them, and b5 assumes them.
- Building dim_date live with generate_series - watching a table appear from a series is the night's small magic trick.
- The conformed-dimension one-liner about two revenue numbers in one board meeting.

## Cut if long
- Part 1 self-study card (when natural keys are fine) - flag dim_date's natural key in one sentence and move on.
- Part 3's "what conformance costs" card - compress to "someone must own the shared dim; forks drift" and point to leader session a3.
- Demo 2 Q2 (price_band) can go to homework; keep Q1 - quarters reappear in b7's mart queries.

## Likely questions
- "Why not hash the natural key instead of row_number?" - Valid pattern (mentioned in Part 1's card): computable without a lookup, but collisions and re-keying have their own scars; this track keeps keys deterministic and visible.
- "Why does dim_date get a natural key when you just argued against them?" - A calendar date never changes, never collides, needs no versions - the three escapes are all moot. Rules follow reasons.
- "Our BI tool auto-generates date logic - do we still need dim_date?" - Yes: the tool's logic lives per-dashboard; the dimension's lives once for every tool, plus fiscal columns and pruning.
- "Who owns the conformed dimension at a real company?" - A named data team or domain owner with a review path for additions - the governance half is leader-track a3.
- "Can a dimension have two natural keys?" - After an acquisition, yes: source_system + source_id pairs on one dimension - exactly Q3's debrief.
