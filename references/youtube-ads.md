# YouTube Ads — Reference

Platform: YouTube (managed via Google Ads)
Attribution window default: 30-day click / 1-day view (Google default) — flag if different.

---

## Campaign Types

| Type | Description | Skippable? |
|------|-------------|------------|
| Skippable In-Stream | Plays before/during video, skip after 5s | Yes |
| Non-Skippable In-Stream | 15s max, no skip option | No |
| Bumper Ads | 6s non-skippable | No |
| In-Feed Video | Appears in search results and feed | N/A |
| Shorts Ads | Vertical ads between Shorts | Yes |

---

## Core Metrics

| Metric | Formula | Industry Benchmark |
|--------|---------|-------------------|
| View Rate | Views / Impressions | > 30% |
| Avg. CPV | Spend / Views | < €0.05 |
| Skip Rate | Skips / Ad starts | < 70% |
| 25% Completion | Views reaching 25% / Total starts | Track vs baseline |
| 50% Completion | Views reaching 50% / Total starts | Track vs baseline |
| 75% Completion | Views reaching 75% / Total starts | Track vs baseline |
| 100% Completion | Views reaching 100% / Total starts | > 10% |
| CTR | Clicks / Impressions | > 0.5% |
| CPA | Spend / Conversions | vs client goal |

Always compare vs client goal first. Flag industry benchmarks as defaults.

---

## Hook Analysis (First 5 Seconds)

For skippable ads, the first 5 seconds are critical — the viewer can skip after this point.

- Track view-through rate at the 5s mark as a proxy for hook strength
- If Skip Rate > 80% → hook is weak, rework opening 5 seconds
- Compare completion curves across ad variants to identify drop-off points

---

## Campaign Mode — Decision Rules

| Decision | Launch Mode | Evergreen Mode |
|----------|------------|----------------|
| Scale | View Rate > 25% AND CPV below goal | View Rate > 30% AND CPV below goal |
| Test more | View Rate > 25% but 100% Completion < 5% → rework ending | View Rate > 30% but CPA above goal → review targeting |
| Kill | View Rate < 15% after 2,000+ impressions | View Rate < 20% after 5,000+ impressions |

---

## Creative Score (0–10)

Weight each signal:
- View Rate vs benchmark: 35% of score
- Skip Rate vs benchmark: 25% of score
- 100% Completion vs benchmark: 25% of score
- CPV vs client goal: 15% of score

Show breakdown in output:
"6.5 — View Rate average (=) · Skip Rate high (-) · Completion Rate weak (-) · CPV on target (+)"

---

## Flags Specific to YouTube Ads

- Skip Rate > 85% on skippable ads → hook is failing, pause and rework
- 100% Completion < 5% → message not landing, review script length and pacing
- CPV rising week-over-week → audience saturation, refresh creative or expand targeting
- Non-skippable ads with low CTR → message mismatch between ad and landing page
