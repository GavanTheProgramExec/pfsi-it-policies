# Parents for Scouting, Inc. (PFSI) — Data Classification Standard
**Document Owner:** Chief Executive Officer (CEO)  
**Document Approver:** Chief Technology Officer (CTO)   
**Applies To:** All PFSI systems, services, devices, accounts, repositories, and communications (including GitHub)  
**Effective Date:** 2026-01-25  
**Version:** 1.0

---

## 1. Purpose
This standard defines how Parents for Scouting, Inc. (PFSI) classifies, stores, shares, and protects data to:
- Safeguard youth
- Protect privacy
- Reduce organizational risk
- Ensure consistent handling of data across technology platforms

This standard is written with a bias toward **youth protection and privacy-by-design**.

---

## 2. Core Rules (Non-Negotiables)
1. **No Youth Personal Data in GitHub**  
   Youth personal data (see Section 5) must not be stored in GitHub repositories, issues, pull requests, wikis, discussions, or logs — even in private repositories.

2. **No Secrets in Repositories**  
   Passwords, API keys, tokens, private keys, certificates, or connection strings must never be committed to GitHub. Use approved secret storage (Section 7).

3. **Minimum Necessary**  
   Collect and retain only what is needed to operate the organization and deliver the program safely.

4. **Least Privilege Access**  
   Access to any non-public data is granted only to those who need it for an approved role, and removed when no longer needed.

5. **Assume Exposure**  
   Any system can fail. Protect data as if it could be accidentally shared.

---

## 3. Data Classification Levels
PFSI uses four classification levels. When unsure, classify at the **higher** (more restrictive) level.

### 3.1 PUBLIC
**Definition:** Information approved for public release.  
**Examples:**
- Public website content already approved for posting
- Public event announcements (no youth PII)
- General program descriptions, policies intended for public viewing

**Allowed in GitHub:** YES (preferred for website/policy repos)  
**Protection:** Basic integrity controls (PR reviews), no sensitive info

---

### 3.2 INTERNAL
**Definition:** Information intended for PFSI leaders/volunteers; not for public distribution, but not sensitive if accidentally disclosed.  
**Examples:**
- Draft planning documents (no youth PII)
- Generic procedures/checklists
- Non-sensitive meeting notes without personal details
- Technical runbooks (with secrets removed)

**Allowed in GitHub:** YES, but avoid including any personal details  
**Protection:**
- Private repos allowed
- PR workflow required
- Limit access to appropriate teams

---

### 3.3 CONFIDENTIAL
**Definition:** Sensitive organizational information where unauthorized disclosure could cause harm to PFSI, leaders, families, or operations.  
**Examples:**
- Adult volunteer personal contact details (phone, address) beyond what is already public
- Internal financial details (banking workflows, vendor invoices) excluding full account numbers
- Security details (system architecture diagrams showing defenses)
- Non-public vendor contracts or quotes

**Allowed in GitHub:** GENERALLY NO  
If absolutely necessary, only in **private repos** with CTO approval and redaction of personal details.
**Protection:**
- Private storage only
- Access limited to specific adult roles
- Encryption at rest and in transit (platform default + best practice)
- Logging/auditability
- Retention limits (do not keep longer than needed)

---

### 3.4 RESTRICTED (Highest)
**Definition:** Highly sensitive data where unauthorized disclosure could cause significant harm, including any data about youth.  
**Examples (not exhaustive):**
- **Youth personal data (PII)**: name + contact info, DOB, address, phone, email, parent/guardian details
- **Youth program data**: rosters, patrol lists, advancement records, attendance tied to names
- **Health/medical information**: medications, allergies, medical forms, incident reports
- **Background check or screening results**
- **Any incident, allegation, or youth protection report**
- **Credentials/secrets**: passwords, API keys, tokens, private keys, SSH keys, certificates

**Allowed in GitHub:** NO (never)  
**Protection:**
- Store only in approved systems designed for this data type
- Strong access controls and auditing
- Share only with authorized adults and only through approved channels
- Immediate escalation if mishandled (Section 9)

---

## 4. What This Means for GitHub (PFSI Rules)
GitHub is approved for:
- Code
- Infrastructure templates (no secrets)
- Policies, SOPs, and technical docs
- Public website content that does not identify youth

GitHub is NOT approved for:
- Rosters, advancement, medical, incident reporting, or any youth personal data
- Credentials of any kind
- Any sensitive personal conversations

**Communication rule:** Work happens in Issues/PRs with adult oversight. Avoid private 1:1 messaging related to youth participation.

---

## 5. Definitions: Personal Data (PII) and Sensitive Data
**Personal Data / PII:** Any information that can identify a person directly or indirectly, including name when combined with contact details, photos identifying a youth, or unique identifiers.

**Sensitive Data:** Includes youth data, health/medical, financial account numbers, authentication secrets, and incident/allegation reports.

**Youth Data:** Any personal or program information about a youth participant, including photos if the youth is identifiable and the photo is not already approved for public release.

---

## 6. Handling Requirements by Classification
### PUBLIC
- Can be shared publicly
- PR review required for official repos (website/policies)

### INTERNAL
- Share within PFSI roles as needed
- Avoid personal details
- Store in private repos if needed

### CONFIDENTIAL
- Store only in approved private systems
- Do not place in GitHub unless CTO approves and content is redacted
- Share only to specific adults who need it

### RESTRICTED
- Never store in GitHub
- Never email as an attachment unless explicitly approved and encrypted
- Use approved systems and role-based access
- Report mishandling immediately

---

## 7. Approved Storage Locations (Guidance)
**GitHub:**
- PUBLIC and INTERNAL only  
- CONFIDENTIAL only with CTO approval and redaction  
- RESTRICTED never

**Secrets:**
- GitHub Actions Secrets (for CI/CD), or an approved password/secret manager
- Never in code, never in README, never in `.env` committed to GitHub

**Youth program records:**
- Use Scouting America approved systems (e.g., Scoutbook / official platforms) and official unit record practices
- Any exports containing youth data must be stored in a restricted-access location (not GitHub)

---

## 8. Examples (Common Scenarios)
✅ OK in GitHub:
- Website source code and images that do not identify youth
- “How to reset the troop email password” (without the password)
- Generic event signup form template using placeholder data

❌ Not OK in GitHub:
- “Troop roster.csv”
- “MedicalForms/”
- A bug report that includes a youth’s full name + phone number
- A screenshot showing youth names, emails, or advancement status
- `.env` file containing API keys

---

## 9. Incident Response (If Data is Mishandled)
If prohibited or sensitive data is found in GitHub or shared improperly:
1. **Stop**: Do not further copy/share the data
2. **Notify**: Contact the CTO immediately
3. **Contain**: Remove data from the repository and history if needed
4. **Rotate**: If secrets were exposed, rotate/revoke them immediately
5. **Document**: Record what happened, what data was involved, and corrective actions

For any youth protection concern, follow PFSI escalation procedures and Scouting America reporting expectations.

---

## 10. Enforcement
- The CTO and Technology Department maintain the authority to restrict access, remove content, or suspend accounts to protect youth and PFSI.
- Violations may result in removal of access and additional corrective actions.

---

## 11. Change Log
- v1.0 (2026-01-25): Initial release

