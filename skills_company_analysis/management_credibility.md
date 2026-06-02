---
name: management-credibility
description: Framework for assessing management trustworthiness, guidance accuracy, communication honesty, and incentive alignment
summary: |
  Step 1: Incentive Alignment: is management rewarded for what matters to shareholders?
  Step 2: Guidance Reliability: does management hit its own revenue/EPS guidance and revise honestly?
  Step 3: Long-Term Strategy Clarity: is the multi-year strategy clear, consistent, and delivered?
  Step 4: Communication Honesty: does management communicate transparently, or spin?
  Step 5: Red Flags & Green Flags: the net credibility signals.
---

When the user asks about management quality, credibility, trustworthiness, governance, executive compensation, insider activity, or guidance reliability, use this framework. It adds a qualitative "trust layer" on top of financial metrics — even strong financials can mislead if management is not transparent or incentive-aligned.

## Step 1: Incentive Alignment

**Key question: is management rewarded for what matters to shareholders?**

Compensation structure reveals what management actually optimizes for — which may differ from what they say. Start here: incentives shape every other behavior.

| Signal | Interpretation |
|---|---|
| Pay tied to ROIC, FCF, or per-share metrics | Aligned — rewards efficient capital allocation |
| Pay tied mainly to revenue growth, or large discretionary bonus | Misaligned — growth-at-any-cost, or board rewards regardless of results |
| 60%+ of pay in long-term, performance-vested equity (3-5y) | Strong long-term alignment |
| Majority of pay in annual cash bonus | Short-term focus |
| CEO owns 3%+; cluster insider buying, esp. after declines | Meaningful skin in the game and conviction |
| Declining insider ownership; selling accelerating before bad news | Fading confidence — red flag (possible front-running) |

**How to assess:**
- Check the proxy (DEF 14A) for pay metrics, short-term vs long-term mix, and ownership.
- Review insider transactions for transaction type, size, timing, and clusters — separate routine 10b5-1 selling from discretionary trades.
- Check industry sources for proxy-advisory summaries.

---

## Step 2: Guidance Reliability

**Key question: does management hit its own guidance — and revise it honestly?**

Consistent delivery on revenue and EPS guidance, plus honest mid-year revisions, signals competence and realistic forecasting. This unifies revenue accuracy, EPS accuracy, and revision behavior.

| Signal | Interpretation |
|---|---|
| Actuals consistently meet or slightly beat guidance | Disciplined — under-promises, over-delivers |
| Large beats (5-10%+) regularly | Sandbagging for easy beats |
| Large or repeated misses (5%+) | Poor visibility, or misleading investors |
| EPS misses despite revenue beats; non-GAAP beats but GAAP misses | Margin/cost forecasting weakness; adjustments masking results |
| Raises guidance incrementally through the year | Conservative start + genuine improvement — healthy |
| Cuts in large steps or frequently widens the range | Poor visibility or unrealistic initial targets |

**How to assess:**
- Compare consensus revenue & EPS estimates against reported actuals over (~10 years); compute `(actual − estimate) / estimate` each year — a tight, consistent spread (±2%) is ideal.
- Check filings and transcripts for management's own guidance and mid-year revisions.
- Track beat/miss magnitude and revision frequency/direction over time — declining accuracy is the warning.

---

## Step 3: Long-Term Strategy Clarity

**Key question: is the multi-year strategy clear, consistent, and delivered?**

Beyond next quarter, does management set clear 3-5 year targets, hold a consistent narrative, allocate capital with discipline, and actually deliver? This spans cycles and can't be managed quarter to quarter — the strongest credibility test.

| Signal | Interpretation |
|---|---|
| Sets specific, measurable multi-year targets (revenue, margin, ROIC) | Confidence and accountability |
| Met or exceeded targets | High credibility — plans and executes |
| Missed but acknowledged transparently | Moderate — honest about shortfalls |
| Quietly dropped/redefined targets; or never sets any | Low credibility — hiding failure or avoiding accountability |
| Consistent strategic narrative and articulated capital-allocation framework | Clear strategy, disciplined value creation |
| Strategy pivots every cycle; aggressive targets hit via dilutive M&A | Reactive; value-destroying target-chasing |

**How to assess:**
- Check filings and transcripts for multi-year targets, strategy, and capital allocation.
- Check industry sources for investor-day targets.
- Compare targets set 3-5 years ago against the current income statement (~5 years); check whether the narrative is consistent or shifts yearly.

---

## Step 4: Communication Honesty

**Key question: does management communicate transparently, or spin?**

