# LedgerGuard AI 🛡️🤖
*Automated Trial Balance Anomaly Detection & Substantive Procedure Generator*

## Overview
**LedgerGuard AI** is a Python-powered audit intelligence engine designed to automate the initial analytical review phase of statutory financial audits. By combining statistical data modeling (`Pandas` & `SciPy`) with generative AI (`Gemini API`), the tool ingests raw general ledger trial balances, identifies statistical outliers, and autonomously drafts preliminary substantive audit procedures.

---

## Key Features
- **Automated ERP Data Ingestion:** Parses trial balance exports and normalizes financial categories.
- **Statistical Variance Detection:** Applies robust Z-score statistical analysis to flag balance sheet and income statement anomalies exceeding risk tolerances.
- **AI-Driven Audit Workpapers:** Interfaces with the Gemini API to generate tailored substantive testing recommendations and audit inquiries aligned with professional reporting standards (FRS 102 / IFRS).
- **Executive Exception Reporting:** Outputs clean CSV workpaper reports for audit senior review.

---

## Tech Stack
- **Language:** Python
- **Libraries:** Pandas, NumPy, SciPy
- **AI Integration:** Google Gemini API
- **Domain:** Statutory Audit & Financial Technology

---

## Example Pipeline Logic
```python
import pandas as pd
from scipy import stats

tb = pd.read_excel("trial_balance.xlsx")
tb["z_score"] = stats.zscore(tb["balance"])
flags = tb[abs(tb["z_score"]) > 2.5]
