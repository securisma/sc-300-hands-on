# SC-300 Hands-On Project Documentation  
Comprehensive 7–10 Day Practical Implementation  
Author: Securisma  
Location: Belgium  
Date: September 2026  

---

## 📌 Overview
This repository documents a full hands-on implementation of Azure AD / Entra ID identity security concepts aligned with the SC-300 certification.  
It includes configurations, scripts, diagrams, logs, and governance artifacts.

---

## 📁 Repository Structure
```
├── 01-Tenant-Setup/
├── 02-Conditional-Access/
├── 03-Identity-Protection/
├── 04-PIM/
├── 05-App-Registrations/
├── 06-Access-Packages/
├── 07-Access-Reviews/
├── 08-B2B-B2C/
├── 09-Monitoring-Automation/
├── 10-Architecture-Diagram/
└── README.md
```

---

## 🧩 1. Tenant Setup & Baseline
### Summary
Document the initial configuration of your Azure AD tenant.

### Checklist
- Tenant created  
- Security Defaults enabled  
- MFA enforced  
- Break-glass account created  
- Baseline export (users, groups, roles)

### Evidence
- Screenshots  
- PowerShell export commands  
- Notes on decisions  

### Deep Dive Links
- [Create test tenant](ca://s?q=Guide_me_to_create_test_Azure_AD_tenant)  
- [Security Defaults](ca://s?q=Explain_Azure_AD_Security_Defaults)  

---

## 🔐 2. Conditional Access Policies
### Summary
Record all CA policies created and tested.

### Policies Implemented
- Require MFA for all users  
- Block non-trusted countries  
- Require compliant device  
- Session controls (sign-in frequency)

### Evidence
- Policy JSON exports  
- Sign-in logs  
- Test user results  

### Deep Dive Links
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)

---

## 🛡️ 3. Identity Protection
### Summary
Configure and test risk-based policies.

### Implemented
- User risk policy  
- Sign-in risk policy  
- MFA registration policy  

### Evidence
- Risky user reports  
- Risky sign-in logs  
- Screenshots  

### Deep Dive Links
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)

---

## 👑 4. Privileged Identity Management (PIM)
### Summary
Document JIT access and role governance.

### Implemented
- JIT activation  
- Approval workflow  
- Activation duration limits  
- Role assignments  

### Evidence
- PIM activation logs  
- Screenshots  
- Audit exports  

### Deep Dive Links
- [PIM](ca://s?q=Explain_Azure_PIM)

---

## 🧱 5. App Registrations & Enterprise Apps
### Summary
Create and configure an application with permissions.

### Implemented
- App Registration  
- API permissions  
- Client secret  
- Enterprise App conversion  
- SSO testing  

### Evidence
- App manifest  
- Sign-in logs  
- Screenshots  

### Deep Dive Links
- [App Registration](ca://s?q=Show_me_how_to_create_App_Registration)

---

## 🧩 6. Identity Governance — Access Packages
### Summary
Implement Entitlement Management.

### Implemented
- Catalog  
- Resource roles  
- Policies  
- Guest user onboarding  

### Evidence
- Access package configuration  
- Approval workflow screenshots  

### Deep Dive Links
- [Access Packages](ca://s?q=Explain_Access_Packages)

---

## 🔍 7. Access Reviews
### Summary
Configure periodic access reviews.

### Implemented
- Group membership review  
- App role review  
- Guest user review  
- Auto-apply results  

### Evidence
- Review results export  
- Screenshots  

### Deep Dive Links
- [Access Reviews](ca://s?q=Explain_Access_Reviews)

---

## 🌍 8. B2B & B2C
### Summary
Document external identity configurations.

### Implemented
- B2B guest access  
- Conditional Access for guests  
- Optional: B2C tenant + user flow  

### Evidence
- Guest user logs  
- B2C user flow screenshots  

### Deep Dive Links
- [B2B](ca://s?q=Explain_Azure_AD_B2B)  
- [B2C](ca://s?q=Explain_Azure_AD_B2C)

---

## 📊 9. Monitoring, Logs & Automation
### Summary
Configure monitoring and automate identity tasks.

### Implemented
- Log Analytics integration  
- Workbook dashboard  
- Alerts  
- KQL queries  
- PowerShell / Graph automation  

### Evidence
- KQL scripts  
- Dashboard screenshots  
- Runbook code  

### Deep Dive Links
- [Azure AD logging](ca://s?q=Explain_Azure_AD_logging)

---

## 🧭 10. Architecture Diagram
### Summary
Include a visual representation of your identity architecture.

### Suggested Diagram Elements
- Conditional Access flow  
- PIM activation flow  
- App Registration + SSO  
- Identity Governance lifecycle  

### Evidence
- PNG/SVG diagram  
- Draw.io source file  

---

## 🗂️ Appendix — Scripts & Exports
Include:
- PowerShell scripts  
- Graph API calls  
- JSON policy exports  
- KQL queries  

---

## 🏁 Final Summary
Write a short summary of what you learned and how this project demonstrates SC-300 mastery.

---

## 📬 Contact
Author: Securisma  
Location: Belgium  
