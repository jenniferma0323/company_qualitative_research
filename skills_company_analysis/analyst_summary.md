---
name: analyst_summary
description: Critical synthesis layer that fuses the six qualitative research skills (snapshot, demand, supply, moat, management, what_matters) into one coherent investment narrative AND a research agenda — it reconciles quality of business and competitive advantage into a single verdict, hunts internal contradictions, stress-tests the drivers against that verdict, and outputs the key questions and evidence still needed.
summary: |
  Section 1: Key Product / Segment — what the company actually is and where the money concentrates.
  Section 2: Drivers — the ranked root forces that move the future.
  Section 3: Quality of Business & Competitive Advantage — moat, lock-in, margins, competition, and management fused into ONE verdict, with internal-consistency checks.
  Section 4: Drivers vs Quality — which drivers reinforce the competitive advantage and which challenge it.
  Section 5: How It Will Evolve — where demand, supply, and moat trajectories point, and what resolves the debate.
  Section 6: Key Questions & Evidence Needed — the research agenda: open questions, contradictions to resolve, and the specific evidence to verify.
---

This skill does **not** fetch data. It is a **processing and critique agent**: it consumes the JSON outputs of the five upstream framework skills plus the snapshot, reconciles them into one analyst-grade narrative, and then does the work the upstream skills cannot — it checks whether the conclusions are **internally consistent**, where they **contradict**, and **what still needs to be researched**. The upstream skills answer narrow questions in isolation; this skill's job is to connect them, pressure-test them, and hand back a verified story plus a list of what to verify next.

Two deliverables, equally important:
1. **A coherent narrative** an investor can act on.
2. **A research agenda** — the contradictions, unverified claims, and open questions that must be resolved before trusting the thesis.

## Inputs

Provide as many of the six upstream JSON artifacts as exist. Each maps to a [skill file](.) in this directory:

| Input | Source skill | Carries |
|---|---|---|
| `snapshot` | [snapshot.md](snapshot.md) | segments, products, business model, competitors, key debates, debate intensity |
| `demand` | [demand_analysis.md](demand_analysis.md) | customer type, demand durability, growth sources, lock-in, willingness to pay |
| `supply` | [Supply_analysis](Supply_analysis) | competitive set, margins, market structure, differentiation, capex/capacity, disruption |
| `moat` | [Moat_analysis.md](Moat_analysis.md) | ROIC/margin/pricing indicators, moat sources, moat risks, durability |
| `management` | [management_credibility.md](management_credibility.md) | incentive alignment, guidance reliability, strategy, communication honesty |
| `what_matters` | [What_matters.md](What_matters.md) | ranked root drivers, causal chains, market-vs-management divergence |

**Missing inputs:** if an artifact is absent, write the dependent section from what remains and flag the gap in `coverage.missing_inputs`. Never invent a field that no upstream skill produced.

---

## Section 1: Key Product / Segment

**Question: what is this company, really, and where does the money concentrate?**

Strip the company to its economic core. One or two segments/products usually drive the thesis; name them and say why they dominate.

Pull from:
- `snapshot.segment_revenue` + `snapshot.main_products` → the revenue concentration and what each product does.
- `demand.customers` → who actually pays (B2C / B2B / B2B2C) and the end-demand driver.
- `supply.competitor_comparison.subject_company_rank` → where this company sits in its set.

Write: the dominant segment(s) by revenue mix, the core product and the job it does for the customer, the customer type, and the single segment the investment case actually rides on. If revenue is concentrated (one segment >50%), say so plainly — the thesis lives or dies there.

---

## Section 2: Drivers

**Question: what root forces will move the future, and how exposed is the company?**

Lead with `what_matters.drivers` (already ranked, with causal chains and KPI exposure). State each cleanly here; the critical stress-test against quality happens in Section 4.

