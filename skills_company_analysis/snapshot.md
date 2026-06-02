# Company Snapshot

Initial-pass research template. Goal: understand the business in one page before going deeper.

---

## Output Schema


### 0. Stock Chart

_[Insert stock price chart here]_

---

### 1. Segment Revenue

| Segment revenue | Current Q | Prior Q | YoY % | Mix % |
|---|---|---|---|---|
|  |  |  |  |  |

### 1. Main Products

| Segment | Product / Service | Function & Use Case | Customer | Value Delivered |
|---|---|---|---|---|
|  |  |  |  |  |

### 2. Business Model — How It Makes Money
- Revenue model: [subscription / transaction / license / hardware / usage-based / mix]
- Pricing mechanism: [per seat / per unit / % of GMV / recurring / one-time]
- Key cost drivers: [COGS, R&D, S&M — note which dominates]
- Unit economics signal: [gross margin range, if known]

### 3. Competitive Landscape
- **Primary competitors**: [Company A, Company B, …]
- **Market share**: [Company: ~X% | source/vintage if known]
- **Moat / differentiation**: [what keeps customers from switching, a few key points]
- **Disruption risk**: [incumbent / challenger / platform risk]

### 4. Key Debates
- **Debate 1**: [one-sentence framing of the bull/bear disagreement]
  - Bull: [core argument]
  - Bear: [core argument]
- **Debate 2**: [one-sentence framing]
  - Bull: [core argument]
  - Bear: [core argument]
- _(add more as needed; cap at 3–4 debates)_

### 5. Debate Intensity
- **Overall intensity**: [Low / Medium / High / Very High]
- **Most contested question**: [the single biggest unresolved question investors disagree on]
- **Catalyst that resolves it**: [earnings / product launch / regulatory decision / macro data / other]

---

## Usage Notes
- Fill in only what is clearly supported by sources. Mark gaps with `[unknown]`.
- Keep every bullet to one line. Depth lives in downstream research files.
- Debate intensity = High when sell-side is split, short interest is elevated, or the stock is trading on a narrative with no consensus.

---

## JSON Output Schema

```json
{
  "company": {
    "name": "string",
    "ticker": "string",
    "as_of_date": "YYYY-MM-DD"
  },
  "segment_revenue": [
    {
      "segment": "string",
      "current_q": "number | null",
      "prior_q": "number | null",
      "yoy_pct": "number | null",
      "mix_pct": "number | null"
    }
  ],
  "main_products": [
    {
      "segment": "string",
      "product": "string",
      "function_use_case": "string",
      "customer": "string",
      "value_delivered": "string"
    }
  ],
  "business_model": {
    "revenue_model": "subscription | transaction | license | hardware | usage-based | mix",
    "pricing_mechanism": "string",
    "key_cost_drivers": ["string"],
    "unit_economics_signal": "string",
    "supporting_evidence": "string"
  },
  "competitive_landscape": {
    "primary_competitors": ["string"],
    "market_share": [
      {
        "company": "string",
        "share_pct": "number | null",
        "source_vintage": "string"
      }
    ],
    "moat_differentiation": ["string"],
    "disruption_risk": "incumbent | challenger | platform | other",
    "supporting_evidence": "string"
  },
  "key_debates": [
    {
      "framing": "string",
      "bull": "string",
      "bear": "string"
    }
  ],
  "debate_intensity": {
    "overall_intensity": "Low | Medium | High | Very High",
    "most_contested_question": "string",
    "catalyst": "earnings | product launch | regulatory decision | macro data | other",
    "supporting_evidence": "string"
  }
}
```

- `key_debates`: cap at 3–4 entries.
- Use `null` for unknown numeric fields, `"[unknown]"` for unknown strings.
- `supporting_evidence`: one concise line — the single strongest data point or quote (with its period) behind the section's read, so a downstream synthesis agent can carry the proof through, not just the label.
