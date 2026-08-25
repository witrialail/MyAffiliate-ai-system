---
name: firecrawl-market-research
description: Research and evaluate affiliate markets, categories, and sub-niches using Firecrawl, market evidence, trends, competition, audience signals, content potential, and affiliate commercial potential.
license: ISC

metadata:
  author: firecrawl
  version: "0.1.0-affiliate"
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

The goal is to identify opportunities with strong demand, commercial potential, content potential, and suitable competition.

## Onboarding

Infer from context whenever possible:

- target market or category
- country or geography
- target platform
- audience
- timeframe
- price range

Ask questions only when essential information is missing.

## Research Collection

Use Firecrawl search and scrape to collect relevant evidence from:

- industry reports
- official company or brand pages
- ecommerce platforms
- market reports
- credible news
- trend reports
- financial or industry portals

Prefer recent data when evaluating current market conditions.

## Research Areas

Evaluate:

1. Market demand
2. Market growth and trends
3. Affiliate commercial potential
4. Content potential
5. Competition
6. Audience fit
7. Market risks

## Affiliate Evaluation

After collecting evidence, evaluate the opportunity using:

`references/scoring-framework.md`

Score every factor from 0–10 and calculate the final Opportunity Score.

Do not assign a score without supporting evidence.

## Decision

Classify the market as:

- GO
- TEST
- WATCH
- SKIP

## Output

Return:

- market/category
- target audience
- price range
- major market signals
- competition
- trends
- affiliate potential
- content potential
- risks
- individual scores
- Opportunity Score
- final decision
- recommended next action

## Evidence Rules

- Never fabricate data.
- Separate facts, estimates, and assumptions.
- Cross-reference important numbers whenever possible.
- Note conflicting information between sources.
- Include period and unit for important metrics.
- Identify important data gaps.
- Prefer evidence over assumptions.

## Workflow

Market Research  
→ Evidence Collection  
→ Source Validation  
→ Opportunity Scoring  
→ GO / TEST / WATCH / SKIP  
→ Product Research

## Quality Bar

The final recommendation must be actionable for affiliate decision-making.

A high Opportunity Score means the market may proceed to Product Research.

Do not recommend a category only because it is viral.
