# CISSP Domain & Identity Architecture Mapping

**Version:** 1.0
**Created:** April 2026
**Context:** Derived from a structured legal, privacy, and identity security audit of two anonymized public-facing websites. Maps audit findings and skills developed to CISSP CBK domains and Identity Architecture frameworks.

> This document serves two purposes: (1) a professional reference mapping real-world audit work to industry frameworks, and (2) a study and career development artifact for practitioners pursuing Identity Security Architecture roles.

---

## Part 1: CISSP Domain Mapping

The (ISC)² CISSP Common Body of Knowledge (CBK) is organized into eight domains. This audit touched three domains most directly, with secondary connections to others.

### Domain 1 — Security and Risk Management

**Weight in CISSP exam:** ~15% (largest single domain)

This domain covers the legal, regulatory, ethical, and policy foundations of information security. It is the domain most directly exercised by this audit.

#### Audit Activities Mapped to Domain 1

| Audit Activity | Domain 1 Concept |
|---|---|
| Identifying absent Privacy Policy as a legal violation | Legal and regulatory issues that affect information security |
| Evaluating GDPR, CCPA, CalOPPA, FTC Act Section 5 compliance | Understand and comply with applicable laws and regulations |
| Assessing policy presence and document completeness | Security governance — policies, standards, procedures, guidelines |
| Prioritizing remediation by severity (Critical → Medium) | Risk assessment and risk treatment |
| Documenting findings for stakeholder communication | Security awareness and documentation |
| Building reusable templates and checklists | Security policy development |
| Identifying data collection without consent as a risk | Privacy principles and data governance |

#### Key Domain 1 Concepts Reinforced

- **Due care vs. due diligence:** Publishing a Privacy Policy is due care (taking reasonable precautions). Regularly auditing it against current law is due diligence.
- **Legal liability:** Organizations processing PII without a Privacy Policy face regulatory enforcement, civil litigation, and reputational damage — all risk quantification scenarios.
- **Privacy by design:** The absence of a privacy policy from the initial design of an applicant workflow is a failure of privacy-by-design principles — a core Domain 1 concept.
- **Security governance:** The audit checklist and templates are governance artifacts — they define what "good" looks like and create accountability.

---

### Domain 2 — Asset Security

**Weight in CISSP exam:** ~10%

This domain covers data classification, ownership, retention, and the secure handling of information assets throughout their lifecycle.

#### Audit Activities Mapped to Domain 2

| Audit Activity | Domain 2 Concept |
|---|---|
| Distinguishing B2B contact data (medium sensitivity) from financial/eligibility data (high sensitivity) | Data classification |
| Identifying that Site B collects sensitive PII with no retention policy | Data lifecycle management — retention and disposal |
| Flagging undisclosed third-party processor relationships | Asset ownership and custodianship |
| Noting that application data has no defined destruction schedule | Secure disposal and end-of-life data handling |
| Identifying that consent is never captured for data collection | Data handling requirements — collection limitation principle |
| Assessing that no DPAs exist with vendors | Third-party data handling obligations |

#### Key Domain 2 Concepts Reinforced

- **Data classification:** Not all data is equal. An email address from a contact form and a household income figure in an eligibility application must be classified differently — and protected accordingly.
- **Data ownership vs. custodianship:** The organization (owner) determines classification and policy; vendors/processors (custodians) must implement it under binding agreements.
- **Retention and disposal:** Data kept longer than necessary is excess liability. Defining retention periods in policy is a Domain 2 control.
- **Collection limitation:** The principle that organizations should collect only the minimum data necessary for a defined purpose is violated when no purpose is documented.

---

### Domain 7 — Security Operations

**Weight in CISSP exam:** ~13%

This domain covers the day-to-day operational security activities including monitoring, incident response, patch management, and identity operations.

#### Audit Activities Mapped to Domain 7

