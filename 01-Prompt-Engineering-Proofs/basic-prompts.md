#  Basic Prompt Engineering Proofs  
This folder contains foundational prompt engineering techniques used in FinTech automation.

> Goal: Convert **unclear tasks → clear, structured outputs** that automation systems can trust.

---

## 1️⃣ JSON Enforcement Prompt  
Forcing AI to return **only structured JSON**.

**Bad Prompt:**
“Extract income from this statement.”

**Improved Prompt:**
Extract monthly income from the statement.

Return ONLY JSON in this format:
{
"monthly_income": number,
"confidence": number
}

If unclear, return:
{
"monthly_income": null,
"confidence": 0.0
}

yaml
Copy code

**Why it matters:**  
Automation fails if output keeps changing. JSON makes the system stable.

---

## 2️⃣ Field-Level Extraction Prompt  
Specific fields → Higher accuracy.

**Prompt:**
Extract only these fields:

Name

PAN

Date of Birth

Output JSON:
{
"name": "",
"pan": "",
"dob": ""
}

yaml
Copy code

**Why it matters:**  
LLMs guess less when instructions are strict.

---

## 3️⃣ Step-by-Step Reasoning Prompt  
Break complex tasks into steps.

**Pattern:**
Think step-by-step.

Identify salary credits

Filter recurring ones

Average the amounts
Return JSON output only.

yaml
Copy code

**Why it matters:**  
Better accuracy in financial workflows.

---

## 4️⃣ Guardrails Prompt  
Stop hallucinations.

If data is missing or unclear:

Do NOT guess

Mark as null
Return confidence score

yaml
Copy code

**Why it matters:**  
FinTech systems must NEVER guess financial values.

---

## 5️⃣ Validation & Self-Check Prompt  
Force the AI to check its own output.

After generating JSON:

verify required fields exist

verify all values have correct types

if not valid, regenerate

yaml
Copy code

**Why it matters:**  
This prevents broken automation chains.

---

### 🏁 Summary  
| Pattern | Purpose |
|--------|---------|
| JSON enforcement | Prevent messy output |
| Field targeting | Higher accuracy |
| Step-by-step | Better reasoning |
| Guardrails | No hallucination |
| Self-check | Reliability in automation |

---

### 📌 Final Note  
These basic prompt patterns form the **foundation** of:
- KYC automation  
- Income extraction  
- Fraud detection  
- Multi-agent workflows  
- Rule engine decisions  

Next level → see:  
📂 `extraction-prompts.md`  
📂 `json-output-prompts.md`  
📂 `correction-prompts.md`
