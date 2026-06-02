---
name: demand_analysis
description: Framework for analyzing demand type, demand growth and demand stability.
summary: |
  Step 1: Identify Customers: who are the customers — businesses or consumers?
  Step 2: Consumers: why do they need to buy?
  step 3: Businesses: what specific business problem do they solve?
  Step 4: Demand Growth: is demand growing, and where is the growth coming from?
  Step 5: Lock-In: why can't they buy somewhere else?
---


Analyze a company's customers in five steps: identify who they are, why they buy (consumers vs businesses), whether that demand is growing, and finally why they can't buy elsewhere.

## Step 1: Identify Customers

**Key question: who are the customers — businesses or consumers?**

Establish who actually pays before assessing anything else. The answer routes the rest of the analysis:
- **Consumers (B2C)** → go to **Step 2** to classify the underlying human demand.
- **Businesses (B2B)** → go to **Step 3** to identify the specific problem the product solves.
- **Businesses serving consumers (B2B2C)** → the company's direct customer is a business, but the demand is ultimately driven by that business's consumers (e.g., a payments processor selling to merchants, a chip maker selling to device OEMs, a SaaS platform white-labeled to consumers). Run **Step 3** for the direct business customer *and* **Step 2** for the underlying consumer demand that pulls the product through — the company's growth tracks the end-consumer demand even though it bills the intermediary.
- **Both (mixed)** → the company sells separately to distinct consumer and business segments. Run Step 2 for the consumer segment and Step 3 for the business segment separately.

**How to assess:** Look at the company profile and product-level revenue mix to see who the buyers are; check filings and transcripts for management's description of the customer base.

---

## Step 2: Demand Type — Consumers (Maslow-Based)

**Key question: why do they need to buy?**

Classify the underlying human demand the company's products serve, using a Maslow-style hierarchy. Demand type explains *why* customers buy and how durable that buying is — lower levels are non-discretionary and recession-resilient; higher levels are discretionary, more cyclical, but often carry stronger pricing power and brand premium. **A company can serve multiple demand types** (e.g., Apple spans Connection, Status, and Skill & Achievement); identify all that apply and mark the primary one.

| Level | Demand Type | Examples | Investment Read |
|---|---|---|---|
| 1 | **Survival** | Food, beverage, housing, healthcare, utilities | Most defensive — demand persists through any cycle; usually lower margin, volume-driven |
| 2 | **Safety** | Insurance, security, savings, cybersecurity | Defensive and sticky — fear-driven, non-discretionary; benefits from rising risk awareness |
| 3 | **Connection** | Social media, gaming, communication, dating | Engagement-driven; network effects common; ad/subscription monetization |
| 4 | **Status** | Luxury goods, premium autos, fine watches, high-end consumer | Discretionary and cyclical, but strongest pricing power and brand premium |
| 5 | **Skill & Achievement** | Education, training, professional certification, productivity tools | Tied to career/economic mobility; resilient in downturns (re-skilling) but budget-sensitive |
| 6 | **Self-Actualization** | Art, creation, travel, spiritual growth | Highly discretionary — first cut in downturns; high emotional value when affordable |
| 7 | **Transcendence** | Religion, charity, social mission, environmental protection | Mission/values-driven; loyal but donation/discretionary-funding dependent |

**How to assess:**
- Use the company profile and product-level revenue mix to map what the company actually sells to the demand levels above.
- Check filings and transcripts for management's framing of the core need served.
- For multi-product companies, classify each major segment separately — different segments often serve different levels.
- Identify the **primary** demand type (largest revenue / core identity) and any **secondary** types.
- Read the level for cyclicality and pricing power: Survival/Safety skew defensive and low-margin; Status/Self-Actualization skew cyclical but premium-priced.

---

## Step 3: Problem Solved — Businesses

**Key question: what specific business problem do they solve?**

For business customers, demand is rational and ROI-driven — a company buys because the product solves a concrete problem cheaper, faster, or better than the alternative. Pin down exactly what that problem is and how essential the solution is to the customer's operations.

