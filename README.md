# Identity-Architect-Portfolio
A working portfolio documenting the intersection of **identity security**,
**privacy compliance**, and **IAM/CIAM architecture** built by a Security
Operations Engineer on the path to Identity Security Architect.

This repository contains audit frameworks, reusable policy templates, gap
analyses, and CISSP domain mappings derived from real-world engagements with
public-facing web properties (anonymized). All artifacts are designed to be
reusable across any organization conducting a legal, privacy, or identity
security review.

---

## Contents

| Artifact | Description |
|---|---|
| [Website Audit Checklist](./website_audit_checklist.md) | 106-item legal, privacy & identity security audit framework across 7 sections |
| [Privacy Policy Template](./privacy_policy_template.md) | 15-section template with GDPR, CCPA, COPPA, and CalOPPA coverage |
| [Terms of Service Template](./terms_of_service_template.md) | 16-section ToS template with identity, credential, and application security clauses |
| [Gap Analysis](./gap_analysis.md) | Anonymized findings from two public web properties with prioritized remediation roadmap |
| [CISSP + IAM/CIAM Mapping](./cissp_iam_mapping.md) | Framework mapping to CISSP Domains 1, 2 & 7 and full IAM/CIAM lifecycle architecture |

---

## Project: Website Legal, Privacy & Identity Security Audit

### Background
A structured 6-phase audit evaluating the legal, privacy, and identity
security posture of two anonymized US-based websites, a B2B consulting
platform and a nonprofit community services platform with an applicant
intake workflow.

### Methodology
The audit was conducted across six phases:
1. **Policy Presence & Coverage** - Confirmed whether Privacy Policy and Terms of Service existed and were functional
2. **Deep Policy Review** - Evaluated data collection, usage, sharing, user rights, security language, and legal compliance indicators
3. **Gap Analysis** - Identified missing elements, legal risks, and identity security exposures
4. **Template Creation** - Produced reusable Privacy Policy, Terms of Service, and audit checklist artifacts
5. **Cross-Site Comparison** - Compared both sites across compliance posture, PII sensitivity, and identity risk
6. **CISSP + Identity Architecture Mapping** - Mapped all findings to CISSP domains and IAM/CIAM lifecycle frameworks

### Key Findings
- Site B (nonprofit platform) had **zero legal documentation** despite collecting sensitive financial and eligibility PII - a critical CCPA, GDPR, and FTC Act violation
- Neither site had a confirmed cookie consent mechanism
- Site B's application status workflow implied user accounts with no disclosed session management, credential policy, or identity lifecycle governance
- All findings were mapped to CISSP Domains 1, 2, and 7 and to CIAM consent and provisioning lifecycle stages

### Frameworks & Standards Applied
`GDPR` `CCPA` `CalOPPA` `COPPA` `FTC Act Section 5` `CISSP CBK` `IAM/CIAM` `Data Governance` `Identity Architecture`

---

## About

Built by a Security Operations Engineer pursuing Identity Security
Architecture. All client and site information is anonymized.
Artifacts are intended to be reusable across any organization.

Connect on [LinkedIn](www.linkedin.com/in/aim-b-22407a123) |
Read on [Medium](https://medium.com/@sigilcraftsec)
