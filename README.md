# E-commerce Customer & Order Analysis (Intermediate Level)

Customer behaviour, retention and revenue analysis of an e-commerce store using **Python (pandas, matplotlib)** and an **Excel dashboard**: cleaning, RFM segmentation, cohort retention, revenue concentration, seasonality and data-backed recommendations.
Project for the **ShadowFox Data Analyst Internship – Intermediate Level**.

## Business Questions
1. How is revenue trending and is there seasonality?
2. How many customers come back, and which acquisition channels bring the best customers?
3. Is revenue concentrated in a few customers?
4. Which customer segments matter most and who is at risk of leaving?
5. Which categories, discounts and regions help or hurt profit?
6. What should the business do next?

## Dataset
- `raw_ecommerce_orders_intermediate.csv` – 2,454 raw orders from about 900 customers, Jan 2024 – Dec 2025 (INR).
- 19 columns: customer details (Age_Group, Gender, Acquisition_Channel, Region, City), product details (Category, Product, Price, Cost) and order details (Discount, Shipping, Payment_Mode, Order_Status, Delivery_Days, Rating).
- **Note:** this is a synthetic practice dataset created for learning, not real company data.

## Project Files
| File | Description |
|---|---|
| `raw_ecommerce_orders_intermediate.csv` | Original messy data |
| `intermediate_customer_analysis.ipynb` | Full analysis notebook (also available as `.py`) |
| `cleaned_ecommerce_orders.csv` | Cleaned data (created by the notebook) |
| `customer_rfm_segments.csv` | One row per customer with R, F, M scores and segment |
| `intermediate_analysis_summary.xlsx` | Summary tables exported by the notebook |
| `Intermediate_Dashboard.xlsx` | Excel dashboard: KPIs, 8 charts, cohort heatmap, insights, recommendations |
| `charts/` | Chart images exported by the notebook |

## Data Cleaning
| Problem | Fix |
|---|---|
| 30 duplicate rows | Removed |
| Inconsistent text and case in Category, Region, Status, Channel, City, Customer_ID | Trimmed and standardised |
| Dates in 3 formats | Converted to one date type |
| Missing Region | Filled from the same City |
| Missing Age_Group | Filled from the same customer's other orders |
| Missing Payment_Mode | Filled with "Unknown" |
| Missing Discount_Pct | Filled with 0 (assumption) |
| Invalid ratings (0, 6, 9) | Set to blank |
| 6 rows with negative quantity | Removed |
| 4 Unit_Price typos (10x) | Replaced with the product's median price |

Result: 2,454 raw rows → **2,418 clean rows**.

**Metric definitions:** Revenue = Quantity × Unit_Price × (1 − Discount%). Profit = Revenue − product cost − shipping cost. Only **Delivered** orders count as revenue (cancelled orders earn nothing, returned orders are refunded).

## Key Metrics
| KPI | Value |
|---|---|
| Revenue | ₹52.9 lakh |
| Profit | ₹23.0 lakh (margin 43.4%) |
| Delivered orders | 2,128 |
| Customers | 856 |
| Average order value | ₹2,488 |
| Repeat customers | 56.5% |
| Return rate | 8.5% |

## Analysis Done
- Monthly revenue, 2024 vs 2025 comparison, seasonality index
- New vs returning customer revenue
- Quarterly cohort retention heatmap
- RFM segmentation (Champions, At Risk, Lost, etc.)
- Revenue concentration (Pareto)
- Channel, age and gender segment performance
- Inactive (churn-like) customers
- Category profit and return rate, discount impact
- Regional performance, delivery days vs rating

## Key Insights
1. **Seasonality:** November and December are the strongest months; Q4 brings about 36% of revenue. Revenue grew 73.5% from 2024 to 2025, mostly because more customers were acquired.
2. **Retention is the main lever:** 43.5% of customers buy only once; returning customers generate about 60% of revenue.
3. **Channel quality:** Referral customers repeat 76.5% of the time vs 42.6% for Paid Ads.
4. **Concentration:** the top 20% of customers generate about 51% of revenue. Champions are 19.5% of customers but 39.4% of revenue.
5. **Win-back opportunity:** 123 "At Risk (Loyal)" customers hold about 25% of revenue but have been inactive for months.
6. **Discounts hurt profit:** margin falls from 48.6% (no discount) to 26.7% (30% discount) while basket size does not grow.
7. **Fashion returns** are high at 15.5% versus 2.6–9% for other categories.
8. **East region** has the slowest delivery (6.3 days) and the lowest rating (about 3.5); delivery days and rating are negatively correlated (about −0.38).

## Business Recommendations
- Stock up and start campaigns in October for the Nov–Dec peak; plan a Jan–Feb offer to fill the dip.
- Send a post-purchase email/WhatsApp flow 30–45 days after the first order and start a loyalty scheme.
- Shift part of the paid-ads budget to referral and email programmes.
- Run a win-back campaign for "At Risk (Loyal)" customers; give Champions VIP perks.
- Cap discounts at around 15% except for clearance; use bundles or free-shipping thresholds instead.
- Reduce Fashion returns with size guides and better product pages; improve East-region delivery.

## Limitations
- Synthetic data; patterns are built for practice.
- Revenue growth is driven mainly by new-customer acquisition.
- Recent customers have had less time to repeat, so their repeat rate is understated.
- The 120-day inactivity threshold and "missing discount = 0%" are assumptions.


## How to Run
1. Clone the repo and keep the files in one folder.
2. Install the libraries: `pip install pandas numpy matplotlib openpyxl`
3. Open `intermediate_customer_analysis.ipynb` in Jupyter, VS Code or Google Colab and click **Run All**.
4. Open `Intermediate_Dashboard.xlsx` in Excel to view the dashboard.

## Tools Used
Python · pandas · NumPy · Matplotlib · Jupyter Notebook · Microsoft Excel (SUMIFS, COUNTIFS, AVERAGEIFS, charts, conditional formatting)

