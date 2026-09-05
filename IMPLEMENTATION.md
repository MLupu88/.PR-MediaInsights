# How the app handles the data

These notes explain the details behind the case study. Capabilities were checked against the operational source and test structure; this review did not run the application’s tests or establish a performance benchmark.

## Importing and cleaning

The importer accepts supported `.xlsx` monitoring workbooks and recognizes English and Romanian column aliases. It retains raw values, original row numbers and available source links. Fields can remain missing.

Brand assignments record how they were resolved: explicit fields, trusted file mappings, inference, filename fallback or manual correction. Uncertain assignments remain visible for review.

Duplicate detection uses deterministic fingerprints. One record is canonical and repeated rows point to it. Import and correction use the same rule. Analytics exclude duplicates; related stories are grouped separately through story clusters.

## Classification and review

Classification covers primary and secondary topics, communication category, sentiment and brand role. Results below the confidence threshold enter review; higher-confidence results can be automatically approved. Analysts can correct or flag labels. An approved classification is not proof of human review.

## Metrics and comparisons

Metrics include volume-based Share of Voice, reach and reach share, average and median reach, missing-reach counts and duplicate share. Views also cover topic/category mix, sentiment, brand role, publication and story rankings, concentration and low-confidence results.

Comparisons support quarters, year-over-year periods and groups of quarterly projects. Q1 + Q2, Q3 + Q4 and all four quarters in one year form H1, H2 and full-year views. Coverage is deduplicated across projects. Each side can have its own brand and source-file selection; a project can appear on both sides for brand comparisons.

Comparison results include KPI deltas, ranking changes, entrants and dropouts, and topic shifts. Concentration measures dependence on a small number of publications or stories. Ranking volatility describes rank movement and entries/exits, rather than making a broader claim about business volatility.

## Generated insights and chat

Narrative generation retains an immutable snapshot of its source data. Validators check metric paths and values, known entities, article IDs, URLs and allowed evidence scope. Rejected candidates remain available with rejection reasons. These checks do not establish semantic truth or causation. Narrative insights have no separate human sign-off state.

Chat uses nine fixed tools for project KPIs, brand performance, topics, sentiment, publications, story clusters, articles, period comparisons and validated insights. The application determines the permitted project scope and validates parameters. The model cannot provide arbitrary SQL or select another project ID.

## Excel and PowerPoint

Both project and comparison exports use a shared report-data builder. Each export reads a stable database snapshot in a read-only, repeatable-read transaction. Separate requests can produce different results if data changes between them.

Reports may include eligible system-validated interpretations and recommendations with explicit labels. Chat answers are not automatically included. Article rows, rankings and insight counts have output limits; an export should not be assumed to contain every item visible across the application.

The presentation shown in the case study uses independent styling and is not an operational template.

## Stack and current scope

Python/FastAPI serves the application, with PostgreSQL, SQLAlchemy and Alembic for data storage. The interface uses Jinja2 and Tailwind CSS. Deterministic services handle imports, normalization, analytics, comparisons and report generation; DeepSeek through n8n handles classification and language tasks with authenticated callbacks. Spreadsheet and presentation generation use openpyxl/pandas and python-pptx.

The current product serves a defined retail reporting scope and supported workbook formats. It is an internal working application. An author field may be present in article records, but that is not a dedicated journalist-analysis feature.
