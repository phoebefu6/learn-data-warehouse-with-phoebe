<!-- learn-with-phoebe hub banner -->
> ### 📚 Part of [**Learn with Phoebe**](https://phoebefu6.github.io/learn-with-phoebe/)
> The shelf of 37 free, hands-on courses on AI, data, and the craft around them. **[Browse every course ↗](https://phoebefu6.github.io/learn-with-phoebe/)**
<!-- /learn-with-phoebe hub banner -->

# learn-data-warehouse-with-phoebe

A two-track, interactive data warehouse course you run **in your browser**. You learn by building
the first real warehouse for **Daybreak** - the coffee-subscription brand from
[learn-sql-with-phoebe](https://phoebefu6.github.io/learn-sql-with-phoebe/), grown up. Its OLTP
database plays the messy source system, and session by session you stage it, reshape it into a
star schema, track history with slowly changing dimensions, load it idempotently, serve it through
marts, tune it, and meet the lakehouse. Every builder page runs **real DuckDB** - an actual
columnar OLAP engine - via WebAssembly: editable SQL, 300,000-row demos, SCD merges, Parquet
round trips.

**Live site:** https://phoebefu6.github.io/learn-data-warehouse-with-phoebe/

By Phoebe Fu.

## Two tracks

### 🤝 Leader track (a1-a6) - execs and managers, no code, 6 x 45 min

| Session | Title | Difficulty |
|---------|-------|------------|
| a1 | Why a warehouse | 🟢 easy |
| a2 | The shape of a warehouse | 🟢 easy |
| a3 | The one-truth problem | 🟡 medium |
| a4 | The buy landscape | 🟡 medium |
| a5 | Cost and performance | 🟡 medium |
| a6 | The warehouse in the AI era | 🟡 medium |

### 🛠️ Builder track (b1-b10) - practitioners, live DuckDB, 45 min each (b10: 60)

| Session | Title | Difficulty |
|---------|-------|------------|
| b1 | Row store meets column store | 🟢 easy |
| b2 | Architecture and the staging layer | 🟡 medium |
| b3 | Facts and dimensions | 🟡 medium |
| b4 | Building dimensions | 🟡 medium |
| b5 | Slowly changing dimensions | 🟠 hands-on |
| b6 | Loading patterns | 🟠 hands-on |
| b7 | Marts and serving | 🟠 hands-on |
| b8 | Performance and cost | 🟠 hands-on |
| b9 | Lakehouse and the modern stack | 🔴 hardest |
| b10 | Capstone: the whole warehouse | 🔴 hardest |

Start at [`index.html`](index.html).

## How the live playground works

`assets/warehouse-live.js` turns every playground on a builder page into an editable SQL box
running **DuckDB-WASM** - real DuckDB, the columnar OLAP engine, compiled to WebAssembly. The
engine loads **once from a CDN (about 8 MB)** - that is the one network dependency, stated
honestly. After that first load everything runs client-side: the Daybreak source data
(`assets/dw-seed.js`) is generated in your browser, every query executes locally, and nothing you
type can break the next example. No install, no cloud account, no bill.

## Built from official curricula - honestly

This course is built from IBM Data Warehouse Fundamentals, DeepLearning.AI Data Engineering
(Joe Reis), 365 Data Science Intro to Data Warehousing, and vendor deep dives. It teaches the
working core of those curricula through one running project, but it does not replace them:
the certificates, graded labs, and vendor-specific tooling stay on the official sites, and
if you want the credential, go earn it there.

## Prerequisites and siblings

- [learn-sql-with-phoebe](https://phoebefu6.github.io/learn-sql-with-phoebe/) - the Daybreak database comes from there; take it first
- [learn-data-modeling-with-phoebe](https://phoebefu6.github.io/learn-data-modeling-with-phoebe/) - schema-design depth
- [learn-data-engineering-with-phoebe](https://phoebefu6.github.io/learn-data-engineering-with-phoebe/) - the pipelines around the warehouse

## Structure

```
index.html                     two-track landing + knowledge mindmap
courses/a1..a6-*.html          leader track
courses/b1..b10-*.html         builder track
assets/style.css               design system (steel blue + safety amber)
assets/app.js                  engagement layer (progress, quizzes, zoom)
assets/mindmap.js              the knowledge map on the landing page
assets/warehouse-live.js       the live DuckDB playground engine
assets/dw-seed.js              the Daybreak source data generator
materials/                     source coverage notes
```

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

by Phoebe Fu
