### Project Title

Identifying Inconsistent SaaS Customer Discounts

**Author:** Felipe Maier

#### Executive summary

This project explores an anonymized customer dataset from a SaaS business that offers products through monthly and annual
subscriptions. The goal is to identify customers whose discounts differ substantially from those of similar peers.

The report first evaluates a linear regression model as a predictive baseline, although predicting discounts is not the
project's goal. It then groups customers with similar subscription characteristics and compares their discounts to flag
unusually high or low discounts for review.

#### Rationale

Inconsistent discounts can affect revenue and pricing decisions. Comparing similar customers can help identify unusual 
discounts that deserve further review. Managing and reviewing discounts becomes more complex as the number of customers
increases.

#### Research Question

Do customers with similar revenue, tenure, and subscription plans receive materially different discounts?

#### Data Sources

The project uses an [anonymized customer subscription dataset](data/data.csv) containing **114,440 rows and 17 columns**
before cleaning. Each row represents one customer and captures a snapshot of their discount and subscription information
at a single point in time, including revenue, tenure, and selected historical indicators covering the preceding 90 days.

| Column | Description |
|---|---|
| `customer_key` | Anonymous customer identifier |
| `mrr_net` | Monthly recurring revenue after discounts |
| `mrr_list` | Monthly recurring revenue before discounts |
| `discount_amount` | Monthly discount value |
| `discount_pct` | Discount as a proportion of list price |
| `current_depth_bucket` | Discount-depth category |
| `primary_plan_id` | Anonymous primary plan identifier |
| `primary_plan_name` | Generalized primary plan label |
| `interval` | Billing interval: monthly or yearly |
| `interval_count` | Number of billing intervals |
| `plan_count` | Number of active plans |
| `first_active_date` | Date the customer first became active |
| `tenure_days` | Days since first activity |
| `acquisition_channel` | Discount or full-price acquisition |
| `was_active_90d_ago` | Whether the customer was active 90 days earlier |
| `depth_90d_ago` | Discount proportion 90 days earlier |
| `had_coupon_in_last_90d` | Whether a coupon was used in the last 90 days |

#### Methodology

1. Checked data types, missing values, duplicates, and numeric ranges. Removed records with undefined current discounts
   or a missing acquisition channel, and reviewed unusual list prices without automatically removing them.
2. Explored discount patterns by billing interval, plan, monthly list value, and customer tenure.
3. Trained a linear regression baseline using an 80/20 train/test split, with scaling and categorical encoding fitted
   only on training data. Compared its test MAE and RMSE with predictions based on the training-set average discount.
4. Defined peer groups using plan ID, billing interval, monthly list value before discounts, plan count, and tenure band.
   Assessed only groups containing at least 10 customers.
5. Compared each customer's discount with their group median and flagged differences of at least 10 percentage points
   in either direction as candidates for review.

#### Results

- The cleaned dataset contains **114,321 customers**. Discounts concentrate around **0%, 50%, and 67%**, suggesting common
  discount tiers.
- Linear regression achieved a test **MAE of 4.63** and **RMSE of 9.46 percentage points**, compared with **23.13** and
  **25.55** for the average-discount benchmark. However, **30.42% of test predictions were negative**, limiting its
  practical use.
- Peer comparison covered **113,882 customers (99.62%)** across **170 eligible groups**. The remaining **439 customers**
  belonged to smaller groups and were not assessed.
- Most assessed customers matched their group median discount. The 10-percentage-point rule flagged **764 customers
  (0.67% of those assessed)** for review.

Peer groups and thresholds are exploratory choices. Flagged differences are not confirmed pricing errors and may reflect
promotions or other business circumstances not captured by the groups.

#### Next steps

- Review flagged cases with additional business context to understand possible explanations.
- Test alternative tenure bands, minimum group sizes, and discount-gap thresholds.
- Explore clustering as an alternative way to define peer groups.
- Compare additional regression models with the current baseline in the next project phase.

#### Outline of project

- [Initial report and EDA notebook](notebooks/01_initial_report_eda.ipynb)
- [Dataset](data/data.csv)

##### Contact and Further Information

Felipe Maier
