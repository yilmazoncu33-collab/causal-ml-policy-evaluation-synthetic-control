# Causal Policy Impact Evaluation: Synthetic Control Method (California Proposition 99)

An econometric and constrained optimization implementation of the **Synthetic Control Method (Abadie et al., 2010)** to evaluate the causal impact of California's 1988 tobacco control legislation (Proposition 99) on per-capita cigarette consumption.

## Methodology
1. **Constrained Convex Optimization:** Constructed a "Synthetic California" from a clean donor pool of US states using Sequential Least Squares Programming (`SLSQP`) subject to non-negativity ($w_i \ge 0$) and convexity ($\sum w_i = 1$) constraints, preventing overfitting observed in unconstrained Ridge regression.
2. **Counterfactual Analysis:** Tracked post-intervention divergence between actual California consumption and its synthetic counterfactual across 1989–1992.
3. **In-Space Placebo Inference:** Conducted permutation-based placebo tests across all valid donor states (filtering out units with pre-treatment RMSE $> 2\times$ California's pre-treatment RMSE) to establish statistical significance.

## Key Findings
* **Synthetic Weights:** Pre-1988 California consumption was replicated primarily by Illinois (`44.2%`), Utah (`33.2%`), Delaware (`11.4%`), and Nevada (`11.2%`).
* **Causal Treatment Effect:** Proposition 99 reduced annual per-capita cigarette sales by an average of **11.12 packs** during 1989–1992, reaching a cumulative reduction of **14.41 packs (-17.6%)** by 1992.
* **Statistical Significance:** Ranked **1st out of 35** states in post-treatment consumption drop ($p = 0.029$).
