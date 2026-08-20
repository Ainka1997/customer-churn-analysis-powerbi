# Customer Churn Analysis Dashboard

An end-to-end customer churn analytics project using **Power BI, SQL,
and data cleaning** to identify churn patterns, customer retention
segments, contract risk, and tenure-based churn behavior.

![Customer Churn Dashboard](images/customer-churn-dashboard.png)

## Project Overview

The objective of this project is to turn raw telecom customer data into
an executive-friendly dashboard that answers:

-   How many customers have churned?
-   What is the overall churn rate?
-   Which contract types have the highest churn?
-   How does churn vary by customer tenure?
-   What is the retained-vs-churned customer mix?
-   How do monthly charges differ across customer groups and services?

## Tools & Technologies

-   **Power BI** --- data modeling, DAX, dashboard design and
    visualization
-   **Power Query** --- data cleaning and transformation
-   **SQL / PostgreSQL** --- data preparation and quality checks
-   **CSV** --- source dataset

## Dataset

The source snapshot contains **7,048 customer records and 21 fields**.

Key fields include:

-   Customer ID
-   Tenure
-   Contract
-   Internet Service
-   Online Security / Backup
-   Tech Support
-   Payment Method
-   Monthly Charges
-   Total Charges
-   Churn

The source file contains data-quality issues such as missing
`TotalCharges`, inconsistent capitalization/spacing, currency symbols in
`MonthlyCharges`, and repeated customer IDs. These are documented in the
SQL cleaning layer.

## Dashboard KPIs

The published dashboard shows:

  KPI                     Value
  -------------------- --------
  Total Customers         7,048
  Churned Customers       1,871
  Churn Rate             26.55%
  Retained Customers      5,177
  Retention Rate         73.45%

## Dashboard Sections

### 1. Customer Churn Overview

High-level KPIs for total customers, churn rate and churned customers.

### 2. Churn by Contract

Shows that month-to-month customers account for the largest share of
churned customers in this dataset.

### 3. Churn Rate by Tenure Band

Compares churn across: - 0--6 months - 6--12 months - 12+ months

The dashboard highlights the highest churn rate among customers with
0--6 months of tenure.

### 4. Customer Retention Overview

A retained-versus-churned customer mix showing the overall retention
position.

### 5. Monthly Charges Analysis

Compares monthly charges across customer types and service combinations.

### 6. Service Analysis

Explores monthly charges in relation to Online Security and Online
Backup service categories.

## Key Business Insights

1.  **Early-tenure customers are the highest-risk segment.** The 0--6
    month tenure band has the highest churn rate in the dashboard.
2.  **Month-to-month contracts are strongly associated with churn.**
    They represent the overwhelming majority of churned customers.
3.  **Retention is still the majority state.** About 73.45% of customers
    are retained, while 26.55% have churned.
4.  **Contract structure is an important retention lever.** Customers on
    longer contracts show substantially lower churn than month-to-month
    customers.
5.  **Customer service and subscription features can be investigated as
    potential churn drivers**, especially when combined with tenure and
    contract type.

## Data Preparation

The SQL layer performs:

-   Whitespace standardization
-   Contract category normalization
-   Currency-symbol removal from monthly charges
-   Numeric type conversion
-   Missing-value handling for `TotalCharges`
-   Duplicate customer-ID checks
-   Basic data-quality validation

> Note: The published dashboard preserves the 7,048-row source snapshot
> so that the displayed KPI values remain reproducible. Duplicate IDs
> are therefore flagged for investigation rather than automatically
> removed.

## Repository Structure

``` text
customer-churn-analysis/
│
├── data/
│   └── telco_churn_unclean.csv
│
├── docs/
│   └── data_dictionary.csv
│
├── images/
│   └── customer-churn-dashboard.png
│
├── powerbi/
│   └── DAX_Measures.txt
│
├── sql/
│   └── data_cleaning.sql
│
├── Customer_Churn_Analysis.pbix
├── .gitignore
└── README.md
```

## How to Reproduce

1.  Load `data/telco_churn_unclean.csv` into PostgreSQL or Power BI.
2.  Apply the transformations in `sql/data_cleaning.sql` or reproduce
    them in Power Query.
3.  Create the DAX measures in `powerbi/DAX_Measures.txt`.
4.  Build the dashboard using the KPI and analysis sections described
    above.
5.  Save the Power BI file as `Customer_Churn_Analysis.pbix`.
6.  Add the `.pbix` file to the repository if its size is suitable for
    GitHub.
