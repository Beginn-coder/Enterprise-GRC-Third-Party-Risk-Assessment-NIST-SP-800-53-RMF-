# Enterprise-GRC-Third-Party-Risk-Assessment-NIST-SP-800-53-RMF-
A real-world Governance, Risk, and Compliance (GRC) assessment and Plan of Action and Milestones (POA&amp;M) remediation project evaluating a third-party cloud EdTech vendor against federal security control baselines 

## 📌 Executive Summary

Modern enterprise IT environments heavily rely on third-party SaaS vendors. However, onboarding vendor technologies introduces operational, regulatory, and data privacy risks—especially within public sector environments managing sensitive student PII (Personally Identifiable Information).

This project simulates an enterprise **Cybersecurity & Third-Party Risk Assessment** conducted for the **New York City Department of Education (NYC DOE)**. It covers the evaluation of a third-party EdTech analytics platform (*CloudEd Solutions*), the identification of security control deficiencies, and the creation of an actionable **POA&M (Plan of Action & Milestones)** tracker to guide risk mitigation and continuous monitoring.

---

## 🎯 Target System & Scope

* **Assessed System:** CloudEd Solutions (*EdTech Student Analytics SaaS*)
* **Assessing Body:** NYC DOE Information Security & Risk Management Division
* **Data Classification:** Confidential / High-Impact (PII, FERPA, COPPA Compliance Scope)
* **Assessment Frameworks:** 
  * **NIST SP 800-53 Rev. 5:** *Security and Privacy Controls for Information Systems and Organizations*
  * **NIST SP 800-37 Rev. 2:** *Risk Management Framework (RMF) for Information Systems and Organizations*
  * **NIST SP 800-30 Rev. 1:** *Conducting Risk Assessments*

---

## 📊 Risk Scoring & Assessment Methodology

Security findings were evaluated based on **Likelihood vs. Impact Matrix** following NIST SP 800-30 criteria:

| Severity | Description | Action Required |
| :--- | :--- | :--- |
| 🔴 **High** | Critical control failure impacting data confidentiality, integrity, or key authentication mechanisms. | Immediate remediation required (< 30 days) or system authorization suspended. |
| 🟡 **Medium** | Moderate control gap violating organizational baselines or operational policies. | Remediation required within 60–90 days with approved compensating controls. |
| 🟢 **Low** | Minor procedural or operational non-compliance with minimal systemic risk. | Remediated during standard release/patch cycles (< 120 days). |

---

## 📝 Findings & POA&M Tracker Summary

Below is an overview of the security findings identified during the control audit and third-party vendor review:

| Finding ID | NIST Control | Control Name | Domain | Description of Deficiency | Risk Level | Target Completion | Status |
| :--- | :--- | :--- | :--- | :--- | :---: | :---: | :---: |
| **FIND-2026-001** | `IA-2(1)` | Multi-Factor Authentication | TPRM / Identity | Vendor cloud portal administrative accounts lack enforced Multi-Factor Authentication (MFA). | 🔴 **High** | 2026-11-15 | In Progress |
| **FIND-2026-002** | `SC-13` | Cryptographic Protection | Data Protection | Vendor database storing student PII uses AES-128 encryption instead of required AES-256 baseline. | 🟡 **Medium** | 2026-12-01 | In Progress |
| **FIND-2026-003** | `AU-2` | Event Logging | Audit & Logging | SaaS user application logs retained for only 30 days locally (fails NIST 1-year retention baseline). | 🟡 **Medium** | 2026-11-30 | In Progress |
| **FIND-2026-004** | `CA-3` | Information Exchange | TPRM / Governance | Vendor utilizes a 4th-party analytics sub-processor without prior SOC 2 Type II or DPA review. | 🔴 **High** | 2026-10-31 | In Progress |
| **FIND-2026-005** | `AC-2(3)` | Inactivity Disablement | Access Control | Inactive vendor platform accounts disabled after 90 days (DOE policy mandates 45 days). | 🟢 **Low** | 2026-11-10 | In Progress |
| **FIND-2026-006** | `CP-9` | Contingency Planning | Continuity | Vendor has not conducted an annual Disaster Recovery (DR) restoration test in 14 months. | 🟡 **Medium** | 2026-12-15 | Open |

---

## 🛠️ Deep-Dive Analysis & Compensating Controls

### 1. Missing Administrative MFA (`IA-2(1)`)
* **Core Issue:** Administrative accounts on the vendor platform relied on single-factor password authentication, exposing administrative privileges to credential stuffing and phishing attacks.
* **Remediation Plan:** Enforce SAML 2.0 Single Sign-On (SSO) integration with NYC DOE Entra ID, mandating FIDO2/phishing-resistant MFA.
* **Compensating Control (Interim):** Strict IP whitelisting restricted to DOE administrative subnets and automated session timeouts capped at 15 minutes.

### 2. Fourth-Party Sub-Processor Governance (`CA-3`)
* **Core Issue:** Vendor routed anonymized usage data through a data analytics sub-processor without verifying the sub-processor's security posture or executing a formal Data Protection Agreement (DPA).
* **Remediation Plan:** Require the vendor to submit the sub-processor’s annual SOC 2 Type II report, conduct a vendor assessment, and execute an explicit DPA outlining data handling restrictions.
* **Compensating Control (Interim):** Verification of client-side data masking and anonymization protocols before data ingestion by the sub-processor.

---

## 📁 Repository Artifacts

* [NYC DOE GRC Vendor Risk Assessment & POA&M Tracker (Spreadsheet)](https://docs.google.com/spreadsheets/d/1C3LCSk5oWwI9c8fWyE5L7HAj7WUkIqnm3O2ZkG28cgg/edit?usp=drivesdk): Full enterprise POA&M spreadsheet containing complete risk matrices, control mappings, owner assignments, and milestone tracking.
* [Vendor_Security_Assessment_Report.pdf](./Vendor_Security_Assessment_Report.pdf): Executive risk summary report intended for technical leaders and business stakeholders.

---

## 🚀 Key Takeaways & Demonstrated Competencies

Through this project, key competencies demonstrated include:
* **Framework Alignment:** Mapping technical vulnerabilities and architectural gaps to NIST SP 800-53 Rev. 5 controls and RMF lifecycle steps.
* **Third-Party Risk Management (TPRM):** Evaluating SaaS vendor compliance, SOC 2 reports, and sub-processor supply chain risk.
* **Risk Reporting & Stakeholder Bridge:** Translating complex technical audit findings into actionable business risk reports with clear remediation timelines and milestone tracking.
* **GRC Tooling Proficiency:** Building structured, enterprise-ready risk trackers in Excel/ServiceNow formats
