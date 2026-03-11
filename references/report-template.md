# HTML Report Template — Reference

## CANONICAL TEMPLATE

**The standard HTML design is `report-template.html`** (saved in this same `/references/` folder).
This file is the exact template to replicate for all report output — layout, CSS variables, chart types, and component patterns all come from this file.

Key rules:
- All content must be in **English** — no Spanish, regardless of client location
- Use Chart.js 4.4.0 (`https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js`)
- CSS variables: `--dk:#3D3D3D`, `--bl:#3B82F6`, `--wh:#FFFFFF`, `--mg:#6B7280`, `--lg:#EBEBED`, `--gn:#059669`, `--rd:#EF4444`, `--yl:#F97316`
- Floating sticky pill nav (`position:sticky; top:24px`) with `.nav-inner` dark rounded container, section anchor links
- Dark header band with title only (no badge pills)
- KPI cards in `.kpi-row.r4` grid (4 per row)
- Chart types: doughnut (`cutout:'60%'`), horizontal bar (`indexAxis:'y'`), dual-axis line, vertical bar
- Tables: `th { background: var(--dk) }` dark header, `.good/.bad/.warn` colored text
- Insight boxes: `.insight` (blue border), `.insight-warn` (yellow), `.insight-bad` (red)
- Funnel: `.funnel` > `.funnel-step` > `.funnel-bar` + `.funnel-arrow` + `.funnel-rate`
- Recommendations: `.rec-grid` (2-col) with `.rec`, `.num-badge`, `.rec-pause`, `.rec-scale`

All reports are generated as self-contained `.html` files. Two versions are always generated.

---

## Two Versions

### Agency Version
Audience: The ads analyst and internal agency team.
Tone: Technical, complete, all metrics included.

Sections (in order):
1. Executive Summary — 3–5 bullet top insights
2. Flags — all warnings (frequency fatigue, budget pacing, zero conv)
3. Campaign Performance table — all metrics vs client goals vs industry benchmarks
4. Creative Analysis — scores, verdicts, Hook/Hold/CTR breakdown per ad, ranked
5. Funnel Analysis — CPL by stage, conversion rates, drop-off points
6. Cross-platform comparison — CPL/CPA chart + ROAS chart (if 2+ platforms)
7. Budget reallocation recommendation
8. Numbered action items

### Client Version
Audience: The end client. Non-technical.
Tone: Plain language, insight-led, no jargon, no raw metric tables.

Sections (in order):
1. Data notice (only if primary metric is unavailable) — plain-language explanation before anything else:
   "We don't have [lead/purchase] data for your [Platform] campaigns in this report. Your account manager will need to export a fuller file to show your cost per lead. What we can confirm: your ads were active and delivering impressions during this period."
   If all primary metrics are available, skip this section entirely.
2. Executive Summary — 3–5 plain-language highlights ("Your best-performing ad drove leads at €12, well below your €18 target.")
3. Campaign highlights — what worked and what didn't, in plain language
4. Top performing creatives — show top 3 ads with plain-language explanation of why they worked
5. Key recommendations — what we're doing next, written as decisions not data points

---

## File Naming

```
[csv-folder]/reports/[type]-[data-end-date]-agency.html
[csv-folder]/reports/[type]-[data-end-date]-client.html
```

Save location: always create a `/reports/` subfolder inside the same folder where the CSV files are located. Never save to a system root path.

Date in filename: use the latest data end date across all uploaded files — not today's date. If periods differ across platforms, use the most recent end date.

Always include the actual data period in the report header (e.g. "Data period: Meta Mar 1 · Google Feb 1–Mar 1") so the filename date and the data period are both visible.

Report types:
- `weekly` — weekly performance report
- `launch-recap` — post-launch summary
- `creative-analysis` — creative-focused report
- `monthly` — monthly KPI consolidation

Examples:
```
/Users/.../datos visual/reports/weekly-2026-03-01-agency.html
/Users/.../datos visual/reports/weekly-2026-03-01-client.html
```

---

## Technical Spec

- Single self-contained `.html` file — no external dependencies except Chart.js CDN
- Chart.js via CDN: `https://cdn.jsdelivr.net/npm/chart.js`
- Responsive layout — works on desktop and mobile
- No raw CSV data included — processed metrics only

