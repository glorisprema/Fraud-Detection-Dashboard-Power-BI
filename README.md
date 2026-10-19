<img width="1112" height="625" alt="Screenshot 2026-10-19 122423" src="https://github.com/user-attachments/assets/42bbb720-4ec3-4777-aff5-502cf6e54848" />
<img width="1112" height="625" alt="Screenshot 2026-10-19 122423" src="https://github.com/user-attachments/assets/487eedcd-399e-4632-866f-e24f59c05dfb" />
<img width="1115" height="627" alt="Screenshot 2026-10-19 122530" src="https://github.com/user-attachments/assets/d6264174-be94-40b7-b679-26711c216742" />
<img width="1112" height="625" alt="Screenshot 2026-10-19 122423" src="https://github.com/user-attachments/assets/2e65cfdb-0681-4b8b-b48e-fa4182b334b0" />
# Fraud Detection Dashboard - Power BI

Analyzed 26K fraud transactions ($15M total) across Hamilton, Toronto, Oakville.

## KPIs
- Fraud Count: 26K
- Total Fraud Amount: $15M
- Online Withdrawal Fraud: $2M
- Q-Rule Impact: $4.72M (3,684 cases)

## Q-Rule Definition
**IF Channel = Online AND Amount >= $2,500 THEN Flag High Risk**
- Exposure: $4.72M
- Risk ≠ Fraud - Flag means "Needs extra OTP verification"
- Highest risk: Hamilton Downtown, Online 40.1%

## Dashboard - Executive Summary

## Dashboard - Q-Rule Deep Dive (High Risk >$2500 Online)

## Files
- Fraud_Dashboard.pbix / .pdf
- Power BI, DAX
