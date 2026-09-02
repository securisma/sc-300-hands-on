# Day‑11 — Zero Trust Identity Architecture

## 📌 Overview
Day‑11 focuses on designing and validating a **Zero Trust Identity Architecture** using all components you built in Days 1–10.  
You will map your lab environment to Zero Trust principles, validate identity controls, create architecture diagrams, and document your final design.

This day transforms your hands‑on work into a professional‑grade identity architecture.

---

## 1. Understand Zero Trust Identity Principles

Zero Trust is built on three core principles:

### **1. Verify Explicitly**
- Authenticate and authorize based on:
  - User identity  
  - Device health  
  - Location  
  - Risk  
  - App sensitivity  
  - Session context  

### **2. Use Least Privilege Access**
- JIT access  
- JEA (Just Enough Access)  
- Role‑based access control  
- Access reviews  

### **3. Assume Breach**
- Monitor continuously  
- Detect anomalies  
- Respond automatically  
- Limit blast radius  

---

## 2. Map Your Lab Components to Zero Trust

### **Identity Layer**
- Microsoft Entra ID  
- MFA  
- Conditional Access  
- Identity Protection  
- B2B/B2C External Identities  

### **Access Layer**
- PIM (Privileged Identity Management)  
- Access Packages  
- Access Reviews  
- App Registrations  
- Enterprise Apps  

### **Monitoring Layer**
- Sign‑in logs  
- Audit logs  
- Log Analytics  
- Alerts  
- Automation (Graph API / PowerShell)  

Document this mapping:

```
11-Zero-Trust/zero-trust-mapping.md
```

---

## 3. Build Your Zero Trust Identity Architecture Diagram

### **Components to Include**
- Users (internal + external)  
- Devices (compliant + non‑compliant)  
- Conditional Access  
- Identity Protection  
- PIM  
- Access Packages  
- Enterprise Apps  
- Monitoring + Log Analytics  
- Automation workflows  

### **Suggested Diagram Flow**
1. User attempts sign‑in  
2. Conditional Access evaluates context  
3. Identity Protection evaluates risk  
4. PIM controls privileged access  
5. Access Packages govern lifecycle  
6. Access Reviews maintain least privilege  
7. Monitoring detects anomalies  
8. Automation responds  

Save diagram:

```
11-Zero-Trust/zero-trust-architecture.drawio
```

---

## 4. Validate Zero Trust Controls in Your Lab

### **Identity Controls**
- [ ] MFA enforced  
- [ ] Risk‑based policies active  
- [ ] Device compliance enforced  
- [ ] Session controls applied  

### **Access Controls**
- [ ] PIM activation tested  
- [ ] Access Packages functional  
- [ ] Access Reviews completed  
- [ ] Guest access restricted  

### **Monitoring Controls**
- [ ] Logs flowing to Log Analytics  
- [ ] KQL queries working  
- [ ] Alerts firing  
- [ ] Automation scripts tested  

Document results:

```
11-Zero-Trust/control-validation.md
```

---

## 5. Create Zero Trust Policies

### **Identity Policies**
- Require MFA  
- Block legacy authentication  
- Enforce sign‑in frequency  
- Enforce compliant device  

### **Access Policies**
- JIT admin access  
- Approval workflows  
- Access lifecycle expiration  
- Guest access restrictions  

### **Monitoring Policies**
- Alert on risky sign‑ins  
- Alert on failed sign‑ins  
- Alert on admin role activation  
- Automated remediation  

Save policies:

```
11-Zero-Trust/policies.md
```

---

## 6. Build a Zero Trust Identity Playbook

### **Sections to Include**
- Incident detection  
- Incident classification  
- Response workflow  
- Automated actions  
- Manual actions  
- Evidence collection  
- Post‑incident review  

Example automated actions:
- Disable risky user  
- Remove user from group  
- Revoke sessions  
- Reset password  

Save playbook:

```
11-Zero-Trust/identity-playbook.md
```

---

## 7. Create a Zero Trust Gap Analysis

### **Steps**
1. Compare your lab to Microsoft’s Zero Trust model  
2. Identify gaps:
   - Missing controls  
   - Weak policies  
   - Missing automation  
   - Missing monitoring  
3. Recommend improvements

Save gap analysis:

```
11-Zero-Trust/gap-analysis.md
```

---

## 8. Day‑11 Completion Checklist
- [ ] Zero Trust principles documented  
- [ ] Architecture diagram created  
- [ ] Controls validated  
- [ ] Policies documented  
- [ ] Playbook created  
- [ ] Gap analysis completed  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Zero Trust Architecture](ca://s?q=Explain_Zero_Trust_Architecture)
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)
- [PIM](ca://s?q=Explain_Azure_PIM)
- [Access Packages](ca://s?q=Explain_Access_Packages)
- [Monitoring](ca://s?q=Explain_Entra_Monitoring)
