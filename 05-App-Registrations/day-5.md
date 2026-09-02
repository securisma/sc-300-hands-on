# Day‑5 — App Registrations & Enterprise Apps

## 📌 Overview
Day‑5 focuses on creating and configuring **App Registrations** and **Enterprise Applications** in Microsoft Entra ID.  
You will build an application, configure permissions, create a client secret, test SSO, and collect sign‑in logs.

This is a core SC‑300 skill and appears frequently in real‑world identity architecture.

---

## 1. Verify Prerequisites
Before starting:

- You must have **Entra ID P1 or P2**.
- Ensure test users exist:
  - `lab-user1`
  - `lab-user2`
- Ensure break‑glass accounts are documented and excluded from app assignments.

**Reference:**  
- [App Registration](ca://s?q=Show_me_how_to_create_App_Registration)

---

## 2. Create a New App Registration

### **Steps**
1. Go to **Entra admin center → Applications → App registrations → New registration**
2. Configure:
   - **Name:** `Lab-Demo-App`
   - **Supported account types:** Single tenant
   - **Redirect URI:**  
     `https://jwt.ms` (for testing tokens)
3. Click **Register**

### **Record the following:**
- Application (client) ID  
- Directory (tenant) ID  
- Object ID  

Store these in your GitHub repo under:

```
05-App-Registrations/app-info.md
```

---

## 3. Configure API Permissions (Microsoft Graph)

### **Steps**
1. Go to **Lab-Demo-App → API permissions**
2. Add:
   - **Microsoft Graph → Delegated → User.Read**
3. Click **Grant admin consent**

### **Expected Behavior**
The app can read basic user profile information when users sign in.

---

## 4. Create a Client Secret

### **Steps**
1. Go to **Lab-Demo-App → Certificates & secrets**
2. Create:
   - **New client secret**
   - Description: `lab-secret`
   - Expiry: 6 months (lab only)
3. Copy the secret **immediately** and store it securely.

### **Store in GitHub (never store real secrets!)**
Create a placeholder file:

```
05-App-Registrations/client-secret-placeholder.md
```

---

## 5. Convert App Registration into an Enterprise Application

### **Steps**
1. Go to **Entra admin center → Applications → Enterprise applications**
2. Search for **Lab-Demo-App**
3. Open the app and configure:
   - **Users and groups → Add assignment**
   - Assign:
     - `lab-user1`
     - `lab-user2`

### **Expected Behavior**
Users can now sign in to the app using Entra ID.

---

## 6. Test SSO Using jwt.ms

### **Steps**
1. Sign in as `lab-user1`
2. Navigate to:
   ```
   https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize?
   client_id=<clientID>&response_type=id_token&redirect_uri=https://jwt.ms&scope=openid&nonce=12345
   ```
3. Confirm:
   - Successful sign‑in  
   - Token appears on jwt.ms  
   - Claims include:
     - `aud` = App ID  
     - `oid` = User Object ID  
     - `roles` (if assigned)

### **Store Evidence**
```
05-App-Registrations/sso-test-results.md
05-App-Registrations/jwt-token-sample.json
```

---

## 7. Review Sign‑In Logs

### **Steps**
1. Go to **Monitoring → Sign‑in logs**
2. Filter by:
   - Application: `Lab-Demo-App`
3. Export:
   - Sign‑in events  
   - Conditional Access results  
   - Token issuance details  

### **Store in GitHub**
```
05-App-Registrations/signin-logs.csv
05-App-Registrations/signin-analysis.md
```

---

## 8. Optional: Add App Role Assignments

### **Steps**
1. Go to **Lab-Demo-App → App roles**
2. Create:
   - Role name: `App.Reader`
   - Allowed member types: Users/Groups
3. Assign:
   - `lab-user1` → App.Reader

### **Expected Behavior**
The role appears in the user’s ID token under `roles`.

---

## 9. Day‑5 Completion Checklist
- [ ] App Registration created  
- [ ] Graph API permissions added  
- [ ] Admin consent granted  
- [ ] Client secret created  
- [ ] Enterprise App configured  
- [ ] Users assigned  
- [ ] SSO tested  
- [ ] Token validated  
- [ ] Sign‑in logs exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [App Registration](ca://s?q=Show_me_how_to_create_App_Registration)
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
- [Identity Governance](ca://s?q=Explain_Access_Packages)

