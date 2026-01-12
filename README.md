# Marketing Budget Optimization with Linear & Mixed Integer Programming

**Course:** RM 294 – Optimization I  
**Project:** Integer Programming Marketing Optimization  
**Team:** Archie Korale Arachchige Don, Jake Embleton, Gabriel Kinshuk, Vinay Sangamalli  
**Date:** November 2025  
**Tools:** Python, Gurobi, NumPy, Pandas, Jupyter Notebook  

---

## Project Overview

This project develops and evaluates optimization models for allocating a **$10M marketing budget** across multiple advertising platforms under realistic strategic and operational constraints.

We model diminishing and non-monotonic returns using **tiered ROI structures**, and compare **Linear Programming (LP)** and **Mixed Integer Programming (MIP)** approaches to identify allocations that maximize ROI while remaining robust and feasible in practice.

Beyond single-period optimization, the project explores:
- Cross-evaluation across different ROI forecasts
- Platform investment caps and minimum spend requirements
- Rolling monthly reinvestment strategies
- Allocation stability over time

---

## Business Objective

Maximize total expected **Return on Investment (ROI)** subject to:
- A fixed total budget
- Strategic diversification constraints
- Platform-level spending caps
- Tier activation and sequencing logic
- Operational stability considerations

The problem mirrors real-world marketing and portfolio allocation decisions where return, risk, and feasibility must be balanced.

---

## Modeling Approach

### Linear Programming (LP)
- Assumes concave ROI functions
- Continuous decision variables for tier investments
- Computationally efficient but sensitive to ROI forecast error
- Serves as a baseline optimization model

**Objective:**  
Maximize Σ ROIᵢ × xᵢ  

Subject to budget, platform relationship, tier-bound, and optional cap constraints.

---

### Mixed Integer Programming (MIP)
- Handles non-monotonic and tier-dependent ROI
- Introduces binary variables to enforce:
  - Sequential tier activation
  - Logical investment ordering within platforms
- Produces more realistic and robust allocations

---

## Advanced Analyses

### Cross-Model Evaluation
Allocations optimized on one company’s ROI forecast are evaluated on another company’s ROI data.

**Result:**  
MIP generalizes better, with a smaller out-of-sample ROI drop (39.3%) compared to LP (48.9%).

---

### Platform Cap Sensitivity
Removing platform caps yields only modest ROI improvements (~2–3%) but leads to highly concentrated allocations. Caps meaningfully improve diversification and robustness.

---

### Minimum Spend Constraints
All-or-nothing platform participation constraints ensure baseline investment in selected platforms without materially reducing ROI.

---

### Rolling Monthly Reinvestment
A rolling MIP model reinvests 50% of monthly returns into subsequent budgets, achieving **70.8% annual growth (theoretical)**.  
However, this comes at the cost of extreme allocation volatility.

---

## Allocation Stability Analysis

Month-to-month platform spending changes were evaluated using a ±$1M stability threshold.

**Findings:**
- 32 stability violations
- Frequent full exits and re-entries into platforms
- Indicates significant operational risk despite high returns

---

## Key Results Summary

| Model | In-Sample ROI | Out-of-Sample Drop | Stability |
|------|--------------|-------------------|----------|
| LP | Higher | Large (48.9%) | Stable |
| MIP | Slightly lower | Smaller (39.3%) | Stable |
| Rolling MIP | Very high | N/A | Unstable |

**Recommended Model:**  
Mixed Integer Programming with platform caps and minimum spend constraints.

---

## Repository Structure
- Optimization_Project_2.ipynb
- annotated-RM_294_Optimization_I_Project_2.pdf
- README.md

---

## Key Takeaways

- MIP provides superior robustness under ROI uncertainty
- Platform caps improve diversification with minimal ROI loss
- Rolling reinvestment maximizes growth but sacrifices stability
- Practical optimization must balance return, robustness, and feasibility
