# Fraud Detection Dashboard - Power BI | GTA Branches

## Overview
Power BI dashboard built to monitor high-risk fraud transactions across GTA branches - Hamilton Downtown, Toronto Main, and Oakville. Flags high-risk online transactions for investigation.

This dashboard helps fraud teams prioritize investigations and reduce exposure.

## KPIs - Executive Summary
- **26K Fraud Count** - Total confirmed fraud cases across all branches
- **$15M Total Fraud Amount** - Total potential savings
- **$2M Online Withdrawal Amount** - High-risk channel exposure
- **$3.72M Q-Rule Impact** - Online AND Amount > $2,500 Flag (665 cases)

## Key Insights
- **Total Fraud Amount $15M** across GTA branches (26K cases)
- **Hamilton Downtown has highest fraud by branch** - requires priority monitoring
- **Online channel is highest risk** - $2M exposure in withdrawals
- **Q-Rule: Online AND Amount > $2,500** - Flags $3.72M exposure, 665 high-risk transactions for immediate investigation
- **Flagged Transactions = 665** - This is your version of the sample 3,684 (based on your dataset size)

## Visuals
- **Page 1 - Executive Summary:**
    - KPI Cards: 26K Fraud Count, $15M Total Fraud Amount, $2M Online Withdrawal, $3.72M Q-Rule Impact
    - Total Fraud Amount by Branch: Bar chart showing Hamilton Downtown > Toronto Main > Oakville
    - Fraud Count by Channel: Donut chart - Online, Branch, ATM distribution

- **Page 2 - Q-Rule Deep Dive:**
    - Sum of Amount: 3.72M
    - Channel: Online
    - 🚩 Flagged Transactions: 665
    - High Risk Detail Table: Customer ID, Branch, Sum of Amount (highlighted orange)

## Tools & DAX Used
- **Power BI Desktop**
- **DAX Measures:**
    - `Total_Fraud_Amount = SUM(Fraud_Amount)`
    - `Fraud_Count = COUNT(Fraud_Flag)`
    - `Q_Rule_Flag = IF(AND(Channel="Online", Amount>2500), 1, 0)`
    - `Q_Rule_Amount = CALCULATE(SUM(Amount), Channel="Online", Amount>2500)`
    - `Flagged_Txn_Count = COUNT(Customer_ID)`
- **Data Cleaning:** Python (Pandas) / Power Query
- **Data Source:** Fraud transactions dataset (GTA Branches)

## Files
- `Fraud_Detection_Dashboard.pbix` - Main Power BI file
- `/screenshots/` - Dashboard screenshots
    - `Executive_Summary.png`
    - `Q_Rule_Detail.png`

## Business Impact
This dashboard helps fraud teams prioritize investigations by focusing on Hamilton Downtown branch and Online channel. Flags $3.72M in high-risk online transactions (> $2,500) across 665 cases, potentially saving $3M+ in fraud losses.

## Author
**Glory Prema - Aspiring Data Analyst | Hamilton, ON**
- Focus: Fraud Analytics, Power BI, GTA Banking
- LinkedIn: (Add your LinkedIn link here)

## Dashboard - Executive Summary
![Executive Summary](screenshots/Executive_Summary.png)

## Dashboard - Q-Rule Deep Dive
![Q-Rule Deep Dive](screenshots/Q_Rule_Detail.png)

## How It Works
Q-Rule flags transactions where risk score is high and channel is online. Helps investigators prioritize cases with highest financial exposure.

## Project Link
https://github.com/gloryprema/Fraud-Detection-Dashboard-Power-BI
