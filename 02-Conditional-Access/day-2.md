# Day‑2 — Conditional Access (Step‑by‑Step)

## 📌 Overview
Day‑2 focuses on building core Conditional Access (CA) policies in Microsoft Entra ID.  
You will create MFA enforcement, location‑based controls, device‑based controls, and session controls — then validate each policy using test accounts.

---

## 1. Prepare Your Environment
Before creating CA policies:

- Ensure **Security Defaults are disabled** (CA cannot be used while they are enabled).
- Confirm you have:
  - `lab-admin` (Global Admin)
  - `lab-user1`, `lab-user2` (test users)
  - `Test-Users` group

**Reference:**  
- [Conditional Access basics](ca://s?q=Create_Conditional_Access_policy)

---

## 2. Create MFA Enforcement Policy (All Cloud Apps)

### **Steps**
1. Go to **Entra admin center → Protection → Conditional Access → Policies → New policy**  
2. Name: **CA‑Require‑MFA‑All‑Apps**
3. **Assignments**
   - Users: **Include → All users**
   - Exclude: **Break‑glass accounts**
4. **Cloud apps**
   - Include: **All cloud apps**
5. **Grant controls**
   - Require **Multi‑factor authentication**
6. **Enable policy**: **On**

### **Test**
- Sign in as `lab-user1`
- Confirm MFA is required

---

## 3. Create Location‑Based Policy (Block Non‑Trusted Countries)

### **Steps**
1. Go to **Conditional Access → Named locations**
2. Create:
   - **Trusted Location:** Your country (Belgium)
   - **Untrusted Location:** All other countries (or use “All locations” except trusted)
3. Create new policy:
   - Name: **CA‑Block‑Untrusted‑Countries**
4. **Assignments**
   - Users: **Test-Users**
   - Cloud apps: **All cloud apps**
5. **Conditions → Locations**
   - Include: **All locations**
   - Exclude: **Trusted locations**
6. **Grant**
   - Block access
7. **Enable policy**: **On**

### **Test**
- Use VPN to simulate a foreign IP  
- Sign in as `lab-user2`  
- Access should be **blocked**

---

## 4. Create Device‑Based Policy (Require Compliant Device)

### **Steps**
1. Ensure you have at least one **Intune‑enrolled device** (Windows or mobile).
2. Create new policy:
   - Name: **CA‑Require‑Compliant‑Device**
3. **Assignments**
   - Users: **Test-Users**
   - Cloud apps: **All cloud apps**
4. **Conditions → Device filters**
   - Require **device to be marked compliant**
5. **Grant**
   - Require **compliant device**
6. **Enable policy**: **On**

### **Test**
- Sign in from:
  - **Compliant device** → Access allowed  
  - **Non‑compliant device** → Access blocked  

---

## 5. Add Session Controls (Sign‑In Frequency)

### **Steps**
1. Create new policy:
   - Name: **CA‑Session‑Control‑SignInFrequency**
2. **Assignments**
   - Users: **Test-Users**
   - Cloud apps: **Microsoft 365**
3. **Session**
   - Sign‑in frequency: **Every 12 hours**
   - Persistent browser session: **Never persistent**
4. **Enable policy**: **On**

### **Test**
- Sign in as `lab-user1`
- Wait for session expiration or manually trigger reauthentication

---

## 6. Validate All Policies Using Sign‑In Logs

### **Steps**
1. Go to **Entra admin center → Monitoring → Sign‑in logs**
2. Filter by:
   - `lab-user1`
   - `lab-user2`
3. Validate:
   - MFA enforcement  
   - Location block  
   - Device compliance  
   - Session control triggers  

Export logs to your GitHub repo:

```
02-Conditional-Access/
  signin-logs-day2.csv
  policy-results.md
```

---

## 7. Day‑2 Completion Checklist
- [ ] MFA CA policy created  
- [ ] Location‑based block created  
- [ ] Device‑compliance policy created  
- [ ] Session control policy created  
- [ ] Break‑glass accounts excluded  
- [ ] All policies tested  
- [ ] Sign‑in logs exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Create Conditional Access policy](ca://s?q=Create_Conditional_Access_policy)
- [Security Defaults vs CA](ca://s?q=Explain_Azure_AD_Security_Defaults)
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)

