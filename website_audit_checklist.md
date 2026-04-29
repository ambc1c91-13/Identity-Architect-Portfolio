# Website Legal, Privacy & Identity Security Audit Checklist

**Version:** 1.0
**Effective Date:** April 28, 2026
**Applies To:** All public-facing websites collecting personal data

---

## Section 1: Policy Presence

| Item | Status |
|------|--------|
| Privacy Policy is published and linked from the footer and/or homepage | `[ ]` |
| Terms of Service is published and linked from the footer and/or homepage | `[ ]` |
| Cookie Policy exists (standalone or integrated into Privacy Policy) | `[ ]` |
| All policy links are functional — no 404s, empty pages, or redirect loops | `[ ]` |
| Each policy displays an **Effective Date** and **Last Updated** date | `[ ]` |
| Legal entity name is disclosed (full organization or DBA name) | `[ ]` |
| Privacy/legal contact email or mailing address is published | `[ ]` |

---

## Section 2: Privacy Policy Content

### 2.1 Data Collection
- [ ] Categories of personally identifiable information (PII) collected are explicitly listed
- [ ] Methods of collection are described (e.g., contact forms, cookies, analytics, applications)
- [ ] Sensitive data categories are flagged and explained (financial, health, household, eligibility)
- [ ] Passive data collection (IP address, device type, session data) is disclosed

### 2.2 Data Usage & Legal Basis
- [ ] Purpose(s) for processing personal data are clearly stated
- [ ] Legal basis for processing is identified (consent, legitimate interest, legal obligation, contract)
- [ ] Data is not used beyond the disclosed purposes without additional consent

### 2.3 Data Sharing & Third Parties
- [ ] Third-party service providers are named or categorized (hosting, CRM, analytics, email)
- [ ] Data shared with partners, funders, or government agencies is disclosed
- [ ] A statement confirms personal data is **not sold** (or clearly discloses if it is)
- [ ] All processors are subject to binding data protection agreements (DPAs)

### 2.4 Data Retention
- [ ] Retention periods are defined per data category
- [ ] Deletion or anonymization procedures after retention period are described
- [ ] Application or program data retention periods are specifically addressed (if applicable)

### 2.5 User Rights
- [ ] Right to **access** personal data is stated
- [ ] Right to **deletion** (erasure) is stated
- [ ] Right to **correction** of inaccurate data is stated
- [ ] Right to **data portability** is stated (GDPR)
- [ ] Right to **opt out** of targeted advertising or data sale is stated (CCPA)
- [ ] A rights request mechanism is provided (email address, webform, or both)
- [ ] Response timeframe for rights requests is stated (e.g., 30 days under CCPA, 1 month under GDPR)

### 2.6 Cookies & Tracking
- [ ] Cookie types used are listed (strictly necessary, analytics, marketing, functional)
- [ ] Specific tools are named (e.g., Google Analytics, Meta Pixel, Hotjar)
- [ ] Opt-out instructions for non-essential cookies are provided
- [ ] Cookie banner/consent mechanism is present before non-essential cookies fire

### 2.7 Data Security
- [ ] Security measures are described (encryption, access controls, audits)
- [ ] Breach notification commitment is stated (72-hour notice under GDPR; state law timelines)
- [ ] Contact method for security incidents is provided

### 2.8 Compliance-Specific Language
- [ ] **GDPR:** Data Protection Officer (DPO) contact included (if required)
- [ ] **GDPR:** Right to lodge complaint with supervisory authority is stated
- [ ] **CCPA:** "Do Not Sell or Share My Personal Information" opt-out link present (if applicable)
- [ ] **COPPA:** Children's privacy section present; states site is not directed to children under 13
- [ ] **CalOPPA:** Discloses how the site responds to Do Not Track signals

---

## Section 3: Terms of Service Content

- [ ] Acceptance clause is clearly stated (use = agreement)
- [ ] Eligibility requirements stated (minimum age, jurisdiction)
- [ ] Services offered are described with scope and limitations
- [ ] Prohibited user conduct is explicitly listed
- [ ] Intellectual property ownership and usage restrictions are defined
- [ ] Submitted content clause covers applications, forms, and user-generated material
- [ ] Disclaimer of warranties is present ("AS IS" language)
- [ ] Limitation of liability clause is included
- [ ] Indemnification clause is included
- [ ] Governing law and jurisdiction are stated
- [ ] Dispute resolution process is described (arbitration, litigation, mediation)
- [ ] Change/amendment notification procedure is stated
- [ ] Account suspension or termination conditions are defined (if accounts exist)

---

## Section 4: Identity & Authentication Security

### 4.1 Account Management
- [ ] Account creation requires verified email or phone
- [ ] Password complexity requirements are enforced (minimum length, character mix)
- [ ] Multi-factor authentication (MFA/2FA) is offered or required
- [ ] Account lockout policy is enforced after failed login attempts
- [ ] Password reset flows use time-limited, single-use tokens
- [ ] Users can view and manage active sessions

### 4.2 Session Management
- [ ] Sessions time out after a defined period of inactivity
- [ ] Logout terminates the server-side session (not just clears the cookie)
- [ ] Session tokens are regenerated after authentication events
- [ ] Sensitive operations require re-authentication

