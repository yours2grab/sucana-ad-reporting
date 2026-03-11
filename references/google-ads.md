# Google Ads — Reference

Platform: Google Search, Display, Performance Max
Attribution window default: 30-day click (Google default) — flag if different.

---

## Campaign Types

| Type | Description | Primary Metric |
|------|-------------|----------------|
| Search | Text ads triggered by keywords | CTR, Conversion Rate, CPA |
| Display | Image/banner ads across Google network | CPM, CTR, CPA |
| Performance Max | AI-optimised across all Google surfaces | ROAS, CPA |
| Shopping | Product listing ads (ecommerce) | ROAS, CPA |

---

## Campaign Type Detection

Before applying benchmarks, identify the campaign type:
- Quality Score column present → Search campaign → apply Search benchmarks
- CTR values consistently < 2% AND no Quality Score column → Display campaign → apply Display benchmarks
- "Video played", "View rate", or "CPV" columns present → YouTube campaign → use youtube-ads.md instead

## Core Metrics — Search Campaigns

| Metric | Industry Benchmark | Notes |
|--------|-------------------|-------|
| Quality Score | > 7/10 | Below 5 = keyword/ad/landing page mismatch |
| Impression Share | > 50% | Low share = budget or quality issue |
| CTR | > 5% | Below 2% = ad copy or keyword relevance problem |
| Conversion Rate | > 3% | Varies heavily by industry |
| CPA | vs client goal | Client goal always primary |
| ROAS | > 3× | Client goal always primary |
| Avg. CPC | Context-dependent | Compare vs historical |

## Core Metrics — Display Campaigns

| Metric | Industry Benchmark | Notes |
|--------|-------------------|-------|
| CTR | > 0.5% | Display CTR is structurally lower than Search |
| CPM | Context-dependent | Compare vs historical and platform average |
| Conversion Rate | > 1% | Lower than Search — display is higher funnel |
| CPA | vs client goal | Client goal always primary |
| View-through rate | Track vs baseline | Assisted conversions via impression |

Always compare vs client goal first. Flag industry benchmarks as defaults.
Always state which campaign type benchmarks were applied in the output.

---

## Quality Score Breakdown

Quality Score is made up of three components — flag each when below threshold:

| Component | Benchmark | Action if low |
|-----------|-----------|---------------|
| Expected CTR | Above average | Rewrite ad copy, test new headlines |
| Ad Relevance | Above average | Align keywords tighter to ad copy |
| Landing Page Experience | Above average | Improve page speed, relevance, and copy match |

---

## Campaign Mode — Decision Rules

| Decision | Launch Mode | Evergreen Mode |
|----------|------------|----------------|
| Scale | CPA within +20% of client goal AND Conv Rate > 2% | CPA at or below client goal AND Conv Rate > 3% |
| Test more | CPA within range but Quality Score < 5 → fix ad/landing | Impression Share < 30% → increase bids or budget |
| Kill | CPA > 2× client goal after significant spend | CPA > 1.5× client goal consistently |
| Pause keyword | CTR < 1% after 500+ impressions (Search) | CTR < 2% after 1,000+ impressions (Search) |

---

## Creative Score (0–10)

Weight each signal:
- Quality Score vs benchmark (> 7): 30% of score
- CTR vs benchmark: 30% of score
- Conversion Rate vs benchmark: 25% of score
- CPA vs client goal: 15% of score

Show breakdown in output:
"6.8 — Quality Score strong (+) · CTR average (=) · Conv Rate weak (-) · CPA above goal (-)"

---

## Flags Specific to Google Ads

- Quality Score < 5 on any active keyword → flag immediately
- Impression Share < 20% on Search → budget or bidding problem
- Search Term Report: irrelevant queries consuming budget → add negatives
- PMax cannabilising branded Search campaigns → flag for manual review
