# ♀️Income Detection Workflow (Bank Statement Analyzer)

> Goal: Detect monthly income + salary transactions accurately using pattern rules.

Income verification is critical for:
- Loan eligibility  
- FOIR calculation  
- Risk scoring  
- Banking workflows  

---

## 📌Inputs
- Raw bank statement text / CSV
- OCR extracted text (from PDFs)
- Transaction list

---

## ❄️Workflow (7 Steps)

1️⃣ **Text Cleanup**
- Remove symbols, OCR noise
- Normalize merchant names

2️⃣ **Transaction Extraction**
- Parse date, description, amount, credit/debit

3️⃣ **Salary Pattern Detection**
- Monthly recurring credit
- Similar or equal amounts
- Consistent employer name

4️⃣ **Employer Recognition**
- Detect corporate/HR payroll names
- Match repeated employer pattern

5️⃣ **Average Monthly Salary**
- Handle variations (bonus, partial salary)
- Remove cashback & one-time credits

6️⃣ **Decision & Confidence**
- Confidence increases if:
  - repetition pattern strong
  - employer detected
  - stable monthly timing

7️⃣ **JSON Output**
- Machine-readable for automation

---

## 📌 Example Output
```json
{
  "monthly_income": 58000,
  "salary_transactions": [
    {
      "date": "2025-09-01",
      "amount": 58000,
      "employer_name": "TCS"
    },
    {
      "date": "2025-10-01",
      "amount": 58000,
      "employer_name": "TCS"
    }
  ],
  "confidence": 0.93
}
 ❌Salary Logic Rules
Rule	Description
Recurrence rule	Appears monthly
Employer name match	Ensures salary source
Stable amount rule	Variance within ±15%
Timing rule	Similar day each month

Salary is defined by pattern, not value.

☑ Guardrails & Validation
If unclear → monthly_income = null

Confidence drops if employer not detected

No guessing allowed

📌 Result
A structured, automated income detection system that:

avoids human dependency

increases decision speed

boosts lending safety

🔗 Related Components
♀️ FOIR Engine → /05-FinTech-Rule-Engines/foir-calculator.md

🧠 Rule Agent → /04-Agent-Systems/income-extraction-agent.md

🛠 Debug cases → /06-Debugging-and-Reliability/cashback-vs-salary-issue.md

Income detection ≠ guessing → it’s pattern intelligence.
