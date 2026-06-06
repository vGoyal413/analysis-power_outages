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

The bar chart below shows the number of outages per month. Summer months (June, July, August) tend to have more outages than winter months (December, January, February):


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

The pivot table below shows the number of outages per month in each climate region:

| CLIMATE.REGION | Jan | Feb | Mar | Apr | May | Jun | Jul | Aug | Sep | Oct | Nov | Dec |
|----------------|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
| Central | 26 | 10 | 5 | 15 | 22 | 36 | 30 | 21 | 7 | 8 | 10 | 9 |
| East North Central | 12 | 5 | 10 | 11 | 10 | 21 | 21 | 13 | 9 | 7 | 9 | 10 |
| Northeast | 33 | 36 | 26 | 19 | 26 | 42 | 39 | 31 | 22 | 43 | 18 | 14 |
| Northwest | 14 | 13 | 12 | 10 | 7 | 11 | 13 | 14 | 7 | 4 | 7 | 20 |
| South | 16 | 15 | 13 | 27 | 23 | 31 | 23 | 32 | 18 | 9 | 6 | 14 |

## Assessment of Missingness
### NMAR Analysis
The `OUTAGE.DURATION` column may be Not Missing At Random (NMAR) becaues any outages that were ongoing when the data was collected would not have a recorded duration time.
### Missingness Dependency
Permutation tests were used to determine whether or not missingness of `OUTAGE.DURATION` depends on any other columns. The test statistic of choice was TVD.
- **Dependent on `CAUSE.CATEGORY`:** Observed TVD = 0.1636, p-value = 0.0. Since the p-value < 0.05, it can be concluded that the missingness of `OUTAGE.DURATION` is dependent`CAUSE.CATEGORY`.
- **Independent of `MONTH`:** Observed TVD = 0.0909, p-value = 0.2574. Since the p-value > 0.05, it can be concluded that the missingness of `OUTAGE.DURATION` is independent of `MONTH`.



## Hypothesis Testing
### Test 1: Are outages equally likely to occur each month?
- **Null Hypothesis:** Outages are equally likely to occur during each month.
- **Alternate Hypothesis:** Outages are not equally likely to occur during each month.
- **Test Statistic:** TVD
- **Observed TVD:** 0.1086
- **P-value:** 0.0
- **Conclusion:** Since the p-value < 0.05, the null hypothesis is rejected. The data suggests that the occurence of outages is not equally likely to occur during each month.

### Test 2: Do outages last longer in winter than in the summer?
- **Null Hypothesis:** Outages last the same amount of time in summer and winter.
- **Alternative Hypothesis:** Outages last longer in winter (Dec–Feb) than in summer (Jun–Aug).
- **Test Statistic:** Difference in mean outage duration (Winter months − Summer months)
- **Observed Difference:** 862.82 minutes
- **P-value:** 0.0166
- **Conclusion:** Since the p-value < 0.05, the null hypothesis is rejected. The data suggests that outages tend to last longer in winter than in summer. However, it is important to note that the reason that outages last longer in the winter cannot be concluded.
## Framing a Prediction Problem

## Baseline Model

## Final Model

## Fairness Analysis
