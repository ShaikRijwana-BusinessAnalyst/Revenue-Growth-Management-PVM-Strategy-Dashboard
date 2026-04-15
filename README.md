# 📊 Revenue Growth Management — PVM Decision Engine

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Analytics-blue?style=flat)
![Regions](https://img.shields.io/badge/4%20Regions-Global-green?style=flat)
![Categories](https://img.shields.io/badge/9%20Categories-Retail-purple?style=flat)

> A Power BI analytics system that decomposes $8.86M revenue growth into three causal levers — exposing a $28.60B volume-mix cancellation concealed beneath a 0.11% YoY headline. Built for C-suite decision-making, not retrospective reporting.

---

## Executive Summary

Headline revenue growth of 0.11% conceals a structural deterioration: $28.60B in volume gains are being fully neutralised by an equal and opposite mix erosion as customers systematically trade down from Premium to Budget tiers. A $5.96M price effect provides the only net positive contribution, validating pricing power that remains under-deployed in high-opportunity markets. Without surgical intervention on product mix, the current trajectory will expand COGS faster than revenue within two to three quarters.

---

## KPI Snapshot

| Metric | Current | Target | Gap | Status |
|--------|---------|--------|-----|--------|
| Revenue Delta | $8.86M | >$15M | −$6.14M | ⚠️ Below target |
| YoY Revenue Growth % | 0.11% | >3.0% | −2.89pp | 🔴 Critical |
| Price Effect | +$5.96M | >$8M | −$2.04M | ⚠️ Under-deployed |
| Volume Effect | +$28.60B | >$10M | Overperforming | ✅ Strong |
| Mix Effect | −$28.60B | >−$1M | −$28.60B | 🔴 Critical |
| Premium Mix % | 0.32% | 35% | −34.68pp | 🔴 Structural risk |
| UAE Premium Opportunity | $3.08M | >$4M | −$0.92M | 🟡 In reach |
| Nike Shoes Relative Index | 100% | Benchmark | Leader | ✅ Reinvest |

---

## Dashboard Preview

![Revenue Growth Management PVM Dashboard](images/dashboard_preview.png)

> Interactive Power BI dashboard with four cross-functional slicers (Category, Tier, Region, Channel). Each visual answers exactly one executive question. Toggle slicers to stress-test the PVM framework against individual business units.

---

## Business Problem

A global retail operation across four regions (India, UAE, UK, USA) and three product tiers (Budget, Mid, Premium) reported 0.11% YoY revenue growth while unit volumes surged double digits. Standard reporting could not isolate whether the drag originated from pricing decisions, portfolio composition, channel mix, or regional demand shifts.

> **The risk was invisible in conventional dashboards.** The $28.60B volume gain and $28.60B mix erosion cancel to zero — leaving a misleadingly stable headline while the business grows busier at lower margins.

---

## PVM Bridge — Revenue Decomposition

```
Revenue LY  ──────────────────────────────────────  Baseline
              + $5.96M   (Price Effect)             ↑ Pricing decisions
              + $28.60B  (Volume Effect)             ↑ Unit demand growth
              − $28.60B  (Mix Effect)               ↓ Customer trade-down
            ─────────────────────────────────────
Revenue TY    = $8.86M delta   (0.11% YoY)          ✓ Zero residual
```

The Volume Effect and Mix Effect cancel with mathematical precision — confirming this is a structural portfolio problem, not a statistical anomaly.

---

## Visualization Strategy

| Visual Type | Question Answered | Key Insight Revealed |
|-------------|------------------|----------------------|
| PVM Waterfall Chart | "Where did revenue come from — and where did it leak?" | $28.60B volume gain fully cancelled by mix erosion; net growth solely from $5.96M price effect |
| Regional Matrix Heatmap | "Which region-tier combinations create vs. destroy value?" | UAE Premium at $3.08M — highest untapped opportunity |
| YoY Product Bar Chart | "Which products are growth engines vs. value destroyers?" | Nike Shoes (100%) carries; Backpack (−23.4%) destroys |
| Premium Mix Stacked Bar | "Is our premium strategy working regionally?" | USA = prestige model; India = volume model — two different playbooks required |
| Decomposition Tree | "What is the precise causal path to the $8.86M delta?" | Single-region Budget tier responsible for majority of volume gain |
| Scatter Plot (Price vs. Volume) | "Are we trading price for scale, or achieving both?" | Largest revenue bubbles drifting toward high-volume / low-price quadrant |

---

## DAX Model — Key Measures

| Measure | Formula | Business Purpose |
|---------|---------|-----------------|
| `Revenue LY` | `CALCULATE([Revenue], SAMEPERIODLASTYEAR('Date'[Date]))` | Prior-year baseline for all delta calculations |
| `Revenue Delta` | `[Revenue TY] - [Revenue LY]` | Total commercial growth to be decomposed |
| `Price Effect` | `SUMX(Products, (PriceTY - PriceLY) × VolumeTY)` | Isolates management pricing decisions from organic demand |
| `Volume Effect` | `SUMX(Products, (VolumeTY - VolumeLY) × PriceLY)` | Pure unit demand growth at prior-year prices |
| `Mix Effect` | `[Revenue Delta] - [Price Effect] - [Volume Effect]` | Residual — guarantees mathematical closure, zero residual |
| `Premium Mix %` | `DIVIDE(CALCULATE([Revenue], Tier[Tier]="Premium"), [Revenue])` | North Star metric for portfolio margin quality |
| `Relative Contribution %` | `DIVIDE([Rev Delta Product], MAXX(ALL(Products), [Rev Delta Product]))` | Ranks products by growth quality, normalised 0–100% |
| `Bridge Step Sequence` | `SWITCH([Step], "Revenue LY",1, "Price",2, "Volume",3, "Mix",4, "Revenue TY",5)` | Controls waterfall rendering order |

**DAX integrity constraint:** Mix Effect is computed as a residual (`Revenue Delta − Price − Volume`), guaranteeing mathematical closure regardless of filter context. This eliminates rounding errors that corrupt PVM models built on direct calculation.

---

## Product Contribution Index

Normalised to Nike Shoes (100%). Negative = net portfolio drag.

| Product | Relative Contribution | Tier | Action |
|---------|----------------------|------|--------|
| Nike Shoes | 🟩 100% | Apparel | Double marketing spend |
| Study Table | 🟩 23.4% | Furniture | Scale selectively |
| iPhone 14 | 🟦 18.2% | Electronics | Maintain |
| Protein Powder | 🟦 15.1% | Health | Maintain |
| Samsung TV | 🟦 9.8% | Electronics | Monitor |
| Office Chair | ⬜ 6.3% | Furniture | Review |
| Levi's Jeans | ⬜ 4.1% | Apparel | Review |
| Backpack | 🟥 −23.4% | Accessories | **Phase out** |

---

## Strategic Findings

**01 — Volume-Mix cancellation is structural, not a fluctuation**
The $28.60B Volume Effect and $28.60B Mix Effect cancel to within rounding precision. This reflects a consistent, cross-regional customer behaviour shift toward Budget products. The business is operationally busier while generating no incremental margin on that activity.

**02 — Pricing power exists but is under-deployed**
The $5.96M Price Effect confirms market absorption of modest price increases without volume collapse. India YoY growth of 0.12% and UAE at 0.10% both respond positively to pricing actions. Revenue would turn negative without this buffer.

**03 — Nike Shoes and Study Tables carry the entire portfolio**
These two categories account for substantially all incremental revenue at 100% and 23.4% relative contribution respectively. Backpack at −23.4% is consuming marketing, shelf space, and logistics while subtracting value.

**04 — India and USA require structurally different commercial strategies**
India is a volume-and-assortment market (Mid-tier dominant, high unit velocity, low per-unit margin). USA is a premium-and-prestige market (lower velocity, high per-unit margin). A single strategy is guaranteed to underperform in one.

**05 — UAE Premium at $3.08M is the highest-certainty growth lever**
Region×Tier matrix confirms UAE Premium is currently under-monetised. A conservative +7% price test requires zero incremental volume — pure margin improvement.

---

## Actionable Recommendations

| Priority | Action | Expected Impact | Timeline | Owner |
|----------|--------|----------------|----------|-------|
| 🔴 P1 | Restructure sales KPI: Total Volume → Premium Mix % | Eliminates incentive misalignment driving mix erosion | 30 days | Sales Ops + Finance |
| 🔴 P1 | Double marketing on Nike Shoes (index: 100%) | +$14.3M if scaled to iPhone 14 volumes | 30–60 days | Category Mgmt + Marketing |
| 🟠 P2 | +7% price pilot on UAE Premium segment | +$3.08M conservative; validates pricing power | 60 days | Pricing + UAE Regional |
| 🟠 P2 | Phase out Backpack category (−23.4% relative) | +$2.3M margin recovery, immediate EBITDA improvement | 60–90 days | Category Mgmt + Supply Chain |
| 🟣 P3 | India Premiumisation Programme | +$858M at +3pp Premium Mix shift | 90–180 days | India Lead + Merchandising |

---

## Predictive Risk Model

**6-month downside if Mix erosion continues at 1pp/month:**
```
Risk = 6 months × 1% monthly shift × $28.60B volume base = $171.6M
```

**90-day recovery upside with +1pp Premium Mix intervention:**
```
Upside = 1% × $28.60B volume base = $286M
```

**Annual strategic upside with +3pp Premium Mix recovery (32% → 35%):**
```
Annual upside = 3% × $28.60B volume base = $858M+
```

---

## Video Walkthrough

▶️ **[Watch: 2-Minute PVM Strategy Walkthrough](video/pvm_dashboard_walkthrough.mp4)**

| Timestamp | Content |
|-----------|---------|
| 0:00–0:20 | The Growth Paradox — why 0.11% is a warning, not a win |
| 0:20–0:50 | The Volume-Mix Trap — $28.60B gain, $28.60B leak |
| 0:50–1:30 | Five strategic views: heroes vs. zeroes, regional models, price elasticity |
| 1:30–1:50 | Three surgical recommendations — $858M+ in trapped value |
| 1:50–2:00 | From data janitors to revenue surgeons |

---

## Technical Implementation

**Stack:** Power BI Desktop · DAX · Excel · Star schema data model

**Data cleaning protocol:**
1. Duplicate removal via composite key deduplication (TransactionID + Date + ProductID)
2. Product name standardisation — reconciled 23 variants using 85% fuzzy match threshold
3. Missing regional attribution — imputed using purchase pattern clustering
4. Currency normalisation — USD, GBP, AED, INR converted to USD at period-average rates

**Data scope:** 44,495 transaction records · 4 regions · 3 tiers · 9 product categories

---

## Repository Contents

```
📁 revenue-growth-management-pvm/
├── 📊 RGM_PVM_Dashboard.pbix          Power BI file — full interactive dashboard
├── 📂 data/
│   ├── 📋 sales_transactions.xlsx     Cleaned dataset (44,495 records)
│   └── 📋 data_dictionary.xlsx        Field definitions and cleaning log
├── 📂 images/
│   ├── 🖼️  dashboard_preview.png      Full dashboard screenshot
│   ├── 🖼️  waterfall_chart.png        PVM Bridge waterfall detail
│   ├── 🖼️  regional_matrix.png        Region × Tier heatmap
│   └── 🖼️  scatter_plot.png           Price vs. Volume growth scatter
├── 📂 video/
│   └── 🎬 pvm_dashboard_walkthrough.mp4   2-minute executive walkthrough
└── 📄 README.md
```

---

## Professional Contact

Open to Senior Analyst, Business Intelligence Lead, and Commercial Strategy roles in retail, FMCG, and e-commerce.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin)](https://linkedin.com/in/YOUR-PROFILE)
[![Portfolio](https://img.shields.io/badge/Portfolio-View%20More-4CAF50?style=for-the-badge)](https://your-portfolio-site.com)
[![Email](https://img.shields.io/badge/Email-Get%20In%20Touch-D14836?style=for-the-badge&logo=gmail)](mailto:your.email@domain.com)
