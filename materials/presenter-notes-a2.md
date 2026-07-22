# Presenter notes · Leader session 2 · The shape of a warehouse

## Run of show (45 min)

| Minutes | Beat |
|---------|------|
| 0-3 | Welcome back. Recap a1 in one line ("we build a governed copy - today: what it looks like inside"). Collect a few buy-signal scores from homework. |
| 3-8 | Introduce the factory metaphor BEFORE any jargon: receiving dock, assembly floor, shipping dock. Then map the names: staging, core, marts. |
| 8-15 | Three-layer SVG. Walk order 1017 through the building out loud - the journey strip at the bottom is the beat to slow down on. |
| 15-20 | Staging card ("no business logic here" is the discipline point) + core card. Deliver the meeting-ready line: sources said / business means / teams need. |
| 20-28 | Star schema. Facts = verbs with numbers, dimensions = nouns. Star SVG: point at the fact, then each noun. Land "one obvious join". |
| 28-33 | Why stars make questions cheap - run the revenue-by-month-by-city example verbally, adding one noun at a time. |
| 33-40 | Who does what: engineers/analysts/business mapping, then the "three copies?!" boardroom moment - tell the COO story with the pause before "carry on". |
| 40-45 | Q&A + homework: find the three layers on your own team's diagram (warn: they may be called bronze/silver/gold). |

## Preflight checklist

- [ ] Both SVGs render; check the star's connector lines sit under the boxes, not over text
- [ ] "Expand all" works; first card (Staging) is open by default
- [ ] Quiz answers verified: 1-C, 2-A, 3-B
- [ ] Have one real architecture diagram (anonymized) ready to screen-share for the homework preview
- [ ] Rehearse the coffee-factory metaphor with Daybreak specifics: beans in, roasted batches, packed subscriptions

## Never cut

- The factory metaphor and the trust/shape/convenience triple - it is the retention device
- Order 1017's journey through all three layers
- "Facts are verbs with numbers, dimensions are the nouns"
- Business owns definitions (sets up a3 - do not soften this)

## Cut if long

- Kimball vs Inmon card (self-study; one sentence suffices live: "two schools, both fine, we teach stars")
- The unhealthy-division-of-labor card (self-study)
- Second pass on the marts card - the shipping-dock line carries it

## Likely exec questions + crisp answers

- "Why are we storing three copies of the same data?" - They are stages, not copies: what sources said, what the business means, what each team needs. A factory holds raw stock, assemblies, and packed goods too.
- "Bronze/silver/gold - is that the same thing?" - Yes. Different vendor paint, same factory: staging, core, marts.
- "Can we skip a layer to save money?" - Skipping staging means bad source data lands in board numbers. Skipping core means every mart invents its own truth. The layers ARE the savings.
- "Why not one big table with everything?" - It works until the second team needs a different everything. Stars stay predictable as questions multiply.
- "Who decides what 'active customer' means?" - You do. Business defines, engineering encodes once, analysts reuse. That handshake is next session.