| Problem Type | What It Solves | Investment Read |
|---|---|---|
| **Revenue-generating** | Helps the customer win or grow sales (CRM, ad platforms, payments) | Spend tied to the customer's growth — scales up in good times, cut in downturns |
| **Cost-saving / efficiency** | Reduces labor, time, or input cost (automation, cloud, logistics software) | Resilient — the ROI case strengthens when customers are cutting costs |
| **Mission-critical / compliance** | Keeps the business running or legal (security, ERP, regulatory reporting) | Stickiest — non-negotiable spend, high willingness to pay |
| **Nice-to-have / discretionary** | Marginal convenience or productivity gain | Weakest — first to be cut when budgets tighten |

**How to assess:**
- Check filings and transcripts for how management frames the problem.
- Check industry sources for customer case studies and quantified ROI claims.
- Gauge criticality: is the product embedded in the customer's core workflow (mission-critical) or a peripheral add-on?
- Mission-critical and cost-saving problems support durable demand and pricing power; discretionary ones do not.

### Industrial Companies — Supply Chain Position

For industrial companies (components, materials, equipment, capital goods) that sell physical products *into* a customer's supply chain, the "problem solved" is best read through where they sit in the value chain and how critical their input is to the end product.

| Dimension | What to Assess | Investment Read |
|---|---|---|
| **Value-chain position** | Upstream (raw materials/inputs), midstream (components/processing), or downstream (assembly/finished goods) | Upstream skews commodity/cyclical; specialized midstream components carry pricing power; downstream is demand/brand-driven |
| **Input criticality** | Is the product essential to the end product's function? Single-sourced or designed-in? | Mission-critical, designed-in inputs = high switching cost and pricing power |
| **BOM content** | What % of the customer's bill of materials / total cost does it represent? | Small-% but failure-critical inputs hold the strongest pricing power (high value, low cost-to-switch-risk) |
| **Customer concentration** | How concentrated is the downstream customer base (top customers as % of revenue)? | High concentration = customer bargaining-power risk; diversified = more resilient |
| **Qualification barriers** | Must the customer re-qualify or re-certify to switch suppliers? | Long qualification cycles (auto, aerospace, semis, medical) = durable lock-in |
| **Supplier power (upstream)** | Concentration and substitutability of the company's *own* input suppliers | Concentrated upstream suppliers = input-cost and margin risk |

**How to assess:**
- Use the product-level revenue mix and check filings and transcripts to locate the company in the chain.
- Check filings and transcripts for concentration and design-in dynamics.
- Check industry sources to place the company in the broader chain (e.g., raw material → Tier 2 → Tier 1 → OEM).
- Trace **both directions**: who they buy from (supplier power) and who they sell to (customer power) — the core of supply-chain analysis.

---

## Step 4: Demand Growth

**Key question: is this demand growing — and where is the growth coming from?**

After establishing why customers buy, determine whether that demand is expanding, flat, or shrinking — and decompose the source. Two sub-questions sharpen it: are *existing* customers needing more, and are *new* customers entering? Durable growth comes from a secular driver or rising per-customer intensity, not a one-off cycle.

| Growth Source | What's Driving It | Investment Read |
|---|---|---|
| **New customers (penetration)** | More buyers adopting / share gains in a growing market | TAM expansion or share gain — check whether penetration is early-stage or saturating |
| **Existing customers buying more (expansion)** | Higher usage, upsell, more seats/units per customer | Net revenue retention >100% — the most durable, capital-efficient growth |
| **Secular tailwind** | Structural shift lifting the whole category (AI, electrification, aging demographics) | Durable multi-year driver — verify it's secular, not a cyclical bounce |
| **Geographic / new-market expansion** | Entering new regions or adjacent segments | Extends the runway — weigh execution risk and local competition |
| **New products / use cases** | New SKUs or applications widening the addressable need | Innovation-driven; durable only if the R&D pipeline keeps delivering |
| **Replacement / upgrade cycle** | Periodic refresh of an installed base | Cyclical and lumpy — time the cycle, don't extrapolate the peak |
| **Price / mix** | Higher prices or a shift toward premium tiers | Pricing-power-driven — confirm volumes hold as price rises |

