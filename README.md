# Fraud Detection Dashboard - Power BI

Analyzed 26K fraud transactions ($15M total) across Hamilton, Toronto, Oakville.

## KPIs
- Fraud Count: 26K
- Total Fraud Amount: $15.00M
- Online Withdrawal: $2M
- Q-Rule Impact: $4.72M (3,684 cases flagged)

## Q-Rule Definition
**IF Channel = Online AND Amount >= $2,500 THEN Flag High Risk**
- Risk ≠ Fraud - Flag means "Needs extra OTP verification"
- Highest risk: Hamilton Downtown | Online 40.1%

## Dashboard - Executive Summary
![Executive Summary](<Screenshot 2026-10-19 122423.png>)

## Dashboard - Q-Rule Deep Dive
![Q-Rule Detail](<Screenshot 2026-10-19 122530.png>)

## Tools
Power BI, DAX, Data Modeling