Hosting note: Google Drive does not serve HTML as a live URL. File must be opened locally or hosted on GitHub Pages / Netlify to share as a URL.

---

## Color Palette

| Role | Var | Hex | Usage |
|------|-----|-----|-------|
| Dark | `--dk` | `#3D3D3D` | Nav pill, header band, table headers |
| Blue | `--bl` | `#3B82F6` | Accents, insight borders, positive signals |
| White | `--wh` | `#FFFFFF` | Text on dark, card backgrounds, insight backgrounds |
| Mid Grey | `--mg` | `#6B7280` | Body text, secondary information |
| Light Grey | `--lg` | `#EBEBED` | Page background, subtle fills |
| Green | `--gn` | `#059669` | Above goal — positive signal |
| Red | `--rd` | `#EF4444` | Below goal — negative signal / flag |
| Yellow | `--yl` | `#F97316` | Near goal — warning signal |

---

## Charts (Chart.js)

All charts are conditional — only render a chart if the required data is available. If not, replace the chart slot with a plain-text note explaining what data is needed.

| Chart | Required data | If missing |
|-------|--------------|------------|
| Campaign performance (spend vs conversions) | Spend + conversions both present | Show spend-only bar chart with note: "Conversion data not available in this export" |
| Creative score ranking | At least 2 ads with calculable scores | Only render if 3+ data points available — single-day data is not enough for a meaningful trend |
| Funnel drop-off | Multi-stage conversion data | Replace with: "Funnel data not available — single conversion event only" |
| Cross-platform CPL/CPA | 2+ platforms with matching date ranges AND CPL/CPA available for all | Replace with: "Cross-platform comparison not available — [reason]" |
| Cross-platform ROAS | 2+ platforms with matching date ranges AND ROAS available for all | Same as above |

Chart colors: use palette above. Positive bars in Blue (#3B82F6), negative/flagged in Red (#EF4444).

---

## Conditional Sections — Show Only When Data Is Present

Some sections in the template are specific to clients with appointment-setting / sales-closer models. **Do not render these sections at all** unless the relevant data was included in the uploaded files. No placeholder, no empty chart — just omit the section entirely.

| Section / Element | Required data to show it | What triggers it |
|-------------------|--------------------------|------------------|
| **Funnel: Appointments → Confirmed → Sales** steps | Appointment booking data (e.g. Calendly export, CRM with appt field) | Only extend funnel beyond Leads if appointment count is provided |
| **Appointments by Calendar** (doughnut) | Appointment data broken down by calendar/funnel name | Booking system export or CRM with calendar column |
| **Appointments Confirmed detail table** | Individual appointment records with closer, date, outcome | CRM export with appointment-level rows |
| **Days to Maturation (Lead → Sale)** (bar chart) | CRM with both lead creation date AND sale close date per record | CRM export with sale_date or won_date column |
| **Sales by Month** (bar chart) | Revenue or sale count by month | CRM or sales system export with closed deals |
| **Sales by Closer** (table) | Sales attributed per closer/salesperson | CRM export with closer name and won status |

**Default funnel for standard lead gen** (no sales data): Impressions → Link Clicks → LP Views → CRM Leads. Stop there.

**When appointment/sales data IS uploaded**, extend the funnel and render those sections in full using the template's exact component patterns.

---

## Performance vs Goal — Visual Treatment

In every metrics table, show three columns for each metric:
- Value — the actual number
- vs Goal — color-coded: green (above), yellow (within 10%), red (below)
- % Gap — "+12% above goal" or "-8% below goal"

Example row:
```
| CPL | €14.20 | 🟢 Above goal | +21% above €18 target |
```

---

## Agency Version — Metrics Table Columns

For each campaign/ad set/ad, include:
- Campaign name
- Platform
- Mode (Launch / Evergreen)
- Spend
- Impressions
- Reach
- Frequency
- Primary metric (CPL / ROAS / CPA / CPI — matched to campaign type)
- vs Goal (color + %)
- Industry benchmark
- Creative verdict (Scale / Kill / Test more)
- Score (0–10)
- Flags (if any)
