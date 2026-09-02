# Day‑10 — SC‑300 Final Review & Exam Prep

## 📌 Overview
Day‑10 focuses on **final SC‑300 exam preparation**, combining:
- Hands‑on validation of everything built in Days 1–9  
- A structured review of Microsoft identity concepts  
- Practice scenarios  
- A targeted study plan  
- A readiness checklist  

This day ensures you are fully prepared for the SC‑300 exam.

---

## 1. Validate Your Hands‑On Lab Environment

### **Check Tenant Configuration**
- [ ] Tenant created  
- [ ] Break‑glass accounts documented  
- [ ] Security Defaults disabled (CA enabled)  
- [ ] PIM enabled  
- [ ] Identity Governance enabled  

### **Check Core Features**
- [ ] Conditional Access policies working  
- [ ] Identity Protection policies working  
- [ ] PIM activation workflow tested  
- [ ] Access Packages functional  
- [ ] Access Reviews completed  
- [ ] B2B guest access tested  
- [ ] B2C user flow tested  
- [ ] Monitoring + Log Analytics configured  

---

## 2. Review SC‑300 Core Concepts

### **Identity Fundamentals**
- Authentication vs Authorization  
- Tokens: ID token, Access token, Refresh token  
- OAuth2, OIDC, SAML  

### **Microsoft Entra ID**
- Tenants, directories, domains  
- Users, groups, roles  
- External identities (B2B/B2C)  

### **Conditional Access**
- Conditions  
- Grant controls  
- Session controls  
- Named locations  
- Device filters  

### **Identity Protection**
- User risk  
- Sign‑in risk  
- Risk detections  
- Remediation  

### **Privileged Identity Management**
- Eligible vs Active  
- Activation requirements  
- Approval workflows  
- Role settings  

### **Identity Governance**
- Access packages  
- Access reviews  
- Lifecycle management  

### **Monitoring**
- Sign‑in logs  
- Audit logs  
- Log Analytics  
- KQL  

---

## 3. Practice SC‑300 Scenario Questions

### **Scenario A — MFA Enforcement**
You must enforce MFA for all users except break‑glass accounts.  
Which Conditional Access configuration is correct?

- Users: All users  
- Exclude: Break‑glass  
- Cloud apps: All apps  
- Grant: Require MFA  

### **Scenario B — Guest Access**
A partner needs access to a specific app.  
Which steps are required?

- Invite guest  
- Assign to app  
- Apply CA for guests  
- Monitor sign‑ins  

### **Scenario C — PIM Activation**
A user must activate Security Administrator with MFA and justification.  
Which PIM settings apply?

- Eligible assignment  
- Require MFA  
- Require justification  
- Require approval  

### **Scenario D — Risky Sign‑Ins**
A user signs in from a Tor browser.  
Which Identity Protection policy applies?

- Sign‑in risk policy → Require MFA  

---

## 4. Build Your Personal SC‑300 Notes

Create a folder:

```
10-Exam-Prep/notes/
```

Add files:
- `conditional-access.md`  
- `identity-protection.md`  
- `pim.md`  
- `governance.md`  
- `monitoring.md`  

Summarize:
- Definitions  
- Key settings  
- Exam‑relevant behaviors  
- Common pitfalls  

---

## 5. Use Microsoft Official Practice Resources

### **Recommended**
- Microsoft Learn SC‑300 modules  
- Microsoft practice questions  
- Entra documentation  
- Identity architecture diagrams  

### **Focus Areas**
- Conditional Access logic  
- Identity Protection risk evaluation  
- PIM workflows  
- Governance lifecycle  
- App registration flows  

---

## 6. Final Exam Readiness Checklist

### **Technical Skills**
- [ ] Can create CA policies from scratch  
- [ ] Can configure Identity Protection  
- [ ] Can activate PIM roles  
- [ ] Can build Access Packages  
- [ ] Can run Access Reviews  
- [ ] Can onboard B2B/B2C users  
- [ ] Can query logs with KQL  

### **Conceptual Knowledge**
- [ ] Understand token flows  
- [ ] Understand identity protocols  
- [ ] Understand governance lifecycle  
- [ ] Understand risk evaluation  
- [ ] Understand admin roles  

### **Confidence**
- [ ] Completed all 10 days  
- [ ] Practiced scenarios  
- [ ] Reviewed notes  
- [ ] Ready for exam  

---

## 🔗 Helpful Deep‑Dive Links
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)
- [PIM](ca://s?q=Explain_Azure_PIM)
- [Access Packages](ca://s?q=Explain_Access_Packages)
- [Access Reviews](ca://s?q=Explain_Access_Reviews)
- [B2B](ca://s?q=Explain_Azure_AD_B2B)
- [B2C](ca://s?q=Explain_Azure_AD_B2C)
- [Monitoring](ca://s?q=Explain_Entra_Monitoring)
