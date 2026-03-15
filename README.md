# Ad Reporting — PPC Ads Analyst

A Claude Code skill that analyses paid advertising campaign CSVs and generates client-ready HTML reports. Upload your data, answer 6 questions, get a full analysis with actionable recommendations.

## What It Does

Takes raw CSV exports from ad platforms, runs a complete analysis engine, outputs insights in chat, and generates polished HTML reports (agency + client versions).

## Supported Platforms

| Platform | Auto-Detected? | Reference File |
|----------|---------------|----------------|
| Meta Ads (Facebook + Instagram) | Yes (via `facebook`/`instagram` values) | `references/meta-ads.md` |
| Google Ads (Search + Display) | No (asks user) | `references/google-ads.md` |
| YouTube Ads | No (asks user) | `references/youtube-ads.md` |
| TikTok Ads | No (asks user) | `references/tiktok-ads.md` |

Platform detection for Meta is language-independent. Google/TikTok/YouTube column names vary by language, so the skill asks which platform.

## The Flow

### 5 Steps, 6 Questions

The skill asks exactly 6 questions. Everything else runs silently.

| # | Question | When |
|---|----------|------|
| Q1 | "Found: [summary]. Ready to analyse?" | After reading CSV |
| Q2 | "Which period should this report cover?" | After Q1 confirmed |
| Q3 | "What type of campaign is this?" | After Q2 answered |
| Q4 | "What is your target [CPL/ROAS/CPM/CPI]?" | After Q3 answered |
| Q4b | "What is your target CPC?" | Google Ads only |
| Q5 | "Tag each campaign: Launch or Evergreen?" | After Q4 answered |
| Q6 | "Generate the HTML report?" | After chat analysis |

### Step 1: Data Ingestion
- Reads all uploaded CSV files
- Detects platform from column headers
- Handles multi-language exports (Spanish, Portuguese, etc.)
- Derives missing metrics when possible (CTR from clicks/impressions, CPA from spend/conversions)
- Flags truly unavailable metrics upfront

### Step 2: Questions
- All questions use numbered lists (no open-ended prompts)
- Campaign types: Lead gen, Ecommerce, Brand awareness, App installs
- Target metrics adapt to campaign type (CPL, ROAS, CPM, CPI)
- Multi-market detection: if ad sets contain geo codes (SPA, USA, LATAM), asks if targets vary by market
- Filename hints auto-suggest Launch/Evergreen tagging

### Step 3: Analysis Engine (Silent)
Runs without user interaction:

**Per platform:**
- Aggregates raw data by ad name (never calculates on single-day rows)
- Compares vs client goal (primary) then industry benchmark (secondary)
- Detects Google campaign type from CTR values and Quality Score presence
- Applies Launch vs Evergreen thresholds per campaign

**Creative analysis (per ad):**
- Verdict: Scale / Kill / Test more
- Score: 0-10 with weighted breakdown adapted to available metrics
- Full data: Hook Rate (40%) + Hold Rate (30%) + CTR (20%) + CPL (10%)
- No video metrics: CTR (70%) + CPL (30%)
- No CPL: CTR (100%)

**Funnel analysis:** CPL per stage, conversion rates, drop-off points

**Flags:** Frequency fatigue, budget pacing (3+ days only), zero conversions after 2x target spend

**Cross-platform:** Side-by-side comparison with budget reallocation recommendation (only if date ranges match)

### Step 4: Chat Output
1. Executive summary (3-5 bullet insights)
2. Flags (frequency fatigue, pacing, zero conversions)
3. Per-platform metrics with color signals (green/red/yellow) and % vs goal
4. Creative verdicts with scores
5. Cross-platform comparison (if applicable)
6. Numbered action items

### Step 5: HTML Report
Two versions generated from a single template:
- **Agency version:** Full data, internal notes
- **Client version:** Clean, presentable

## Column Mapping

The skill matches columns by meaning, not name. Handles exports in any language:

| Metric | Recognized Column Names |
|--------|------------------------|
| Spend | Amount spent, Importe gastado, Costo, Cost, Spend |
| Impressions | Impressions, Impresiones, Impr. |
| Clicks | Link clicks, Clics en el enlace, Clicks |
| Reach | Reach, Alcance |
| Conversions | Results, Conversiones, Conversions |
| CPA | Cost per result, Costo/conv., Cost/conv. |

## File Structure

```
ad-reporting/
├── SKILL.md                          # Main skill definition
├── product.md                        # Changelog (updated with every SKILL.md change)
└── references/
    ├── meta-ads.md                   # Meta platform metrics + benchmarks
    ├── google-ads.md                 # Google platform metrics + benchmarks
    ├── youtube-ads.md                # YouTube platform metrics + benchmarks
    ├── tiktok-ads.md                 # TikTok platform metrics + benchmarks
    ├── report-template.md            # HTML report generation rules
    ├── report-template.html          # Full HTML template
    └── report-template-demo.html     # Demo report with sample data
```

## Install

Copy the entire `ad-reporting/` folder into your `.claude/skills/` directory.

## Requirements

- Claude Code CLI
- CSV exports from any supported ad platform

## Credits

Built by Virgil Brewster and Victor Chasaraz at [Sucana](https://sucana.ai) — AI-powered analytics for B2B SaaS.

---

## The Lead — AI Workflows for Marketers

Every Friday, one real AI workflow from inside our build. No theory. No hype. Just what worked, what flopped, and what we'd do differently.

[Join The Lead →](https://sucana.ai/newsletter)

Built by [Virgil Brewster](https://www.linkedin.com/in/virgilbrewster/) at [Sucana](https://sucana.ai)