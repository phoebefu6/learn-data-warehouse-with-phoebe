# learn-data-warehouse-with-phoebe - official course map

Built 2026-07-22. Build-first mode: constructed from verified public syllabi; Phoebe's platform
notes slot in later (marked NOTES-SLOT). Re-verify engine specifics (Snowflake/BigQuery pricing,
DuckDB-WASM versions) before each delivery - fast-moving space.

## Scope contract (locked with Phoebe, 2026-07-22)

- **Owns:** warehouse architecture (staging / core / marts), OLTP vs OLAP, columnar storage,
  ELT loading patterns (full / incremental / MERGE / idempotency), SCD in practice, engine
  landscape (Snowflake / BigQuery / Redshift / Databricks / DuckDB), lakehouse vs warehouse,
  performance + cost.
- **Prereq siblings (do NOT re-teach in depth):** `learn-data-modeling` (Kimball depth, schema
  design theory), `learn-data-engineering` (pipelines, orchestration, Spark/streaming),
  `learn-sql` (query language - Daybreak DB originates there).
- **Running case:** Daybreak coffee, grown up - the learn-sql OLTP database becomes the source
  system; the course builds Daybreak's first warehouse on top of it.
- **Live layer:** `warehouse-live.js` - DuckDB-WASM (real columnar OLAP engine, in-browser).
  Loaded from jsDelivr CDN (~8MB compressed one-time; raw wasm is 41MB - too heavy to vendor).
  Honest note on pages: playground needs network for first load, cached after.
- **Hub:** bucket `deng`, diff 3. Ladder: sql (2) -> data-modeling (3) -> **data-warehouse (3)**
  -> data-engineering (4) -> dataops (4).

## Source universe (verified syllabi, fetched 2026-07-22)

| # | Source | Status | Role |
|---|--------|--------|------|
| S1 | Coursera - IBM **Data Warehouse Fundamentals** | full syllabus fetched | spine: architecture, marts/lakes/lakehouse, facts+dims, staging, populate, query, cubes/rollups/materialized views |
| S2 | DeepLearning.AI **Data Engineering C4: Data Modeling, Transformation, Serving** (Joe Reis) | full syllabus fetched | authority: Inmon vs Kimball, normalization, star schema, data vault, one big table, serving, views/mat views |
| S3 | 365 Data Science **Introduction to Data Warehousing** | full curriculum fetched | deltas: SCD, partitioning, indexing, perf optimization, real-time DW, DW vs lakehouse, lifecycle, capstone shape |
| S4 | LinkedIn Learning **Advanced Snowflake: Deep Dive** (Janani Ravi) | TOC fetch 403-blocked; topics from search: micropartitioning, clustering, table types | perf-session delta only; re-verify TOC before teaching |
| S5 | LinkedIn Learning **Introduction to Data Warehouses** (Deepak Goyal) | topic-level only | nugget: when NOT to use dimensional modeling |
| S6 | Udemy dbt Bootcamp + companion repo (github.com/nordquant/complete-dbt-bootcamp-zero-to-hero) | not fetched | optional ELT-transform flavor in b6; dbt depth belongs to data-engineering sibling |

**Overlap finding:** S1, S2, S3 share ~70% spine (star schema, ETL/ELT, architecture, SCD).
Shared core taught ONCE across b2-b7; per-source deltas noted per session below.

## Not covered by design (honest list)

- Kimball bus-matrix / dimensional-design depth -> `learn-data-modeling`
- Orchestration, Spark, streaming, CDC (S2 module 3) -> `learn-data-engineering`
- ML feature modeling (S2 module 2) -> ds bucket courses; a6/b10 mention serving-for-ML only
- Vendor certifications, BI tool depth (Cognos/Tableau/Power BI), dbt beyond one demo
- SQL syntax itself -> `learn-sql`

## Session coverage map

Legend: ✓ = taught to ~80% working depth · ◐ = touched, pointer given

### Leader track (a1-a6, 45 min each, exec thinking-mode)

| Session | Covers | S1 | S2 | S3 |
|---------|--------|----|----|----|
| a1 Why a warehouse | OLTP vs OLAP, what breaks without one, Daybreak dashboard chaos story | ✓ M1 overview | ◐ | ✓ S2 foundations |
| a2 Shape of a warehouse | staging/core/marts, star schema in plain words, one-truth flow | ✓ M2 architecture | ✓ M1 star | ✓ S3 design |
| a3 One-truth problem | why two dashboards disagree; conformed dims, metric layer, governance handshake | ◐ | ✓ M1 | ✓ S4 quality/governance |
| a4 Buy landscape | warehouse vs lake vs lakehouse; Snowflake/BigQuery/Redshift/Databricks/DuckDB; cloud vs on-prem | ✓ M1 systems | ◐ | ✓ S6 tools, S7 lakehouse |
| a5 Cost + performance | why bills explode; columnar, partitioning, caching in exec terms; questions to ask | ◐ M2 cubes | ◐ M4 | ✓ S3 partitioning/indexing |
| a6 Warehouse in AI era | serving analytics + ML/AI, real-time DW, what to ask your team, roadmap | ◐ | ✓ M4 serving | ✓ S7 real-time |