| Audit Activity | Domain 7 Concept |
|---|---|
| Flagging absence of breach notification commitment | Incident response — notification and communication |
| Recommending security header audit (CSP, HSTS, X-Frame) | Configuration management and patch management |
| Identifying broken policy links as an operational failure | Change management and configuration control |
| Noting that session management is undocumented for applicant accounts | Identity and access management operations |
| Recommending credential breach monitoring (HaveIBeenPwned) | Threat intelligence and operational monitoring |
| Identifying need for account lockout policy | Access control operations — failed authentication response |
| Recommending security.txt file | Vulnerability disclosure and responsible operations |

#### Key Domain 7 Concepts Reinforced

- **Incident response lifecycle:** Detect → Contain → Eradicate → Recover → Post-Incident Review. The audit's recommendation for a breach notification commitment maps to the Communicate phase of this lifecycle.
- **Configuration management:** Security headers (CSP, HSTS, Referrer-Policy) are configuration items that must be audited, baselined, and maintained — a Domain 7 operations responsibility.
- **Identity operations:** Provisioning, deprovisioning, session management, and access recertification are ongoing Domain 7 operational activities, not one-time setup tasks.

---

### Secondary Domain Connections

| Domain | Connection to This Audit |
|---|---|
| **Domain 3 — Security Architecture & Engineering** | HTTP headers (CSP, HSTS), TLS enforcement, cookie security flags, and HTTPS-everywhere are security engineering controls identified in the checklist |
| **Domain 4 — Communication & Network Security** | TLS/HTTPS, Secure cookie transport, and data-in-transit encryption recommendations |
| **Domain 5 — Identity & Access Management** | MFA, session timeout, RBAC, account lifecycle, and credential management recommendations map directly to Domain 5 |
| **Domain 6 — Security Assessment & Testing** | The audit itself is a security assessment. Vendor DPA review, cookie auditing, and header scanning are assessment and testing activities |

---

## Part 2: Identity Architecture Framework Mapping

Identity Architecture operates at the intersection of security engineering, enterprise architecture, and user experience. Two primary frameworks apply to this audit:

---

### IAM — Identity and Access Management (Internal Focus)

IAM governs how an organization manages identities and access for its workforce, systems, and services. While these sites are externally facing, IAM principles apply to their internal administration and backend operations.

#### IAM Concepts Surfaced in This Audit

| Finding | IAM Concept |
|---|---|
| Administrative access to CMS/backend with no disclosed MFA policy | Privileged Access Management (PAM) |
| No defined process for onboarding/offboarding staff access to site systems | Joiner-Mover-Leaver (JML) lifecycle |
| No vendor access inventory or third-party access controls | Third-party identity governance |
| No RBAC model disclosed for who can access applicant data | Role-Based Access Control (RBAC) |
| No access recertification process mentioned | Periodic access review / attestation |

#### IAM Lifecycle Model (Joiner-Mover-Leaver)

```
JOINER                    MOVER                     LEAVER
------                    -----                     ------
Staff hired            →  Role changes            →  Staff departs
Account provisioned       Permissions updated         Account disabled
Access granted            Access adjusted             Access revoked
Credentials issued        Re-authentication           Credentials invalidated
                          required
```

**Audit relevance:** Neither site documents this lifecycle for staff or vendor access. For Site B, the applicant workflow creates an external identity (CIAM) that follows a parallel lifecycle — and it too is entirely undocumented.

---

### CIAM — Customer Identity and Access Management (External Focus)

CIAM governs how organizations manage identity for external users — customers, applicants, citizens, or members. It adds consent management, self-service capabilities, and privacy-by-design requirements to standard IAM.

Site B's application workflow is a **textbook CIAM use case**: a member of the public creates an identity, submits personal data, and tracks a process outcome — all through a web interface.

#### CIAM Lifecycle for Site B's Application Workflow

