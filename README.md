# Company Qualitative Research

A pipeline of qualitative research skills that turn raw company input data into one coherent investment narrative plus a research agenda.

## Folder structure

```
company_qualitative_research/
├── README.md                      # this file
└── skills_company_analysis/       # the skills, run in the order below
    ├── snapshot.md                # Stage 1  — one-page first pass
    ├── demand_analysis.md         # Stage 2  — demand type, growth, lock-in
    ├── Supply_analysis            # Stage 2  — competitors, structure, capex, disruption
    ├── Moat_analysis.md           # Stage 2  — moat indicators & sources
    ├── management_credibility.md  # Stage 2  — incentives, guidance, honesty
    ├── What_matters.md            # Stage 2  — ranked root drivers
    └── analyst_summary.md         # Stage 3  — synthesis + research agenda
```

## Pipeline

Three stages. Each stage's output feeds the next; the original input data flows through all of them.

```
                 ┌─────────────────┐
   input data ──▶│  1. snapshot    │──▶ snapshot.json
                 └─────────────────┘
                          │
        input data + snapshot.json
                          │
            ┌─────────────┼───────────────┬───────────────┬───────────────┐
            ▼             ▼               ▼               ▼               ▼
      ┌──────────┐ ┌──────────┐   ┌──────────┐   ┌──────────────┐ ┌──────────────┐
      │  demand  │ │  supply  │   │   moat   │   │  management  │ │ what_matters │   2. framework skills
      └──────────┘ └──────────┘   └──────────┘   └──────────────┘ └──────────────┘
            │             │               │               │               │
            └─────────────┴───────────────┴───────┬───────┴───────────────┘
                                                  │
                       snapshot + all five framework outputs (JSON)
                                                  │
                                                  ▼
                                        ┌───────────────────┐
                                        │ 3. analyst_summary│──▶ narrative + research agenda
                                        └───────────────────┘
```

### Stage 1 — Snapshot (first pass)
`input data` → **snapshot**. Produces the one-page read: segments, products, business model, competitors, key debates. This frames the company before any deep work.

### Stage 2 — Framework skills (parallel)
`input data + snapshot output` → each of **demand_analysis, Supply_analysis, Moat_analysis, management_credibility, What_matters**. They run independently; each receives the same two inputs and emits its own JSON. The snapshot gives them shared context (what the company is, where revenue concentrates) so they don't each re-derive the basics.

### Stage 3 — Analyst summary (synthesis)
`snapshot output + all five framework outputs` → **analyst_summary**. This is a processing and critique agent, not another data-gatherer. It:
- carries the upstream verdicts through verbatim (with their concise `key_evidence`),
- fuses moat + lock-in + competition + management into one **quality of business & competitive advantage** verdict,
- runs **internal-consistency checks** (e.g. a high moat must be anchored in captivity or a supply advantage),
- stress-tests the **drivers against that quality verdict**,
- projects **how it will evolve** (scenario-based), and
- outputs a **research agenda** — key questions, second-order/reflexive effects, and out-of-box factors none of the upstream skills were built to see.

## Conventions

- The skills are **tool- and data-source agnostic** — they describe the analytical framework and what to look for, not which provider or API to pull it from. Wire them to whatever data tooling you use.
- Each skill ends with a single JSON `Output Schema`; that JSON is the contract passed downstream.
- Headline verdicts carry a concise `key_evidence` line so the proof — not just the rating — flows to `analyst_summary`.
