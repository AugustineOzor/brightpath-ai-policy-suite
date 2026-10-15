# Generative AI Data Policy (Prompt Data Policy)
| Document ID | BPR-POL-AI-004 | Version | 1.0 |
|---|---|---|---|
| Owners | Data Protection Officer & CISO | Approved by | Executive Committee |
| Effective date | 2026-09-01 | Next review | 2027-03-01 |
| Classification | Internal | Related | Data Classification Standard; AI Acceptable Use Policy; Colleague Privacy Notice |

---

## 1. Purpose
Anything entered into a generative AI tool — prompts, uploaded files, connected data — may be stored, processed by third parties, or exposed in outputs. This policy defines **what data may go into which class of GenAI tool**, using BrightPath's existing four-level data classification.

## 2. Scope
All workers and all generative AI tools, including chat assistants, copilots in office suites, coding assistants, image generators, transcription/meeting tools, and GenAI features inside other applications.

## 3. Tool Classes

| Class | Description | Examples |
|---|---|---|
| **Class A — Enterprise approved** | Contracted, SSO, no training on our data, data residency agreed, logging available, DLP integrated | BrightPath Enterprise GenAI tenant; approved office-suite copilot |
| **Class B — Approved with restrictions** | Contracted and assessed but with narrower assurances or specific purpose | Approved coding assistant; approved image generator |
| **Class C — Public / unapproved** | Consumer or free tools, personal accounts, unapproved extensions | Any public chatbot on a personal account |

## 4. Data-to-Tool Matrix

| Data classification | Examples | Class A | Class B | Class C |
|---|---|---|---|---|
| **Public** | Published prices, press releases, public website content | ✅ | ✅ | ✅ (still subject to AUP) |
| **Internal** | Store procedures, internal comms, non-sensitive planning | ✅ | ✅ | ❌ |
| **Confidential** | Supplier cost prices & terms, unreleased promotions, sales performance, customer personal data, colleague personal data, source code | ✅ with minimisation | ⚠️ Only if the tool's approval covers that data type | ❌ |
| **Restricted** | Payment card data (PAN), authentication secrets, colleague health/HR case data, legal-privileged material, M&A, security vulnerability details | ❌ unless a specific use case is approved by DPO + CISO | ❌ | ❌ |

## 5. Rules

### 5.1 Always prohibited (any tool, unless specifically approved)
1. Payment card numbers, CVV, or full bank details.
2. Passwords, API keys, tokens, private keys, connection strings.
3. Special-category data (health, ethnicity, religion, sexual orientation, trade-union membership, biometrics) about any individual.
4. Colleague grievance, disciplinary, medical or occupational-health information.
5. Legally privileged advice or litigation material.
6. Unpatched vulnerability or security-architecture details.
7. Data received under a supplier or partner NDA that prohibits third-party processing.

### 5.2 Personal data
8. Before entering personal data into a Class A tool, workers **MUST** ask: *is the personal data necessary for this task?* If not, remove or pseudonymise it.
9. Bulk personal data (more than 50 individuals' records) **MUST NOT** be uploaded without an approved use case and DPIA.
10. GenAI **MUST NOT** be used to profile or make inferences about identifiable customers or colleagues outside approved systems.

### 5.3 Files, connectors and agents
11. Connecting a GenAI tool to mailboxes, drives, CRM or other data sources is permitted only for Class A tools, and retrieval **MUST** respect existing access permissions.
12. Workers **MUST NOT** use GenAI to aggregate data they are entitled to see individually in a way that creates a new, more sensitive dataset (e.g., compiling colleague absence patterns).

### 5.4 Outputs
13. Outputs inherit the **highest classification** of the data used to produce them.
14. Outputs containing personal data **MUST** be stored only in approved repositories and retained per the Retention Schedule.

### 5.5 Prompt hygiene — before you press Enter
| ✔ Check | |
|---|---|
| Am I in an approved tool, logged in with my BrightPath account? | |
| Have I removed names, emails, phone numbers, loyalty IDs and account numbers I don't need? | |
| Does this contain supplier cost prices or terms? → Class A only | |
| Does this contain anything Restricted? → Stop | |
| Will I check the output before relying on it? | |

## 6. Technical Controls

| Control | Implementation | Owner |
|---|---|---|
| CASB category control | Class C GenAI domains: coaching page → block for Confidential uploads | CISO |
| DLP on Class A tenant | Pattern detection for PAN, credentials, NI numbers; block + notify | CISO |
| SSO enforcement | Class A/B tools only reachable via BrightPath identity | IAM |
| Retention & logging | Class A prompts/outputs retained 90 days for investigation | CISO / DPO |
| Admin consent for connectors | Third-party GenAI apps cannot be granted mail/drive scope by users | IAM |

## 7. Incident Handling
If Confidential or Restricted data is entered into the wrong tool, the worker **MUST** report it within **24 hours** via the Service Desk (*AI Incident*). The DPO assesses whether it is a personal data breach requiring ICO / DPC notification within 72 hours.

## 8. Worked Examples

| Scenario | Decision |
|---|---|
| Summarise 300 customer complaints with names and loyalty IDs | Class A only, after removing names and IDs; DPIA if done routinely |
| Ask a public chatbot to improve wording of a public job advert | Permitted (Public data) |
| Upload supplier cost-price spreadsheet to negotiate-prep in Enterprise GenAI | Permitted in Class A only; check supplier NDA |
| Paste a colleague's sickness record to draft an absence letter | ❌ Prohibited — use HR templates |
| Paste a stack trace containing a database connection string into a coding assistant | ❌ Remove the secret first |
