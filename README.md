# Fraud Detection Dashboard - Power BI

Analyzed 26K fraud transactions ($15M total) across Hamilton, Toronto, Oakville.

## KPIs
- Fraud Count: 26K
- Total Fraud Amount: $15.00M
- Online Withdrawal: $2M
- Q-Rule Impact: $4.72M (3,684 cases flagged)

## Q-Rule Definition
**IF Channel = Online AND Amount >= $2,500 THEN Flag High Risk**
- Exposure: $4.72M
- Risk ≠ Fraud - Flag means "Needs extra OTP verification"
- Highest risk: Hamilton Downtown | Online 40.1%

## Dashboard - Executive Summary
KPIs, Fraud by Branch, Fraud by Channel

## Dashboard - Q-Rule Deep Dive
Customer_ID, Branch, Amount, Channel - All Online >$2500

## Tools
Power BI, DAX, Data Modeling
