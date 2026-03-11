# Meta Ads — Reference

Platform: Facebook & Instagram
Attribution window default: 7-day click / 1-day view
Post-iOS 14.5: Meta ROAS is modelled data, not exact — flag this in every report.

---

## Ad Naming Convention

Standard pattern:
```
Ad [#] - Hook [#] + Body [letter] + CTA [#]
Example: Ad 65 - Hook 1 + Body A + CTA 1
```

When analysing creative variants, compare by:
1. Hook performance — which Hook # generates the best Hook Rate
2. Body performance — which Body letter retains viewers best (Hold Rate)
3. CTA performance — which CTA # drives the most link clicks and conversions
4. Combined winner — best Hook + Body + CTA combination

---

## Ad Formats

| Format | Dimensions |
|--------|-----------|
| Horizontal | 16:9 — 1920×1080px |
| Vertical | 9:16 — 1080×1920px |

---

## Funnel Stages (Targeting)

| Stage | Description |
|-------|-------------|
| Cold | Broad audiences, interest targeting, lookalikes |
| Warm | Website visitors, video viewers (25–75%) |
| Retargeting | High-intent signals, landing page visitors |

---

## Campaign Modes

| | Launch Mode | Evergreen Mode |
|--|-------------|----------------|
| Duration | Time-boxed (days/weeks) | Always-on |
| Spend | Aggressive — higher daily budgets | Efficiency-focused — stable budgets |
| ROAS target | > 2× (or client goal) | > 3× (or client goal) |
| CPL tolerance | Higher — volume over cost | Lower — cost efficiency priority |
| Creative refresh | Weekly | Monthly |
| Frequency alert | Cold > 3, Warm > 5 | Cold > 2, Warm > 4 |
| Goal | Maximise leads/sales in window | Sustain profitability long-term |

---

## Core Metrics

| Metric | Formula | Industry Benchmark |
|--------|---------|-------------------|
| Hook Rate | 3s video plays / Impressions | > 30% |
| Hold Rate | ThruPlay / 3s video plays | > 20% |
| CTR (Link) | Link clicks / Impressions | > 1.5% |
| CPL | Spend / Leads | vs client goal |
| CPA | Spend / Purchases | vs client goal |
| ROAS | Revenue / Spend | > 2× launch · > 3× evergreen |
| Frequency | Impressions / Reach | Launch: cold >3, warm >5 · Evergreen: cold >2, warm >4 |
| CPM | (Spend / Impressions) × 1000 | Context-dependent |

Always compare vs client goal first. Flag industry benchmarks as defaults.

---

## Creative Analysis — Decision Rules

### Scale / Kill / Test More

| Decision | Launch Mode | Evergreen Mode |
|----------|------------|----------------|
| Scale | Hook Rate > 25% AND CPL within +20% of client goal | Hook Rate > 30% AND CPL at or below client goal |
| Test more | Hook Rate > 25% but Hold Rate < 15% → rework body | Hook Rate > 30% but Hold Rate < 20% → rework body |
| Kill | Hook Rate < 15% after 800+ impressions | Hook Rate < 20% after 1,000+ impressions |
| Frequency fatigue | Cold > 3 → refresh creative | Cold > 2 → refresh creative |

### Creative Score (0–10)

Weight each signal:
- Hook Rate vs threshold: 40% of score
- Hold Rate vs threshold: 30% of score
- CTR vs benchmark: 20% of score
- CPL vs client goal: 10% of score

Show breakdown in output:
"7.2 — Hook Rate strong (+) · Hold Rate weak (-) · CTR average (=) · CPL on target (+)"

---

## Funnel Analysis

When multi-stage data is present, calculate:
- CPL per funnel stage (Cold → Landing → Lead Magnet → VSL → Purchase)
- Conversion rate between each stage
- Drop-off points — which stage is losing the most volume
- Compare CPL at each stage vs overall CPL target
