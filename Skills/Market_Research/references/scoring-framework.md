# Market Research Scoring Framework

## Purpose

This framework converts sourced market research into a consistent opportunity score for affiliate market, category, and sub-niche evaluation.

Use together with the `firecrawl-market-research` skill.

The framework must work across multiple affiliate categories and platforms, including:

- TikTok
- TikTok Shop
- Shopee
- Shopee Video
- Pinterest
- other relevant affiliate or discovery platforms

---

# Scoring Scale

Score every factor from **0–10**.

- **0–2:** Very weak
- **3–4:** Weak
- **5–6:** Moderate
- **7–8:** Strong
- **9–10:** Very strong

Do not assign scores without supporting evidence.

---

# Core Factors

## 1. Market Demand — 25%

Evaluate:

- market size
- search demand
- consumer demand signals
- marketplace activity
- sales/activity signals
- category popularity
- purchase frequency
- demand consistency

### High Score

Strong and sustained demand supported by multiple reliable sources.

---

## 2. Market Growth & Trend — 15%

Evaluate:

- historical growth
- current trend direction
- industry forecasts
- emerging consumer behavior
- recent market developments
- search trend direction
- social-platform trend signals

Where relevant, evaluate platform-specific trend signals such as:

- TikTok trend activity
- marketplace search activity
- Pinterest Trends
- Google Trends

### High Score

The market shows sustained, stable, or accelerating growth rather than temporary virality alone.

---

## 3. Affiliate Commercial Potential — 20%

Evaluate:

- typical product price
- purchase frequency
- conversion potential
- availability of affiliate products
- commission attractiveness
- seller availability
- number of relevant brands
- attribution window
- refund/cancellation impact
- stock reliability
- affiliate-program eligibility

Also identify the platform monetization model.

### Direct Commerce Platforms

Examples:

- TikTok Shop
- Shopee
- other marketplaces

Evaluate:

- native purchase flow
- affiliate commission
- conversion friction
- marketplace trust
- checkout convenience

### Discovery / Referral Platforms

Examples:

- Pinterest
- blogs
- search-driven platforms

Evaluate:

- outbound affiliate-link capability
- product tagging
- traffic potential
- search discoverability
- content lifespan
- click-through opportunity
- ability to send users to affiliate-enabled destinations

Do not assume every platform contributes equally to direct conversion.

### High Score

The category can generate meaningful and repeatable affiliate revenue through one or more viable platforms.

---

## 4. Content Potential — 15%

Evaluate whether the category can generate multiple repeatable content angles.

Examples:

- product reviews
- comparisons
- styling
- use cases
- problems and solutions
- educational content
- trend content
- tutorials
- visual inspiration
- buying guides
- purchase-intent content
- evergreen search content

Also evaluate platform-content fit.

### TikTok / Short Video

Consider:

- hooks
- demonstrations
- entertainment
- problem-solution content
- short product reviews
- trend participation

### Shopee Video

Consider:

- product-focused demonstrations
- review content
- buying-intent content
- direct conversion

### Pinterest

Consider:

- visual inspiration
- evergreen content
- search-driven discovery
- boards
- product Pins
- comparison graphics
- guides
- styling ideas
- tutorials
- problem-solving content
- long-tail keyword potential

### High Score

The category supports many differentiated and repeatable content formats across relevant platforms.

---

## 5. Competition — 10%

Evaluate:

- number of major competitors
- creator saturation
- brand concentration
- marketplace saturation
- keyword/content saturation
- difficulty differentiating content
- competitive intensity

Scoring is reversed:

- Low competition = high score
- High competition = low score

Competition should be evaluated separately when major platforms behave differently.

Example:

```yaml
platform_competition:
  tiktok:
  shopee:
  pinterest:
```

The overall competition score should represent the realistic opportunity across the target platform mix.

---

## 6. Audience Fit — 10%

Evaluate:

- clarity of target audience
- purchasing power
- platform fit
- online shopping behavior
- search/discovery behavior
- match with target demographic
- problem relevance
- likelihood of responding to affiliate content

Where possible, evaluate audience fit by platform.

Example:

```yaml
platform_audience_fit:
  tiktok:
  shopee:
  pinterest:
```

