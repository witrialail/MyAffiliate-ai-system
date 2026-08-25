---
name: firecrawl-market-research
description: Research and evaluate affiliate markets, categories, and sub-niches using Firecrawl, current market evidence, platform signals, competition, audience fit, content potential, affiliate economics, and execution readiness.
license: ISC

metadata:
  author: firecrawl
  version: "0.2.0-affiliate"
  homepage: https://www.firecrawl.dev
  source: https://github.com/firecrawl/firecrawl-workflows

inputs:
  - name: FIRECRAWL_API_KEY
    description: Firecrawl API key for hosted Firecrawl requests.
    required: true
---

# Affiliate Market Research

## Purpose

Research and evaluate markets, categories, and sub-niches before product-level affiliate research begins.

The goal is to identify opportunities with:

- strong and sustainable demand;
- viable affiliate economics;
- repeatable content potential;
- suitable audience-platform fit;
- manageable competition and risk;
- sufficient evidence quality;
- realistic execution readiness.

This skill must remain category-agnostic and work across markets such as fashion, beauty, electronics, home and living, sports, automotive, digital products, and other affiliate categories.

---

## Onboarding

Infer from context whenever possible:

- target market
- category
- sub-niche
- country or geography
- target platforms
- audience
- timeframe
- price range

Do not ask questions if the available context is sufficient.

Ask only when missing information would materially prevent useful research.

---

## Research Collection

Use Firecrawl search and scrape to collect relevant evidence.

Prioritize sources in this order:

1. Government, regulator, or official public sources
2. Official platform documentation
3. Official company or brand sources
4. High-quality industry and market reports
5. Investor relations or company filings
6. Credible financial or industry portals
7. Credible news
8. Marketplace observations
9. Community discussions

Use community sources primarily for:

- consumer pain points
- user experience
- unmet needs
- recurring complaints
- consumer language

Do not use community discussions as primary evidence for:

- market size
- revenue
- regulatory rules
- official platform policies

Prefer recent evidence when evaluating current market conditions.

---

## Research Areas

Evaluate:

1. Market demand
2. Market growth and trends
3. Affiliate commercial potential
4. Content potential
5. Competition
6. Audience fit
7. Market risk

Also evaluate:

8. Evidence confidence
9. Critical data gaps
10. Compliance and hard risks
11. Platform roles
12. Platform-specific fit
13. Execution readiness

---

## Platform Assessment

When multiple platforms are included, evaluate them separately.

Possible platforms include:

- TikTok
- TikTok Shop
- Shopee
- Shopee Video
- Pinterest
- other relevant affiliate or discovery platforms

Do not assume all platforms perform the same role.

Possible platform roles:

- DIRECT_COMMERCE
- DISCOVERY
- TRAFFIC
- CONTENT
- SEARCH
- CONVERSION
- RETENTION
- SECONDARY
- NOT_RECOMMENDED

Examples:

TikTok Shop may function as:

- CONTENT
- DISCOVERY
- DIRECT_COMMERCE
- CONVERSION

Shopee may function as:

- SEARCH
- DIRECT_COMMERCE
- CONVERSION

Pinterest may function as:

- DISCOVERY
- SEARCH
- TRAFFIC
- CONTENT

Pinterest must not automatically be treated as equivalent to a native marketplace.

---

## Affiliate Evaluation

After evidence collection, evaluate the opportunity using:

`references/scoring-framework.md`

Score every core factor from **0–10**.

Calculate the weighted Opportunity Score exactly according to the scoring framework.

Do not assign scores without supporting evidence.

---

## Platform Scores

When multiple platforms are evaluated, always return structured platform scores.

For each platform include:

- audience_fit
- content_fit
- commercial_fit

Example:

```yaml
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
```

Platform scores supplement the main Opportunity Score.

They do not replace the core weighted scoring model.

---

## Evidence Confidence

Every evaluation must include an Evidence Confidence score from **0–10**.

Confidence must consider:

- source quality
- recency
- number of independent sources
- consistency between sources
- relevance to the exact category
- relevance to the exact sub-niche
- platform-specific evidence
- affiliate-specific commercial evidence

A high Opportunity Score with weak evidence must not automatically receive a final GO decision.

---

## Compliance and Hard Risk Gate

Evaluate major legal, safety, authenticity, platform-policy, and regulatory risks before finalizing the recommendation.

Possible statuses:

- PASS
- REVIEW
- REJECT

### PASS

No critical issue identified.

### REVIEW

Important information is missing or uncertain.

Execution readiness cannot exceed `TEST` until validated.

### REJECT

A critical legal, safety, authenticity, or platform-policy issue exists.

Final decision must be:

`SKIP`

regardless of Opportunity Score.

---

## Critical Data Gaps

Identify data gaps that could materially affect affiliate execution.

Examples:

- actual SKU commission
- seller eligibility
- attribution rules
- stock stability
- conversion data
- cancellation or refund rates
- product authenticity
- regulatory status
- platform-specific commercial evidence

Important missing data must affect scoring or execution readiness according to the scoring framework.

---

## Decision Layers

Always separate:

### Market Opportunity

How attractive the market itself is.

Possible statuses:

- GO
- TEST
- WATCH
- SKIP

### Execution Readiness

How ready the opportunity is for actual affiliate execution.

Possible statuses:

- GO
- TEST
- WATCH
- SKIP

### Final Decision

Use the field:

```yaml
decision:
```

Do not use alternate field names such as:

```yaml
final_decision:
```

If Market Opportunity and Execution Readiness differ, use the more conservative status for `decision`.

Example:

```yaml
market_opportunity: GO
execution_readiness: TEST
decision: TEST
```

---

## Output

Always return structured results including:

```yaml
market:
category:
sub_niche:
country:

platforms:

platform_roles:

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

opportunity_score:
evidence_confidence:

compliance_gate:
  status:
  issues:

market_opportunity:
execution_readiness:
decision:

key_evidence:

verified_facts:

estimates:

assumptions:

risks:

data_gaps:

recommended_platform_mix:

recommended_next_action:
```

---

## Evidence Rules

- Never fabricate data.
- Separate verified facts, estimates, assumptions, and data gaps.
- Cross-reference important numbers whenever possible.
- Note conflicting information between sources.
- Explain why conflicting figures may differ.
- Include period and unit for important metrics.
- Prefer primary and official evidence.
- Use secondary sources only where appropriate.
- Do not present assumptions as facts.
- Do not derive false precision from incomplete data.

---

## Platform Allocation Rules

If recommending platform allocation percentages, label them as:

`TEST HYPOTHESIS`

unless they are supported by observed performance data.

Example:

```text
TikTok Shop: 45%
Shopee: 40%
Pinterest: 15%

Status: TEST HYPOTHESIS
```

Do not present estimated platform allocations as optimized strategy.

---

## Recommended Next Action

The recommendation must specify what should happen next.

A positive market result should normally move into:

`Product Research`

but only when:

- market attractiveness is sufficient;
- evidence confidence is acceptable;
- no critical compliance issue requires rejection;
- at least one viable monetization route exists;
- remaining gaps can reasonably be validated at product level.

Do not jump directly to public product recommendations.

---

## Workflow

```text
Market Research
      ↓
Evidence Collection
      ↓
Source Validation
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

---

## Quality Bar

The final recommendation must be actionable for affiliate decision-making.

A high Opportunity Score alone is not sufficient for a final `GO`.

Always consider:

1. Opportunity Score
2. Evidence Confidence
3. Critical Data Gaps
4. Compliance / Hard Risk Gate
5. Execution Readiness
6. Platform Fit

When multiple platforms are evaluated, always include `platform_scores` inside the structured output.

Use the field name `decision` consistently for the final overall decision.

Platform allocation percentages must be labeled as hypotheses unless supported by observed performance data.

Do not recommend a category only because it is viral.

Do not force all platforms into the same commercial role.

Prefer sustainable affiliate opportunities over short-lived hype.
