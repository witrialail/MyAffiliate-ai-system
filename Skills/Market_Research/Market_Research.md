---
name: firecrawl-market-research
description: Research and evaluate affiliate markets, categories, and sub-niches using Firecrawl, current market evidence, platform signals, competition, audience fit, content potential, affiliate economics, proportional risk handling, and execution readiness.
license: ISC

metadata:
  author: Witriliun
  version: "0.2.2-affiliate"
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

The skill should support progression, not block promising opportunities because of small uncertainties.

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

For current-market evaluations, prioritize evidence from the current year whenever reliable data is available.

Older evidence may be used for:

- historical comparison
- long-term trend context
- regulatory background

Older evidence must not replace newer reliable evidence when newer data exists.

Clearly label older evidence as historical context.

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
14. Risk severity

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

## Proportional Risk Handling

Apply risk proportionally.

Not every problem, uncertainty, or missing data point should block progression.

Classify unresolved issues as:

### MINOR

Examples:

- secondary demographic detail missing;
- small source inconsistency;
- non-essential historical data unavailable;
- minor platform-specific uncertainty.

Handling:

- do not block Product Research;
- no automatic downgrade required;
- record the issue for later validation.

### MODERATE

Examples:

- actual SKU commission not yet known;
- stock stability not yet verified;
- warranty quality unclear;
- conversion data unavailable;
- attribution route needs testing.

Handling:

- normally continue as `TEST`;
- proceed to Product Research;
- validate during product-level research.

### CRITICAL

Examples:

- illegal or prohibited product category;
- missing mandatory legal certification;
- serious safety concern;
- counterfeit or clearly unauthenticated product supply;
- prohibited platform behavior;
- no viable affiliate monetization route.

Handling:

- use `REVIEW` or `SKIP`;
- do not proceed to execution until resolved.

Do not downgrade or block an otherwise promising market solely because of MINOR issues.

MODERATE uncertainty should normally support progression to Product Research under `TEST`.

---

## Compliance and Hard Risk Gate

Evaluate major legal, safety, authenticity, platform-policy, certification, prohibited-claim, and regulatory risks before finalizing the recommendation.

The Compliance Gate must contain only issues related to:

- legal requirements
- regulatory requirements
- safety
- authenticity
- mandatory certification
- prohibited or unsupported claims
- platform-policy restrictions
- prohibited product categories

Do **not** place normal commercial uncertainty inside the Compliance Gate.

The following belong under `Critical Data Gaps` or `Execution Readiness` instead:

- commission rates
- conversion rates
- stock stability
- warranty quality
- refund rates
- cancellation rates
- observed performance data

Possible statuses:

- PASS
- REVIEW
- REJECT

### PASS

No critical compliance issue identified.

Minor compliance uncertainty that does not materially affect legality, safety, authenticity, or platform eligibility may still proceed to Product Research.

### REVIEW

Important legal, regulatory, safety, authenticity, certification, claim, or platform-policy information is unresolved.

Use REVIEW only when the uncertainty is meaningful enough to affect execution.

Moderate unresolved issues may still proceed to Product Research under `TEST` if they can reasonably be verified during the next stage.

### REJECT

A confirmed critical legal, safety, authenticity, certification, prohibited-claim, or platform-policy issue exists.

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
- warranty quality
- product authenticity
- regulatory status
- platform-specific commercial evidence
- observed product performance

Classify important gaps as:

- MINOR
- MODERATE
- CRITICAL

Not every data gap is a blocker.

### MINOR

Useful but non-essential information is missing.

Proceed normally.

### MODERATE

Could materially affect commercial performance.

Proceed to Product Research with `TEST` status.

### CRITICAL

Could invalidate:

- legality
- safety
- authenticity
- monetization
- platform eligibility

Must be resolved before execution.

Do not automatically classify commercial data gaps as compliance issues.

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

Do not generate a numeric Execution Readiness score unless a separate scoring formula is explicitly defined in the framework.

By default, return only:

```yaml
execution_readiness: GO
```

or:

```yaml
execution_readiness: TEST
```

or:

```yaml
execution_readiness: WATCH
```

or:

```yaml
execution_readiness: SKIP
```

### Final Decision

Use the field:

```yaml
decision:
```

Do not use:

```yaml
final_decision:
```

If Market Opportunity and Execution Readiness differ, use the more conservative status for `decision`.

However, `TEST` is a valid progression state and should normally continue to Product Research.

Example:

```yaml
market_opportunity: GO
execution_readiness: TEST
decision: TEST
```

This means:

- market opportunity is strong;
- some validation remains;
- Product Research should continue.

---

## Progression Rule

Market Research is a market-level filter.

It should not attempt to resolve every product-level uncertainty.

Proceed to Product Research when:

- Market Opportunity is `GO` or `TEST`;
- no confirmed CRITICAL compliance issue exists;
- at least one plausible monetization route exists;
- remaining MINOR or MODERATE gaps can be validated at product level.

Example:

```text
Market Opportunity: GO
Execution Readiness: TEST
Unresolved Issues: MODERATE

→ PROCEED TO PRODUCT RESEARCH
```

Only stop progression when:

```text
Confirmed CRITICAL issue
→ REVIEW / SKIP
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

risk_summary:
  minor:
  moderate:
  critical:

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
  minor:
  moderate:
  critical:

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
- Distinguish current-year evidence from historical context.
- If current-year evidence is unavailable, say so explicitly.

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

A positive Market Research result should normally move directly into:

`Product Research`

when the market receives:

- GO
- TEST

and no confirmed CRITICAL blocker exists.

Do not require a content-performance pilot before Product Research.

Product Research must happen before product-level testing because it identifies:

- candidate products
- seller eligibility
- commissions
- compliance status
- product quality signals
- stock
- commercial viability

Performance testing should occur later.

Correct flow:

```text
Market Research
      ↓
Product Research
      ↓
Product Scoring
      ↓
Product Validation
      ↓
Content Pilot
      ↓
Performance Analysis
```

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
Recency Check
      ↓
Platform Role Assessment
      ↓
Risk Severity Classification
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
GO / TEST / WATCH / SKIP
      ↓
Progression Check
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
7. Evidence Recency
8. Risk Severity

Do not overreact to minor uncertainty.

MINOR issues should not block progression.

MODERATE issues should normally allow progression under `TEST`.

Only confirmed CRITICAL issues should prevent progression.

When multiple platforms are evaluated, always include `platform_scores`.

Use the field name `decision` consistently.

Do not generate unsupported numeric Execution Readiness scores.

Platform allocation percentages must be labeled as hypotheses unless supported by observed performance data.

Compliance issues and commercial execution gaps must remain clearly separated.

For current-market research, prefer current-year evidence whenever reliable evidence exists.

Do not recommend a category only because it is viral.

Do not force all platforms into the same commercial role.

Prefer sustainable affiliate opportunities over short-lived hype.