For each top driver (cap at the top 3–4):
- State the **root cause and causal chain** (`.root_cause`, `.causal_chain`) — not the surface symptom.
- Attach **exposure** (`.kpi_link.revenue_exposure`, `.margin_direction`).
- Tag **fundamental vs valuation** (`.type`) and **duration** (`.duration`) — multi-year structural drivers outrank near-term ones.
- Carry the **market-vs-management divergence** (`.divergence`, `.market_narrative`, `.management_stance`).
- Note whether the exposure figure is **disclosed and dated** or an estimate — undated/undisclosed exposure becomes a Section 6 evidence item.

---

## Section 3: Quality of Business & Competitive Advantage

**Question: is this a good, defensible business — and do the pieces actually agree?**

This is the consolidated quality section. Moat, customer captivity, margin structure, competitive position, and management are all measuring the **same thing from different angles**: how durable the economics are. Fuse them into one verdict — then check that the verdict is internally coherent.

### 3a. The quality picture

| Quality dimension | Primary evidence | Corroborating evidence |
|---|---|---|
| **Returns & pricing power** | `moat.moat_indicators.roic`, `.pricing_power` | `supply.competitor_comparison` margin spread |
| **Moat (why returns persist)** | `moat.verdict`, `moat.moat_sources` (active ones) | `demand.lock_in.synthesis.lock_in_verdict` |
| **Customer captivity / stickiness** | `demand.lock_in` mechanisms, `willingness_to_pay` | `moat` switching-cost source |
| **Competitive position & structure** | `supply.market_share_and_structure`, `competitor_comparison` rank | `supply.product_differentiation` |
| **Share trajectory** | `supply.historical_change.structure_trajectory` | `moat.moat_indicators.market_share` |
| **Stewardship** | `management.verdict`, `incentive_alignment` | `management.guidance_reliability`, `long_term_strategy` |

Reconcile the deliberate overlaps (switching costs, network effects, contracts appear in both moat and demand): report the **strongest converging mechanism once**, not twice. State the verdict as: returns level → what protects them → market structure that allows it → how durable → whether management is a trustworthy steward.

### 3b. Internal-consistency checks (the core of this skill)

A quality conclusion is only trustworthy if its parts corroborate each other. A **high moat must be visibly anchored** in customer captivity, supply-side advantage, or a structural barrier — a rating with no underlying source is a red flag, not a moat. Run each check; every failed check becomes a Section 6 research item.

| If the conclusion is… | It MUST be backed by… | If not → flag |
|---|---|---|
| **Moat = Strong / Widening** | ≥1 strong source: customer captivity/lock-in, OR supply advantage (scale/cost/MES), OR network effects/data flywheel, OR license/resource control | `Unsupported moat rating` — high moat with no identifiable source |
| **ROIC well above WACC, durable** | Gross-margin spread above peer median (`supply.competitor_comparison`) | `Returns without margin evidence` — excess returns no peer comparison confirms |
| **Pricing power = Strong** | Product differentiation = Differentiated (`supply.product_differentiation`) | `Pricing power without differentiation` |
| **Lock-in / captivity = Strong** | Retention proof: NRR/GRR, low churn, or contract coverage (`demand.lock_in.retention_metrics`) | `Claimed stickiness without retention proof` |
| **Moat durability = Widening** | Share trajectory = Gaining AND margin spread widening | `Widening moat but flat/losing share` |
| **Management = High credibility** | Guidance reliability + incentive alignment both supportive | `Credibility rating exceeds its evidence` |
| **Strong moat + strong returns** | Should also show high barriers to entry / low disruption risk (`supply.disruption.verdict`) | `Defensible economics but open to disruption` |

Conversely, look for **hidden strength**: a strong supply advantage or deep captivity that the moat rating *understates*. Inconsistency cuts both ways.

Surface `moat.moat_risks`, `demand.synthesis.key_vulnerability`, and `supply.overall_verdict.biggest_supply_risk` as the standing threats to quality.

---

## Section 4: Drivers vs Quality

**Question: do the drivers strengthen the competitive advantage, or threaten it — and which conclusions does that put in doubt?**

Now re-examine the Section 2 drivers **through the lens of the Section 3 quality verdict**. Every driver has a relationship to the moat; classify it.

