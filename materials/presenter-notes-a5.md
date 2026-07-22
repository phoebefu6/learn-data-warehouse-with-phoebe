# Presenter notes · Leader session a5 · Cost and performance

## Run of show (45 min)

| Minutes | Beat |
|---------|------|
| 0-3 | Welcome. Hook: "the warehouse bill is the most negotiable line in your data budget - and the least read." |
| 3-10 | Part 1 bill-anatomy SVG. Land the shape first: storage sliver, compute bulk, amber waste band. Then the three culprits: SELECT *, auto-refresh for nobody, the intern's cross join. |
| 10-15 | The meter runs on scans, not answers. Dashboard-that-cost-more-than-the-analyst story. |
| 15-20 | Why "add an index" fails here - bridges anyone with app-database instincts to the columnar toolkit. |
| 20-30 | Part 2 four-levers SVG, one lever at a time with its plain-words payoff: ask for less / skip most of the data / compute once read many / warehouses that sleep. |
| 30-34 | Translation drill: what each lever sounds like in a status update. The doubling question: "if data doubled, would the bill double?" |
| 34-41 | Part 3 five monthly questions + what good answers sound like. Boardroom moment: 80% spend growth defended in ninety seconds. |
| 41-42 | Balance beat: when the bill SHOULD go up - target is no amber band, not a small number. |
| 42-45 | Quiz + Q&A. Homework: get the bill, predict the split before looking. |

## Preflight

- Test both SVG zooms; the four-levers figure is the session's anchor slide.
- If possible, bring ONE anonymized real bill screenshot - it triples engagement.
- Rehearse the five questions from memory; execs copy them down live.

## Never cut

- Storage sliver vs compute bulk vs amber band - the whole session hangs on this picture.
- The meter charges for data touched, not answers returned.
- Lever order: 1-3 need attention, not budget; teams wrongly reach for 4 first.
- The five monthly questions (the take-home deliverable).

## Cut if long

- The index self-study card (name it, skip it).
- Two of the four "status update" translations (keep levers 1 and 3).
- The when-bills-should-rise card - compress to its one line: judge the bill by what came back.

## Likely exec questions

- "What's a normal warehouse spend?" - "There is no benchmark that survives contact with your workload. The healthy sign is answered questions, not a target number."
- "Should we just renegotiate the contract?" - "After shrinking the amber band - negotiating on a wasteful workload locks the waste in."
- "Isn't this the data team's job?" - "Pulling levers, yes. Asking the five questions monthly is governance - that is yours."
- "How fast can the bill come down?" - "Auto-suspend and refresh schedules move in days; partitioning and materialized views in weeks. The story arrives before the savings."
