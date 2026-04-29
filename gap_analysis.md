# Privacy & Identity Security Audit — Gap Analysis

**Audit Date:** April 2026
**Auditor:** Security Operations Engineer (Identity Architecture Practice)
**Sites Reviewed:** Site A (B2B Consulting Platform) | Site B (Nonprofit Community Services Platform)
**Classification:** Portfolio Artifact — Client Information Anonymized

> **Note:** Both sites have been anonymized to protect organizational identity. Site A refers to a professional consulting and brand strategy platform. Site B refers to a community-facing nonprofit platform with an applicant intake and eligibility workflow. All findings are based on publicly observable site behavior, footer links, page structure, and policy content as of the audit date.

---

## Executive Summary

This gap analysis documents the findings of a structured 6-phase legal, privacy, and identity security audit of two U.S.-based public-facing websites. The audit evaluated policy presence, privacy and legal document quality, technical security posture, and identity/authentication controls.

**Key findings:**

- **Site A** has both a Privacy Policy and Terms of Service present. Full policy text depth could not be confirmed without authenticated access to document endpoints, but structural compliance indicators are in place.
- **Site B** has **zero legal documentation** — no Privacy Policy, no functional Terms of Service — despite operating an applicant workflow that collects sensitive PII including financial and eligibility data.
- Site B represents a **critical compliance failure** under CCPA, GDPR (if EU-accessible), FTC Act Section 5, and multiple U.S. state privacy laws.
- Neither site has a confirmed cookie consent banner or independently accessible data rights mechanism.

| Dimension | Site A | Site B |
|---|---|---|
| Overall Compliance Posture | Partial | Non-Compliant |
| Legal Risk Level | Low–Medium | Critical |
| Policy Presence | Both present | Both absent |
| PII Sensitivity | Medium (B2B contact data) | High (financial, eligibility, household) |
| Identity/Auth Exposure | Low (no visible login) | High (application status tracking) |
| Cookie/Consent Compliance | Unconfirmed | Non-existent |

---

## Section 1: Policy Presence

### Findings

| Document | Site A | Site B | Risk if Missing |
|---|---|---|---|
| Privacy Policy | ✅ Present (footer link) | ❌ Missing | Critical — violates CCPA, FTC Act, CalOPPA |
| Terms of Service | ✅ Present (footer link) | ⚠️ Broken/empty link | High — no enforceable user agreement |
| Cookie Policy | ❓ Unconfirmed | ❌ Missing | High — required under GDPR for EU visitors |
| Data Rights Mechanism | ❓ Unconfirmed | ❌ Missing | High — CCPA and GDPR require accessible opt-out/deletion |
| Legal Entity Disclosure | ✅ Footer copyright | ⚠️ Brand name only | Medium — no legal org name disclosed |
| Effective/Updated Date | ❓ Unconfirmed | N/A | Medium — undated policies are not compliant |

### Remediation Required — Site B

1. **Immediately publish a Privacy Policy** — this is the single highest-priority remediation item
2. **Fix or rebuild the Terms of Service page** — a broken link is legally equivalent to no document
3. **Add an effective date and last-updated date** to both documents once published
4. **Disclose legal organization name** in the footer and within each policy

---

## Section 2: Privacy Policy Content Gaps

### Site A — Assessment

Full text could not be retrieved for independent review. Based on site structure, footer presence, and publicly observable behavior, the following is assessed:

| Area | Assessment | Risk |
|---|---|---|
| PII categories disclosed | Likely present — unverified | Medium |
| Third-party processors named | Unverified | Medium |
| User rights mechanism | Not observed on public pages | Medium |
| Cookie/tracking disclosure | No banner observed | Medium |
| Breach notification language | Unverified | Medium |
| Data retention periods | Unverified | Medium |
| GDPR/CCPA specific language | Unverified | Medium |

**Recommendation:** Conduct a full internal review of the policy text against the 30-item Section 2 checklist in the Website Audit Checklist. Prioritize confirming: user rights mechanism, processor list, and data retention statements.

### Site B — Assessment

No policy exists. Every item in this section is a gap.

| Area | Status | Risk |
|---|---|---|
| PII categories disclosed | ❌ None | Critical |
| Collection methods disclosed | ❌ None | Critical |
| Data usage and legal basis | ❌ None | Critical |
| Third-party processors named | ❌ None | Critical |
| User rights mechanism | ❌ None | Critical |
| Cookie/tracking disclosure | ❌ None | Critical |
| Security language | ❌ None | Critical |
| Breach notification | ❌ None | Critical |
| Data retention periods | ❌ None | Critical |
| GDPR compliance language | ❌ None | Critical |
| CCPA compliance language | ❌ None | Critical |
| Children's privacy statement | ❌ None | High |

**Special risk factor:** Site B's application workflow collects data that may include financial records, household composition, and eligibility information — categories that are treated with heightened protection under CCPA, GDPR Article 9, and various state laws. The complete absence of any governing policy over this collection is the most significant finding of this audit.

---

## Section 3: Terms of Service Content Gaps

| Clause | Site A | Site B |
|---|---|---|
| Acceptance clause | ✅ Present (assumed from TOS existence) | ❌ Missing |
| Eligibility / age requirements | ❓ Unverified | ❌ Missing |
| Service description | ❓ Unverified | ❌ Missing |
| Prohibited conduct | ❓ Unverified | ❌ Missing |
| Account / credential security | ❓ Unverified | ❌ Missing |
| IP ownership | ❓ Unverified | ❌ Missing |
| Application / submitted content clause | N/A (no applications) | ❌ Missing — critical given application workflow |
| Disclaimer of warranties | ❓ Unverified | ❌ Missing |
| Limitation of liability | ❓ Unverified | ❌ Missing |
| Governing law / jurisdiction | ❓ Unverified | ❌ Missing |
| Change notification procedure | ❓ Unverified | ❌ Missing |

