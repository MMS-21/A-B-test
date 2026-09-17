# A/B Test Analysis

A/B tests are very commonly performed by data analysts and data scientists. For this project, I worked through an A/B test run by an e-commerce website to determine whether the company should:

- Implement the new webpage
- Keep the old webpage
- Run the experiment longer before making a decision

## 🎯 Objective

Determine if the new landing page leads to a statistically significant increase in conversion rate compared to the old page, and provide a data-driven recommendation.

## 📊 Dataset

The analysis uses an A/B testing dataset containing user-level experiment data:

| File | Description |
|------|-------------|
| `ab_data.csv` | User-level experiment data with page assignment and conversion outcomes |
| `countries.csv` | Country metadata for user segmentation |

Key fields in `ab_data.csv`:
- `user_id` — unique user identifier
- `timestamp` — when the user was recorded
- `group` — control (old page) or treatment (new page)
- `landing_page` — which page the user saw
- `converted` — whether the user converted (0/1)

## 🔍 Methodology

1. **Data Validation** — Checked for data quality issues: misassigned users (user in one group but saw the other page), duplicate user IDs, and balanced group sizes.
2. **Exploratory Analysis** — Computed conversion rates for each group and visualized the distribution.
3. **Hypothesis Testing** — Conducted a two-proportion z-test to evaluate whether the difference in conversion rates is statistically significant.
4. **Confidence Intervals** — Computed confidence intervals around the conversion rate difference to quantify the range of plausible effects.
5. **Practical Significance** — Evaluated whether any observed difference is large enough to matter for the business.

## 📈 Key Concepts Applied

- **Null hypothesis (H₀):** The new page has no effect on conversion rate (p_new = p_old)
- **Alternative hypothesis (H₁):** The new page changes the conversion rate (p_new ≠ p_old)
- **Two-proportion z-test:** Tests whether two proportions are significantly different
- **P-value interpretation:** Probability of observing the data (or more extreme) if H₀ is true
- **Type I / Type II errors:** False positive vs false negative in the A/B test context
- **Confidence intervals:** Range of plausible values for the true difference in conversion rates

## 📂 Repository Structure

```
├── ab_data.csv                          # A/B test user-level data
├── countries.csv                        # Country reference data
├── Analyze_ab_test_results_notebook.ipynb   # Main analysis notebook
├── Analyze_ab_test_results_notebook.html    # Notebook exports as HTML
└── README.md
```

## 🛠️ Tools

Python · pandas · numpy · scipy · statistics · A/B testing · hypothesis testing

## 📌 Learnings

- Always validate A/B test data for contamination (misassigned users) before drawing conclusions
- Statistical significance does not always imply practical/business significance
- Sample size and experiment duration matter — underpowered tests can miss real effects
- Checking balance between control and treatment groups is a critical first step