### Builder track (b1-b10, 45 min each, Daybreak running project, live DuckDB playgrounds)

| Session | Covers | S1 | S2 | S3 | S4 |
|---------|--------|----|----|----|----|
| b1 Row store meets column store | Daybreak OLTP recap, DuckDB intro, columnar vs row demo, first OLAP queries | ✓ M1 | ◐ | ✓ S2 | |
| b2 Architecture + staging | 3-layer architecture, build staging layer, raw loads, data quality gates | ✓ M2 staging + quality labs | ◐ | ✓ S3/S4 | |
| b3 Facts + dimensions applied | OLTP schema -> star schema transform (modeling as prereq, applied here), grain | ✓ M2 facts/dims | ✓ M1 star, Inmon vs Kimball | ✓ S3 | |
| b4 Building dimensions | surrogate keys, date dimension, conformed dims | ✓ M2 | ✓ M1 | ◐ | |
| b5 SCD in practice | Type 0/1/2 (+3 mention), live MERGE Type 2 | ◐ | ◐ | ✓ S7 SCD | |
| b6 Loading patterns | ETL vs ELT, full vs incremental, idempotency, MERGE, automation; dbt one demo | ✓ M2 populate labs | ✓ M1 dbt | ✓ S5 loading/automation | |
| b7 Marts + serving | data marts, views vs materialized views, cubes/rollups, BI serving | ✓ M1 marts + M2 cubes | ✓ M4 serving/views | ✓ S6 querying | |
| b8 Performance + cost | columnar internals, partitioning, clustering, pruning, micropartitions, cost model | ◐ | ◐ | ✓ S3 perf | ✓ deltas |
| b9 Lakehouse + modern stack | Parquet, external tables live in DuckDB, warehouse vs lakehouse vs lake, OBT + data vault (when-not-dimensional) | ✓ M1 lakes/lakehouse | ✓ M1 vault/OBT | ✓ S7 | |
| b10 Capstone | Daybreak warehouse end-to-end: stage -> star -> SCD -> marts + quality checks + cost lens | ✓ M3 final project shape | ✓ M4 capstone shape | ✓ S8 capstone | |

## NOTES-SLOT markers

When Phoebe finishes S1/S2/S3 and passes notes: verify each note against this map, correct
gaps explicitly (comprehension check), and weave her framing into a1-a3 ledes and the
"From your subscriptions" rows on each session's coverage section.

## Fetched syllabi appendix

### S1 - IBM Data Warehouse Fundamentals (Coursera)

- M1 (2h): DW overview · popular DW systems · selecting a system · data marts · Db2 Warehouse ·
  data lakes · lakehouses
- M2 (5h): architectures · cubes, rollups, materialized views/tables · facts + dimensional
  modeling · star + snowflake · staging areas · verify data quality · populating a DW ·
  querying. Labs: facts/dims tables, staging area setup, data quality verify, populate w/
  PostgreSQL, query w/ PostgreSQL
- M3 (9h): practice project + final assignment (Db2, Cognos)

### S2 - DLAI Data Engineering C4: Data Modeling, Transformation, Serving

- M1 (9h): conceptual/logical/physical modeling · normalization · star schema · Inmon vs
  Kimball · data vault · one big table · dbt demos. Labs: normalization, star transform, dbt
- M2 (7h): modeling for ML (OUT OF SCOPE here)
- M3 (7h): batch patterns, Hadoop/Spark, EMR, Glue, streaming (OUT OF SCOPE -> data-engineering)
- M4 (10h): serving for analytics + ML · views and materialized views · capstone (ETL +
  modeling, quality + orchestration + visualization)

### S3 - 365DS Introduction to Data Warehousing (3h, 31 lessons)

- S2 basics: foundations, history, components, real-world apps
- S3 architecture/design: traditional vs modern, dimensional modeling, schema design,
  partitioning, indexing, query perf
- S4 implementation: lifecycle, quality + governance, security + privacy
- S5 ETL: extraction, transformation, loading strategies, automation
- S6 tools: tech landscape, querying, cloud vs on-prem, viz/reporting
- S7 advanced: DW vs lakehouse, real-time DW, SCD, advanced schemas, large volumes
- S8 capstone: requirements -> architecture -> implement + monitor