---

## Section 4: Identity and Authentication Security Gaps

### Site A

No visible user login or account portal was observed on public-facing pages. This significantly reduces the IAM attack surface. However:

| Item | Status | Risk |
|---|---|---|
| Backend CRM identity (newsletter, contact form handlers) | Unverifiable externally | Medium |
| Session handling for any admin portal | Unverifiable externally | Medium |
| Credential hygiene policy disclosed | ❌ Not disclosed | Low |
| MFA for administrative access | Unverifiable externally | Medium |

**Assessment:** Low external identity risk. Internal operational risk from undisclosed backend tool chains.

### Site B

An application status tracking workflow was observed, strongly implying user accounts or session-linked identity records exist on the platform.

| Item | Status | Risk |
|---|---|---|
| User provisioning process documented | ❌ None | High |
| Session management policy disclosed | ❌ None | High |
| Credential security requirements disclosed | ❌ None | High |
| MFA availability disclosed | ❌ None | Medium |
| Session timeout behavior | ❌ Unconfirmed | High |
| Account deprovisioning process | ❌ None | High |
| RBAC / least-privilege controls | ❌ Unverifiable | High |

**CIAM Risk:** Site B operates a citizen-facing identity journey (apply → check status → receive determination) with no consent capture, no credential policy, and no disclosed session management. This is a foundational CIAM failure.

---

## Section 5: Technical Security Observations

The following were assessed from publicly observable signals only. Internal infrastructure, server configuration, and backend systems were not tested.

| Control | Site A | Site B |
|---|---|---|
| HTTPS enforced | ✅ Confirmed | ✅ Confirmed |
| Security headers (CSP, HSTS, X-Frame) | ❓ Not confirmed | ❓ Not confirmed |
| Cookie Secure / HttpOnly flags | ❓ Not confirmed | ❓ Not confirmed |
| Cookie consent banner | ❌ Not observed | ❌ Not observed |
| CSRF protection on forms | ❓ Not confirmed | ❓ Not confirmed |
| No sensitive data in URLs | ✅ Observed (no visible PII in URLs) | ❓ Not confirmed for application flow |
| Security.txt file | ❓ Not checked | ❓ Not checked |

**Recommendation for both sites:** Run a full HTTP header audit using [securityheaders.com](https://securityheaders.com) and address any missing headers.

---

## Section 6: Consent and Cookie Compliance

| Item | Site A | Site B |
|---|---|---|
| Cookie consent banner present | ❌ Not observed | ❌ Not observed |
| Pre-consent cookie loading | ❓ Unverified | ❓ Unverified |
| Granular consent categories | ❌ Not observed | ❌ Not observed |
| Consent records logged | ❓ Unverifiable | ❌ None (no mechanism) |
| CCPA opt-out mechanism | ❌ Not observed | ❌ Not observed |

**Regulatory exposure:** Under GDPR, non-essential cookies must not fire before consent is granted. Under CCPA, an opt-out mechanism is required if behavioral data is shared with third parties (e.g., analytics platforms). Neither site demonstrates compliance with either requirement.

---

## Section 7: Audit Failure Summary

The following items represent findings that would result in an **automatic fail** on any formal privacy or compliance audit:

| Finding | Site | Severity |
|---|---|---|
| No Privacy Policy while collecting PII | Site B | 🔴 Critical |
| Broken/non-functional Terms of Service link | Site B | 🔴 Critical |
| Application workflow collecting sensitive financial/eligibility PII with zero governing documentation | Site B | 🔴 Critical |
| No user rights mechanism (access, deletion, opt-out) | Site B | 🔴 Critical |
| No cookie consent mechanism | Both | 🟠 High |
| No data retention policy | Site B | 🟠 High |
| No third-party processor disclosure | Site B | 🟠 High |
| No breach notification commitment | Site B | 🟠 High |
| No legal organization name disclosed | Site B | 🟡 Medium |
| User identity lifecycle (provisioning/deprovisioning) undocumented | Site B | 🟠 High |
| Security headers not confirmed | Both | 🟡 Medium |

---

## Section 8: Prioritized Remediation Roadmap

### Site A — Priority Order

1. Confirm full Privacy Policy text against the 30-item checklist (Section 2 of the Audit Checklist)
2. Add cookie consent banner and audit all cookies loaded on the site
3. Verify user rights mechanism is accessible and functional
4. Confirm HTTPS security headers (run securityheaders.com scan)
5. Add data retention periods to the Privacy Policy

### Site B — Priority Order

1. **Publish a Privacy Policy immediately** (use the Privacy Policy Template in this repository)
2. **Rebuild the Terms of Service page** (use the Terms of Service Template in this repository)
3. Document the identity/application lifecycle — provisioning, session management, deprovisioning
4. Add cookie consent banner before any analytics or tracking loads
5. Disclose all third-party processors in the Privacy Policy
6. Implement and disclose data retention periods
7. Add a user rights request mechanism (email address at minimum)
8. Run a full security headers audit and remediate gaps
9. Conduct internal review of application data handling and access controls

---

*Audit conducted as part of the Identity-Architect-Portfolio project. All client information anonymized. Templates referenced in the remediation roadmap are available in the `/templates` directory of this repository.*
