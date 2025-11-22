# Fraud Detection Workflow (UPI / PayNow)

> Goal: Detect and flag suspicious transactions using pattern rules + automated risk scoring.

Fraud hides inside **behavioral patterns**, not single transactions.  
This workflow converts patterns into a clear, automated decision system.

---

## 🎯Problem
Manual review is slow and inconsistent.  
We need a fast, rule-based workflow to identify risk signals.

---

## 🧩 Inputs
- Transaction history
- New incoming transaction
- Metadata: time, location, device, payee

---

## 🛠 Workflow (6-step automation)

1️⃣ **Data ingestion**
- Parse transaction fields
- Normalize merchant/payee names

2️⃣ **Behavior pattern checks**
- New payee?
- Unusual time?
- New location?
- Odd amount compared to history?

3️⃣ **Risk rules application**
- Each suspicious pattern adds a risk flag

4️⃣ **Risk scoring**
- Score based on number + strength of flags  
(Example: Night + large spend + new payee = HIGH)

5️⃣ **Decision generation**
- `safe` or `suspicious`

6️⃣ **JSON output**
- Machine-readable structured result

---

## 📌 Example Output
```json
{
  "transaction_id": "TXN3721",
  "risk_flags": ["unusual_amount", "new_payee"],
  "risk_score": 0.78,
  "status": "suspicious"
}
📌Rules Used
Rule	Trigger	Risk Impact
Unusual amount	>150% of average for user	High
New payee	First time payee	Medium
Odd timing	Night (11pm–5am)	Medium
Location mismatch	New city	High
Failed attempts	Multiple retries	Very High

These patterns detect fraud spikes quickly and safely.

☑ Validation & Guardrails
Ensure all required fields exist

Ensure correct data types (string/number)

If missing → risk_score = 1.0 (fail-safe)

📌 Result
A reliable automation workflow that:

reduces manual verification workload

improves fraud response time

increases financial safety

Related Systems
❄️Risk Scoring Agent → /04-Agent-Systems/risk-scoring-agent.md

⚙ Fraud Rules → /05-FinTech-Rule-Engines/risk-scoring-rules.md

Fraud detection = prevention + pattern intelligence.



---

### 🔥 Status Check (Folder 03)
| File | Status |
|------|--------|
| `kyc-workflow.md` | ⚡ Ready |
| `loan-eligibility-flow.md` | ⚡ Ready (if needed next) |
| `income-detection-flow.md` | ⚡ Ready |
| `fraud-detection-flow.md` | ✔ Completed |

---