**How to assess:**
- Use growth rates and the income statement (~10 years) for the multi-year revenue trajectory — is growth accelerating or decelerating?
- Check filings and transcripts to split growth into volume vs price and new vs existing customers.
- Check industry sources for the underlying market growth rate and structural drivers.
- Separate **secular** (durable) from **cyclical** (temporary) growth, and **volume** (real demand) from **price** (inflation/mix) — the best signal is rising volume powered by a secular driver.

---

## Step 5: Lock-In

**Key question: why can't they buy somewhere else?**

Lock-in generally results in **higher customer willingness to pay** and **high switching costs**, which together protect revenue durability and pricing power. These are the strategic mechanisms companies use to lock in customers — a company may employ several simultaneously, so assess each and weigh the cumulative effect.

### 5.1 Contractual Commitments

Formal agreements that bind customers for a set period, with penalties for leaving early.

- **Strong**: multi-year terms, auto-renewal, early-termination fees >6 months of value, >70% of revenue under contract.
- **Weak**: month-to-month or at-will contracts.
- **Examples**: enterprise SaaS, telecom plans, defense contracts, commercial leases.
- **Assess**: check filings and transcripts for contract term, RPO, backlog, renewal rates; the income statement for revenue stability (high coverage → low volatility).

### 5.2 Brand-Specific Training

Customers invest time mastering the product; that learned skill is a sunk cost that discourages switching.

- **Strong**: vendor certifications, steep learning curve with high payoff, large trained-professional ecosystem.
- **Weak**: simple/commodity product, easily transferable skills.
- **Examples**: Salesforce certs, Adobe, SAP/Oracle ERP, AutoCAD, Bloomberg Terminal.
- **Assess**: check filings and transcripts for certification/onboarding discussion; check industry sources for product-specific job postings as a depth proxy.

### 5.3 Loyalty Programs

Reward systems where accumulated benefits raise the cost of leaving.

- **Strong**: slow-accruing high-value points, tiered status, low breakage.
- **Weak**: rewards easily earned and redeemed across competitors.
- **Examples**: airline miles, hotel tiers, credit-card rewards, Amazon Prime, Starbucks Rewards.
- **Assess**: check filings and transcripts for members, redemption, breakage; the balance sheet for deferred revenue as a lock-in proxy.

### 5.4 Search Costs

The effort and uncertainty of evaluating alternatives keeps customers with the known option.

- **Strong**: complex product, outcomes hard to judge upfront, opaque/bundled pricing, long sales cycles.
- **Weak**: transparent pricing, standardized products, strong comparison infrastructure.
- **Examples**: healthcare providers, B2B enterprise software, financial advisors, legal services.
- **Assess**: check filings and transcripts for sales-cycle length, RFP/POC processes; sales cycles >6 months signal high search costs.

### 5.5 Network Effects

The product gets more valuable as more people use it, so leaving means a smaller network.

- **Strong**: value scales with user count, two-sided marketplace, critical mass reached.
- **Weak**: users multi-home across competing platforms.
- **Examples**: social media, Visa/Mastercard, marketplaces, WhatsApp/WeChat, LinkedIn, app stores.
- **Assess**: check filings and transcripts for active users, engagement, two-sided dynamics; the income statement for revenue-per-user trend.

### 5.6 No Viable Alternative

The customer has no realistic substitute — a regulated sole supplier, a de facto standard, or patent-protected technology.

- **Strong**: regulated sole source, >80% share / de facto standard, patent on essential tech.
- **Weak**: multiple competitors each with >10% share.
- **Examples**: utilities, ASML (EUV), Google Search (~90%), Windows in enterprise, TSMC (advanced nodes).
- **Assess**: check filings and transcripts for market position and regulatory status; the peer list and income statement for share gaps; check industry sources for share data.
- **Watch**: patent-based positions are temporary (check expiry); regulatory positions can shift with policy.

### 5.7 Product Bundles

Multiple products sold as a package worth more together, so dropping one component is costly.

