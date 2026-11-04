Dataset link: https://www.kaggle.com/datasets/blastchar/telco-customer-churn
---

# SaaS Unit Economics

Business Objective
The primary goal of this project is to evaluate the financial viability of a subscription-based product by forecasting Customer Lifetime Value (LTV) and predicting churn. By applying survival analysis to historical subscription data, the project models unit economics (CAC, LTV/CAC, Payback Period) and calculates mathematically safe discount margins to optimize the company's upsell strategy.

Tech Stack

Python: Data manipulation and unit economics simulation using `pandas`, `numpy`.

Survival Analysis: Kaplan-Meier estimation for right-censored churn data using `lifelines`.

Visualization: Cohort retention and survival curves using `matplotlib`.

Environment: Jupyter Notebook, Git.

### Dataset

Telco Customer Churn (from Kaggle)

Key Features:`tenure` (months active), `MonthlyCharges` (ARPU), `Contract` (subscription type), and `Churn` (target variable).

### Methodology

1. Data Preparation: Handled missing financial values, mapped categorical churn flags to binary arrays, and isolated cohorts based on contract types.
2. Kaplan-Meier Survival Analysis: Modeled customer retention probabilities over time. Unlike standard average lifespan calculations, this algorithm accounts for right-censored data (active customers who haven't churned yet), providing a highly accurate Expected Lifetime prediction.
3. Unit Economics Simulation: Integrated a 70% gross margin assumption and synthetic Customer Acquisition Costs (CAC) scaled by contract length (e.g., $60 for 1-month, $250 for 2-year). Calculated LTV, LTV/CAC Ratio, and Payback Period.
4. Tariff Strategy & Discount Modeling: Reverse-engineered the LTV formula from a baseline LTV/CAC ratio of 3.0 to determine the absolute minimum ARPU required for profitability, revealing the maximum allowable discount for long-term contract upsells.

### Key Findings & Business Insights

The Month-to-Month Paradox: Users on month-to-month plans generate the highest average monthly revenue (ARPU $66.40) but result in the lowest overall LTV ($1,693) due to rapid drop-offs (Expected Lifetime: 36.4 months).

Long-Term Contract Value: Two-year contracts yield a massive Expected Lifetime of 72.5 months. This loyalty generates an LTV of $3,083—nearly double that of monthly users—despite having the lowest monthly price ($60.77).

Capital Efficiency: All cohorts demonstrate healthy SaaS metrics (LTV/CAC > 3). However, while the Month-to-month plan recovers its $60 CAC in just 1.3 months, its absolute lifetime revenue is fundamentally limited compared to long-term plans.

### Strategic Recommendations

1. Aggressive Upsell Campaigns: The discount modeling proves the business has an enormous margin of safety. To migrate users from monthly to 1-year contracts, marketing can offer up to an 85.2% discount on the standard monthly rate before the cohort's unit economics drop below the profitable 3.0 LTV/CAC benchmark.
2. Reallocate Marketing Budget: The $3,000+ LTV of 2-year contracts justifies significantly higher acquisition costs. The company should increase its CAC limits (e.g., higher bidding caps in paid ads, extended retargeting) specifically for long-term subscription acquisitions, prioritizing absolute revenue growth over immediate payback periods.
