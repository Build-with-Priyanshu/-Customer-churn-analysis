# Bank Customer Churn — Statistical EDA

Exploratory data analysis of bank customer churn, using proper statistical hypothesis
testing including Chi-square tests, point-biserial correlation, and Mann-Whitney U tests to
identify which factors actually drive customer attrition.

## Overview

| Relationship type              | Method used                          |
|--------------------------------|---------------------------------------|
| Categorical vs. categorical    | Chi-square test of independence       |
| Numeric vs. binary target      | Point-biserial correlation, Mann-Whitney U |
| Churn rate comparisons         | Grouped churn-rate tables             |

## Dataset

- **Source:** [Kaggle](https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn/data)
- **Rows:** ~10,000 customers
- **Target:** `Exited` (1 = customer churned, 0 = retained)
- **Features:** Geography, Gender, Age, Tenure, Balance, NumOfProducts, HasCrCard,
  IsActiveMember, EstimatedSalary, CreditScore

## What this analysis covers

1. **Churn-rate group comparisons** across categorical variables, instead of relying
   on boxplot overlap
2. **Proper statistical tests** — Chi-square for categorical vs. categorical,
   point-biserial correlation / Mann-Whitney U for numeric vs. binary target
3. **Class imbalance check** on the target variable
4. **Investigation of the `Balance` column's zero-inflation** and its bimodal structure
5. **Feature engineering** — age bins and an interaction feature
   (`IsActiveMember x NumOfProducts`)
6. **Duplicate and outlier checks**, beyond simple null counts
7. **A consolidated churn-rate summary table** across all key categorical variables
8. **Updated, non-deprecated plotting calls** (matplotlib / seaborn)

## Key findings

- **NumOfProducts** is one of the strongest signals — churn rate at 3–4 products is
  far higher than at 1–2
- **Geography** shows a statistically significant relationship with churn (confirmed
  via Chi-square test)
- **Age** is a meaningful driver of churn, backed by a significant Mann-Whitney result
- **IsActiveMember** matters both independently and in combination with
  `NumOfProducts`
- **Balance**'s zero-inflation is a structural pattern worth encoding as a separate
  feature, not noise to average over

## Recommended next steps for modeling

1. Encode `HasZeroBalance` and `AgeBin` as explicit features alongside raw numeric columns
2. Address class imbalance in `Exited` (class weighting or stratified sampling) rather
   than optimizing for raw accuracy
3. Include `IsActiveMember x NumOfProducts` as an engineered interaction feature


## Tech stack

- Python 3.11
- pandas, numpy
- matplotlib, seaborn
- scipy (statistical tests)


## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
