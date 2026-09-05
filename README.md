<div align="center">

# Media Insights

### From messy media coverage to a report you can defend.

Media Insights is a reporting workspace for PR and communications teams. It turns large, inconsistent media-monitoring workbooks into a repeatable analysis: clean coverage, comparable performance, evidence-backed conclusions and client-ready reports.

<br />

<img src="assets/hero-workflow.svg" alt="Media Insights turns imported workbooks into a trusted dataset, supported findings and presentation-ready outputs" width="100%" />

<br />

`Portfolio case study` &nbsp;·&nbsp; `Synthetic data` &nbsp;·&nbsp; `Operational source kept private`

</div>

## The problem was never just making charts

A media report may begin as nine Excel files and end as a polished presentation, but there is a surprising amount of fragile work between those two points. Column names vary. Company names are missing or inconsistent. The same article appears more than once. Reach figures need a consistent definition. A mention is not necessarily the subject of the story. Then someone still has to explain what changed, find the articles that support that conclusion and rebuild the same analysis in a deck.

Dropping the files into a general-purpose AI chat only changes where that work happens. It does not create a durable dataset, a repeatable calculation method or a reliable path back to the source.

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

## One project keeps the entire reporting context together

The workspace is organized around a reporting period, not a chat session. Source files, normalized records, duplicate decisions, classifications, metrics, generated insights and conversations all remain attached to the same project.

<img src="assets/analyst-workspace.svg" alt="Synthetic Media Insights workspace showing project health, competitor performance, topic mix and a supported finding" width="100%" />

The analyst can see whether the project is actually ready before trusting its charts: how many files were imported, how many rows are valid, which records are duplicates and whether the remaining coverage has been classified. That status is part of the product, not a preprocessing detail hidden behind the dashboard.

## The data changes shape, but it does not lose its provenance

The hardest product decision was deciding what each layer is allowed to claim.

| Layer | What it contains | What it must not do |
|---|---|---|
| Uploaded records | The original workbook values and source links | Pretend the input is already consistent |
| Normalized coverage | Validated fields, resolved formats and explicit missing values | Turn unknown values into zero |
| Duplicate handling | Suspected or confirmed repeated coverage | Silently erase source records |
| Calculated metrics | Volume, reach, Share of Voice, averages, medians and distributions | Depend on a language model for arithmetic |
| Model classifications | Topic, category and other interpretation labels | Masquerade as source data |
| Generated insights | Draft explanations grounded in project metrics | Invent evidence or unsupported causality |
| Analyst judgment | Reviewed conclusions and recommendations | Become indistinguishable from generated text |
| Reports | A reproducible view of the approved analysis | Introduce a second version of the truth |

This separation matters because a polished answer can still be wrong. In Media Insights, a conclusion should be traceable through the metric that triggered it and back to the coverage records behind that metric.

<img src="assets/evidence-chain.svg" alt="A supported finding connected to its calculated metric and synthetic source articles" width="100%" />

## Why this instead of Claude?

Claude is useful when an analyst wants help interpreting a manageable set of material. Media Insights solves the part that a conversation window does not: keeping tens of thousands of articles available as structured project context, applying the same cleaning and calculation rules every time, retaining review decisions, comparing reporting periods and producing repeatable outputs without moving the dataset from Excel to chat to slides and back again.

The conversational analyst is still valuable, but it sits on top of the system rather than replacing it. Questions are answered through controlled project queries. The answer can return the supporting metric, article IDs and source links, while deterministic services remain responsible for calculations. The model helps the analyst navigate and explain the evidence; it does not get to manufacture the evidence.

## Comparison is where reporting becomes useful

A standalone quarter answers “what happened?” A comparison starts answering “what changed?” Media Insights can compare reporting projects so shifts in visibility, reach and subject matter do not have to be reconstructed by copying tables between workbooks.

