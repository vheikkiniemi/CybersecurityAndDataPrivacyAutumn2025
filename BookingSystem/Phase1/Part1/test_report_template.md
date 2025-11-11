# 1️⃣ Introduction

**Tester(s):**  
- Name:  

**Purpose:**  
- Describe the purpose of this test (e.g., identify vulnerabilities in registration and authentication flows).

**Scope:**  
- Tested components:  
- Exclusions:  
- Test approach: Gray-box / Black-box / White-box

**Test environment & dates:**  
- Start:  
- End:  
- Test environment details (OS, runtime, DB, browsers):

**Assumptions & constraints:**  
- e.g., credentials provided, limited time, etc.

---

# 2️⃣ Executive Summary

**Short summary (1-2 sentences):**  

**Overall risk level:** (Low / Medium / High / Critical)

**Top 5 immediate actions:**  
1.  
2.  
3.
4.
5.

---

# 3️⃣ Severity scale & definitions

- **Critical** → Leads to full system compromise or data breach. *Immediate fix required.*  
- **High** → Exposes sensitive data or enables privilege escalation. *Fix ASAP.*  
- **Medium** → Requires specific conditions or user action. *Fix soon.*  
- **Low** → Minor issue or misconfiguration. *Monitor and fix in maintenance.*  
- **Informational** → No direct risk, but useful for hardening. *For awareness.*

---

# 4️⃣ Findings (filled with examples → replace)

> Fill in one row per finding. Focus on clarity and the most important issues.

| ID | Severity | Finding | Description | Evidence / Proof |
|------|-----------|----------|--------------|------------------|
| F-01 | 🔴 Critical | SQL Injection in registration | Input field allows `' OR '1'='1` injection | Screenshot or sqlmap result |
| F-02 | 🟠 High | Session fixation | Session ID remains unchanged after login | Burp log or response headers |
| F-03 | 🟡 Medium | Weak password policy | Accepts passwords like "12345" | Screenshot of registration success |

✅ **Tips:**  
- Include up to 5 findings total.   
- Keep each description short and clear.

---

# 5️⃣ OWASP ZAP Test Report (Attachment)

**Purpose:**  
- Attach or link your OWASP ZAP scan results (Markdown format preferred).

---

**Instructions (CMD version):**
1. Run OWASP ZAP baseline scan:  
   ```bash
   zap-baseline.py -t https://example.com -r zap_report_round1.html -J zap_report.json
   ```
2. Export results to markdown:  
   ```bash
   zap-cli report -o zap_report_round1.md -f markdown
   ```
3. Save the report as `zap_report_round1.md` and link it below.

---

📁 **Attach full report:** → `check itslearning` → **Add a link here**

---