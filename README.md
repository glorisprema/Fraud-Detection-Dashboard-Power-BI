# Fraud Detection Dashboard - Power BI | GTA Branches

## Overview
Power BI dashboard built to monitor high-risk fraud transactions across GTA branches - Hamilton Downtown, Toronto Main, and Oakville. Flags high-risk online transactions for investigation.

This dashboard helps fraud teams prioritize investigations and reduce exposure.

## KPIs - Executive Summary
- **26K Fraud Count** - Total confirmed fraud cases across all branches
- **$15M Total Fraud Amount** - Total potential savings
- **$2M Online Withdrawal Amount** - High-risk channel exposure
- **$3.72M Q-Rule Impact** - Online AND Amount > $2,500 (665 cases)

## Key Insights
- **Total Fraud Amount $15M** across GTA branches (26K cases)
- **Hamilton Downtown has highest fraud by branch** - requires priority monitoring
- **Online channel is highest risk** - $2M exposure in withdrawals
- **Q-Rule: Online AND Amount > $2,500 Flag High-Risk** - $3.72M exposure, 665 high-risk transactions for immediate investigation
- **🚩 Flagged Transactions = 665** - High-Risk Detail table for investigation

## Visuals
- **Page 1 - Executive Summary:**
    - KPI Cards: 26K Fraud Count, $15M Total Fraud Amount, $2M Online Withdrawal, $3.72M Q-Rule Impact
    - Total Fraud Amount by Branch: Hamilton Downtown > Toronto Main > Oakville
    - Fraud Count by Channel: Donut chart - Online, Branch, ATM

- **Page 2 - Q-Rule Deep Dive:**
    - Sum of Amount: 3.72M
    - Channel: Online
    - Flagged Transactions: 665
    - High Risk Detail Table: Customer ID, Branch, Sum of Amount (orange highlight)

## Tools & DAX Used
- **Power BI Desktop**
- **DAX Measures:**
    - `Total_Fraud_Amount = SUM(Fraud_Amount)`
    - `Fraud_Count = COUNT(Fraud_Flag)`
    - `Q_Rule_Flag = IF(AND(Channel="Online", Amount>2500), 1, 0)`
    - `Q_Rule_Amount = CALCULATE(SUM(Amount), Channel="Online", Amount>2500)`
    - `Flagged_Txn_Count = COUNT(Customer_ID)`
- **Data Source:** Fraud transactions dataset (GTA Branches)

## Files
- `Fraud_Dashboard.pbix` - Main Power BI file
- `Fraud Detection Dashboard.png` - Executive Summary screenshot
- `High Risk online.png` - Q-Rule Deep Dive screenshot

## Business Impact
This dashboard helps fraud teams prioritize investigations by focusing on Hamilton Downtown branch and Online channel. Flags $3.72M in high-risk online transactions (> $2,500) across 665 cases, potentially saving $3M+ in fraud losses.

## Author
**Gloris Prema - Aspiring Data Analyst | Hamilton, ON**
- Focus: Fraud Analytics, Power BI, GTA Banking

## Dashboard - Executive Summary
![Executive Summary](Fraud%20Detection%20Dashboard.png)

## Dashboard - Q-Rule Deep Dive
![Q-Rule Deep Dive](High%20Risk%20online.png)

## How It Works
Q-Rule flags transactions where Channel = Online AND Amount > $2,500. This helps investigators prioritize cases with highest financial exposure for Hamilton and Toronto branches.

## Project Link
https://github.com/glorisprema/Fraud-Detection-Dashboard-Power-BI
