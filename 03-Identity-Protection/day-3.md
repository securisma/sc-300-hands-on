# Day‑3 — Identity Protection (Step‑by‑Step)

## 📌 Overview
Day‑3 focuses on Microsoft Entra **Identity Protection**, including user risk, sign‑in risk, MFA registration enforcement, and simulated risky sign‑ins.  
You will configure policies, trigger risk events, and export reports for your SC‑300 project.

---

## 1. Verify Prerequisites
Before starting:

- You must have **Entra ID P2** (Identity Protection requires P2).
- Ensure test users exist:
  - `lab-user1`
  - `lab-user2`
- Ensure break‑glass accounts are documented and excluded from policies.

**Reference:**  
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)

---

## 2. Configure User Risk Policy

### **Steps**
1. Go to **Entra admin center → Protection → Identity Protection → User risk policy**
2. Set:
   - **Users** → All users  
   - **Exclude** → Break‑glass accounts  
3. **User risk level** → Medium and above  
4. **Controls** → Require password change  
5. **Enable policy** → On

### **Expected Behavior**
If a user is flagged as “risky,” they must reset their password before continuing.

---

## 3. Configure Sign‑In Risk Policy

### **Steps**
1. Go to **Identity Protection → Sign‑in risk policy**
2. Set:
   - **Users** → All users  
   - **Exclude** → Break‑glass accounts  
3. **Sign‑in risk level** → Medium and above  
4. **Controls** → Require MFA  
5. **Enable policy** → On

### **Expected Behavior**
Risky sign‑ins will trigger MFA challenges.

---

## 4. Configure MFA Registration Policy

### **Steps**
1. Go to **Identity Protection → MFA registration policy**
2. Set:
   - **Users** → All users  
3. **Enable policy** → On

### **Expected Behavior**
Users without MFA will be forced to register.

---

## 5. Simulate Risky Sign‑Ins

### **Methods**
Use one or more of the following:

#### **Method A — Sign‑in from Tor Browser**
- Download Tor Browser  
- Sign in as `lab-user1`  
- This often triggers “Atypical travel” or “Anonymous IP address” risk.

#### **Method B — Use a foreign VPN**
- Connect to a non‑EU VPN  
- Sign in as `lab-user2`  
- This triggers “Unfamiliar sign‑in properties.”

#### **Method C — Use incorrect passwords repeatedly**
- Attempt multiple failed sign‑ins  
- Then sign in successfully  
- This may trigger “Password spray” or “Brute force” risk.

---

## 6. Review Risky Users & Risky Sign‑Ins

### **Steps**
1. Go to **Identity Protection → Risky users**
2. Review:
   - Risk level  
   - Risk history  
   - Risk events  
3. Go to **Identity Protection → Risky sign‑ins**
4. Review:
   - Sign‑in risk level  
   - Risk detections  
   - Conditional Access outcomes

### **Export Reports**
Save the following to your GitHub repo:

```
03-Identity-Protection/
  risky-users.csv
  risky-signins.csv
  identity-protection-summary.md
```

---

## 7. Remediate Risky Users

### **Steps**
1. Select a risky user (e.g., `lab-user1`)
2. Choose:
   - **Confirm user compromised**  
   - **Dismiss user risk**  
3. Document:
   - Reason  
   - Remediation steps  
   - Policy behavior  

---

## 8. Day‑3 Completion Checklist
- [ ] User risk policy configured  
- [ ] Sign‑in risk policy configured  
- [ ] MFA registration policy enabled  
- [ ] Risky sign‑ins simulated  
- [ ] Risky users reviewed  
- [ ] Risky sign‑ins reviewed  
- [ ] Reports exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Identity Protection](ca://s?q=Explain_Azure_AD_Identity_Protection)
- [Conditional Access](ca://s?q=Create_Conditional_Access_policy)
- [Security Defaults](ca://s?q=Explain_Azure_AD_Security_Defaults)