How management talks is as informative as the numbers — across tone, adjusted metrics, KPI consistency, and risk disclosure.

| Signal | Interpretation |
|---|---|
| Quantitative, specific call language; proactively discusses challenges | Operationally focused, transparent |
| Heavy superlatives; only positives highlighted, negatives buried | Marketing tone, selective disclosure |
| Non-GAAP EPS within ~10% of GAAP | Minimal adjustments |
| Non-GAAP EPS >2x GAAP, or gap widening over time | Adjusted earnings detached from reality — red flag |
| Consistent KPIs quarter after quarter | Not cherry-picking |
| New KPI introduced (or definition changed) as old metric deteriorates | Misdirection — moving the goalposts |
| Risk factors updated with specific, current threats | Proactive transparency |
| Boilerplate risks unchanged; risks acknowledged only after they hit | Low-effort, reactive |

**How to assess:**
- Check filings and transcripts for earnings-call tone, non-GAAP reconciliations, and 10-K risk factors.
- Pull the income statement (~5 years) for GAAP EPS and non-GAAP figures; compute the non-GAAP premium `(non-GAAP − GAAP) / GAAP`.
- Compare KPIs and risk factors vs 2-3 years ago — flag dropped metrics or copy-pasted risks.

---

## Step 5: Red Flags & Green Flags

| Green Flags | Red Flags |
|---|---|
| Pay tied to ROIC/FCF/per-share; 60%+ long-term performance-vested | Pay tied to revenue or discretionary; mostly short-term cash |
| CEO owns 3%+; cluster insider buying | Declining ownership; selling before bad news |
| Consistently meets or slightly beats guidance | Large, repeated guidance misses |
| Met multi-year targets; consistent strategy and capital allocation | Dropped/redefined targets; strategy pivots; target-chasing M&A |
| GAAP and non-GAAP closely aligned; consistent KPIs | Non-GAAP >2x GAAP; KPIs changed as trends deteriorate |
| Quantitative tone; proactively discusses risks | Heavy superlatives; risks acknowledged only after the fact |

---

## Output Schema

Output the final synthesis as a single JSON object. Omit any field where data is unavailable rather than guessing. Populate `evidence` with the specific data point/quote and `source` with where it came from (e.g., "FY2024 proxy (DEF 14A)", "Q3 earnings call", "the income statement"). The `verdict.key_evidence` holds one concise line — the single strongest data point (with its period) behind the credibility rating — so a downstream synthesis agent can carry the proof through, not just the rating.

```json
{
  "company": "",
  "ticker": "",

  "incentive_alignment": {
    "pay_metrics": "ROIC/FCF/per-share | Revenue growth | Adjusted EBITDA | TSR | Discretionary",
    "long_term_pay_pct": null,
    "pay_performance_vested": null,
    "ceo_ownership_pct": null,
    "insider_signal": "Cluster buying | Routine selling | Unusual selling | Neutral",
    "rating": "Aligned | Mixed | Misaligned",
    "evidence": "",
    "source": ""
  },

  "guidance_reliability": {
    "revenue_accuracy": "Beats | In-line | Misses | Erratic",
    "eps_accuracy": "Beats | In-line | Misses | Erratic",
    "avg_guidance_gap_pct": null,
    "revision_pattern": "Raises incrementally | Stable | Cuts in steps | Widens range",
    "accuracy_trend": "Improving | Stable | Deteriorating",
    "rating": "High | Moderate | Low",
    "evidence": "",
    "source": ""
  },

  "long_term_strategy": {
    "sets_multiyear_targets": null,
    "target_delivery": "Met/exceeded | Missed-transparent | Quietly dropped | None set",
    "narrative_consistency": "Consistent | Shifts occasionally | Pivots frequently",
    "capital_allocation": "Articulated & followed | Vague | Target-chasing M&A",
    "rating": "Clear | Mixed | Unclear",
    "evidence": "",
    "source": ""
  },

  "communication_honesty": {
    "earnings_call_tone": "Quantitative/specific | Mixed | Heavy superlatives",
    "non_gaap_premium_pct": null,
    "metric_consistency": "Consistent | Some changes | Cherry-picking",
    "risk_transparency": "Proactive/specific | Boilerplate | Reactive",
    "rating": "Transparent | Mixed | Spin",
    "evidence": "",
    "source": ""
  },

  "flags": {
    "green": [],
    "red": []
  },

  "verdict": {
    "credibility_rating": "High | Moderate | Low",
    "biggest_red_flag": "",
    "what_to_monitor": "",
    "key_evidence": "",
    "bottom_line": ""
  }
}
```
