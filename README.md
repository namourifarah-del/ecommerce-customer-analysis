<div align="center">

# Behind the Orders
### E-commerce sales, repeat purchases & returns

An online store’s data, explored through SQL and a few business questions.

**SQL · BigQuery · Python · pandas · matplotlib**

[Explore the notebook →](ecommerce_customer_analysis.ipynb)

</div>

---

## What brings customers back?

After completing Kaggle’s Intro to SQL course, I wanted to work through
an analysis of my own.

I used TheLook’s synthetic e-commerce dataset to explore three questions:
Which categories bring in the most revenue? How many customers buy
again? And where do returns deserve a closer look?

The analysis covers orders placed in **2025**.

## The numbers

| Completed sales revenue | Eligible orders | Customers | Average order value |
|:---:|:---:|:---:|:---:|
| **588,586.77** | **6,869** | **6,603** | **85.69** |

**9,886 completed items** · **258 repeat customers** · **3.91% repeat purchase rate**

## Three things that stood out

### 01 — The biggest revenue category wasn’t the biggest seller

**Outerwear & Coats** led completed sales revenue at **73,213.99**,
followed by **Jeans** at **67,202.89**.

Meanwhile, **Intimates** had the highest completed-item count, at **751**.
Looking at both revenue and volume gives a fuller picture of category
performance.

**What I would explore next:** margins and stock availability in the
leading categories before recommending more promotional spending.

### 02 — Most customers made one eligible purchase during the year

Of **6,603 customers**, **258** placed at least two eligible orders in
2025. That puts the repeat purchase rate at **3.91%**.

This gives us a starting point for investigating repeat buying.
Customers who purchased near the end of the year had less time to
return within the analysis period.

**What I would test:** a follow-up campaign after the first completed
purchase, measuring whether it increases second purchases.

### 03 — Return volume and return rate tell different stories

**Leggings** had the highest return rate at **35.10%**, with **86**
returned items.

**Sleep & Lounge** had a slightly lower rate of **34.40%**, but accounted
for **300 returns**, the largest return count across categories.

That makes Sleep & Lounge a useful starting point for further investigation.

**What I would investigate:** return reasons, product-level patterns,
and whether sizing guidance or descriptions need attention.

## How I approached it

1. Explored the tables, columns, date range, and order statuses.
2. Checked completed items for conflicting return information.
3. Defined which items qualified for the sales analysis.
4. Used SQL joins and aggregations to calculate the metrics.
5. Created category revenue and return-rate charts in Python.
6. Reconciled the totals before writing recommendations.

The notebook includes the queries, comments, saved outputs, and charts.

## A few definitions matter

| Metric | Definition used |
|---|---|
| Completed sales revenue | Sum of completed-item sale prices, with no item return date, excluding cancelled or returned orders |
| Eligible orders | Distinct orders contributing to completed sales revenue |
| Average order value | Completed sales revenue divided by eligible orders |
| Repeat purchase rate | Customers with at least two eligible orders divided by all eligible customers within 2025 |
| Category return rate | Returned items divided by completed plus returned items in that category |

The analysis uses **order creation dates** to select 2025 orders.
Statuses reflect the records when the queries ran.

## Checks before conclusions

- [x] Category revenue reconciles with total completed sales revenue.
- [x] Category item counts reconcile with the sales summary.
- [x] Customer counts agree between the sales and repeat purchase analyses.

The initial status-quality check uses item creation dates, so its scope
differs slightly from the order-date-based analysis.

## Read or run the project

**To read:** open [the notebook](ecommerce_customer_analysis.ipynb).
The saved outputs let you follow the analysis without running queries.

**To run:**

1. Open the notebook in Google Colab.
2. Replace the project ID in `bigquery.Client(...)` with your own
   Google Cloud project ID.
3. Complete Google authentication.
4. Run the cells from top to bottom.

Queries are capped at **1 GB processed per query**.

**Data source:** `bigquery-public-data.thelook_ecommerce`

## Context behind the results

TheLook is a **synthetic dataset**. The findings describe this dataset
and provide practice in making business decisions from data.

Repeat purchases are measured within one calendar year. The analysis
does not track retention at a fixed interval after each customer’s
first purchase.

Return reasons and full accounting records are unavailable.
Revenue here follows the completed-item definition above.

The public dataset can change, so future runs may produce different results.

---

**Farah Namouri**  
Built after completing Kaggle’s Intro to SQL course.
