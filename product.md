# Ad Reporting Skill — Changelog

> This file tracks every change made to SKILL.md and reference files.

---

## v2.0.2 — 2026-03-10

**Type:** Patch — intake flow overhaul
**Author:** Virgil Brewster

### Step 2 — Questions
- Period selection added as new Q2: users choose Last 7 days / 14 days / 30 days / Custom from a numbered list. If CSV contains a date range, the matching option is pre-selected and confirmed.
- All questions now use numbered options — no open-ended text prompts
- Campaign type (Q3) now presented as explicit numbered list (1–4)
- Target metric (Q4) now presented as numbered ranges per campaign type — no free-text number entry. Options: CPL (Under €10 / €10–€20 / €20–€40 / Custom), ROAS (2× / 3× / 5× / Custom), CPM (Under €5 / €5–€10 / €10–€20 / Custom), CPI (Under €2 / €2–€5 / €5–€10 / Custom)
- CPC target question (Q4b) added for Google Ads sessions: Under €0.50 / €0.50–€1.00 / €1.00–€2.00 / Custom
- Client/agency question removed — both report versions always generated, no question needed
- Total question count updated from 5 to 6

---

## v2.0.1 — 2026-03-10

**Type:** Patch — real-data testing fixes
**Author:** Virgil Brewster
**Test data:** Visual Faktory Meta + Google Display CSVs (Spanish-language exports)

### Step 1 — Data Ingestion
- Platform detection rebuilt: Meta now detected via `facebook`/`instagram` values in Platform column (language-independent). Google, TikTok, YouTube always ask — column names are not reliable across languages.
- Added multi-row header handling: plain-text title rows before column headers are skipped automatically
- Derived metrics added: Frequency = Impressions / Reach, CTR = Clicks / Impressions, CPA = Spend / Conversions. Only flag a metric as unavailable if it cannot be derived.
- Missing column flag changed: no longer blocks — proceeds with available data and lists limitations in summary

### Step 2 — Questions
- Multi-market CPL: after goal is entered, if ad set names contain market codes (SPA, USA, LATAM, EXPAT etc.), ask whether goal is the same across markets or varies
- Campaign mode detection: reads filename for "Evergreen" or "Launch" hint, pre-suggests and confirms instead of asking cold

### Step 3 — Analysis Engine
- Aggregation added: all rows grouped by ad name across dates and platforms before any metric calculation
- Column mapping layer added: matches columns by meaning across English, Spanish, and other languages
- Google campaign type detection: infers Search vs Display from CTR values and column presence, applies correct benchmarks per type
- Adaptive creative scoring: redistributes score weights to available metrics when Hook Rate / Hold Rate / CPL are missing. Always states which metrics the score is based on.

### Step 4 — Chat Output
- Prominent missing metric notice: opens output before executive summary when primary metric is unavailable
- Budget pacing guard: pacing flag only runs when data covers 3+ days
- Market breakdown: auto-detects geographic codes in ad set names, defaults to market-level view
- Cross-platform comparison guard: skipped with explanation when date ranges don't match across platforms

### Step 5 — HTML Report
- Charts are now conditional: each chart only renders if required data is available, otherwise replaced with plain-text explanation
- Filename date: uses latest data end date across all uploaded files, not today's date. Data period always shown in report header.
- Client version: adds plain-language data notice before executive summary when primary metric is unavailable
- Save path: defaults to a `/reports/` subfolder inside the same folder as the uploaded CSVs. Never saves to system root.

---

## v2.0.0 — 2026-03-10

**Type:** Full rebuild — proper skill packaging
**Author:** Virgil Brewster

### Changes

- Rebuilt from raw CLAUDE.md into a proper deployable skill (SKILL.md + YAML frontmatter + references/ folder)
- Added TikTok Ads as a 4th platform (alongside Meta, Google, YouTube)
- Introduced 5-question simplicity constraint — maximum 5 mandatory questions per clean session
- Platform detection now auto-identifies from CSV column headers — only asks if ambiguous
- Campaign mode (Launch / Evergreen) now tagged per campaign, not per session — both modes can coexist
- Zero-conversion flag threshold set at 2× target CPL/CPA
- Creative output now includes both verdict (Scale / Kill / Test more) AND score (0–10 with breakdown)
- Cross-platform comparison added: CPL/CPA and ROAS side by side when 2+ platforms present
- Budget reallocation recommendation always included in cross-platform sessions
- HTML report now generates two versions: agency (full detail) and client (plain language, insight-led)
- No raw data in reports — processed metrics only
- Neutral color palette retained (#1F2937 · #2563EB · #DBEAFE · #FFFFFF · #6B7280)
- Added green/red/yellow color signals for above/below/near goal in metrics tables
- Split all platform-specific content into references/ files for progressive loading
- SKILL.md kept under 300 lines per skill anatomy guidelines

### New Files

- `SKILL.md` — main skill file with frontmatter, workflow, hard rules
- `references/meta-ads.md` — Meta Ads metrics, creative rules, campaign modes
- `references/google-ads.md` — Google Ads metrics, Quality Score, decision rules
- `references/youtube-ads.md` — YouTube Ads metrics, hook analysis, decision rules
- `references/tiktok-ads.md` — TikTok Ads metrics, Spark Ads, creative fatigue rules (NEW)
- `references/report-template.md` — Two-version HTML report spec, Chart.js, color palette

### Archived

- `Skills/Ad Reporting Skill /CLAUDE.md` — original monolith (v1.2.0) — preserved for reference

---

## v1.2.0 — 2026-03-09

**Type:** Full redesign — generic, agency-agnostic skill
**Author:** Fan Convert

- Removed all Pablo Gil / Fan Convert specific context
- Skill made fully generic with placeholder client context
- Report output simplified to HTML only
- Added 3 human loops (campaign setup, data gate, report gate)
- Added campaign mode support (Launch vs Evergreen)
- Added attribution window documentation (7-day click / 1-day view default)

---

## v1.1.0 — 2026-03-03

**Type:** Skill update — Evergreen support, attribution window

- Added Campaign Modes table (Launch vs Evergreen)
- Added attribution window section
- Creative analysis decision rules split by campaign mode

---

## v1.0.0 — 2026-03-03

**Type:** Initial release
**Author:** Fan Convert

- Pablo Gil client context (pablogiltrader.com)
- Meta, Google, YouTube platforms
- Creative analysis (Hook Rate, Hold Rate, Scale/Kill/Test)
- HTML, Google Slides, and Google Docs report output
