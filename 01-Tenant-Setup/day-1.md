# Day‑1 — Tenant Setup & Security Baseline

## 📌 Overview
Day‑1 establishes your Microsoft Entra ID lab tenant, baseline users, groups, MFA enforcement, break‑glass accounts, and initial exports.  
This forms the foundation for all SC‑300 hands‑on exercises.

---

## 1. Create a Dedicated Test Tenant
- Create a new Microsoft Entra ID tenant (or Microsoft 365 Developer tenant).
- Recommended region: **EU (Belgium)**.
- Choose an initial domain such as:  
  `yourlab.onmicrosoft.com`
- Record:
  - Tenant ID  
  - Initial domain  
  - Global Admin UPN  
- Store credentials securely.

**Reference:**  
- [Create test tenant](ca://s?q=Guide_me_to_create_test_Azure_AD_tenant)

---

## 2. Create Core Users & Groups

### Users
- `lab-admin` → Global Administrator  
- `lab-user1` → Standard user  
- `lab-user2` → Standard user  

### Groups
- `Sec-Admins`  
- `Test-Users`  

Add `lab-user1` and `lab-user2` to **Test-Users**.

---

## 3. Enable Security Defaults
Security Defaults provide baseline identity protection.

### Steps
- Go to **Identity → Overview → Properties**  
- Select **Manage Security Defaults**  
- Set **Enable Security Defaults = Yes**

This enforces:
- MFA for all users  
- Blocking legacy authentication  
- Basic admin protections  

**Reference:**  
- [Security Defaults](ca://s?q=Explain_Azure_AD_Security_Defaults)

---

## 4. Configure MFA for All Users

### Steps
- Sign in as `lab-user1`  
- Complete Microsoft Authenticator registration  
- Sign out and sign in again to confirm MFA enforcement  
- Repeat for `lab-user2`

**Reference:**  
- [Configure MFA](ca://s?q=Show_me_how_to_configure_MFA)

---

## 5. Create Break‑Glass (Emergency) Accounts
Break‑glass accounts ensure access even if MFA/CA fails.

### Steps
- Create two cloud‑only accounts:
  - `bg-admin-01@yourlab.onmicrosoft.com`
  - `bg-admin-02@yourlab.onmicrosoft.com`
- Assign **Global Administrator** role  
- Set long, unique passwords (store in password manager)  
- Document these accounts clearly  
- Test sign‑in from a clean browser session

---

## 6. Export Baseline (Users, Groups, Roles)

### Steps
- Export **Users** → CSV  
- Export **Groups** → CSV  
- Document **Roles**:
  - Global Admins  
  - Standard users  
  - Break‑glass accounts  

### Store in GitHub
```
01-Tenant-Setup/
  users-baseline.csv
  groups-baseline.csv
  roles-baseline.md
```

---

## 7. Day‑1 Completion Checklist
- [ ] Tenant created  
- [ ] Core users created  
- [ ] Groups created  
- [ ] Security Defaults enabled  
- [ ] MFA tested  
- [ ] Break‑glass accounts created  
- [ ] Baseline exported  
- [ ] GitHub folder updated  