- **Strong**: >30% bundle discount, tight integration, customer uses 3+ components.
- **Weak**: loosely coupled components that can be cherry-picked.
- **Examples**: Microsoft 365, Apple ecosystem, Amazon (Prime+Marketplace+AWS), Adobe CC, Google Workspace.
- **Assess**: check filings and transcripts for cross-sell and products-per-customer; the product-level revenue mix for multi-product revenue growth.

### 5.8 Low-Cost Offering

Prices so low that any alternative costs more even after switching costs — lock-in through economics.

- **Strong**: structural cost advantage from scale, profitable while cheapest, durable across cycles.
- **Weak**: low prices funded by unsustainable subsidies or losses.
- **Examples**: Costco, Amazon, Walmart, Southwest, index funds (Vanguard/Fidelity).
- **Assess**: the income statement and peer list to confirm low prices with healthy margins; check industry sources for price comparisons.

---

## Output Schema

Output the final synthesis as a single JSON object. The schema mirrors the five steps in order — `customers` (Step 1), `consumer_demand` (Step 2), `business_demand` (Step 3), `demand_growth` (Step 4), `lock_in` (Step 5) — followed by a cross-step `synthesis`. The synthesis block's `key_evidence` holds one concise line — the single strongest data point or quote (with its period) behind the headline durability/lock-in verdict — so a downstream synthesis agent can carry the proof through, not just the rating.

**Rules:**
- Omit any field where data is unavailable rather than guessing.
- For every assessment, populate `evidence` with the specific data point or quote that supports it, and `source` with where it came from (e.g., `"FY2024 10-K"`, `"Q3 2024 earnings call"`, `"income statement"`, `"industry report"`).
- Fill `consumer_demand` if the company serves consumers directly (Step 1 = B2C or Mixed) or if end-consumer demand pulls the product through an intermediary (B2B2C). Fill `business_demand` if it serves businesses (B2B, B2B2C, or Mixed). Omit the block that does not apply. For B2B2C, populate both: `business_demand` for the direct customer, `consumer_demand` for the end demand driver.
- Within `business_demand`, include `supply_chain_position` only for industrial companies that sell physical products into a customer's supply chain; omit it otherwise.
- In `lock_in.mechanisms`, keep all eight entries. For mechanisms that do not apply, set `present: false` and `strength: "N/A"` and leave the detail fields null.