### 4.3 Credential Hygiene
- [ ] Passwords are stored as salted hashes (bcrypt, Argon2, PBKDF2) — never plaintext
- [ ] Credential breach monitoring is in place (e.g., HaveIBeenPwned API integration)
- [ ] Admin and privileged accounts are protected by MFA
- [ ] Default credentials are changed on all systems and integrations

### 4.4 Identity Lifecycle (IAM/CIAM)
- [ ] User provisioning process is defined (how accounts are created)
- [ ] User deprovisioning process is defined (how accounts are deleted or disabled)
- [ ] Role-based access control (RBAC) is applied — users only access what they need
- [ ] Privileged access is reviewed and recertified periodically
- [ ] Third-party/vendor identity access is inventoried and scoped

---

## Section 5: Technical Security Controls

### 5.1 Transport & Encryption
- [ ] HTTPS/TLS is enforced site-wide (no HTTP fallback)
- [ ] HTTP Strict Transport Security (HSTS) header is present
- [ ] TLS certificate is valid and not expired
- [ ] No mixed content (HTTP assets on HTTPS pages)
- [ ] Data at rest is encrypted (databases, file storage, backups)

### 5.2 HTTP Security Headers
- [ ] `Content-Security-Policy (CSP)` header is configured
- [ ] `X-Frame-Options` or `frame-ancestors` CSP directive is set (prevents clickjacking)
- [ ] `X-Content-Type-Options: nosniff` is present
- [ ] `Referrer-Policy` is configured
- [ ] `Permissions-Policy` is configured (limits browser feature access)

### 5.3 Cookie Security
- [ ] Session and auth cookies have the `Secure` flag set
- [ ] Session and auth cookies have the `HttpOnly` flag set
- [ ] Cookies have the `SameSite` attribute set (`Strict` or `Lax`)
- [ ] Cookie expiration is appropriately scoped

### 5.4 Application Security
- [ ] Forms are protected against Cross-Site Request Forgery (CSRF)
- [ ] Inputs are validated and sanitized (prevent XSS and SQL injection)
- [ ] Sensitive data is not exposed in URL query strings
- [ ] Error messages do not expose stack traces or system information
- [ ] Security.txt file is present at `/.well-known/security.txt`

---

## Section 6: Consent & Cookie Compliance

- [ ] Cookie consent banner appears before any non-essential cookies fire
- [ ] Consent is **opt-in** for GDPR jurisdictions (pre-ticked boxes are non-compliant)
- [ ] Consent is **granular** — users can accept/reject by category
- [ ] Consent records are logged with timestamp, version, and user identifier
- [ ] Users can withdraw consent as easily as they gave it
- [ ] CCPA opt-out link ("Do Not Sell or Share") is accessible on all pages (if applicable)
- [ ] Cookie audit has been performed — all cookies are inventoried and categorized

---

## Section 7: Operational & Governance Compliance

### 7.1 Policy Maintenance
- [ ] Privacy Policy is reviewed and updated at least annually
- [ ] Terms of Service is reviewed and updated at least annually
- [ ] Material policy changes are communicated to users before taking effect
- [ ] Archived versions of prior policies are retained

### 7.2 Vendor & Third-Party Risk
- [ ] Data Processing Agreements (DPAs) are in place with all vendors handling PII
- [ ] Third-party integrations are inventoried (analytics, CRM, payment, email)
- [ ] Vendor security posture is periodically reviewed
- [ ] Subprocessors are listed or disclosed as required by GDPR

### 7.3 Incident Response
- [ ] Incident response plan is documented and accessible to relevant staff
- [ ] Breach notification procedures comply with applicable law (GDPR 72-hour rule, state laws)
- [ ] Security contact or responsible disclosure channel is published
- [ ] Breach simulation or tabletop exercise has been conducted

### 7.4 Staff & Training
- [ ] Staff with access to PII are trained on data handling procedures
- [ ] Role-specific data governance policies are communicated
- [ ] Access is provisioned on a least-privilege basis

---

## Section 8: CISSP Domain Cross-Reference

| Checklist Area | CISSP Domain |
|----------------|-------------|
| Policy presence, legal compliance, risk disclosure | Domain 1 — Security & Risk Management |
| Data classification, retention, third-party sharing | Domain 2 — Asset Security |
| HTTPS, headers, cookie flags, application controls | Domain 3 — Security Architecture & Engineering |
| Transport encryption, TLS, data at rest | Domain 3 — Security Architecture & Engineering |
| Authentication, MFA, session management | Domain 5 — Identity & Access Management |
| Vendor DPAs, subprocessor inventory | Domain 6 — Security Assessment & Testing |
| Incident response, breach notification, monitoring | Domain 7 — Security Operations |

---

## Audit Summary

| Section | Items Reviewed | Items Passed | Items Failed | Notes |
|---------|---------------|-------------|-------------|-------|
| 1 — Policy Presence | 7 | | | |
| 2 — Privacy Policy Content | 30 | | | |
| 3 — Terms of Service | 14 | | | |
| 4 — Identity & Auth Security | 17 | | | |
| 5 — Technical Security | 18 | | | |
| 6 — Consent & Cookie Compliance | 7 | | | |
| 7 — Operational & Governance | 13 | | | |
| **TOTAL** | **106** | | | |

---

*Prepared by: ___________________________*
*Audit Date: ___________________________*
*Website Reviewed: ___________________________*
*Next Review Date: ___________________________*
