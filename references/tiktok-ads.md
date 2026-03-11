# TikTok Ads — Reference

Platform: TikTok Ads Manager
Attribution window default: 7-day click / 1-day view — flag if different.
Note: TikTok is a creative-first platform. Performance is driven more by the creative than by targeting. Refresh cadence is faster than any other platform.

---

## Campaign Types

| Type | Description | Best For |
|------|-------------|----------|
| In-Feed Ads | Appear in the For You feed between organic content | Lead gen, traffic, conversions |
| TopView | First ad seen when user opens TikTok — full screen | Brand awareness, launches |
| Spark Ads | Boost existing organic TikTok posts as ads | Social proof, warm audiences |
| Branded Effects | Custom AR filters and effects | Brand awareness, engagement |

---

## Ad Formats

| Format | Dimensions | Duration |
|--------|-----------|----------|
| Vertical video | 9:16 — 1080×1920px | 5–60s (optimal: 15–30s) |
| Square | 1:1 — 1080×1080px | 5–60s |

Vertical 9:16 is the dominant format. Always optimise for vertical-first.

---

## Core Metrics

| Metric | Formula | Industry Benchmark |
|--------|---------|-------------------|
| Hook Rate (2s) | 2-Second Video Views / Impressions | > 25% |
| Hook Rate (6s) | 6-Second Video Views / Impressions | > 15% |
| View Rate | Views (at least 50% watched) / Impressions | > 20% |
| CTR | Clicks / Impressions | > 1% |
| CPM | (Spend / Impressions) × 1000 | Context-dependent |
| CPC | Spend / Clicks | vs client goal |
| CVR | Conversions / Clicks | > 2% |
| CPA | Spend / Conversions | vs client goal |
| ROAS | Revenue / Spend | > 2× launch · > 3× evergreen |

Always compare vs client goal first. Flag industry benchmarks as defaults.

---

## Campaign Modes

| | Launch Mode | Evergreen Mode |
|--|-------------|----------------|
| Duration | Time-boxed (days/weeks) | Always-on |
| Spend | Aggressive — higher daily budgets | Efficiency-focused — stable budgets |
| ROAS target | > 2× (or client goal) | > 3× (or client goal) |
| CPL tolerance | Higher — volume over cost | Lower — cost efficiency priority |
| Creative refresh | Every 5–7 days (fatigue hits faster on TikTok) | Every 2–3 weeks |
| Frequency alert | Cold > 2.5 | Cold > 1.5 |
| Goal | Maximise leads/sales in window | Sustain profitability long-term |

TikTok creative fatigue occurs faster than Meta or Google. Refresh thresholds are tighter.

---

## Creative Analysis — Decision Rules

### Scale / Kill / Test More

| Decision | Launch Mode | Evergreen Mode |
|----------|------------|----------------|
| Scale | Hook Rate (2s) > 25% AND CPL within +20% of client goal | Hook Rate (2s) > 30% AND CPL at or below client goal |
| Test more | Hook Rate (2s) > 25% but View Rate < 15% → rework video body | Hook Rate (2s) > 25% but CVR < 1.5% → review landing page |
| Kill | Hook Rate (2s) < 15% after 1,000+ impressions | Hook Rate (2s) < 20% after 2,000+ impressions |
| Frequency fatigue | Cold > 2.5 → refresh immediately | Cold > 1.5 → refresh immediately |

### Hook Analysis

On TikTok, the first 2 seconds determine everything:
- Hook Rate (2s) is the primary creative signal
- If 2s Hook Rate is strong but 6s Hook Rate drops sharply → opening grabs attention but loses it fast, rework seconds 2–6
- If both 2s and 6s are weak → the creative concept itself is the problem

### Creative Score (0–10)

Weight each signal:
- Hook Rate (2s) vs threshold: 40% of score
- View Rate vs threshold: 25% of score
- CTR vs benchmark: 20% of score
- CPA vs client goal: 15% of score

Show breakdown in output:
"7.0 — Hook Rate (2s) strong (+) · View Rate average (=) · CTR weak (-) · CPA on target (+)"

---

## Spark Ads

When running Spark Ads (boosting organic posts):
- Check organic engagement rate before boosting — high organic engagement signals strong creative
- Compare Spark Ad CPL vs standard In-Feed CPL for the same audience
- Spark Ads retain social proof (likes, comments, shares) — factor this into creative quality assessment

---

## Flags Specific to TikTok Ads

- Hook Rate (2s) < 15% after 500+ impressions → kill or rework immediately (TikTok punishes low-engagement creative with higher CPMs)
- CPM rising > 20% week-over-week → audience saturation, expand targeting or refresh creative
- View Rate < 10% consistently → content style not matching TikTok feed expectations
- No Spark Ads in account → missing social proof amplification opportunity, flag as recommendation
