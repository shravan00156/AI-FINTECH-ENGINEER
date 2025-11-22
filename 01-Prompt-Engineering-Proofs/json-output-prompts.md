#  JSON Output Enforcement Prompts  
FinTech automation requires reliable **machine-readable** output.  
These prompt patterns guarantee **strict JSON** formatting.

> If JSON is inconsistent → the entire workflow can break.

---

## 1️⃣ Strict JSON Format Prompt

Return ONLY valid JSON with this exact structure:

{
"field1": "",
"field2": number,
"confidence": number
}

Do NOT include any text outside JSON.
If a field is missing, set it to null.

yaml
Copy code

✔ Prevents model from adding explanation text

---

## 2️⃣ Schema Validation Prompt

Before final output:

ensure all required fields exist

ensure correct data types

ensure JSON structure is valid

If invalid → regenerate
Return ONLY valid JSON

yaml
Copy code

✔ AI corrects its own mistakes before output

---

## 3️⃣ No Guessing Rule

If data is unclear:

Do NOT guess

Set missing fields to null and confidence to 0.0

Return ONLY JSON.

yaml
Copy code

✔ Zero hallucinations for FinTech data

---

## 4️⃣ Output Sanitization Prompt

Remove:

extra spaces

special characters

hidden strings

markdown formatting

Return clean JSON only.

yaml
Copy code

✔ Prevents broken parsing in systems

---

## 5️⃣ Confidence Score Enforcement

Every extracted field must include a confidence score.

Valid range: 0.0 → 1.0

yaml
Copy code

✔ Helps rule-engines filter unreliable results

---

### 🔍 Example: Salary Extraction JSON

{
"monthly_income": 52000,
"salary_transactions_count": 3,
"confidence": 0.91
}

yaml
Copy code

✔ short  
✔ clean  
✔ consistent  
✔ automation-ready

---

# JSON Output Checklist (Always Apply)

| Requirement | Why it matters |
|------------|----------------|
| Strict schema | Stable pipelines |
| No outside text | Easy parsing |
| Confidence score | Risk handling |
| Correct data types | Safe processing |
| Clear null policy | Transparency |

---

> **Remember:**  
> If the output is not consistent →  
> **the system is not ready for production.**

---

📌 Connect With:
- `extraction-prompts.md`
- `correction-prompts.md`
- `guardrails` & reliability flows
