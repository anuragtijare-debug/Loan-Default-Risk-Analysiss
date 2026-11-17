# Loan Default Risk Analysis Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Measures-blue)
![Power Query](https://img.shields.io/badge/Power%20Query-ETL-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

A five-page Power BI dashboard that analyzes loan default risk across borrower profiles, credit behavior, income, debt load, and portfolio value, using **~255K loan records (2013 – 2018)**.

---

## 📑 Table of Contents

- [About This Project](#about-this-project)
- [Business Problem](#business-problem)
- [Business Questions](#business-questions)
- [Dataset Overview](#dataset-overview)
- [Project Structure](#project-structure)
- [Methodology](#methodology)
- [Dashboard Walkthrough](#dashboard-walkthrough)
  - [1. Executive Overview](#1-executive-overview)
  - [2. Risk Analysis](#2-risk-analysis)
  - [3. Customer Analysis](#3-customer-analysis)
  - [4. Financial Analysis](#4-financial-analysis)
  - [5. Default Prediction](#5-default-prediction)
- [Key Findings](#key-findings)
- [Business Recommendations](#business-recommendations)
- [Technical Specifications](#technical-specifications)
- [How to Review the Project](#how-to-review-the-project)
- [Limitations](#limitations)
- [Author](#author)

---

## About This Project

Loan default directly affects profitability and portfolio quality for banks, NBFCs and lending companies. This project turns borrower-level loan data into an interactive dashboard that shows **who defaults, how often, and why**, so lending decisions can be backed by data.

The project demonstrates:

- **Data preparation:** cleaning and transforming the dataset with Power Query.
- **Segmentation:** calculated columns for age, income, DTI, interest-rate and credit-score groups.
- **KPI design:** DAX measures for portfolio size, default rate and averages.
- **Dashboard design:** five themed pages with consistent navigation, a year slicer and a reset button.
- **Business interpretation:** each page is turned into findings and recommendations.

## Business Problem

A high default rate hurts profitability, increases risk exposure and lowers portfolio quality. Looking at one overall default number hides which customers drive it. This dashboard breaks the default rate down by borrower and loan characteristics to locate the risky segments.

## Business Questions

1. What is the overall default rate, and how has it moved over the years?
2. Which borrower segments (age, income, employment, marital status) are the riskiest?
3. How do DTI ratio and credit score relate to default?
4. Which loan purposes carry the most risk?
5. What does the portfolio look like in loan value, interest rates and loan size?
6. What actions can reduce future defaults?

## Dataset Overview

| Attribute | Details |
|---|---|
| Records | ~255K loans |
| Period | 2013 – 2018 |
| Source format | CSV / Excel |
| Target variable | `Default` (1 = defaulted, 0 = performing) |
| Download | [Google Drive](https://drive.google.com/file/d/1LxdlX7Yh6IrifvobCMpdk9i0jH-raSqF/view?usp=sharing) – see [`Dataset/README.md`](Dataset/README.md) |

| Column | Description |
|---|---|
| Loan ID | Unique identifier for each loan |
| Age | Age of the borrower |
| Income | Annual income of the borrower |
| Loan Amount | Loan amount sanctioned |
| Credit Score | Borrower credit score |
| Months Employed | Employment duration in months |
| Number of Credit Lines | Number of existing credit lines |
| Interest Rate | Interest rate charged on the loan |
| Loan Term | Repayment duration |
| DTI Ratio | Debt-to-income ratio |
| Education | Education level |
| Employment Type | Full-time, Part-time, Self-employed, Unemployed |
| Marital Status | Single, Married, Divorced |
| Has Mortgage | Whether the borrower has a mortgage |
| Has Dependents | Whether the borrower has dependents |
| Loan Purpose | Home, Business, Education, Auto, Other |
| Has Co-Signer | Whether the loan has a co-signer |
| Default | Target variable indicating loan default |

## Project Structure

```
Loan-Default-Risk-Analysis/
│
├── README.md
│
├── Dataset/
│   └── README.md              # Google Drive download link
│
├── Power BI/
│   └── README.md              # place the .pbix file here
│
└── Screenshots/
    ├── 01_Overview.png
    ├── 02_Risk_Analysis.png
    ├── 03_Customer_Analysis.png
    ├── 04_Financial_Analysis.png
    └── 05_Default_Prediction.png
```

## Methodology

1. **Import & review:** loaded the loan dataset and checked column names, data types and field meanings.
2. **Clean & transform (Power Query):** fixed data types and prepared fields for analysis.
3. **Segment (calculated columns):** created groups for age, income, DTI, interest rate and credit-score risk.
4. **Measure (DAX):** built KPI measures such as total loans, total portfolio, average loan amount and default rate.
5. **Visualize:** designed five pages with a left navigation panel, a **Year** slicer and a **Reset** button.
6. **Interpret:** converted each page into findings and recommendations.

### Segment Definitions

| Segment | Groups |
|---|---|
| Age group | 18–25, 26–35, 36–45, 46–55, 56–69 |
| Income group | <30K, 30–60K, 60–90K, 90–120K, 120K+ |
| DTI group | <20%, 20–40%, 40–60%, 60–80%, >80% |
| Interest-rate group | 2–7%, 7–12%, 12–17%, 17–22%, 22–25% |

| Credit Risk Category | Credit Score |
|---|---|
| Low Risk | 700+ |
| Medium Risk | 600–699 |
| High Risk | 500–599 |
| Critical Risk | Below 500 |

### Core KPIs

| KPI | Description |
|---|---|
| Total Portfolio | Total value of loans issued |
| Total Loans | Number of loans |
| Avg Loan Amount | Average sanctioned loan amount |
| Default Rate % | Share of loans that defaulted |
| Non-Default Rate % | Share of loans that are performing |

---

## Dashboard Walkthrough

### 1. Executive Overview

![Executive Overview](Screenshots/01_Overview.png)

**What this page shows:** a high-level health check of the whole portfolio. Five KPI cards sit on top, followed by yearly trends, the default vs non-default split, loan value by purpose, and default rate by credit-risk type.

**KPI cards**

| Metric | Value |
|---|---|
| Total Portfolio | $32.58B |
| Total Loans | 255K |
| Avg Loan Amount | $127.6K |
| Default Rate | 11.61% |
| Non-Default Rate | 88.39% |

**Chart-by-chart reading**

- **Loans & Default Counts by Year:** yearly loan volume stays in a narrow range, and default counts move up and down with it.
- **Default Trend Over Years:** the default rate is stable between **11.50% and 11.75%** across 2013–2018. It peaked at 11.75% in 2016 and dipped to 11.50% in 2014 and 2017.
- **Default vs Non-Default Rate:** about **1 in 9 loans** (11.61%) defaults; 88.39% perform.
- **Loan Amount by Loan Purpose:** Home, Business, Education and Auto each hold about 7bn, and Other about 6bn, so the portfolio is spread evenly across purposes.
- **Loans & Default Rate by Risk Type:** the default rate falls as credit quality improves, from the highest at **Critical Risk** to the lowest at **Low Risk**.

**Insight:** the overall default rate is steady over time, so the risk is driven by *who* the borrowers are, not by *when* the loan was issued. The following pages identify those segments.

---

### 2. Risk Analysis

![Risk Analysis](Screenshots/02_Risk_Analysis.png)

**What this page shows:** how default rate changes with employment type, loan purpose, age and DTI, plus the size of each credit-score segment.

**KPI cards**

| Card | Value | Meaning |
|---|---|---|
| High Risk (500–599) | 46K | Loans in the high-risk credit-score band |
| Critical Risk (<500) | 93K | Loans in the critical credit-score band |
| Low Risk (700+) | 69K | Loans in the low-risk credit-score band |
| Unemployed default | 13.55% | Default rate of unemployed borrowers |

**Chart-by-chart reading**

- **By Employment Type:** Unemployed **13.55%** > Part-time 11.97% > Self-employed 11.46% > Full-time **9.46%**. Stable full-time employment is linked to the lowest default rate.
- **By Loan Purpose:** Business **12.33%** is highest; Auto 11.88%, Education 11.84% and Other 11.79% are close together; Home **10.23%** is lowest.
- **By Age Group:** a steep fall with age, from **20.76%** (18–25) to 16.08%, 11.55%, 8.45% and **5.50%** (56–69).
- **By DTI Group:** the default rate rises from **10.36%** (<20%) to about **12.2%** at 60–80% and above, then levels off.

**Insight:** age is the strongest differentiator on this page (about 4x between youngest and oldest). Employment, loan purpose and DTI have a smaller but consistent effect.

---

### 3. Customer Analysis

![Customer Analysis](Screenshots/03_Customer_Analysis.png)

**What this page shows:** who the borrowers are and how default rate varies by income, marital status and mortgage status.

**KPI cards**

| Metric | Value |
|---|---|
| Avg Borrower Age | 44 |
| Married Borrowers | 85K |
| With Mortgage | 128K |
| With Dependents | 128K |
| With Co-Signer | 128K |

**Chart-by-chart reading**

- **Loans Count by Age Group:** 56–69 is the largest group (69K) and 18–25 the smallest (39K). The riskiest age group is therefore also the smallest.
- **Default Rate by Income Group:** the sharpest pattern in the project. It drops from **21.96%** for incomes below 30K to 12.78% (30–60K), 10.16% (60–90K), 9.30% (90–120K) and **9.03%** (120K+).
- **Borrower Distribution by Education:** Bachelor's, High School, Master's and PhD are roughly balanced.
- **Default Rate by Mortgage Status:** the split between borrowers with and without a mortgage is nearly even.
- **Default Rate by Marital Status:** Divorced **12.53%** > Single 11.91% > Married **10.40%**.

**Insight:** low income is the single biggest warning sign, and the benefit of higher income flattens out after about 90K. Married borrowers default less than single or divorced borrowers.

---

### 4. Financial Analysis

![Financial Analysis](Screenshots/04_Financial_Analysis.png)

**What this page shows:** the money side of the portfolio: loan size, interest rates and value over time.

**KPI cards**

| Metric | Value |
|---|---|
| Max Loan Amount | $250K |
| Min Loan Amount | $5K |
| Min Interest Rate | 2.00% |
| Max Interest Rate | 25.00% |
| Avg Loan Amount | $127.6K |

**Chart-by-chart reading**

- **Avg Amount by Education:** PhD and Master's borrowers have slightly higher average loans than High School and Bachelor's. The y-axis is zoomed in (about 127.0K–127.8K), so the real difference is small.
- **Total Amount Over Years:** yearly loan value stays between about **5.37bn and 5.46bn** (2013: 5.457bn, 2014: 5.373bn, 2015–2016: 5.443bn, 2017: 5.384bn, 2018: 5.477bn).
- **Total Loans by Rate Group:** loans are spread evenly across 2–7%, 7–12%, 12–17% and 17–22% (about 55–56K each), with fewer in the 22–25% band (33K).
- **Default Rate by Income:** repeats the income pattern (21.96% → 9.03%) next to the financial view.

**Insight:** the portfolio is balanced in size and pricing and shows no year-on-year growth shock. Loan sizes range widely ($5K–$250K) but the average is similar across education levels.

---

### 5. Default Prediction

![Default Prediction](Screenshots/05_Default_Prediction.png)

**What this page shows:** a risk-scoring view that combines the strongest drivers into one place, with a segment table ranked by risk level.

**KPI cards**

| Metric | Value |
|---|---|
| Overall Default Probability | 11.61% |
| Young Borrower Risk (18–25) | 20.76% |
| Senior Borrower Risk (56–69) | 5.50% |

**Segment-wise risk table**

| Segment | Segment Count | Default % | Risk |
|---|---|---|---|
| Income <30K | 28,405 | 22.00% | 🔴 Critical |
| Age 18–25 | 39,016 | 20.80% | 🔴 Critical |
| Unemployed | 63,824 | 13.60% | 🟡 High |
| Score <500 | 93,029 | 12.80% | 🟡 High |
| No Co-Signer | 127,646 | 12.90% | 🟡 High |
| Home Loan | 51,286 | 10.20% | 🟢 Low |
| Divorced | 85,033 | 12.50% | 🔵 Medium |
| Business Loan | 51,298 | 12.30% | 🔵 Medium |

*(Table percentages are rounded to one decimal in the dashboard.)*

**Insight:** the two **Critical** segments are low income and young age. The **High** segments are the largest in size (for example No Co-Signer with about 128K loans and Score <500 with about 93K), so they matter most for total exposure. Home loans are the only segment rated Low risk.

> **Note:** the "default probability" shown here is the *observed historical default rate*. It is not the output of a predictive model.

---

## Key Findings

1. **The overall default rate is 11.61% and very stable** (11.50%–11.75%) across 2013–2018.
2. **Age is the strongest driver:** 18–25 defaults at 20.76% vs 5.50% for 56–69.
3. **Income is the second strongest:** below 30K defaults at 21.96% vs 9.03% for 120K+.
4. **Employment matters:** unemployed 13.55% vs full-time 9.46%.
5. **DTI shows a clear upward trend** from 10.36% (<20%) to about 12.2% (60%+).
6. **Business loans are the riskiest purpose** (12.33%); **home loans the safest** (10.23%).
7. **Marital status:** divorced 12.53%, single 11.91%, married 10.40%.
8. **Lower credit-score bands show higher default rates**, and the Critical band (<500) holds about 93K loans.

## Business Recommendations

1. **Tighten underwriting for young borrowers (18–25).** Add income and employment verification.
2. **Review limits for borrowers earning below $30K.** Reconsider loan limits and approval thresholds for this group.
3. **Encourage co-signers for high-risk profiles.** The large no-co-signer group (about 128K loans) defaults at 12.9%.
4. **Apply DTI-based approval rules.** Monitor applicants above 60% DTI more closely.
5. **Monitor the critical credit-score band (<500).** Use early-warning indicators for this large segment.
6. **Grow safer segments.** Senior borrowers, higher-income borrowers and home loans show the best repayment behavior.

## Technical Specifications

| Component | Technology / Approach |
|---|---|
| Data input | CSV / Excel |
| Data preparation | Power Query |
| Measures | DAX |
| Dashboard | Microsoft Power BI |
| Interactivity | Year slicer, page navigation, reset button |
| Analysis type | Descriptive and exploratory analysis |

## How to Review the Project

1. **Browse the dashboard pages** in the [walkthrough](#dashboard-walkthrough) above.
2. **Download the dataset** from the link in [`Dataset/`](Dataset/README.md).
3. **Open the Power BI file** in `Power BI/` with Power BI Desktop, update the data source path and refresh.
4. **Use the Year slicer** at the top right of each page to filter by year.

## Limitations

- Findings describe patterns in this dataset and should not be generalized to all lenders.
- Default rate is **descriptive** (observed history), not a predictive model.
- Group differences show association, not causation (for example, income and age may overlap).
- Cost, recovery and loss-given-default data are not available, so financial loss is not measured.
- External data validation is out of scope.

## Author

**Anurag Tijare**
Data Analyst / BI Developer

---

**Loan Default Risk Analysis** · Power BI • DAX • Power Query • Business Insights
