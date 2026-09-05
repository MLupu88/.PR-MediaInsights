<div align="center">

# Media Insights

### From messy media coverage to a report you can defend.

Media Insights is a reporting workspace for PR and communications teams. It turns large, inconsistent media-monitoring workbooks into a repeatable analysis: clean coverage, comparable performance, evidence-backed conclusions and client-ready reports.

<br />

<img src="assets/hero-workflow.svg" alt="Media Insights turns imported workbooks into a trusted dataset, supported findings and presentation-ready outputs" width="100%" />

<br />

`PR & communications` &nbsp;·&nbsp; `Product case study` &nbsp;·&nbsp; `Synthetic examples`

</div>

## The problem was never just making charts

A media report may begin as several Excel files and end as a polished presentation, but there is a surprising amount of fragile work between those two points. Column names vary. Company names are missing or inconsistent. The same article appears more than once. Reach figures need a consistent definition. A mention is not necessarily the subject of the story. Then someone still has to explain what changed, find the articles that support that conclusion and rebuild the same analysis in a deck.

For recurring reporting, the useful question is how to preserve the dataset, calculation rules and evidence between reporting cycles. A conversation is one part of that workflow; the application keeps the underlying work organized.

The product begins after coverage has been collected by a monitoring provider. It is not a crawler or a social-listening clone. Its job is to turn exported coverage into a trustworthy piece of analysis and then into the report that a client or communications lead can actually use.

Media Insights was built around the full analyst workflow:

<table>
  <tr>
    <td><strong>01 · Collect</strong><br />Bring multiple monitoring workbooks into one reporting project.</td>
    <td><strong>02 · Clean</strong><br />Validate rows, normalize fields and preserve missing values.</td>
    <td><strong>03 · Organize</strong><br />Resolve brands, flag duplicates and classify coverage.</td>
  </tr>
  <tr>
    <td><strong>04 · Analyze</strong><br />Calculate volume, reach, Share of Voice and topic mix consistently.</td>
    <td><strong>05 · Explain</strong><br />Ask questions and draft conclusions from controlled project data.</td>
    <td><strong>06 · Report</strong><br />Export the enriched workbook or build a presentation-ready report.</td>
  </tr>
</table>

*Visuals below are portfolio illustrations of implemented workflows, using fictional data and independent styling. They are not captures of the live application.*

## One project keeps the entire reporting context together

The workspace is organized around a reporting period, not a chat session. Source files, normalized records, duplicate decisions, classifications, metrics, generated insights and conversations all remain attached to the same project.

<img src="assets/analyst-workspace.svg" alt="Illustrative Analytics view showing brand performance, reach and topic mix" width="100%" />

The analyst can see whether the project is actually ready before trusting its charts: how many files were imported, how many rows are valid, which records are duplicates and whether the remaining coverage has been classified. That status is part of the product, not a preprocessing detail hidden behind the dashboard.

## Clean the records, then review the interpretation

The importer recognizes supported English and Romanian column names and preserves original row numbers, raw values and available article links. Brand assignment records how it was resolved, including explicit fields, trusted file mappings, inference and manual corrections. Uncertain assignments remain visible for review.

Duplicates are resolved with deterministic fingerprints: one record becomes canonical and repeated rows point back to it. Import and correction use the same rule, and analytics exclude duplicates from the reporting population. This is record deduplication; related stories are analyzed separately through story clusters.

<img src="assets/import-review.svg" alt="Illustration of source normalization, canonical duplicate records and classification review" width="100%" />

Classification covers primary and secondary topics, communication category, sentiment and brand role. Low-confidence classifications enter a review queue; higher-confidence results can start in the approved state automatically. Analysts can correct labels or flag them for review. An approved classification therefore does not, by itself, prove that a person reviewed it.

## An insight should come with evidence

Generated insights are checked against the immutable data snapshot captured for that generation. The application checks cited metric paths and values, known entities, article IDs and source URLs. Rejected candidates are retained with rejection reasons instead of silently disappearing.

<img src="assets/evidence-chain.svg" alt="An illustrative interpretation grounded in calculated Share of Voice and article evidence, with system validation distinguished from human review" width="100%" />

| Layer | What the application preserves or checks |
|---|---|
| Source records | Original values, source file, row number and available links |
| Normalized articles | Parsed fields, assignment provenance and explicit missing values |
| Duplicate state | Canonical record and links from duplicate rows |
| Calculated metrics | Defined populations and deterministic calculations |
| Classifications | Model labels, confidence and review/correction status |
| Generated insights | Evidence references, snapshot, validation result and caveats |
| Reports | Filtered analytics and eligible validated interpretations or recommendations |

**System validation checks the references; it does not certify that an interpretation is correct.** Analysts still decide whether a conclusion is persuasive and what to recommend. The product does not provide a separate human sign-off state for narrative insights.

## Why this instead of Claude?

The reason to build Media Insights was the work around the conversation: importing large coverage datasets, keeping reporting periods organized, applying consistent definitions, retaining corrections and generating the next report without reconstructing the context from scratch.

For coverage sets containing tens of thousands of article records, the project data lives in a database. A model receives the bounded evidence or query result it needs for a task, rather than being expected to remember the entire dataset. That is the useful distinction here: a persistent reporting application with a conversational interface, designed around the analyst's recurring work.

<img src="assets/grounded-chat.svg" alt="Illustrative Chat view answering a brand Share of Voice question with a calculated metric and a follow-up source article query" width="100%" />

Chat works over individual projects and comparison scopes. Its fixed tools retrieve KPIs, brand performance, topics, sentiment, publications, story clusters, articles, period comparisons and validated insights. The model supplies validated parameters; the application determines the allowed project scope. The model cannot supply arbitrary SQL or choose a different project's ID.

