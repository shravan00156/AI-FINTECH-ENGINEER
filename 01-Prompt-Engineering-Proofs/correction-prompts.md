# Correction Prompts for FinTech Automation

Real-world automation often produces outputs that are:
- missing fields  
- wrong values  
- mixed formats  
- low confidence  

These prompts **repair and improve** bad or incomplete AI responses.

> Goal: **Take imperfect output → fix → return a clean JSON** suitable for pipelines.

---

## 1️⃣ Format Correction Prompt

**Problem:** Output JSON has inconsistent structure

**Prompt:**
You are a JSON correction engine.
Fix the structure to strictly match this format:

{
"field": "",
"confidence": number
}

If any value is missing or unclear, set:
"field": null, "confidence": 0.0

Return ONLY valid JSON.

yaml
Copy code

---

## 2️⃣ Value Validation Prompt

**Problem:** AI mixes cashback with salary

**Prompt:**
Check each credit transaction.
If inconsistent monthly pattern → mark as cashback, not salary.

Correct the output by removing cashback from salary detection.
Return corrected JSON only.

yaml
Copy code

---

## 3️⃣ Data Cleaning Prompt

**Problem:** OCR introduces noise & special characters

**Prompt:**
Clean and normalize the text:

remove noise, symbols, repeated characters

normalize dates to YYYY-MM-DD

normalize merchant names

Return structured and cleaned output only.

yaml
Copy code

---

## 4️⃣ Confidence Boosting Prompt

**Problem:** AI is unsure about extracted values

**Prompt:**
Add reasoning only inside the model.
Do NOT include reasoning in the output.

Increase confidence ONLY if:

recurring salary pattern exists

employer name pattern matches

Return final JSON only.

yaml
Copy code

---

## 5️⃣ Re-Check & Regenerate Prompt

**Problem:** Output passes extraction but violates rules

**Prompt:**
Re-check:

required fields exist

types match (string/number)

FinTech rules are satisfied

If not valid → regenerate output.
Return final JSON only.

yaml
Copy code

---

## 🧠 Bonus: Universal Correction Pattern

Fix → Validate → Return JSON

NEVER add text outside JSON.
NEVER guess financial values.

yaml
Copy code

---

### 🏁 Summary Table

| Correction Type | When used | Result |
|----------------|-----------|--------|
| Format Correction | Wrong structure | Valid JSON |
| Value Validation | Salary vs Cashback issue | Accurate values |
| Data Cleaning | OCR noise | Clean, normalized data |
| Confidence Update | Low certainty | Reliable scoring |
| Re-Check | Rule-breaking outputs | Production-ready JSON |

---

### 📌 Where This Helps in System Design
These patterns are critical in:
- Loan approvals  
- Risk scoring  
- Income verification  
- KYC matching  
- Any automation workflow using AI  

Always combine correction prompts with:
👉 guardrails (see: `json-output-prompts.md`)  
👉 workflows (see: `03-Automation-Workflows/`)

---

If AI output is not structured →  
**Automation breaks.**  
Correction prompts prevent failure.
