Name: Vedika Goyal

---

## Introduction
The dataset consists of information about major power outages around the continental U.S. from January 2000 to July 2016. Each row contains details of a single outage affecting one state.

**Question: When do major power outages tend to occur?**

Understanding when outages are most likely to happen helps in managing utility planning and emergency response. The relevant columns are:

| Column | Description |
|--------|-------------|
| `MONTH` | Month in which the outage occurred (1–12) |
| `YEAR` | Year in which the outage occurred |
| `CLIMATE.REGION` | U.S. climate region of the affected state |
| `CAUSE.CATEGORY` | General cause of the outage |
| `OUTAGE.DURATION` | Duration of the outage (minutes) |
| `CUSTOMERS.AFFECTED` | Number of customers affected |

---

## Data Cleaning and Exploratory Data Analysis

Multiple steps were required to clean the raw dataset:
- Two individual columns (date and time) were combined into single datetime columns: `OUTAGE.START` and `OUTAGE.RESTORATION`.
- The original individual columns were dropped.
- Any metadata rows that were not relevant for the analysis were dropped.

The bar chart below shows the number of outages per month. Summer months (June, July, August) tend to have more outages than winter months (December, January, February).


<iframe
  src="assets/outages-by-month.html"
  width="800"
  height="500"
  frameborder="0"
></iframe>

<iframe
  src="assets/outages-by-region.html"
  width="800"
  height="500"
  frameborder="0"
></iframe>
## Assessment of Missingness

## Hypothesis Testing

## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis
