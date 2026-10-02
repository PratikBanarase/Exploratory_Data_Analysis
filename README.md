# Exploratory Data Analysis – Retail Customers

An end-to-end exploratory data analysis (EDA) of a 1,000-row retail customer and purchase dataset. The notebook profiles the data, visualises distributions, relationships and trends, and turns the results into business insights and recommendations.

## Project Structure

```
.
├── Exploratory_Data_Analysis.ipynb   # Main analysis notebook
├── eda_retail_customers.csv          # Input dataset (must be added by you)
├── figures/                          # Auto-generated charts (PNG / HTML)
├── eda_findings.md                   # Auto-generated summary of insights
└── README.md
```

> `figures/` and `eda_findings.md` are created automatically when the notebook is run.

## Dataset

`eda_retail_customers.csv` – 1,000 rows × 16 columns, one row per customer purchase.

| Column | Type | Description |
|---|---|---|
| `customer_id` | text | Unique customer ID |
| `age` | int | Customer age (18–65) |
| `gender` | category | Female / Male |
| `city` | category | 6 cities (e.g. Mumbai, Pune, Delhi, Bengaluru, Nashik) |
| `annual_income` | float | Annual income (Rs) |
| `membership` | category | Basic / Silver / Gold |
| `product_category` | category | 6 categories (e.g. Electronics, Clothing, Grocery, Sports, Beauty, Home & Kitchen) |
| `quantity` | int | Units purchased |
| `discount_pct` | int | Discount applied (0–35%) |
| `purchase_amount` | float | Order value (Rs) |
| `payment_method` | category | 5 methods (e.g. UPI, Cash on Delivery) |
| `purchase_date` | date | Date of purchase (2025) |
| `visits_per_month` | float | Store/site visits per month |
| `days_since_last_purchase` | int | Recency of previous purchase |
| `satisfaction_score` | float | Rating from 1 to 5 |
| `returned` | category | Yes / No |

**Data quality:** no duplicate rows. Missing values: `annual_income` (20), `visits_per_month` (10), `satisfaction_score` (30). Rows are kept and missing values are skipped in statistics and plots; impute only if moving on to modelling.

## Analysis Steps

1. **Load and inspect** – head, dtypes, shape, duplicates, missing values
2. **Descriptive statistics** – mean, median, std, quartiles, IQR, skewness
3. **Distributions** – histograms with KDE; log-scale view of the heavily skewed `purchase_amount`
4. **Correlations** – Pearson heatmap, strongest pairs, plus Spearman for skewed data
5. **Box plots** – by category, membership, city and payment method; IQR outlier counts
6. **Time trends** – monthly revenue, orders and average order value; category trends; rolling average; quarterly share
7. **Group-by analysis** – category, membership, payment method and city summaries
8. **Scatter plots** – age vs income, income vs purchase, quantity vs purchase, discount vs satisfaction, pairplot
9. **Data-driven insights** – computed programmatically, not hard-coded
10. **Conclusions and recommendations** – exported to `eda_findings.md`

## Key Findings

- **Revenue is concentrated in Electronics** – 23% of orders but 57% of revenue; the top three categories bring in 82%.
- **Membership drives spend** – median order value is about 1.5x higher for Gold than Basic members, and Gold members visit more often (4.7 vs 3.2 per month).
- **Returns are a Clothing problem** – 14.4% return rate vs 6.1% overall.
- **Cash on Delivery customers are less satisfied** – 3.37 vs 3.65 for other payment methods.
- **Modest Q4 seasonality** – Q4 delivers 30% of revenue (27% excluding the top 1% of orders); one very large order of about Rs 531,000 inflates December.
- **Customer value varies by city** – Gold share ranges from 14% (Nashik) to 39% (Mumbai).
- **Income tracks age (r = 0.75)** but only weakly predicts order size (Spearman r = 0.23).
- `purchase_amount` is highly right-skewed (skew ≈ 7.1), so medians describe the typical customer better than means.

## Recommendations (summary)

1. Protect Electronics while cross-selling other categories to reduce dependence.
2. Invest in the membership ladder and target high-income Silver customers for upgrades.
3. Reduce Clothing returns with better size guides, photos and fit reviews.
4. Improve the COD experience and nudge customers toward UPI.
5. Prepare for a modest Q4 lift with high-ticket stock and bundles.
6. Use discounts selectively, since they correlate only weakly with satisfaction.

## Requirements

- Python 3.8+
- `numpy`, `pandas`, `matplotlib`, `seaborn`
- `plotly` (optional – enables interactive charts saved as HTML)

```bash
pip install numpy pandas matplotlib seaborn plotly jupyter
```

## How to Run

1. Place `eda_retail_customers.csv` in the same folder as the notebook.
2. Launch Jupyter and open the notebook:
   ```bash
   jupyter notebook Exploratory_Data_Analysis.ipynb
   ```
3. Run all cells from top to bottom.

The notebook can also be run in Google Colab – upload the CSV to the session storage first.

## Outputs

- `figures/01_histograms_kde.png` … `figures/11_pairplot.png` – static charts
- `figures/scatter_interactive.html` and other interactive charts (if Plotly is installed)
- `eda_findings.md` – insights, conclusions and limitations in Markdown

## Limitations

- A few missing values are ignored rather than imputed.
- Correlation does not imply causation.
- Only one year of data, so repeat seasonality cannot be confirmed.
- Group differences should be validated with significance tests before major business decisions.