### High Score

The audience is clearly identifiable, reachable, relevant to the category, and likely to take commercial action.

---

## 7. Market Risk — 5%

Evaluate:

- demand volatility
- trend dependency
- regulatory risk
- platform dependency
- seasonal dependency
- data uncertainty
- seller reliability
- counterfeit risk
- commission volatility
- platform-policy changes
- content-policy risk

Scoring is reversed:

- Low risk = high score
- High risk = low score

---

# Platform Role Assessment

Every market evaluation should identify the role of each relevant platform.

Possible roles:

```text
DIRECT_COMMERCE
DISCOVERY
TRAFFIC
CONTENT
SEARCH
CONVERSION
RETENTION
SECONDARY
NOT_RECOMMENDED
```

Example:

```yaml
platform_roles:
  tiktok:
    - CONTENT
    - DISCOVERY
    - DIRECT_COMMERCE

  shopee:
    - DIRECT_COMMERCE
    - CONVERSION

  pinterest:
    - DISCOVERY
    - SEARCH
    - TRAFFIC
    - CONTENT
```

Do not force every platform into the same role.

A platform may be valuable even if it does not provide the strongest direct checkout conversion.

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

| Score | Market Opportunity | Meaning |
|---|---|---|
| 8.0–10 | GO | Strong market opportunity |
| 6.5–7.9 | TEST | Promising but requires validation |
| 5.0–6.4 | WATCH | Keep monitoring |
| Below 5.0 | SKIP | Weak opportunity |

These thresholds determine **market attractiveness**, not automatic execution readiness.

---

# Evidence Requirements

Every score must include supporting evidence.

Prefer sources in this order:

1. Government / regulatory / official public sources
2. Official platform documentation
3. Official company or brand sources
4. High-quality industry and market reports
5. Company investor relations
6. Credible financial or industry portals
7. Credible news
8. Marketplace observations
9. Community discussions

Community sources such as Reddit should primarily support:

- consumer pain points
- user experience
- recurring problems
- unmet needs
- consumer language

Do not use community discussion as primary evidence for market size, revenue, or regulatory facts.

Cross-reference important numbers whenever possible.

If sources conflict:

```text
Status: CONFLICTING DATA
```

Explain why the figures may differ before scoring.

---

# Evidence Confidence

Every market evaluation must include an Evidence Confidence Score from **0–10**.

Evaluate confidence based on:

- source quality
- source recency
- number of independent sources
- consistency between sources
- relevance to the exact category
- relevance to the exact sub-niche
- platform-specific evidence availability
- availability of affiliate-specific commercial data

## Confidence Guide

- **9–10:** Strong primary evidence with recent and consistent data
- **7–8.9:** Good evidence with minor gaps
- **5–6.9:** Moderate evidence with important assumptions
- **Below 5:** Weak evidence; decision remains provisional

Output:

```yaml
evidence_confidence:
```

---

# Critical Data Gap Penalty

Important missing data must affect scoring or execution readiness.

Critical affiliate data may include:

- actual SKU commission
- conversion data
- click-through data
- cancellation or refund rate
- seller eligibility
- stock stability
- attribution rules
- product legality
- authenticity
- category-specific demand evidence
- platform-specific commercial data

## Minor Gap

No score penalty required.

Example:

A secondary demographic detail is unavailable.

## Important Gap

Reduce the relevant factor score by approximately:

```text
0.5–1.0 points
```

Example:

Platform commission is available only at category level rather than SKU level.

## Critical Gap

A market cannot receive an unconditional execution `GO`.

Example:

```text
Market Opportunity: GO
Execution Readiness: TEST
Final Decision: TEST
```

until the missing data is validated.

---

# Hard Risk and Compliance Gate

Certain risks must be evaluated before final Opportunity Scoring.

If a critical compliance issue exists, scoring alone must not override it.

Possible hard gates include:

- illegal products
- prohibited products
- missing mandatory registration
- counterfeit or unauthenticated products
- unsupported medical or health claims
- serious consumer safety concerns
- platform-prohibited categories
- seller not eligible for affiliate commission
- prohibited affiliate-link behavior

Possible outcomes:

