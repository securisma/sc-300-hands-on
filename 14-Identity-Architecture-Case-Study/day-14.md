# Day‑14 — Identity Architecture Case Study

## 📌 Overview
Day‑14 presents a **full enterprise identity architecture case study**.  
You will analyze business requirements, design a Microsoft Entra identity solution, map Zero Trust principles, propose governance controls, and produce a final architecture document.

This case study is designed to be included in your professional portfolio.

---

# 1. Case Study: Contoso Global Manufacturing

## 🏢 Company Background
Contoso Global Manufacturing is a multinational company with:
- 12,000 employees  
- 3,000 external partners  
- 4 factories across EU  
- 2 R&D centers  
- A hybrid identity footprint (on‑prem AD + Entra ID)  
- A mix of SaaS, custom apps, and legacy systems  

Contoso is undergoing a **digital transformation** and wants to modernize identity, security, and governance.

---

# 2. Business Requirements

## 🔐 Identity & Security Requirements
- Enforce MFA for all users  
- Block legacy authentication  
- Apply risk‑based access controls  
- Protect privileged roles  
- Enforce device compliance  
- Support external partners (B2B)  
- Support customer identity (B2C)  

## 🧩 Governance Requirements
- Automate access lifecycle  
- Implement access reviews  
- Enforce least privilege  
- Provide auditability for compliance (ISO 27001)  

## 📊 Monitoring Requirements
- Centralize identity logs  
- Detect risky sign‑ins  
- Alert on admin role activations  
- Automate remediation  

## 🛠️ Application Requirements
- Modernize authentication for custom apps  
- Support OAuth2 / OIDC  
- Integrate with Microsoft Graph  
- Support app roles and RBAC  

---

# 3. Architecture Overview

File:

```
14-Identity-Architecture-Case-Study/architecture-overview.md
```

## 🧱 Core Components
- Microsoft Entra ID (primary identity provider)  
- Entra ID Connect (Cloud Sync)  
- Conditional Access  
- Identity Protection  
- Privileged Identity Management  
- Identity Governance  
- External Identities (B2B/B2C)  
- Log Analytics + KQL  
- Automation (Graph API + GitHub Actions)  

---

# 4. Conditional Access Architecture

File:

```
14-Identity-Architecture-Case-Study/conditional-access.md
```

## 🎯 Policies
- **CA‑Require‑MFA‑All‑Users**  
- **CA‑Block‑Legacy‑Auth**  
- **CA‑Require‑Compliant‑Device**  
- **CA‑Block‑Non‑EU‑Countries**  
- **CA‑Admins‑Require‑PIM‑Activation**  
- **CA‑Guests‑Require‑MFA**  

## 🧠 Logic Flow
1. User attempts sign‑in  
2. CA evaluates:
   - User risk  
   - Sign‑in risk  
   - Device compliance  
   - Location  
   - App sensitivity  
3. Grant or block access  
4. Session controls applied  

---

# 5. Identity Protection Architecture

File:

```
14-Identity-Architecture-Case-Study/identity-protection.md
```

## 🔍 Policies
- User risk policy → Require password change  
- Sign‑in risk policy → Require MFA  
- MFA registration policy → Enforced  

## 🧪 Risk Detections
- Anonymous IP  
- Impossible travel  
- Password spray  
- Token replay  

## 🔧 Remediation
- Automated password reset  
- Session revocation  
- User risk dismissal workflow  

---

# 6. Privileged Identity Management Architecture

File:

```
14-Identity-Architecture-Case-Study/pim.md
```

## 🔐 Roles Protected
- Global Administrator  
- Security Administrator  
- Privileged Role Administrator  
- Application Administrator  

## 🔒 Activation Requirements
- MFA  
- Justification  
- Approval  
- Time‑bound activation  
- Notifications  

## 📜 Auditability
- Activation logs  
- Approval logs  
- Expiration logs  

---

# 7. Identity Governance Architecture

File:

```
14-Identity-Architecture-Case-Study/governance.md
```

## 🧩 Access Packages
- Internal employees  
- External partners  
- R&D restricted access  
- Factory floor access  

## 🔄 Lifecycle
- Expiration  
- Renewal  
- Auto‑apply results  

## 🔍 Access Reviews
- Groups  
- App roles  
- Guest users  

---

# 8. External Identities Architecture

File:

```
14-Identity-Architecture-Case-Study/external-identities.md
```

## 🧳 B2B
- Partner onboarding  
- Guest restrictions  
- Guest Conditional Access  
- Guest access reviews  

## 🛒 B2C
- Customer identity  
- Sign‑up/sign‑in user flows  
- Token validation  
- App integration  

---

# 9. Monitoring & Analytics Architecture

File:

```
14-Identity-Architecture-Case-Study/monitoring.md
```

## 📊 Logs Sent to Log Analytics
- Sign‑in logs  
- Audit logs  
- Provisioning logs  
- Risky users  
- Risky sign‑ins  

## 🔎 KQL Queries
- Failed sign‑ins  
- Risky sign‑ins  
- Admin activations  
- Guest activity  

## 🚨 Alerts
- Risky sign‑ins  
- Failed sign‑ins  
- PIM activations  

---

# 10. Automation Architecture

File:

```
14-Identity-Architecture-Case-Study/automation.md
```

## 🤖 GitHub Actions Pipeline
- Authenticate to Graph  
- Export logs  
- Remove inactive guests  
- Enforce group membership  
- Rotate secrets  
- Auto‑revoke risky sessions  

## 🧰 PowerShell Scripts
- Get sign‑ins  
- Disable user  
- Remove group membership  
- Assign app roles  

---

# 11. Zero Trust Mapping

File:

```
14-Identity-Architecture-Case-Study/zero-trust.md
```

## 🔐 Verify Explicitly
- MFA  
- CA  
- Identity Protection  

## 🧩 Least Privilege
- PIM  
- Access Reviews  
- App roles  

## 🔥 Assume Breach
- Monitoring  
- Alerts  
- Automation  

---

# 12. Final Architecture Document

File:

```
14-Identity-Architecture-Case-Study/final-case-study.md
```

### Include:
- Executive summary  
- Architecture diagrams  
- Identity flows  
- Governance model  
- Security controls  
- Monitoring strategy  
- Automation strategy  
- Zero Trust mapping  
- Improvement plan  

This becomes your **professional identity architecture case study**.

---

# 13. Day‑14 Completion Checklist
- [ ] Case study analyzed  
- [ ] Architecture documented  
- [ ] CA architecture written  
- [ ] PIM architecture written  
- [ ] Identity Protection documented  
- [ ] Governance documented  
- [ ] External identities documented  
- [ ] Monitoring documented  
- [ ] Automation documented  
- [ ] Zero Trust mapped  
- [ ] Final case study assembled  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Zero Trust](ca://s?q=Explain_Zero_Trust_Architecture)
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)
- [PIM](ca://s?q=Explain_Azure_PIM)
- [Access Packages](ca://s?q=Explain_Access_Packages)
- [Monitoring](ca://s?q=Explain_Entra_Monitoring)
- [Graph API](ca://s?q=Explain_Microsoft_Graph_API)