<img src="assets/period-comparison.svg" alt="Synthetic quarterly comparison showing a Share of Voice gain, a reach change and the coverage topics behind the movement" width="100%" />

The useful output is not a green arrow by itself. It is the combination of the change, the metric definition, the topic or coverage pattern behind it and the articles an analyst can inspect before turning it into a recommendation.

## The analysis leaves the system in useful forms

The product does not stop at a dashboard. Analysts can export an enriched Excel workbook for review and handoff, generate narrative insights, and produce a PowerPoint report from the same project context. The operational implementation uses a defined presentation structure; this public case study deliberately shows a new, unbranded synthetic template rather than the employer-owned one.

<img src="assets/report-outputs.svg" alt="Synthetic Excel export and PowerPoint report generated from one approved Media Insights project" width="100%" />

That output layer removes a particularly expensive kind of repetition: recalculating or reinterpreting the analysis while transferring it into the format a client or leadership team will actually receive.

## What exists today

The operational product supports a project-based workflow with:

- multi-file `.xlsx` ingestion, validation and normalization;
- explicit valid, invalid and duplicate counts;
- trusted brand mapping for incomplete source files;
- reviewable article classification;
- brand and competitor analysis across article volume, Share of Voice, reach, reach share, average reach, median reach, primary-focus coverage and mentions;
- topic and communication-category distributions;
- project comparisons and ranking changes;
- generated narrative insights grounded in calculated analytics;
- a project-scoped conversational analyst using controlled backend queries;
- enriched Excel export and generated PowerPoint reporting.

The broader product direction includes richer derived-period reporting and additional diagnostic metrics. Those ideas are useful, but this case study does not present roadmap work as finished functionality.

## Where AI helps, and where it stops

AI is used for interpretation-heavy work: classifying article meaning, drafting narrative insights and understanding an analyst's question. It is deliberately not the authority for row validation, duplicate state, metric definitions or arithmetic.

| AI is useful for | The application remains responsible for |
|---|---|
| Interpreting what an article is mainly about | Preserving the uploaded record |
| Assigning reviewable topic and category labels | Cleaning and normalizing fields |
| Turning approved metrics into a first narrative draft | Calculating every reporting metric |
| Translating a natural-language question into a controlled query | Restricting the available query surface |
| Explaining an answer in plain language | Returning the evidence behind the answer |

That boundary is less exciting than “chat with all your data,” but much more useful when the result will become a client recommendation.

## Inside the implementation

The private operational application uses a Python service layer around a persisted, project-scoped data model. Deterministic services handle ingestion, normalization, analytics, comparisons and report generation. DeepSeek is used through n8n for classification and language tasks, with authenticated callbacks into the application. Separate generators produce enriched `.xlsx` and `.pptx` outputs.

The architecture follows one practical rule: every generated claim should be downstream of data the application can retrieve and show. The model receives only the controlled context required for its task, while the application owns project state, calculations and evidence.

## Why I built it

I work in product marketing, where it is easy to have confident opinions about what a technical product should do while remaining comfortably far away from the decisions that make it trustworthy.

Media Insights started with a simple question: could I remove the repetitive work between receiving media-monitoring spreadsheets and producing a useful performance report? Building it made the harder questions unavoidable. What counts as the same article? Is missing reach really zero? When is a brand the subject of a story rather than merely mentioned? Which conclusions can be generated, and which still require an analyst to make the call? How do you let someone talk to a large dataset without letting the model invent its own version of it?

“Marketer who can code” is not the interesting part. The useful part is getting close enough to the system that data choices, product trade-offs, UX decisions and positioning stop being abstract.

**Understanding the system makes the product story better. Building the system makes the opinions harder to fake.**

---

### About this repository

This is a public portfolio case study, not the operational source repository. All companies, publications, filenames, article examples, dates, metrics and conclusions shown here are synthetic. No client data, production configuration, internal URLs, credentials, employer branding or proprietary presentation templates are included.