```
DISCOVERY          REGISTRATION        AUTHENTICATION     AUTHORIZATION
---------          ------------        --------------     -------------
User finds site →  Submits form    →   Returns to     →   Can view own
Learns about       Personal data       check status       application
program            collected           Session created     status only
                   Identity created    Credentials used    Not others'


CONSENT            DATA USE            DEPROVISIONING
-------            --------            --------------
Should be          Application data    Account/record
captured here  →   processed       →   deletion or
(currently         Shared with         archival after
absent)            partners?           program end
                   Retained how long?  (not documented)
```

#### CIAM Failure Points in Site B

| CIAM Stage | Requirement | Site B Status |
|---|---|---|
| Discovery | Site explains what data is collected before user engages | ❌ No policy exists |
| Registration | Informed consent captured before PII collection | ❌ No consent mechanism |
| Authentication | Credential requirements and MFA options disclosed | ❌ Not disclosed |
| Session Management | Session timeout and security behavior documented | ❌ Not documented |
| Authorization | Applicants can only access their own data (least privilege) | ❓ Unverifiable |
| Data Use | Data usage, sharing, and retention disclosed | ❌ Not disclosed |
| Rights Management | Users can request access, correction, or deletion | ❌ No mechanism |
| Deprovisioning | Account/data lifecycle after program completion defined | ❌ Not defined |

---

### Data Governance Framework Mapping

Data governance defines the policies, processes, and accountability structures that ensure data is trustworthy, protected, and used appropriately.

| Governance Pillar | This Audit's Findings |
|---|---|
| **Data Inventory** | Neither site has a disclosed inventory of data collected, stored, or shared |
| **Data Classification** | Neither site classifies data by sensitivity — Site B collects highly sensitive data without any classification framework |
| **Data Ownership** | No data owner or DPO is identified at either site |
| **Data Quality** | No accuracy or correction mechanism is available at Site B despite collecting eligibility-critical information |
| **Data Retention** | No retention schedules are defined or disclosed at either site |
| **Data Access** | No access control policy governs who can access applicant data at Site B |
| **Data Sharing** | Third-party data sharing is undisclosed at both sites |
| **Consent Management** | No consent management platform or mechanism exists at either site |
| **Breach Response** | No breach response procedure is documented at either site |

---

## Part 3: Identity Security Architect Career Mapping

This section explains how this audit project builds skills directly relevant to an Identity Security Architect role.

### Core Architect Competencies Developed

| Competency | How This Audit Builds It |
|---|---|
| **Requirements Engineering** | Translating legal mandates (GDPR, CCPA) into technical and procedural controls (consent banners, session timeouts, MFA) |
| **Threat Modeling** | Identifying that a missing privacy policy is not just a legal risk — it signals undefined trust boundaries and ungoverned data flows that create attack surfaces |
| **Risk Communication** | Producing a gap analysis with severity ratings (Critical / High / Medium) that engineering, legal, and leadership teams can act on |
| **Framework Fluency** | Demonstrating ability to map practical findings to CISSP, IAM, CIAM, and data governance frameworks simultaneously |
| **Architecture Documentation** | Producing reusable artifacts (checklist, templates, mapping document) that define the "should be" state — a core architect deliverable |
| **Cross-Domain Thinking** | Connecting privacy policy absence → CIAM consent failure → IAM lifecycle gap → Domain 1 governance failure in a single analytical thread |

### Role Progression Relevance

| Role Level | Skills Demonstrated by This Project |
|---|---|
| **Security Analyst** | Identifying gaps, documenting findings, creating checklists |
| **Security Engineer** | Translating findings into technical control recommendations (headers, MFA, session management) |
| **IAM Engineer** | Mapping application workflows to identity lifecycle stages (provisioning, session, deprovisioning) |
| **Identity Architect** | Designing the governance framework, compliance posture, and CIAM architecture that would remediate all findings |
| **CISO / vCISO** | Communicating risk in business terms and prioritizing remediation by organizational impact |

---

*This document is part of the Identity-Architect-Portfolio. All site-specific findings reference anonymized subjects. Templates and checklists referenced are available in the `/templates` and `/checklists` directories of this repository.*
