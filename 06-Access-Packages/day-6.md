# Day‑6 — Identity Governance: Access Packages

## 📌 Overview
Day‑6 focuses on Microsoft Entra **Identity Governance**, specifically **Access Packages** and **Entitlement Management**.  
You will create a catalog, define resources, build policies, onboard a guest user, and test the full request/approval lifecycle.

This is a major SC‑300 topic and highly relevant for real‑world identity governance.

---

## 1. Verify Prerequisites
Before starting:

- You must have **Entra ID P2** (Identity Governance requires P2).
- Ensure test users exist:
  - `lab-user1`
  - `lab-user2`
- Ensure break‑glass accounts are documented and excluded from governance workflows.

**Reference:**  
- [Access Packages](ca://s?q=Explain_Access_Packages)

---

## 2. Create an Identity Governance Catalog

### **Steps**
1. Go to **Entra admin center → Identity Governance → Entitlement Management → Catalogs**
2. Click **New catalog**
3. Configure:
   - **Name:** `Lab-Governance-Catalog`
   - **Description:** Catalog for SC‑300 lab access packages
   - **Enabled:** Yes
4. Save the catalog

### **Expected Behavior**
You now have a container for resources and access packages.

---

## 3. Add Resources to the Catalog

### **Steps**
1. Open **Lab-Governance-Catalog**
2. Go to **Resources → Add resources**
3. Add:
   - **Groups:** `Test-Users`, `Sec-Admins`
   - **Applications:** `Lab-Demo-App` (from Day‑5)
4. Assign resource roles:
   - `Test-Users` → Member  
   - `Sec-Admins` → Member  
   - `Lab-Demo-App` → Default role (User)

### **Expected Behavior**
Resources are now available for Access Packages.

---

## 4. Create an Access Package

### **Steps**
1. Go to **Entitlement Management → Access packages → New access package**
2. Configure:
   - **Name:** `Lab-Access-Package`
   - **Catalog:** `Lab-Governance-Catalog`
3. Under **Resources**, add:
   - `Test-Users` (Member)
   - `Lab-Demo-App` (User)
4. Save and continue

### **Expected Behavior**
The package bundles group membership + app access.

---

## 5. Create Access Package Policies

You will create two policies:

### **Policy A — Internal Users**
1. Under **Policies**, click **Add policy**
2. Configure:
   - **Name:** `Internal-Users-Policy`
   - **Users:** `lab-user1`, `lab-user2`
   - **Approval:** No approval required
   - **Lifecycle:** Access expires after 30 days
3. Save

### **Policy B — External Users (B2B Guests)**
1. Add another policy:
   - **Name:** `External-Users-Policy`
   - **Users:** External users (specific domain or “All external users”)
2. Configure:
   - **Approval:** Required  
     - Approver: `lab-admin`
   - **Lifecycle:** Access expires after 14 days
3. Save

### **Expected Behavior**
Internal users get automatic access; external users require approval.

---

## 6. Invite a Guest User (B2B)

### **Steps**
1. Go to **Identity → Users → New guest user**
2. Invite:
   - Email: `guest-user@example.com`
3. Assign:
   - No roles (guest will request access through the package)

### **Expected Behavior**
Guest receives an invitation email and appears in your directory.

---

## 7. Test Access Package Request Workflow

### **Internal User Test**
1. Sign in as `lab-user1`
2. Go to **My Access → Access packages**
3. Request **Lab-Access-Package**
4. Confirm:
   - No approval required
   - Access granted automatically

### **External User Test**
1. Sign in as `guest-user@example.com`
2. Request **Lab-Access-Package**
3. Approver (`lab-admin`) receives approval request
4. Approver approves the request
5. Guest receives access

### **Expected Behavior**
Both internal and external workflows function as configured.

---

## 8. Review Access Package Assignments

### **Steps**
1. Go to **Entitlement Management → Access packages → Lab-Access-Package**
2. Open **Assignments**
3. Review:
   - Active assignments  
   - Expired assignments  
   - Pending approvals  
4. Export assignments to CSV

### **Store in GitHub**
```
06-Access-Packages/assignments.csv
06-Access-Packages/access-package-summary.md
```

---

## 9. Day‑6 Completion Checklist
- [ ] Catalog created  
- [ ] Resources added  
- [ ] Access package created  
- [ ] Internal user policy created  
- [ ] External user policy created  
- [ ] Guest user invited  
- [ ] Internal workflow tested  
- [ ] External workflow tested  
- [ ] Assignments exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Access Packages](ca://s?q=Explain_Access_Packages)
- [B2B Collaboration](ca://s?q=Explain_Azure_AD_B2B)
- [App Registration](ca://s?q=Show_me_how_to_create_App_Registration)