```json
{
  "company": "",
  "ticker": "",
  "analysis_date": "",

  "customers": {
    "customer_type": "B2C | B2B | B2B2C | Mixed",
    "segments": [
      {
        "name": "",
        "buyer": "Consumer | Business | Business (end demand: consumer)",
        "pct_of_revenue": null,
        "description": ""
      }
    ],
    "end_demand_driver": "",
    "evidence": "",
    "source": ""
  },

  "consumer_demand": {
    "demand_types": [
      {
        "level": null,
        "type": "Survival | Safety | Connection | Status | Skill & Achievement | Self-Actualization | Transcendence",
        "is_primary": null,
        "products_served": "",
        "rationale": "",
        "evidence": "",
        "source": ""
      }
    ],
    "demand_profile": {
      "primary_demand_type": "",
      "discretionary": "Non-discretionary | Mixed | Discretionary",
      "cyclicality": "Defensive | Neutral | Cyclical",
      "pricing_power": "Strong | Moderate | Weak",
      "demand_durability": "High | Moderate | Low",
      "notes": ""
    }
  },

  "business_demand": {
    "problems_solved": [
      {
        "problem_type": "Revenue-generating | Cost-saving / efficiency | Mission-critical / compliance | Nice-to-have / discretionary",
        "products_served": "",
        "criticality": "Mission-critical | Important | Peripheral",
        "roi_evidence": "",
        "is_primary": null,
        "evidence": "",
        "source": ""
      }
    ],
    "supply_chain_position": {
      "value_chain_position": "Upstream | Midstream | Downstream",
      "input_criticality": "Essential / designed-in | Important | Commoditized",
      "single_sourced": null,
      "bom_content_pct": null,
      "customer_concentration": {
        "top_customer_pct": null,
        "top_customers_pct": null,
        "assessment": "Concentrated | Moderate | Diversified"
      },
      "qualification_barriers": "High | Moderate | Low",
      "supplier_power": "High | Moderate | Low",
      "evidence": "",
      "source": ""
    },
    "demand_profile": {
      "cyclicality": "Defensive | Neutral | Cyclical",
      "pricing_power": "Strong | Moderate | Weak",
      "demand_durability": "High | Moderate | Low",
      "notes": ""
    }
  },

  "demand_growth": {
    "trajectory": "Accelerating | Steady | Decelerating | Flat | Declining",
    "revenue_cagr_pct": null,
    "cagr_period": "",
    "growth_sources": [
      {
        "source": "New customers (penetration) | Existing customers buying more (expansion) | Secular tailwind | Geographic / new-market expansion | New products / use cases | Replacement / upgrade cycle | Price / mix",
        "is_primary": null,
        "contribution": "Primary | Secondary | Minor",
        "evidence": "",
        "source": ""
      }
    ],
    "volume_vs_price": "Volume-led | Balanced | Price-led | Unknown",
    "secular_vs_cyclical": "Secular | Mixed | Cyclical",
    "market_tam": {
      "size": "",
      "growth_rate_pct": null,
      "penetration_stage": "Early | Mid | Saturating",
      "source": ""
    },
    "durability": "Durable | Moderate | At-risk",
    "notes": ""
  },

  "lock_in": {
    "mechanisms": [
      {
        "type": "Contractual commitments",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "avg_contract_duration": "",
        "pct_revenue_under_contract": null,
        "early_termination_fees": null,
        "auto_renewal": null,
        "evidence": "",
        "source": ""
      },
      {
        "type": "Brand-specific training",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "certification_ecosystem": null,
        "learning_curve": "Steep | Moderate | Shallow | N/A",
        "evidence": "",
        "source": ""
      },
      {
        "type": "Loyalty programs",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "tiered_status": null,
        "deferred_revenue_liability": null,
        "rewards_fungible": null,
        "evidence": "",
        "source": ""
      },
      {
        "type": "Search costs",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "product_complexity": "High | Moderate | Low | N/A",
        "pricing_transparency": "Opaque | Mixed | Transparent | N/A",
        "sales_cycle_length": "",
        "evidence": "",
        "source": ""
      },
      {
        "type": "Network effects",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "sided": "Two-sided | One-sided | N/A",
        "multi_homing": null,
        "critical_mass_reached": null,
        "evidence": "",
        "source": ""
      },
      {
        "type": "No viable alternative",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "market_share_pct": null,
        "basis": "Regulatory | De facto standard | Patent | N/A",
        "patent_expiry_risk": null,
        "evidence": "",
        "source": ""
      },
      {
        "type": "Product bundles",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "products_per_customer": null,
        "bundle_discount_pct": null,
        "integration_depth": "Tight | Loose | N/A",
        "evidence": "",
        "source": ""
      },
      {
        "type": "Low-cost offering",
        "present": null,
        "strength": "Strong | Moderate | Weak | N/A",
        "is_price_leader": null,
        "cost_advantage_source": "Scale | Subsidy | Margin sacrifice | N/A",
        "advantage_is_sustainable": null,
        "evidence": "",
        "source": ""
      }
    ],
    "retention_metrics": {
      "gross_revenue_retention_pct": null,
      "net_revenue_retention_pct": null,
      "customer_churn_pct": null,
      "revenue_volatility": "Low | Moderate | High",
      "remaining_performance_obligations": null,
      "evidence": "",
      "source": ""
    }
  },

  "synthesis": {
    "demand_durability": {
      "assessment": "Strengthening | Stable | Eroding",
      "horizon": "Near-term | Medium-term | Long-term",
      "erosion_risks": []
    },
    "willingness_to_pay": {
      "pricing_power": "Strong | Moderate | Weak | None",
      "rationale": ""
    },
    "lock_in_verdict": {
      "lock_in_rating": "Strong | Moderate | Weak | None",
      "active_lock_in_types": [],
      "strongest_mechanism": "",
      "highest_switching_cost": ""
    },
    "key_vulnerability": "",
    "key_evidence": "",
    "bottom_line": ""
  }
}
```
