# Extraction Prompts for FinTech Automation  
These prompts extract specific financial fields from documents like:
- Bank statements
- PAN/Aadhaar
- UPI/PayNow transactions

> Goal: Extract **only required fields** with **high accuracy** and **strict JSON** formatting.

---

## 1️⃣ Bank Statement → Salary Extraction

Extract ONLY salary-related entries.
Detect recurring monthly credits with similar amounts.

Output ONLY JSON:
{
"salary_transactions": [
{
"date": "YYYY-MM-DD",
"amount": number,
"employer_name": ""
}
],
"monthly_salary": number,
"confidence": number
}

yaml
Copy code

**Key rule:**  
Repeat + employer match → salary

---

## 2️⃣ Transaction Categorization Extraction

Identify merchant name and transaction category.

Return ONLY JSON:
{
"merchant": "",
"category": "",
"tags": []
}

yaml
Copy code

**Categories include:**  
Food, Shopping, Travel, Utilities, EMI, Salary, etc.

---

## 3️⃣ PAN Card Extraction

Extract these fields ONLY:

PAN number

Name

DOB

Output JSON only:
{
"pan": "",
"name": "",
"dob": ""
}

yaml
Copy code

**Rule:** PAN must be 10 characters (ABCDF1234E format)

---

## 4️⃣ Aadhaar Extraction

Extract:

Full name

Address

DOB

Aadhaar masked number (xxxx-xxxx-1234)

Return JSON only.

yaml
Copy code

**Note:** Do NOT reveal full Aadhaar number.

---

## 5️⃣ UPI / PayNow Fraud Signal Extraction

Check transaction:

timestamp odd hours?

new payee?

unusual amount?

Output JSON:
{
"risk_flags": [],
"risk_score": number
}

yaml
Copy code

**Flags added only if pattern exists.**

---

## 🧠 BONUS: Universal Extraction Pattern

Extract ONLY required fields.
Never assume missing information.
If unclear → set null.
Return ONLY valid JSON.

yaml
Copy code

---

### ✔ Why Extraction Prompts Matter
They ensure:
- consistency  
- automation pipeline stability  
- faster decision-making  
- fewer manual corrections  

These prompts are used heavily in:
- Lending apps  
- KYC verification systems  
- Neo-banks  
- Fraud monitoring tools  

---

Next → correction + reliability prompts  
See: `correction-prompts.md` and `json-output-prompts.md`

---

