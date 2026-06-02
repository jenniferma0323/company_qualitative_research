# Skill: What Matters – Root Driver Extractor

## Objective

Identify and rank the true root economic drivers of the company.

A driver is a force that will lead to future changes, the root cause of a better or worse future.

Do NOT stop at segment level KPIs, go deep into root causes.


Primary sources:
- Last 4 quarterly transcripts
- Q&A sections (highest signal)
- Earnings releases
- Broader industry context if discussed

---

## Analytical Framework

### Step 1: find dirvers

There are 2 types of drivers, **fundamental drivers** and **valuation drivers**:

**Fundamentals drivers** are the ones related to fundamental economic engines of how the company makes money, including:
- A new product
- A contract
- A customer
- A production ramp
- A secular force
- A competitive shift

**valuation driver** is linked to the market narrative, often times related to quality of business, it can overlap with fundamental, but sometimes is not related to fundamental changes, it can be a enthusiasm or fear from, which is the persistence of cash flow:
- A secular narrative change
- A macro narrative
- A market skepticism 

**segment level analysis** Go into each of the segments and find drivers, why is the segment revenue changing?
**macro level analysis** topics and theme that affect the company as a whole
examine the business environment and broader industry theme, especially things like:
- AI disruption risk
- Industry pricing compression
- Macro slowdown
- Commodity cycles
- Competitive entry
- Regulatory shift


Pay attent to **Q&A section in transctipts** cross 4 quarters, pay attention to:

- latest product/program references
- key debates
- the divergence of sentiment of management comments and the question
- structural concerns
- forward-looking statements
- new investments/capex deployment
- new breakdown of segments/product constribution


---

### Step 2: KPI link and exposure Mapping

- Driver must be quantified, is should impact a **specific KPI** in a segment.

example: one product in A segment is the driver, is should impact both the revenue and profit, the company may not disclose the impact but you should find the most relavent proxy, for example a segment that the company reports. 
- Try very hard to quantify it, usually analyst will try to ask exposure, if you find a data, you need to specify when is this data disclosed. 
- Data may change, find the **lastest data**

Extract:
- driver's revenue/profit contribution
- higher margin or lower margin


---

### Step 3: Root Cause deep dive

Think from a causal chain effect, find the root cause
For each candidate dirver, determine What drives this element to change, is there a **deeper driver** at company level?
DO NOT stay at the surface fo to the above level drivers in a causal chain:
- example: driver can be new product/platform, because: product ramps -> fulfull new demand -> more revenue 
- example: drivers can be a change of competition: competitiors closed capacity -> more order intake from competitiors -> more revenue 

Revenue impact > margin-only impact unless structurally material.

Largest revenue pool + fastest growth + structural force rank highest.


---

## Ranking Rules

Rank maximum 5 drivers based on level of importance:

1. Revenue/profit exposure
2. how long will this driver effective, the longer the better
3. when is this driver first mentioned? the lastest ones are important
4. repeated mentioned in Q&A = structural important
5. Concerns and skeptics impact on valuation narrative
6. how different is the market narrative and the management guidance? if the market is very concerned but the managment talks bullish, this is important

revenue drivers is usually more important
Structural/significant/hard to veritfy multi-year drivers outrank short-term.
Example: the narrative of software will be replaced by AI is more powerful than a new feature update, the regeme is more important.

---

## Output Format (Concise)

## What Matters for [Company]

---
Driver 1: [Root Driver Name]

Why it matters:  
Concise explanation of the underlying economic or narrative driver.

Revenue and profit exposure: [Segment + % or qualitative scale]

market narrative: [Investor framing, Recurring skepticism or None material]

Management guidance: [Forward framing, changes to before]

---
Driver 2: …

(Repeat structure)

---

## Root Driver Examples

Example 1

Incorrect:
Theme: Engine Products growth

Correct:
Theme: Airfoil demand driven by data center ramp


---

Example 2

Incorrect:
Theme: revenue growth

Correct:
Theme: LRAA program ramp

---

Example 3

Incorrect:
Theme: Software segment weakness

Correct:
Theme: AI disruption risk to core SaaS pricing power


## Output Constraints

- Very concise.
- No transcript summary.
- Identify root cause, not reporting structure.
- Institutional tone.
- Use bn / mn format.and currency like "$" before numbers
- Avoid em dashes.
- **citation to the time of the data** is very important, you link a data to its time frame: "in xx quarter, the company disclosed xx"

---

## Output Schema

```typescript
WhatMattersResult {
  // — Free-form reasoning (LLM scratchpad, context for downstream EDD) —
  thinking: string  // full markdown reasoning trace

  // — Structured drivers (max 5, ranked) —
  drivers: Array<{
    rank: number                          // 1–5
    name: string                          // "Airfoil demand driven by data center ramp"
    type: 'fundamental' | 'valuation'     // two top-level driver categories from Step 1

    category: 'product' | 'contract' | 'customer' | 'production_ramp'
            | 'secular' | 'competitive' | 'narrative' | 'macro' | 'regulatory'
            | 'other'

    // Causal chain
    root_cause: string                    // one sentence — the true root, not surface symptom
    causal_chain: string[]               // ["competitor closed capacity", "orders shifted over", "revenue +X%"]

    // KPI / exposure mapping (Step 2)
    kpi_link: {
      segment: string | null             // "Data Center" / null if cross-segment
      revenue_exposure: string | null    // "$1.2bn" or "~15% of total" or null if undisclosed
      margin_direction: 'higher' | 'lower' | 'neutral' | 'unknown'
      data_period: string | null         // "Q1-2026 earnings call" — when was this data disclosed
    }

    // Market narrative vs. management (Ranking Rule 6)
    market_narrative: string | null      // what the market is worried about
    management_stance: string | null     // what management is saying
    divergence: 'high' | 'medium' | 'low' | 'none'   // gap between the two

    // Importance signals (Ranking Rules 3 & 4)
    first_mentioned: string | null       // "Q3-2025" — earliest appearance across 4 quarters
    qa_frequency: 'recurring' | 'occasional' | 'one-off'
    duration: 'multi_year' | 'multi_quarter' | 'near_term'

    // Evidence grounding
    evidence_quotes: Array<{
      quote: string                      // verbatim excerpt
      source: string                     // "Q1-2026 transcript, Q&A section"
    }>

    confidence: 'high' | 'medium' | 'low'
  }>

  // — Cross-driver metadata —
  cross_driver_themes: string[]          // macro / industry themes affecting multiple drivers
  top_market_concern: string | null      // single biggest investor skepticism across all drivers
  analysis_period: string               // "Q2-2025 through Q1-2026"
}
```

---

## End of Skill
