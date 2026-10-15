# AI Development Standards
| Document ID | BPR-STD-AI-003 | Version | 1.0 |
|---|---|---|---|
| Owner | Chief Data Officer | Approved by | Technology Governance Board |
| Effective date | 2026-09-01 | Next review | 2027-03-01 (6-monthly in year one) |
| Classification | Internal | Related | Secure SDLC Standard; Data Classification Standard; Model Risk Tiering Guide |

---

## 1. Purpose
To set minimum, mandatory standards for designing, building, validating, deploying, monitoring and retiring AI systems developed by or for BrightPath, so that internally built AI is reliable, fair, secure, explainable to the degree its use requires, and auditable.

## 2. Scope
All machine-learning models, LLM-based applications (including RAG and agents) and AI features developed by BrightPath teams or by contractors on BrightPath's behalf — including forecasting, replenishment, markdown pricing, personalisation, fraud/loss-prevention and colleague-facing tools.

## 3. Risk Tiers (determine which standards apply)

| Tier | Examples | Standards applicable |
|---|---|---|
| **T1 High** | Dynamic pricing visible to customers; loss-prevention models flagging individuals; colleague scheduling or performance tools | All sections; independent validation; AI Risk Committee approval |
| **T2 Medium** | Demand forecasting; customer personalisation; customer chatbot | All sections; peer validation |
| **T3 Low** | Internal analytics, colleague productivity copilots with no decision impact | Sections 4, 5, 8, 9 |

## 4. Lifecycle Stage Gates

| Gate | Stage | Required artefacts | Approver |
|---|---|---|---|
| G0 | Ideation | Use-case brief; inventory registration; preliminary tier | Product owner + AI Governance |
| G1 | Design | Problem framing; success & harm metrics; data plan; DPIA screening; human-oversight design | Tech lead (+ DPO if personal data) |
| G2 | Build complete | Model card draft; data sheet; experiment log; test results | Tech lead |
| G3 | Pre-production | Validation report; fairness report (T1/T2); security review; monitoring plan; rollback plan | T1: AI Risk Committee · T2: Head of Data Science · T3: Tech lead |
| G4 | Post-deploy review (30 days) | Live performance vs. acceptance criteria | Product owner |
| G5 | Retirement | Decommission plan; data disposal; inventory update | Product owner |

## 5. Data Standards
- **D1** Training, validation and test data **MUST** have documented provenance, lawful basis and licence (data sheet).
- **D2** Personal data **MUST** be minimised; direct identifiers **MUST** be removed unless required and justified in the DPIA.
- **D3** Special-category data and proxies (e.g., postcode as an ethnicity proxy) **MUST** be identified and their use justified or mitigated (T1/T2).
- **D4** Data quality checks (completeness, timeliness, label quality, representativeness across regions and store formats) **MUST** be recorded.
- **D5** Train/test splits **MUST** prevent leakage, including temporal leakage for forecasting models.
- **D6** Restricted data (e.g., cardholder data) **MUST NOT** be used for model development.

## 6. Model Development & Validation
- **M1** Every model **MUST** have a model card: intended use, out-of-scope uses, owners, data, metrics, limitations, fairness results, version.
- **M2** Acceptance criteria **MUST** be defined at G1 before results are known.
- **M3** Models **MUST** be benchmarked against a simple baseline (e.g., seasonal naive for forecasting).
- **M4** T1 models **MUST** be validated by a person independent of the development team.
- **M5** Explainability **MUST** be proportionate: T1 models affecting individuals require local explanations available to reviewers.
- **M6** Experiments, code, data versions and hyperparameters **MUST** be reproducible from the model registry.

## 7. Fairness & Customer Impact
- **F1** T1/T2 models affecting customers or colleagues **MUST** be tested for disparate performance or outcomes across relevant groups and geographies (e.g., store catchment deprivation deciles).
- **F2** Dynamic pricing **MUST NOT** use personal characteristics or inferred vulnerability to set individual prices; price changes **MUST** stay within approved guardrails enforced outside the model.
- **F3** Loss-prevention models **MUST NOT** trigger action against an individual without human review.

## 8. Security Standards
- **S1** AI systems **MUST** follow the Secure SDLC Standard (threat modelling, code review, SAST/SCA, secrets management).
- **S2** Threat models **MUST** cover AI-specific threats: data poisoning, model extraction, adversarial inputs, and — for LLM apps — prompt injection, insecure output handling, sensitive information disclosure and excessive agency (OWASP Top 10 for LLM Applications).
- **S3** LLM applications **MUST** enforce authorisation outside the model; retrieval in RAG **MUST** respect the user's existing access rights.
- **S4** Agents **MUST** use dedicated least-privilege service identities, tool allow-lists, and deterministic limits on consequential actions.
- **S5** Third-party models and libraries **MUST** come from approved sources and be scanned (model files for unsafe serialisation).
- **S6** Model artefacts **MUST** be stored in the access-controlled model registry.

## 9. Deployment, Monitoring & Operations
- **O1** Deployment **MUST** be via CI/CD with registry-gated promotion; manual production deployment is prohibited.
- **O2** Monitoring **MUST** cover input drift, prediction drift, performance against ground truth (when available) and, for T1/T2, fairness metrics.
- **O3** Alert thresholds and owners **MUST** be defined; breach triggers investigation within 5 business days (T1: 1 business day).
- **O4** A **rollback or kill-switch** path **MUST** exist and be tested before G3 for T1/T2.
- **O5** Inputs, outputs and decisions **MUST** be logged with retention per the Records Retention Schedule.
- **O6** Retraining is a change: material changes (new features, data sources, populations) **MUST** re-pass G3.

## 10. Documentation & Records
All gate artefacts **MUST** be stored in the AI system's repository and linked from the AI Inventory.

## 11. Compliance
Non-conformance identified by the AI Governance or Internal Audit teams **MUST** be remediated under the corrective action process. Exceptions follow BPR-POL-AI-001 Section 8.

## Annex A — Model Card Template (minimum fields)
`Model name · Version · Owner · Tier · Intended use · Out-of-scope uses · Training data summary · Evaluation data · Metrics & acceptance criteria · Results · Fairness analysis · Known limitations · Human oversight · Monitoring plan · Approval record`
