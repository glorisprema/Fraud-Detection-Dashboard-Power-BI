# Fraud Detection Dashboard - Power BI | Python + SQL + Power BI | 100K Banking Transactions

**Author: Gloris Prema | Hamilton, ON | Synthetic Banking Data**
**Repo:** `Fraud-Detection-Dashboard-Power-BI`
**Stack:** Python (Pandas) | SQL (sqlite3, CASE, GROUP BY, JULIANDAY) | Power BI (DAX)

### Executive Dashboard

![Executive Dashboard](Fraud%20Detection%20Dashboard.png)

**KPIs from Dashboard:**
- **26K Fraud Count**
- **$15M Total Fraud Amount**
- **$2M Online Withdrawal Fraud**
- **$4.72M Risk Impact**
- **Top Branch: Hamilton Downtown | Top Channel: Online**

### High-Risk Deep Dive - $3.72M Proof

![High Risk Detail](High%20Risk%20online.png)

- **665 High-Risk Transactions WHERE Amount > $2,500**
- **$3.72M Sum of Amount at Risk**
- **Channel: Online | Customer Detail: CUST1271, CUST1956 etc**

**Funnel - No Double Counting:**
### Phase 1: Python + SQL - Banking_project_cleaned.ipynb

**File:** `Banking_project_cleaned.ipynb`
**Output Files:** `q_velocity.csv (20,6)` and `risk_view.csv (99002,18)`

**1. Python Cleaning:**
- Imported 100K → Cleaned to 99,002 rows
- Created DB: `sqlite3.connect('banking_project_cleaned.db')` → `df.to_sql('banking_transaction')`

**2. SQL Analysis with pd.read_sql (All 10 Queries):**

- `SELECT COUNT(*) FROM banking_transaction` → 99,002
- `SELECT Branch, COUNT(*) GROUP BY Branch` → Hamilton Downtown, Toronto Main, Oakville
- `SELECT Channel, COUNT(*) FROM banking_transaction WHERE Is_Fraud=1 GROUP BY Channel` → Online highest fraud
- `SELECT Transaction_type, SUM(Amount), COUNT(*) GROUP BY Transaction_type`
- `SELECT Transaction_type, COUNT(*) as Fraud_count, SUM(Amount) WHERE Is_Fraud=1 GROUP BY Transaction_type`
- `SELECT Channel, Transaction_type, COUNT(*) as Fraud_count, SUM(Amount) WHERE Is_Fraud=1 GROUP BY Channel, Transaction_type ORDER BY Fraud_count DESC` → Online Withdrawal 1222 flagged
- **Q-Velocity (20,6):** Self-join with `JULIANDAY()`
  `SELECT Customer_ID, CAST((JULIANDAY(Deposit_Time)-JULIANDAY(Withdrawal_Time))*1440 AS INT) as Days_Diff FROM banking_transaction d JOIN banking_transaction w ON d.Customer_ID=w.Customer_ID WHERE w.Transaction_type='Withdrawal' AND d.Transaction_type='Deposit' AND Deposit_Time > Withdrawal_Time` → Saved as `q_velocity.csv` → Shape (20,6)
- **Q-Rule:** `WHERE Is_Fraud=1 AND Channel='Online' AND Amount>500` → `SELECT Channel, Transaction_type, COUNT(*) as Flagged_Txn, SUM(Amount) as Blocked_Amount, AVG(Amount) GROUP BY Channel, Transaction_type`
- **Risk Measure:** `SELECT CASE WHEN Amount<500 THEN 'small' WHEN Amount BETWEEN 500 AND 5000 THEN 'medium' ELSE 'Large(>5k)-flag' END as risk_bucket, COUNT(*), SUM(CASE WHEN Is_Fraud=1 THEN Amount ELSE 0 END) GROUP BY risk_bucket` → **small 62,970 / medium 35,978 / Large 54**
- **Risk Flags Final View (99002,18):** `SELECT *, CASE WHEN Channel='Online' AND Is_Fraud=1 THEN 1 ELSE 0 END as is_online, CASE WHEN Channel='Online' AND Transaction_type='Withdrawal' AND Is_Fraud=1 THEN 1 ELSE 0 END as is_online_withdrawal_fraud, CASE WHEN Amount<500 THEN 'small' WHEN Amount BETWEEN 500 AND 5000 THEN 'Medium' ELSE 'Large' END as risk_bucket FROM banking_transaction` → `is_online_withdrawal_fraud SUM = 3,437` → Saved as `risk_view.csv` → Shape (99,002, 18)

### Phase 2: Power BI - Fraud_Dashboard.pbix

**File:** `Fraud_Dashboard.pbix`
- Import Mode, 16 tables from banking_project_cleaned.db
- **DAX:** `HighRiskAmount = CALCULATE(SUM(Amount), is_online_withdrawal_fraud=1, Amount>2500)` → Result 665 / $3.72M
- Visuals: Fraud by Branch, Fraud Count by Channel, Customer Detail Table

### Project Structure - Files in this Repo

- `Banking_project_cleaned.ipynb` - Python + SQL cleaning + 10 SQL queries
- `q_velocity.csv` - Q-Velocity result (20 rows, 6 cols) - Proof of JULIANDAY self-join
- `risk_view.csv` - Final flags (99,002 rows, 18 cols) - Proof of 3,437 flags and 62,970/35,978/54 buckets
- `Fraud_Dashboard.pbix` - Power BI Dashboard File
- `Fraud Detection Dashboard.png` - Executive Screenshot ($15M, 26K, $2M, $4.72M)
- `High Risk online.png` - High Risk Detail Screenshot (665, $3.72M)

### Tools

Python, SQL (sqlite3, CASE, GROUP BY, JULIANDAY, JOIN), Power BI, DAX, Fraud Analytics, Risk Scoring

### How to Replicate

1. Run `Banking_project_cleaned.ipynb` → Get 99,002 cleaned, 3,437 flags, 20 velocity
2. Verify: `SELECT SUM(Amount) FROM banking_transaction WHERE is_online_withdrawal_fraud=1 AND Amount>2500` → $3.72M, `COUNT` → 665
3. Load DB into Power BI → Recreate DAX → Build dashboard

### Contact

Gloris Prema | Hamilton, ON | Open to Data Analyst roles | LinkedIn: [Add your LinkedIn link here]
