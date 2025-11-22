# 🎗️Loan Eligibility Workflow (FOIR-Based Decision)

> Goal: Automate loan decisions using FOIR + income + obligations with clean JSON output.

Loan decisioning must be:
✔ fast  
✔ consistent  
✔ rule-driven  
✔ explainable  

This workflow turns bank data into a **clear approval/rejection**.

---

## Inputs
- Monthly income (from statement analyzer)
- Monthly obligations (existing EMIs/loans)
- Loan amount requested (optional)
- Customer profile metadata

---

## 🛠 Workflow (6 Steps)

1️⃣ **Fetch Financial Inputs**
- Income from Income Detection System  
- Existing liabilities (EMIs, deductions)

2️⃣ **Calculate FOIR**
FOIR = Monthly EMI / Monthly Income

yaml
Copy code

3️⃣ **Apply Lending Rules**
Example:
- FOIR ≤ 50% → Eligible  
- FOIR > 50% → High risk → Reject or lower amount

4️⃣ **Adjust Eligible Loan Amount**
- Based on DTI (Debt-to-Income)
- Tenure assumptions (optional)

5️⃣ **Generate Decision**
- `approve` | `reject` | `review`

6️⃣ **Structured JSON Output**
- For automated pipelines

---

## 📌 Example JSON Output
```json
{
  "monthly_income": 60000,
  "monthly_obligations": 12000,
  "foir": 0.20,
  "decision": "approve",
  "eligible_loan_amount": 450000,
  "confidence": 0.91
}
❌Rule Engine Logic
Check	Rule	Reason
FOIR threshold	FOIR ≤ 50%	Enough repayment capacity
Stability	Income consistent	Lower default risk
Clean obligations	No pending NPAs (future rule)	Safety

Lower FOIR → better eligibility.

☑ Guardrails
If income unclear → reject → confidence low

Missing EMI data → manual review

Extreme FOIR → fail-safe “Reject”

Never fabricate financial values

❌Result
A professional lending workflow that:

speeds up loan approvals

reduces human decision errors

provides explainable rule-based results

🔗 Related Components
Income detection → /03-Automation-Workflows/income-detection-flow.md

FOIR rule engine → /05-FinTech-Rule-Engines/foir-calculator.md

Loan Agent → /04-Agent-Systems/loan-decision-agent.md

Loan automation = trust + speed + consistency.

yaml
Copy code

---

### 📌 Folder 03 — FULL STATUS ✔

| Workflow | Status |
|---------|--------|
| KYC Workflow | ✔ Done |
| Income Detection Flow | ✔ Done |
| Fraud Detection Flow | ✔ Done |
| Loan Eligibility Flow | ✔ Done |

📈 Folder 03 is now **100% complete**!

