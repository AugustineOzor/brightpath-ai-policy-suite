# Policy-to-Gap Mapping
**BrightPath Retail Group** · Document ID: BPR-AIG-MAP-001 · Version 1.0 · Owner: Head of AI Governance

---

## 1. Purpose
Demonstrates that each policy clause exists for a reason. Every gap identified in the baseline assessment is traced to the clause(s) that close it, the enforcement mechanism, and the framework requirement it satisfies. This is the document an auditor or regulator uses to test that the policy suite is **complete and proportionate**.

## 2. Baseline Evidence Sources
14 stakeholder interviews · employee survey (n = 1,212) · CASB 90-day data · review of 11 existing policies · procurement records (24 months) · 2 incident reports.

**Selected survey and telemetry findings**

| Finding | Value |
|---|---|
| Employees using GenAI for work at least weekly | 58% |
| …of whom using personal accounts | 71% |
| Believed it was "allowed" or "not covered" | 83% |
| Monthly uploads to consumer GenAI flagged by DLP as Confidential | ~410 |
| AI-enabled SaaS products bought without security review | 9 of 11 |

## 3. Gap Register & Mapping

| Gap ID | Gap identified | Evidence | Risk | Closing clause(s) | Enforcement / detection | ISO/IEC 42001 | NIST AI RMF | Status |
|---|---|---|---|---|---|---|---|---|
| G-01 | No definition of which AI tools are permitted | Interviews; survey (83% unsure) | Data leakage, inconsistent practice | AUP 4.1(1–3) | AI Tool Register; CASB | 5.2, A.2.2 | GV-1.1 | Closed |
| G-02 | Staff use personal accounts on consumer GenAI | CASB; survey | Loss of control of company data | AUP 4.1(2); GenAI-DP §3, §4 | SSO; CASB block for Class C | A.9.2 | GV-1.2 | Closed |
| G-03 | Confidential supplier data entered into public chatbot | Incident INC-2207 | Contract breach; competition risk | GenAI-DP §4, 5.1(7) | DLP; coaching page | A.7.2, A.9.2 | MP-4.1 | Closed |
| G-04 | No rules on personal data in prompts | DPO review | UK GDPR breach | GenAI-DP 5.2 | DLP; DPIA trigger | A.7.4 | GV-1.1 | Closed |
| G-05 | Unapproved browser extensions and meeting bots | Endpoint inventory (210 installs) | Silent exfiltration | AUP 4.1(4); GenAI-DP 5.3(11) | Extension allow-list; admin consent | A.9.2 | GV-6.1 | Closed |
| G-06 | AI outputs published without review (incl. incorrect allergen claim on web) | Incident INC-2231 | Customer safety; regulatory | AUP 4.3(7–9) | Content workflow approval step | A.9.3, A.9.4 | MG-2.2 | Closed |
| G-07 | No prohibition on AI in HR decisions | Recruiting team piloting CV ranking | Discrimination; Art. 22 | AUP 4.4 P1; Dev Std F1 | HR system approval; procurement gate | A.5.4, A.9.4 | MP-5.1 | Closed |
| G-08 | No AI screening in procurement | Procurement records | Unassessed vendors | Proc 3.1(1–2) | Mandatory question in P2P system | A.10.3 | GV-6.1 | Closed |
| G-09 | P-card and expense purchases bypass review | Finance data | Shadow AI | Proc 3.1(2) | Merchant alerting | A.10.3 | GV-6.1 | Partial — expense alerting live Q4 |
| G-10 | Vendors may train on BrightPath data | Contract review (6 of 11 silent) | IP and data loss | Proc 3.3 data use; 3.4 C1 | Contract template | A.10.3, A.7.5 | GV-6.1 | Closed |
| G-11 | AI features enabled in existing SaaS without notice | Release-note review | Unassessed processing | Proc 3.1(3); 3.4 C2 | CAB checklist | A.10.3, A.6.2.5 | GV-6.2 | Partial — legacy contracts at renewal |
| G-12 | No standard for internally built models | Data science interviews | Unreliable / unfair models | Dev Std §4–9 | Stage gates in MLOps pipeline | A.6.1.2–A.6.2.8 | MS-2.x | Closed |
| G-13 | Markdown pricing model has no guardrails or fairness review | Model review | Consumer harm; reputational | Dev Std F2, O4 | Price-guardrail service | A.5.4, A.6.2.4 | MS-2.11 | Closed |
| G-14 | Loss-prevention alerts acted on without human review | Store ops interview | Wrongful accusation | Dev Std F3; AUP P2 | Case-management workflow | A.9.3 | MG-2.4 | Closed |
| G-15 | No AI-specific threat modelling for LLM apps | AppSec review | Prompt injection; data leakage | Dev Std S2–S4 | Threat-model template; pen test | A.6.2.4 | MS-2.7 | Closed |
| G-16 | No AI incident reporting route | Service-desk categories | Undetected harm | AUP 4.6; GenAI-DP §7 | Service-desk category | A.8.4, A.3.3 | MG-4.3 | Closed |
| G-17 | No AI literacy training | L&D catalogue | Misuse through ignorance; EU AI Act Art. 4 | AUP §6 | LMS completion tracking | 7.2, 7.3 | GV-2.2 | Partial — 87% complete |
| G-18 | No customer disclosure of chatbot use | Website review | Transparency; EU AI Act Art. 50 | AUP 4.5(11) | Chatbot UI banner | A.8.2 | GV-4.2 | Closed |

*GV = GOVERN, MP = MAP, MS = MEASURE, MG = MANAGE.*

## 4. Coverage Check — ISO/IEC 42001 Annex A.2

| Control | Requirement | Evidence |
|---|---|---|
| A.2.2 AI policy | Documented AI policy | Four policies + group statement |
| A.2.3 Alignment with other organisational policies | AI policy aligned with security, privacy, procurement policies | Architecture (README §4); cross-references in each document header |
| A.2.4 Review of the AI policy | Planned review intervals | Review dates in each header; 6-monthly in year one |

## 5. Residual Gaps & Next Steps

| Gap | Remaining action | Owner | Target |
|---|---|---|---|
| G-09 | Expense-system AI merchant alerting | Finance Systems | 2026-12-31 |
| G-11 | Insert C2 change-notification clause at renewal for 7 legacy contracts | Procurement | Rolling to 2027-06 |
| G-17 | Reach 95% completion; launch role-based modules | L&D | 2026-12-31 |