```text
PASS
REVIEW
REJECT
```

## PASS

No critical compliance issue identified.

Proceed to scoring.

## REVIEW

Important compliance information is missing or uncertain.

Execution readiness cannot exceed:

```text
TEST
```

until verified.

## REJECT

A critical legal, safety, platform, or authenticity issue exists.

Final decision:

```text
SKIP
```

regardless of Opportunity Score.

Output:

```yaml
compliance_gate:
  status:
  issues:
```

---

# Platform Policy Check

For every platform included in the strategy, verify where possible:

- affiliate-link permissions
- product-tagging capability
- seller eligibility
- commercial-content disclosure requirements
- prohibited categories
- advertising restrictions
- attribution rules
- analytics availability

Do not assume platform policies are permanent.

Use current official platform documentation whenever platform rules materially affect the recommendation.

---

# Decision Layers

Separate **market attractiveness** from **execution readiness**.

Output:

```yaml
market_opportunity:
execution_readiness:
decision:
```

Example:

```yaml
opportunity_score: 8.2
evidence_confidence: 7.4

market_opportunity: GO
execution_readiness: TEST
decision: TEST
```

Meaning:

- the market itself is attractive;
- affiliate execution still requires validation.

The final decision should use the more conservative status when critical data remains unresolved.

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

Confidence values:

```text
HIGH
MEDIUM
LOW
```

Do not treat assumptions as verified facts.

Clearly separate:

```text
VERIFIED FACT
ESTIMATE
ASSUMPTION
DATA GAP
```

---

# Output Format

```yaml
market:
category:
sub_niche:
country:

platforms:
  - platform:

platform_roles:
  tiktok:
  shopee:
  pinterest:

research_period:

scores:
  market_demand:
  growth_trend:
  affiliate_potential:
  content_potential:
  competition:
  audience_fit:
  market_risk:

platform_scores:
  tiktok:
    audience_fit:
    content_fit:
    commercial_fit:
  shopee:
    audience_fit:
    content_fit:
    commercial_fit:
  pinterest:
    audience_fit:
    content_fit:
    commercial_fit:

opportunity_score:
evidence_confidence:

compliance_gate:
  status:
  issues:

market_opportunity:
execution_readiness:
decision:

key_evidence:
  - source:
    finding:
    period:
    confidence:

verified_facts:

estimates:

assumptions:

risks:

data_gaps:

recommended_platform_mix:

recommended_next_action:
```

---

# Final Rule

The Opportunity Score is a **decision-support tool**, not an automatic decision maker.

A high Opportunity Score alone is not sufficient for a final `GO`.

The final decision must consider:

1. Opportunity Score
2. Evidence Confidence
3. Critical Data Gaps
4. Hard Risk / Compliance Gate
5. Execution Readiness
6. Platform Fit

If critical data is missing, use the more conservative status.

Example:

```text
Market Opportunity: GO
Execution Readiness: TEST
Final Decision: TEST
```

A market should proceed to Product Research when:

- the opportunity is commercially promising;
- evidence quality is sufficient;
- no critical compliance issue requires rejection;
- at least one viable affiliate monetization route exists;
- relevant platforms show sufficient audience/content fit;
- remaining data gaps can reasonably be validated at product level.

A platform does not need to be a direct-commerce platform to be valuable.

For example:

```text
Pinterest
↓
Search / Discovery
↓
Evergreen Content
↓
Affiliate Link / Product Destination
↓
Conversion
```

while:

```text
TikTok
↓
Discovery / Content
↓
TikTok Shop
↓
Conversion
```

and:

```text
Shopee
↓
Product Discovery
↓
Shopee Video / Affiliate
↓
Marketplace Checkout
↓
Conversion
```

Final workflow:

```text
Market Research
      ↓
Evidence Validation
      ↓
Platform Role Assessment
      ↓
Compliance / Hard Risk Gate
      ↓
Opportunity Scoring
      ↓
Evidence Confidence
      ↓
Critical Data Gap Check
      ↓
Market Opportunity
      ↓
Execution Readiness
      ↓
Platform Mix Recommendation
      ↓
GO / TEST / WATCH / SKIP
      ↓
Product Research
```
