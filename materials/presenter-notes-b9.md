# Presenter notes - Builder session 9: Lakehouse and the modern stack

## Run-of-show (45 min)

| Min | Beat |
|-----|------|
| 0-3 | Welcome. Frame: "warehouse and lake spent a decade converging - tonight you touch the thing that joined them: files you can run SQL on." |
| 3-16 | Part 1: warehouse vs lake vs lakehouse, the convergence timeline, Parquet + Iceberg/Delta name-drops (no hands-on on table formats). |
| 16-28 | Part 2: beyond the star - One Big Table and Data Vault, when each beats Kimball, honest "star is still Daybreak's default". |
| 28-42 | Demo 1 + Demo 2: the Parquet round trip LIVE (COPY to file, SELECT from file), then export a mart; self-study OBT build. |
| 42-45 | Quiz + cheat. Forward: b10 uses this export as the shippable board pack. |

## Preflight
- Press Run on the Demo 1 Parquet box before class - it both caches the engine and confirms the in-browser filesystem write works on the room's network.
- Have the OBT self-study answer ready in case someone asks "how many columns did it flatten to."

## Never cut
- The Parquet round trip. "You just built lakehouse mechanics in a browser tab" is the aha moment.
- The honest guidance that star remains the default - stops people cargo-culting Data Vault into a 5-table shop.

## Cut if long
- The Iceberg/Delta detail in Part 1 - name them, say "transactions on top of files", move on.
- The Data Vault deep bits - it is a "know it exists" topic for this course.

## Likely questions
- "Is DuckDB reading Parquet the same as a real lakehouse?" - Mechanically yes (SQL over columnar files); a production lakehouse adds a catalog, transactions, and cloud storage. Same idea, more plumbing.
- "When would I actually pick One Big Table?" - Small team, a BI tool that hates joins, one dominant query shape. It trades storage and flexibility for join-free speed.
- "Lake or warehouse first for a new company?" - Almost always a warehouse first. The lakehouse pitch is for scale and variety you probably do not have yet.