Answers can include supporting metrics, article IDs and available source links. This helps an analyst move from “which brand gained visibility?” to the coverage worth inspecting, without moving the dataset between tools.

## Comparison is where reporting becomes useful

Compare individual quarters, the same quarter across years, or groups of projects. Selecting Q1 + Q2, Q3 + Q4, or all four quarters of one year forms H1, H2 or full-year views, with articles deduplicated across projects. The same project can appear on both sides to compare selected brands within one period.

Each side can have its own brand and source-file selection. The comparison includes KPI deltas, Share of Voice and reach-share changes, rankings, new entrants and dropouts, topic/category shifts, sentiment and brand role. Publication and story concentration show how much coverage depends on a few sources or stories; rank movement and entry/exit counts describe ranking volatility.

<img src="assets/period-comparison.svg" alt="Synthetic quarterly comparison showing Share of Voice, reach and median-reach changes alongside supported comparison scopes" width="100%" />

Volume, reach and Share of Voice answer different questions. Showing them together helps an analyst distinguish more mentions from a larger share of coverage, then inspect the topic mix and stories before proposing a next step.

## The analysis leaves the system in useful forms

Both project and comparison analyses can leave the application as Excel workbooks and PowerPoint reports. Excel carries ranked analysis and article details, including available URLs, for inspection and handoff. PowerPoint presents the findings in a defined slide structure. The illustration below uses independent styling; it is not an exported operational template.

Reports include eligible system-validated interpretations and recommendations, clearly labelled. Chat answers are not included automatically. Each export reads a stable database snapshot; separate Excel and PowerPoint requests can differ if the underlying data changes between them.

<img src="assets/report-outputs.svg" alt="Illustrative PowerPoint and Excel outputs from project analytics" width="100%" />

That output layer removes a particularly expensive kind of repetition: recalculating or reinterpreting the analysis while transferring it into the format a client or leadership team will actually receive.

## What exists today

| Analyst task | Implemented capability |
|---|---|
| Import monitoring exports | Multiple `.xlsx` files, supported header normalization, validation and source provenance |
| Resolve data issues | Trusted brand mappings, manual corrections, deterministic deduplication and review queues |
| Organize coverage | Primary/secondary topic, category, sentiment, brand role and story clusters |
| Measure performance | Volume, volume-based Share of Voice, reach/share, average/median reach, missing-reach counts and duplicate share |
| Inspect visibility | Publication and story rankings, concentration, topic mix and low-confidence results |
| Compare periods or brands | Quarter, year-over-year and derived H1/H2/full-year views, per-side brand/file filters, deltas and ranking movement |
| Develop the report narrative | Executive summaries, findings, risks, opportunities, recommendations and methodology caveats, checked against stored evidence |
| Ask follow-up questions | Project/comparison chat through nine fixed query tools |
| Deliver the analysis | Project/comparison PowerPoint and Excel exports with consistent definitions and explicit output bounds |

The current implementation is tailored to a defined retail reporting scope and supported monitoring workbook formats. It is an internal working application, not a claim of arbitrary-file support or a general-purpose enterprise platform. Article records can include an author field; that alone should not be confused with a dedicated journalist-analysis product.

## Where AI helps, and where it stops

AI is used for interpretation-heavy work: classifying article meaning, drafting narrative insights and understanding an analyst's question. It is deliberately not the authority for row validation, duplicate state, metric definitions or arithmetic.

| AI is useful for | The application remains responsible for |
|---|---|
| Interpreting what an article is mainly about | Preserving the uploaded record |
| Assigning reviewable topic and category labels | Cleaning and normalizing fields |
| Turning calculated metrics into a first narrative draft | Calculating every reporting metric |
| Translating a natural-language question into a controlled query | Restricting the available query surface |
| Explaining an answer in plain language | Returning the evidence behind the answer |

That boundary matters when the result will become a client recommendation: calculations need to remain repeatable, and interpretations need to remain open to review.

## Inside the implementation

The operational stack is Python/FastAPI, PostgreSQL with SQLAlchemy and Alembic, Jinja2 templates and Tailwind CSS. Deterministic services handle ingestion, normalization, analytics, comparisons and report generation. DeepSeek is used through n8n for classification and language tasks, with authenticated callbacks into the application. Separate generators produce enriched `.xlsx` and `.pptx` outputs.

The evidence boundary is implemented through fixed query tools, immutable narrative snapshots and deterministic validators. Report builders share a data-mapping layer and use a read-only repeatable-read transaction for each export.

The repository includes tests for imports, review, deduplication, analytics, comparisons, chat scope/security, narrative validation and both export formats. This case study was checked against source and test structure; it does not claim a new test run or a production benchmark.

## Why I built it

I work in product marketing, where it is easy to have confident opinions about what a technical product should do while remaining comfortably far away from the decisions that make it trustworthy.

Media Insights started with a simple question: could I remove the repetitive work between receiving media-monitoring spreadsheets and producing a useful performance report? Building it made the harder questions unavoidable. What counts as the same article? Is missing reach really zero? When is a brand the subject of a story rather than merely mentioned? Which conclusions can be generated, and which still require an analyst to make the call? How do you let someone talk to a large dataset without letting the model invent its own version of it?

“Marketer who can code” is not the interesting part. The useful part is getting close enough to the system that data choices, product trade-offs, UX decisions and positioning stop being abstract.

**Understanding the system makes the product story better. Building the system makes the opinions harder to fake.**

---

### About this repository

This is a public portfolio case study, not the operational source repository. All companies, publications, filenames, article examples, dates, metrics and conclusions shown here are synthetic. No client data, production configuration, internal URLs, credentials, employer branding or proprietary presentation templates are included.
