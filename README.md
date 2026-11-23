# Singapore Vehicle Quota & COE Price Intelligence
**Author:** Julie Xiao (`juliexiao`)  
**Cohort:** NUS Master of Science in Business Analytics (MSBA)  
**Dataset:** COE Bidding Results (`../../data/coe_bidding_results.csv`)

---

## 1. Executive Summary & Business Problem

Singapore's Vehicle Quota System (VQS) serves as the primary market-based rationing mechanism to control vehicular population density on the island. Over the past 16 years (2010–2026), Certificate of Entitlement (COE) premiums have experienced non-linear escalation, characterized by supply-driven cyclicality, policy shocks, and a dramatic post-pandemic surge culminating in multi-category six-figure premiums.

This study investigates the strategic question: **How has structural vehicle quota supply restriction driven premium divergence and convergence between Category A (mass market) and Category B (luxury/high-powered) vehicles, and what quantitative bidding, inventory, and fleet strategies should automotive dealership executives and corporate fleet operators adopt?**

Using a curated dataset of 2,000 bidding exercises across all five vehicle classes (Cat A, B, C, D, and E), we assess the supply-elasticity dynamics, quantify the historic spread collapse, and provide decision frameworks for automotive executives.

---

## 2. Key Empirical Findings

### Finding 1: Unprecedented Category A Price Inversion & Historical Record Peak ($139,001)
In November 2026 (Exercise 1), Category A achieved an all-time historical record of **$139,001**, overtaking Category B (**$132,334**) within the exact same exercise. Historically considered the "mass-market" tier, Cat A's surge represents a **+245.1% increase** over its 2020 annual average ($35,404) and a **+651.3% increase** over its January 2010 baseline ($18,502). The primary catalyst was intense middle-market competition fueled by accelerated mass EV adoption (under the 110kW threshold), pushing the bid-to-quota pressure ratio to **1.70x** (2,018 bids competing for 1,189 available quotas).

### Finding 2: The October 2023 Severe Supply Squeeze ($150,000+ Threshold Breach)
In October 2023 (Exercise 2), severe quota curtailment triggered the highest individual clearing prices recorded in Singapore's automotive history:
- **Category B Record:** **$150,001** (Quota restricted to 472 vehicles, 623 bids received).
- **Category E (Open) Record:** **$158,004** (Quota restricted to 138 vehicles, 228 bids received).

Empirical correlation analysis demonstrates a profound inverse relationship between quota volume and clearing premiums:
- **Category E Elasticity:** Strong negative correlation of **r = -0.7680**.
- **Category B Elasticity:** Negative correlation of **r = -0.4689**.
- **Category A Elasticity:** Moderate negative correlation of **r = -0.2325**, reflecting greater demand rigidity and essential transport substitution.

### Finding 3: Structural Luxury Spread Compression (2023 vs 2026)
The price premium of Category B (luxury) over Category A has structurally collapsed:
- In **2023**, the annual mean Category B premium exceeded Category A by **+$27,263** ($121,801 vs $94,538).
- By **2026**, the annual mean spread compressed by **90.6%** to just **+$2,560** ($124,730 vs $122,169).
This compression indicates that car buyers and distributors across both tiers now face uniform psychological and capital thresholds above $120,000, reducing the traditional product tiering segmentation previously leveraged by auto distributors.

---

## 3. Strategic Recommendations

### Recommendation 1: Dynamic Quota-Indexed Hedging for Automotive Dealerships
Automotive dealerships must abandon fixed-price consumer contracts with open-ended COE absorption clauses. When the bid-to-quota ratio exceeds **1.45x** in Exercise 1 of any quarterly quota announcement window:
1. Distributors should lock in guaranteed delivery packages using transferable **Category E** allocations rather than taking directional risk on Cat A/B clearing rounds.
2. Introduce a tiered floating rebate structure where retail contract prices are pegged to a rolling 3-exercise COE moving average, capping distributor margin volatility at ±3.5%.

### Recommendation 2: Fleet Capital Restructuring: Shift to 5-Year Operating Leases
With annual straight-line COE depreciation now exceeding **$13,900/year** ($1,158/month) for a Category A vehicle alone, corporate logistics and commercial fleets face high capital lock-in risk:
1. Fleet managers should transition procurement from 10-year outright ownership to **5-year operational leasing contracts**, shifting terminal quota residual risk onto leasing consortiums.
2. Commercial vehicle operators (Category C) should pre-bid during mid-cycle reallocations when quota increases are phased in, avoiding peak bidding rounds such as July 2026 ($95,000 peak).

---

## 4. Methodology & Data Lineage

- **Primary Source:** Singapore Land Transport Authority (LTA) via `data.gov.sg`.
- **File Reference:** `../../data/coe_bidding_results.csv`
- **Granularity & Scope:** 2,000 individual exercise observations spanning January 2010 to November 2026 across five statutory vehicle classifications:
  - `Category A`: Passenger cars up to 1,600cc / 130bhp, and electric vehicles up to 110kW.
  - `Category B`: Passenger cars above 1,600cc / 130bhp, and electric vehicles above 110kW.
  - `Category C`: Goods vehicles and buses.
  - `Category D`: Motorcycles.
  - `Category E`: Open category (all vehicles except motorcycles).
- **Analytical Transformations:**
  - Calculated longitudinal compound annual growth rates (CAGR) and YoY category spreads.
  - Extracted Pearson correlation coefficients evaluating quota volume availability versus cleared premium.
  - Derived bid-to-quota pressure ratios (`bids_received / quota`).
  - Embedded data in client-side interactive visualization (`submissions/juliexiao/index.html`) using Chart.js CDN for standalone browser execution without external runtime dependencies.
