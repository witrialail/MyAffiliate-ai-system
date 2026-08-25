# Market Research Scoring Framework

## Purpose

This framework converts sourced market research into a consistent opportunity score for affiliate market, category, and sub-niche evaluation.

Use together with the `firecrawl-market-research` skill.

---

## Scoring Scale

Score every factor from **0–10**.

- **0–2:** Very weak
- **3–4:** Weak
- **5–6:** Moderate
- **7–8:** Strong
- **9–10:** Very strong

Do not assign scores without supporting evidence.

---

## Core Factors

### 1. Market Demand — 25%

Evaluate:

- Market size
- Search or consumer demand signals
- Sales/activity signals
- Category popularity
- Demand consistency

**High score:** strong and sustained demand supported by multiple sources.

---

### 2. Market Growth & Trend — 15%

Evaluate:

- Historical growth
- Current trend direction
- Industry forecasts
- Emerging consumer behavior
- Recent market developments

**High score:** market shows sustained or accelerating growth.

---

### 3. Affiliate Commercial Potential — 20%

Evaluate:

- Typical product price
- Purchase frequency
- Conversion potential
- Availability of affiliate products
- Commission attractiveness
- Number of relevant sellers/brands

**High score:** products are easy to monetize through affiliate channels.

---

### 4. Content Potential — 15%

Evaluate whether the category can generate multiple content angles:

- Product reviews
- Comparisons
- Styling/use cases
- Problems and solutions
- Educational content
- Trend content
- Purchase-intent content

**High score:** many repeatable content opportunities exist.

---

### 5. Competition — 10%

Evaluate:

- Number of major competitors
- Creator saturation
- Brand concentration
- Difficulty differentiating content
- Competitive intensity

Scoring is reversed:

- Low competition = high score
- High competition = low score

---

### 6. Audience Fit — 10%

Evaluate:

- Clear target audience
- Audience purchasing power
- Platform fit
- Online shopping behavior
- Match with target demographic

**High score:** audience is easy to identify, reach, and convert.

---

### 7. Market Risk — 5%

Evaluate:

- Demand volatility
- Trend dependency
- Regulatory risk
- Platform dependency
- Seasonal dependency
- Data uncertainty

Scoring is reversed:

- Low risk = high score
- High risk = low score

---

# Opportunity Score Formula

```text
Opportunity Score =
(Market Demand × 0.25)
+ (Growth & Trend × 0.15)
+ (Affiliate Potential × 0.20)
+ (Content Potential × 0.15)
+ (Competition × 0.10)
+ (Audience Fit × 0.10)
+ (Market Risk × 0.05)
```

Maximum score:

```text
10.0
```

---

# Decision Threshold

| Score | Decision | Meaning |
|---|---|---|
| 8.0–10 | GO | Strong opportunity |
| 6.5–7.9 | TEST | Promising but requires validation |
| 5.0–6.4 | WATCH | Keep monitoring |
| Below 5.0 | SKIP | Weak opportunity |

---

# Evidence Requirements

Every score must include supporting evidence.

Prefer:

1. Official company or industry sources
2. Market reports
3. Company investor relations
4. Financial or industry portals
5. Credible news
6. Platform-level market signals

Cross-reference important numbers whenever possible.

If sources conflict:

```text
Status: CONFLICTING DATA
```

Explain the disagreement before scoring.

---

# Data Quality Rules

For every important metric include:

```text
Metric:
Value:
Unit:
Period:
Source:
Confidence:
```

Confidence levels:

- HIGH
- MEDIUM
- LOW

Do not treat assumptions as verified facts.

---

# Output Format

```yaml
market:
category:
sub_niche:
country:
platform:
research_period:

scores:
  market_demand:
  growth_trend:
  affiliate_potential:
  content_potential:
  competition:
  audience_fit:
  market_risk:

opportunity_score:

decision:

key_evidence:
  - source:
    finding:
    period:
    confidence:

risks:

data_gaps:

recommended_next_action:
```

---

# Final Rule

The Opportunity Score is a **decision-support tool**, not an automatic decision maker.

A high score should move the category into deeper product-level validation.

Flow:

```text
Market Research
      ↓
Opportunity Scoring
      ↓
GO / TEST / WATCH / SKIP
      ↓
Product Research
```
