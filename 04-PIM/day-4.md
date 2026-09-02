# Day‑4 — Privileged Identity Management (PIM)

## 📌 Overview
Day‑4 focuses on Microsoft Entra **Privileged Identity Management (PIM)**.  
You will configure just‑in‑time (JIT) access, approval workflows, activation settings, role assignments, and audit log collection.

This is one of the most important SC‑300 hands‑on topics.

---

## 1. Verify Prerequisites
Before starting:

- You must have **Entra ID P2** (PIM requires P2).
- Ensure test users exist:
  - `lab-admin`
  - `lab-user1`
  - `lab-user2`
- Ensure break‑glass accounts are documented and excluded from PIM workflows.

**Reference:**  
- [Azure PIM](ca://s?q=Explain_Azure_PIM)

---

## 2. Enable PIM for Azure AD Roles

### **Steps**
1. Go to **Entra admin center → Identity Governance → Privileged Identity Management**
2. Select **Azure AD roles**
3. If prompted, click **Enable PIM** for your tenant

### **Expected Behavior**
You will now see:
- Eligible assignments  
- Active assignments  
- Role settings  
- Audit logs  

---

## 3. Configure Role Settings (JIT Access)

You will configure JIT access for the **Security Administrator** role.

### **Steps**
1. Go to **Azure AD roles → Security Administrator → Settings**
2. Configure:
   - **Assignment type** → Eligible  
   - **Require MFA on activation** → Yes  
   - **Require justification** → Yes  
   - **Require approval** → Yes  
   - **Activation maximum duration** → 1 hour  
   - **Notification settings** → Enabled for all events

### **Expected Behavior**
Users must activate the role before use and follow the configured workflow.

---

## 4. Assign Eligible Roles to Test Users

### **Steps**
1. Go to **Azure AD roles → Security Administrator → Assignments**
2. Add:
   - `lab-user1` → Eligible  
   - `lab-user2` → Eligible  
3. Confirm assignments appear under **Eligible assignments**

### **Expected Behavior**
Neither user has permanent admin rights until they activate the role.

---

## 5. Test PIM Activation Workflow

### **Steps**
1. Sign in as `lab-user1`
2. Go to **Entra admin center → Identity Governance → PIM → Azure AD roles**
3. Select **Security Administrator**
4. Click **Activate**
5. Provide:
   - MFA  
   - Justification  
   - Approval request  

### **Approval**
1. Sign in as `lab-admin`
2. Go to **PIM → Approve requests**
3. Approve `lab-user1`’s activation

### **Expected Behavior**
`lab-user1` becomes **Active** for the configured duration.

---

## 6. Review PIM Audit Logs

### **Steps**
1. Go to **PIM → Audit history**
2. Review:
   - Role activations  
   - Approval workflows  
   - Notifications  
   - Expired activations  
3. Export logs to CSV

### **Store in GitHub**
```
04-PIM/
  pim-activations.csv
  pim-approvals.csv
  pim-audit-summary.md
```

---

## 7. Configure PIM for Groups (Optional but Recommended)

### **Steps**
1. Go to **PIM → Groups**
2. Select a group (e.g., `Sec-Admins`)
3. Enable:
   - **Eligible membership**
   - **Activation requirements**
   - **Approval workflow**
4. Assign:
   - `lab-user2` → Eligible member

### **Expected Behavior**
Group membership becomes JIT‑controlled.

---

## 8. Day‑4 Completion Checklist
- [ ] PIM enabled  
- [ ] Role settings configured  
- [ ] MFA on activation enforced  
- [ ] Justification + approval workflow enabled  
- [ ] Eligible role assignments created  
- [ ] Activation tested  
- [ ] Approval tested  
- [ ] Audit logs exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Azure PIM](ca://s?q=Explain_Azure_PIM)
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)