For each driver:
- **Relationship to competitive advantage:**
  - `reinforces` — deepens the moat (scale ramp lowering unit cost, network growing, switching cost rising, share gain widening the spread).
  - `neutral` — moves revenue but does not change defensibility.
  - `challenges` — erodes the advantage if it plays out (AI disruption to pricing power, capacity glut compressing margins, new entrant, demand commoditizing, customer concentration rising). **These are the highest-priority research items.**
- **Consistency with the quality verdict:** does the driver fit the conclusion (e.g. a captivity-deepening driver under a "Strong moat" verdict — consistent), or contradict it (e.g. a "Widening moat" verdict but the #1 driver is a pricing-power threat — contradiction)?
- **What would have to be true** for the driver to break the quality thesis, and **what evidence would confirm or kill it** — this feeds Section 6.

A `challenges` driver sitting on top of a high-quality verdict is the single most important thing this agent surfaces: the market may be paying for durability that a live driver is actively eroding.

---

## Section 5: How It Will Evolve (the core of this skill)

**Question: where do the trajectories point over the next 1–3 years, and what resolves the open debate?**

This is the forward synthesis. Each upstream skill emits a *directional* read; the job here is to (a) stack them into one base path, (b) reconcile where they point in opposite directions, and (c) frame the range as explicit scenarios tied to catalysts — not a single point forecast.

### 5a. Reconcile the trajectory vectors

Pull the directional field from every skill and lay them side by side:

| Vector | Field | Reads |
|---|---|---|
| **Demand** | `demand.demand_growth.trajectory`, `secular_vs_cyclical`, `durability` | accelerating + secular = durable tailwind; cyclical = mean-reverting |
| **TAM headroom** | `demand.demand_growth.market_tam.penetration_stage` | early = long runway; saturating = growth decelerating ahead |
| **Supply / pricing** | `supply.capex_and_capacity.cycle_position`, `supply_pricing_implication_2_3y` | late-cycle build = pricing pressure in 2–3y; trough = pricing firms for survivors |
| **Disruption** | `supply.disruption.verdict`, `.new_technology.timeline` | the tail risk to the whole structure; weight by timeline |
| **Moat** | `moat.verdict.durability` | widening / stable / eroding |
| **Drivers** | top `what_matters.drivers[].duration` | multi-year legs vs near-term pops |

**Reconcile conflicts — the tension IS the forecast.** The vectors often point opposite ways, and naming the dominant one is the analytical work. Demand accelerating while a capex glut builds = volume growth *into* pricing pressure (revenue-up, margin-down). A widening moat while demand decelerates = pricing power over a shrinking pie. State which vector dominates and why it wins.

### 5b. Scenarios

Frame the range as three paths, each anchored to which vectors break which way and tied to the resolving catalyst — not to sentiment.

- **Bull** — the vectors that break favorably (driver duration extends, moat widens, disruption stays distant, capex stays disciplined).
- **Base** — the most likely stack of the reconciled vectors.
- **Bear** — the vectors that break against (the `challenges` driver from Section 4 plays out, supply glut lands, moat erodes, disruption pulls forward).

For each path give: the one-line trajectory, the **key assumption** it rests on, and the **confirming signpost** — the observable that would tell you this path is the one playing out. Each signpost feeds Section 6 as a `monitor` item.

### 5c. The debate, its catalyst, and the swing factor

State the single most contested question (`snapshot.debate_intensity.most_contested_question` + `what_matters.top_market_concern`), the bull and bear framing of it, the **catalyst that resolves it** (`snapshot.debate_intensity.catalyst`) and its expected timing (earnings, product launch, regulatory decision, capacity coming online). Close with the **key swing factor** — the single variable that most determines which scenario plays out — and the short watchlist of signposts to monitor.

---

## Section 6: Key Questions & Evidence Needed  (the core of this skill)

**Question: what must be researched before trusting this thesis, and what evidence settles each?**

The agent's defining deliverable. Convert every gap, contradiction, and unverified claim into a concrete research item an analyst could actually go answer. This is the output a downstream deep-research step consumes.

### 6a. Sources of questions

The first six origins are *derived* from the inputs — sweep them all; do not skip any the inputs contain. The seventh, `out_of_box`, is the agent's own contribution and is mandatory: the six upstream skills share a fixed lens, so their collective blind spots are systematic, not random. Generating questions they *structurally could not* is the highest-value thing this agent does.

| Origin | Where it comes from |
|---|---|
| `consistency_check` | each failed internal check in Section 3b |
| `driver_vs_quality` | every `challenges` driver and verdict contradiction in Section 4 |
| `unverified_exposure` | any `what_matters` driver whose `revenue_exposure` is null, undated, or low-confidence |
| `cross_skill_contradiction` | two skills disagreeing on the same fact |
| `upstream_unknown` | `key_vulnerability`, `key_uncertainty`, `what_to_monitor`, `top_market_concern`, `key_risk_to_moat` |
| `scenario_signpost` | the confirm/deny signposts from the Section 5b scenarios |
| `out_of_box` | **the agent's own reasoning — factors NONE of the six skills measured** (see 6b) |

### 6b. Think beyond the sources (`out_of_box`)

After exhausting the derived questions, step back from the inputs entirely and ask: **what could move this company that no upstream skill was built to see?** The frameworks cover demand, supply, moat, management, and drivers — anything outside those lanes is invisible to them. Reason from first principles about the blind spots, for example:

- **Exogenous shocks** — regulation/antitrust, tax, tariffs/trade, geopolitics, litigation, sanctions, FX, rates, commodity inputs.
- **Balance-sheet / financial structure** — debt maturities and refinancing, covenant or liquidity risk, pension/lease obligations, dilution, FX translation — items a *qualitative* lens skips.
- **Stakeholders outside the customer/competitor frame** — employees (unionization, key-talent flight, founder/key-person risk), regulators, activists, large shareholders, partners.
- **Accounting and disclosure quality** — aggressive revenue recognition, capitalized costs, related-party deals, a metric that flatters the story (often only visible by what the company does *not* disclose).
- **Demand-shape risks the Maslow/problem lens misses** — substitution from an adjacent category, a behavioral or fashion shift, a single point of failure in the supply chain, ESG/reputational exposure.
- **The unknown unknowns** — name at least one plausible left-field scenario and the early signal that would reveal it. The goal is not completeness but to surface the risk that is obvious in hindsight and absent from every framework.

**Second-order and reflexive effects.** The single richest source of out-of-box questions, and the one the upstream skills are structurally blind to: they read each force in isolation and in a single step, so they miss the *consequences of the consequences* and the feedback loops. Trace each major conclusion one move further out and ask "and then what?". Work through:

- **Value-chain reflexivity** — a customer who is also (or could become) a competitor by building in-house; a key supplier integrating forward into the company's market; a partner whose incentives flip once the company succeeds. The relationship that is a tailwind today becomes the threat tomorrow.
- **Cross-segment cannibalization** — a driver that grows one segment while quietly eating another (a new product displacing the legacy cash cow, a cheaper tier deflating ASP, a platform shift stranding an installed base). Net effect, not gross.
- **Competitive response** — the upstream supply skill scores today's structure; it does not model how rivals *react*. If this company's driver works, who is forced to respond, and does that response (price war, capacity add, M&A, a copied feature) erode the very advantage the thesis rests on?
- **Customer-economics feedback** — the company's success changes its customers' economics, which changes their demand: pricing power that pushes customers to seek alternatives or vertically integrate; a tool so effective it shrinks its own TAM; a take-rate that invites disintermediation.
- **Reflexivity between narrative and fundamentals** — a rich valuation that is itself a competitive weapon (cheap equity funds land-grab, attracts talent) or a vulnerability (a high multiple that, if it breaks, triggers down-rounds, debt covenants, or employee attrition). Per Soros, perception and fundamentals feed back on each other.
- **Supply-chain and concentration ripples** — a single customer/supplier/geography whose stumble cascades; an input the company depends on that a *competitor* controls; a shared dependency (one foundry, one cloud, one chokepoint) that correlates risks the skills treat as independent.
- **Policy and incentive reflexivity** — a subsidy, regulation, or standard that helped the company being withdrawn *because* the company won; success inviting the antitrust, tax, or political attention that constrains the next leg.

For each, state the first-order move the sources already see, then the second-order consequence they do not, and the early signal that the loop is starting to turn.

**Next opportunity — where the trend pays out elsewhere.** A driver or second-order loop rarely moves only this company. Extend each major trend outward and ask who *else* it re-rates: suppliers and customers up and down this company's value chain, direct competitors, adjacent players, substitutes, and the "picks-and-shovels" enablers that sell into the trend. Output the specific companies and sub-industries likely to benefit or suffer as the trend plays out, the nature of the linkage, and the direction of impact. This is idea-generation that spins *out* of the subject thesis, not part of it — mark each as the analyst's inference and treat it as a lead to research, never a conclusion.

Hold these to the same 6c bar (specific, falsifiable, sourced); tag each `out_of_box` and, where it is pure hypothesis rather than evidence-backed, mark it as the analyst's inference.

### 6c. What makes a usable item

Every question must be:
- **Specific and falsifiable** — name the exact metric or disclosure, not a topic. Good: *"Net revenue retention by cohort for the last 8 quarters."* Bad: *"investigate the moat."*
- **Decision-relevant** — state which conclusion it would change, and whether answering it could *flip* the thesis (overturn the quality verdict or kill a top driver) versus merely refine it. If answering it moves nothing, drop it.
- **verifiable** — point to where the answer lives (a specific filing/transcript line, a KPI, a peer-financials comparison, an industry dataset, a channel check). Reuse the upstream skills' data vocabulary where it applies.
- **Classified by knowability** — `knowable_now` (the data exists; go find it) vs `monitor` (resolves only at a future print or catalyst). The two route to different workflows: research now vs track over time.

### 6d. Prioritize and lead

Rank each item by decision impact:
- **High** — could overturn the quality verdict or a top-3 driver (an unsupported moat rating, a live `challenges` driver, a null exposure on the #1 driver).
- **Medium** — would materially refine a conclusion.
- **Low** — completeness / nice-to-have.

Lead the section with the **single biggest open question** (carried in `investment_summary.biggest_open_question`) — the one whose answer most changes the thesis. Write each as the question an experienced analyst would put to management: e.g. *"What is net revenue retention by cohort? The Strong-moat verdict rests on captivity the lock-in skill never proved with retention data — if NRR is below 100%, the moat rating is unsupported."*

### 6e. Research plan — brainstorm the channels

A question is only useful if there is a route to its answer. For each High- and Medium-priority question, turn the abstract `where_to_look` into a concrete sourcing plan: who to talk to, what to read, where the signal actually lives. Brainstorm widely across channel types — do not stop at filings:

- **Experts** — the specific *roles* whose firsthand knowledge settles the question: former employees (ex-procurement, ex-sales, ex-product), current and churned customers, suppliers, distributors and channel partners, industry consultants, ex-regulators. Name the role and *why they would know*, not just "an expert." Expert networks (Tegus, GLG, AlphaSights) are the access path.
- **Internet / data sources** — filings and transcripts, trade publications, specialist data vendors, government and regulatory databases, patent filings, job postings, app-store and review data, web-traffic and pricing-page trackers.
- **Reddit** — subreddits for end-user sentiment, product complaints, and employee leaks (`r/[industry]`, `r/[product]`, `r/[company]`, and talent boards like r/cscareerquestions for hiring/attrition signal).
- **Industry forums & communities** — trade-association sites, professional forums, Discord/Slack communities, conference proceedings, Glassdoor/Blind for employee signal, niche enthusiast boards.
- **Primary / alternative data** — channel checks, store visits, supply-chain and shipping trackers, satellite data where the question warrants it.

Tie each research point to the question it answers, state the **exact data to extract**, and order the plan so the channels most likely to settle a thesis-flipping question come first.

---

## Writing Guidelines

Inherit the [What_matters.md](What_matters.md) house conventions:
- Institutional tone. Concise. No transcript or skill-output summary — synthesize, don't restate.
- Use bn / mn format with `$` before numbers (e.g. `$1.2bn`).
- Avoid em dashes in prose where the house style avoids them.
- **Preserve citations**: keep the `source`/`data_period` an upstream number carries ("in Q1-2026 the company disclosed…"). A synthesis that drops provenance is unverifiable.
- Every claim must trace to an upstream field. If you assert something no skill supports, mark it as the analyst's inference or push it into Section 6 as a question.

---

## Output Schema

Output the narrative first (Sections 1–6 as prose), then **three JSON objects** in order: **Output 1 — Full Report** (everything), **Output 2 — Research Plan** (the concise action list), and **Output 3 — One-Pager** (the tightest possible read). Outputs 2 and 3 are distilled *from* Output 1 — they restate, they do not add new analysis. Omit any field whose upstream inputs are missing rather than guessing.

**Carry vs. process.** Sections 1–3's pass-through fields are free-text: **copy the upstream verdict verbatim — do not re-derive or re-classify it.** If `moat.verdict.moat_rating` says `"Strong"`, write `"Strong"`; if it carries a nuance ("Strong but narrowing"), keep the nuance. The enumerated, structured blocks are where this agent does its *own* work — `consistency_checks`, `drivers_vs_quality`, `how_it_evolves`, and `key_questions` (Sections 5 and 6 plus the two cross-checks). Reserve the multiple-choice fields for those.

**`supporting_evidence` fields** carry the *concise* proof behind each verdict — one line: the single strongest data point or quote with its period, lifted from the matching upstream skill's `key_evidence` (e.g. `"NRR 118%, churn <2%, Q1-2026 10-K"`). This grounds the pass-through ratings so the `consistency_checks` have something to test against; do not write a paragraph. For `second_order_effects` and `out_of_box_factors`, set `is_inference: true` when the item is the analyst's reasoning rather than an upstream-backed fact.

### Output 1 — Full Report

```json
{
  "company": "",
  "ticker": "",
  "analysis_date": "",

  "key_product_segment": {
    "dominant_segments": [
      { "segment": "", "revenue_mix_pct": null, "core_product": "", "job_to_be_done": "" }
    ],
    "customer_type": "",
    "revenue_concentration": "",
    "thesis_segment": "",
    "supporting_evidence": "",
    "summary": ""
  },

  "drivers": [
    {
      "rank": null,
      "name": "",
      "type": "",
      "root_cause": "",
      "revenue_exposure": "",
      "exposure_disclosed_and_dated": null,
      "margin_direction": "",
      "duration": "",
      "market_vs_management_divergence": "",
      "supporting_evidence": ""
    }
  ],

  "quality_and_competitive_advantage": {
    "returns": { "roic_pct": null, "vs_wacc": "", "pricing_power": "" },
    "moat_rating": "",
    "strongest_mechanism": "",
    "moat_durability": "",
    "customer_captivity": "",
    "supply_advantage": "",
    "market_structure": "",
    "differentiation": "",
    "share_trajectory": "",
    "disruption_risk": "",
    "management_credibility": "",
    "key_vulnerability": "",
    "verdict": "",

    "supporting_evidence": {
      "returns": "",
      "moat": "",
      "captivity": "",
      "supply_advantage": "",
      "competition": "",
      "management": ""
    },

    "consistency_checks": [
      {
        "check": "",
        "conclusion_tested": "",
        "supported_by_evidence": null,
        "status": "Confirmed | Contradicted | Unverified",
        "note": ""
      }
    ]
  },

  "drivers_vs_quality": [
    {
      "driver": "",
      "relationship": "reinforces | neutral | challenges",
      "consistent_with_verdict": null,
      "what_would_break_the_thesis": "",
      "evidence_to_verify": ""
    }
  ],

  "how_it_evolves": {
    "trajectory_vectors": [
      {
        "vector": "Demand | TAM headroom | Supply/pricing | Disruption | Moat | Drivers",
        "direction": "Up | Flat | Down",
        "read": "",
        "source_field": ""
      }
    ],
    "dominant_vector": "",
    "vector_conflict": "",
    "demand_path": "Accelerating | Steady | Decelerating | Flat | Declining",
    "secular_vs_cyclical": "Secular | Mixed | Cyclical",
    "supply_cycle_position": "Early expansion | Mid-cycle | Late cycle | Trough",
    "pricing_implication_2_3y": "",
    "moat_path": "Widening | Stable | Eroding",
    "scenarios": {
      "bull": { "path": "", "key_assumption": "", "confirming_signpost": "" },
      "bear": { "path": "", "key_assumption": "", "confirming_signpost": "" }
    },
    "most_contested_question": "",
    "bull_case": "",
    "bear_case": "",
    "resolving_catalyst": "",
    "catalyst_timing": "",
    "key_swing_factor": "",
    "what_to_monitor": []
  },

  "key_questions": [
    {
      "question": "",
      "origin": "consistency_check | driver_vs_quality | unverified_exposure | cross_skill_contradiction | upstream_unknown | scenario_signpost | out_of_box",
      "why_it_matters": "",
      "evidence_needed": "",
      "where_to_look": "",
      "knowability": "knowable_now | monitor",
      "priority": "High | Medium | Low"
    }
  ],

  "research_plan": [
    {
      "research_point": "",
      "answers_question": "",
      "data_to_extract": "",
      "channels": {
        "experts": [],
        "internet_data": [],
        "reddit": [],
        "industry_forums": [],
        "primary_alt_data": []
      },
      "priority": "High | Medium | Low"
    }
  ],

  "second_order_effects": [
    {
      "loop_type": "Value-chain reflexivity | Cross-segment cannibalization | Competitive response | Customer-economics feedback | Narrative-fundamentals reflexivity | Concentration ripple | Policy reflexivity",
      "first_order_view": "",
      "second_order_consequence": "",
      "early_signal": "",
      "supporting_evidence": "",
      "is_inference": null
    }
  ],

  "next_opportunity": [
    {
      "trend": "",
      "affected_entity": "",
      "ticker": "",
      "linkage": "Supplier | Customer | Competitor | Adjacent | Substitute | Picks-and-shovels",
      "impact": "Positive | Negative | Mixed",
      "thesis": "",
      "is_inference": null
    }
  ],

  "out_of_box_factors": [
    {
      "factor": "",
      "category": "Exogenous shock | Balance-sheet / financial | Stakeholder | Accounting / disclosure | Demand-shape | Unknown unknown",
      "why_it_could_matter": "",
      "early_signal": "",
      "supporting_evidence": "",
      "is_inference": null
    }
  ],

  "cross_skill_reconciliation": {
    "reinforcing_signals": [],
    "contradictions": [
      { "tension": "", "skills_involved": [], "resolution": "" }
    ]
  },

  "investment_summary": {
    "what_it_is": "",
    "What_drives_stock": "",
    "quality_grade": "High | Above-average | Average | Below-average | Low",
    "key_debate": "",
    "biggest_open_question": "",
    "bottom_line": ""
  },

  "coverage": {
    "inputs_used": [],
    "missing_inputs": []
  }
}
```

### Output 2 — Research Plan

The concise action list, distilled from Output 1. Every entry is a short bullet, not a paragraph. `drivers` and `key_questions` are one-liners; `research_plan` pairs each research point with its flattened channel list.

```json
{
  "company": "",
  "ticker": "",
  "drivers": [
    ""
  ],
  "key_questions": [
    ""
  ],
  "research_plan": [
    {
      "research_point": "",
      "answers_question": "",
      "channels": [],
      "priority": "High | Medium | Low"
    }
  ]
}
```

### Output 3 — One-Pager

The tightest possible read, also distilled from Output 1. Two short paragraphs plus two bullet lists — nothing else. `research_plan_and_key_questions` folds the top questions, the research plan, and the most important second-order effect into one bulleted list.

```json
{
  "company": "",
  "ticker": "",
  "business_background": "",
  "business_quality": "",
  "key_debates": [
    ""
  ],
  "research_plan_and_key_questions": [
    ""
  ]
}
```
