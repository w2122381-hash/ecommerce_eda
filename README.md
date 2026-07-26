# E-Commerce Customer Behavior & Sales Trends Analysis

Exploratory Data Analysis on ~530K transactions from a UK-based online retailer (Dec 2010–Dec 2011). Goal: uncover purchasing patterns, segment customers by value, and turn raw transaction logs into decisions a business can act on.

---

## Key Findings

- **4,334 unique customers generated $10.27M in revenue.**
- **Champions (19.4% of customers) drive 63.5% of total revenue** — a strong Pareto effect, and the core insight of this project.
- **Order volume peaks at 12 PM**, with **Thursday** as the busiest day of the week.
- **Saturday has zero recorded orders** — a strong signal this dataset reflects a B2B/wholesale operation, not 24/7 consumer retail.
- **Revenue peaks sharply in November**, nearly 2x the yearly baseline — consistent with holiday-season demand. (December excluded from trend analysis — data collection ends Dec 9, 2011.)
- Champions don't buy different products than everyone else — they buy the **same top-sellers, more often**. Loyalty here is about repeat purchasing, not niche taste.

---

## What Was Done

**Data Cleaning**
- Removed non-product line items (postage, fees, manual adjustments) that were skewing revenue figures.
- Isolated 9,239 cancelled-order rows (negative quantity) into a separate dataset rather than silently dropping them.
- Handled missing `CustomerID` (~25% of rows) as a distinct guest-checkout cohort instead of deleting them.

**Feature Engineering**
- `TotalRevenue`, `PurchaseHour`, `DayOfWeek`, `YearMonth` derived from raw transaction fields.

**RFM Segmentation**
- Scored every customer 1–5 on Recency, Frequency, and Monetary value (quantile-based).
- Segmented into 6 groups: Champions, Loyal Customers, Potential Loyalist, At Risk, Lost, New Customers.

**Analysis**
- Time-of-day and day-of-week order volume trends
- Monthly revenue seasonality
- Top/worst performing products by revenue and order frequency
- Revenue and product-preference breakdown by customer segment

---

## Business Recommendations

1. **Loyalty program for Champions.** They're under 20% of customers but nearly two-thirds of revenue — even small retention improvements here have outsized impact.
2. **Time-targeted promotions around 12 PM–3 PM and Thursdays**, when natural order volume is already highest.
3. **Build Q4 inventory buffers**, especially for top-selling décor/seasonal SKUs, ahead of the November demand spike.
4. **Re-engagement campaign for "At Risk" customers** (637 people) before they fully churn into "Lost."

---

## Tech Stack

Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

---

## Repository Structure

```
├── data/
│   └── online_retail.csv
├── notebooks/
│   └── ecommerce_eda.ipynb
├── README.md
└── requirements.txt
```

---

## How to Run

```bash
git clone https://github.com/w2122381-hash/ecommerce_eda
cd ecommerce_eda
pip install -r requirements.txt
jupyter notebook notebooks/ecommerce_eda.ipynb
```

---

## Notes on Process

This project was built while learning pandas/EDA workflows, with AI-assisted guidance for debugging and concept explanations along the way — including working through a kernel-state bug that temporarily hid 9,239 cancelled orders, and a column-collision error during a merge step. Both are left visible in the notebook as part of the actual analysis process, not edited out.
