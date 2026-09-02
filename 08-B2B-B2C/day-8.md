# Day‑8 — External Identities (B2B & B2C)

## 📌 Overview
Day‑8 focuses on Microsoft Entra **External Identities**, covering both **B2B guest access** and **B2C user flows**.  
You will configure collaboration settings, invite guest users, apply Conditional Access to guests, and optionally deploy a B2C tenant with a working user flow.

This is a major SC‑300 topic and essential for modern identity architecture.

---

## 1. Verify Prerequisites
Before starting:

- You must have **Entra ID P1 or P2**.
- Ensure test users exist:
  - `lab-user1`
  - `lab-user2`
- Ensure at least one guest user exists:
  - `guest-user@example.com`
- Ensure Conditional Access policies from Day‑2 are available.

**Reference:**  
- [B2B External Identities](ca://s?q=Explain_Azure_AD_B2B)  
- [Azure AD B2C](ca://s?q=Explain_Azure_AD_B2C)

---

## 2. Configure External Collaboration Settings (B2B)

### **Steps**
1. Go to **Entra admin center → Identity → External Identities → External collaboration settings**
2. Configure:
   - **Guest user access** → Allow
   - **Guest invite settings** → Admins and users in the directory
   - **Guest user restrictions** → Restricted access (recommended)
3. Save changes

### **Expected Behavior**
Your tenant now supports controlled B2B guest collaboration.

---

## 3. Invite a New Guest User (B2B)

### **Steps**
1. Go to **Identity → Users → New guest user**
2. Invite:
   - Email: `partner-user@example.com`
3. Add a personal message (optional)
4. Assign:
   - No roles (guest will request access through packages or apps)

### **Expected Behavior**
Guest receives an invitation email and appears in your directory.

---

## 4. Assign Guest User to Resources

### **Steps**
1. Go to **Groups → Test-Users**
2. Add:
   - `partner-user@example.com`
3. Go to **Enterprise applications → Lab-Demo-App → Users**
4. Assign:
   - `partner-user@example.com`

### **Expected Behavior**
Guest user receives group membership + app access.

---

## 5. Apply Conditional Access to Guest Users

### **Steps**
1. Go to **Protection → Conditional Access → New policy**
2. Configure:
   - **Name:** `CA-Guests-Require-MFA`
   - **Users:** Include → Guest users  
   - **Cloud apps:** All cloud apps
3. **Grant**
   - Require MFA
4. **Enable policy:** On

### **Expected Behavior**
Guest users must complete MFA before accessing resources.

---

## 6. Test Guest User Sign‑In

### **Steps**
1. Sign in as `partner-user@example.com`
2. Accept the invitation
3. Access:
   - `Lab-Demo-App`
   - Group resources (if applicable)
4. Confirm:
   - MFA prompt  
   - Successful sign‑in  
   - Token issuance  
   - Conditional Access evaluation

### **Store Evidence**
```
08-B2B-B2C/b2b-signin-logs.csv
08-B2B-B2C/b2b-access-summary.md
```

---

## 7. Optional: Deploy Azure AD B2C Tenant

### **Steps**
1. Go to **Entra admin center → Azure AD B2C**
2. Create a new B2C tenant
3. Link it to your subscription
4. Record:
   - B2C tenant ID  
   - Domain (e.g., `yourlabb2c.onmicrosoft.com`)

### **Expected Behavior**
You now have a dedicated B2C identity tenant.

---

## 8. Create a B2C User Flow (Sign‑Up / Sign‑In)

### **Steps**
1. Go to **Azure AD B2C → User flows → New user flow**
2. Select:
   - **Type:** Sign up and sign in
   - **Version:** Recommended (v2)
3. Configure:
   - Identity providers → Email  
   - Attributes → Display name, Email, Country
4. Create the user flow

### **Expected Behavior**
Users can sign up and sign in using the B2C flow.

---

## 9. Test the B2C User Flow

### **Steps**
1. Copy the **Run user flow** URL
2. Open in a private browser window
3. Sign up with a new email
4. Sign in again
5. Validate:
   - Token issuance  
   - Claims  
   - User creation in B2C tenant

### **Store Evidence**
```
08-B2B-B2C/b2c-userflow-test.md
08-B2B-B2C/b2c-token-sample.json
```

---

## 10. Day‑8 Completion Checklist
- [ ] External collaboration settings configured  
- [ ] Guest user invited  
- [ ] Guest assigned to groups/apps  
- [ ] Guest Conditional Access policy created  
- [ ] Guest sign‑in tested  
- [ ] B2C tenant created (optional)  
- [ ] B2C user flow created  
- [ ] B2C user flow tested  
- [ ] Evidence exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [B2B External Identities](ca://s?q=Explain_Azure_AD_B2B)
- [Azure AD B2C](ca://s?q=Explain_Azure_AD_B2C)
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
