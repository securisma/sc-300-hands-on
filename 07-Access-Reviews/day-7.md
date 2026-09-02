# Day‑7 — Access Reviews

## 📌 Overview
Day‑7 focuses on Microsoft Entra **Access Reviews**, a core Identity Governance capability.  
You will create reviews for groups, app roles, and guest users, configure auto‑apply results, complete review cycles, and export evidence.

This is a major SC‑300 topic and essential for real‑world least‑privilege governance.

---

## 1. Verify Prerequisites
Before starting:

- You must have **Entra ID P2** (Access Reviews require P2).
- Ensure test users exist:
  - `lab-user1`
  - `lab-user2`
- Ensure guest user exists:
  - `guest-user@example.com`
- Ensure groups exist:
  - `Test-Users`
  - `Sec-Admins`
- Ensure app roles exist (optional):
  - `Lab-Demo-App` roles from Day‑5

**Reference:**  
- [Access Reviews](ca://s?q=Explain_Access_Reviews)

---

## 2. Create a Group Membership Access Review

### **Steps**
1. Go to **Entra admin center → Identity Governance → Access reviews**
2. Click **New access review**
3. Configure:
   - **Review name:** `Review-Test-Users-Membership`
   - **Scope:** Group → `Test-Users`
   - **Reviewers:** Group owners or `lab-admin`
   - **Duration:** 7 days
   - **Recurrence:** One-time
4. **Settings**
   - Auto‑apply results → **Enable**
   - If reviewer doesn’t respond → **Remove access**
5. Create the review

### **Expected Behavior**
Reviewers must confirm whether each user should remain in the group.

---

## 3. Create an App Role Access Review (Optional but Recommended)

### **Steps**
1. Click **New access review**
2. Configure:
   - **Review name:** `Review-Lab-Demo-App-Roles`
   - **Scope:** Application → `Lab-Demo-App`
   - **Reviewers:** `lab-admin`
   - **Duration:** 7 days
3. **Settings**
   - Auto‑apply results → **Enable**
   - Remove access if reviewer does not respond

### **Expected Behavior**
Reviewers validate app role assignments.

---

## 4. Create a Guest User Access Review

### **Steps**
1. Click **New access review**
2. Configure:
   - **Review name:** `Review-Guest-Users`
   - **Scope:** **All guest users**
   - **Reviewers:** `lab-admin`
   - **Duration:** 7 days
3. **Settings**
   - Auto‑apply results → **Enable**
   - Remove access if reviewer does not respond

### **Expected Behavior**
Guest users who no longer need access are automatically removed.

---

## 5. Complete the Review Cycle

### **Steps**
1. Sign in as `lab-admin`
2. Go to **Identity Governance → Access reviews**
3. Open each active review:
   - `Review-Test-Users-Membership`
   - `Review-Lab-Demo-App-Roles`
   - `Review-Guest-Users`
4. For each user:
   - Approve  
   - Deny  
   - Take no action (auto‑apply will handle)

### **Expected Behavior**
Access is updated based on reviewer decisions.

---

## 6. Validate Auto‑Apply Results

### **Steps**
1. After the review ends, check:
   - Group membership changes  
   - App role assignments  
   - Guest user access  
2. Go to:
   - **Groups → Test-Users**
   - **Applications → Lab-Demo-App → Users**
   - **Users → Guest users**

### **Expected Behavior**
Users removed by auto‑apply should no longer appear in assignments.

---

## 7. Export Access Review Results

### **Steps**
1. Go to **Access reviews → Completed reviews**
2. Select each review
3. Export:
   - Review results (CSV)
   - Reviewer decisions
   - Auto‑apply actions

### **Store in GitHub**
```
07-Access-Reviews/test-users-review.csv
07-Access-Reviews/app-roles-review.csv
07-Access-Reviews/guest-users-review.csv
07-Access-Reviews/access-review-summary.md
```

---

## 8. Day‑7 Completion Checklist
- [ ] Group membership review created  
- [ ] App role review created  
- [ ] Guest user review created  
- [ ] Auto‑apply enabled  
- [ ] Review cycle completed  
- [ ] Access changes validated  
- [ ] Reports exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Access Reviews](ca://s?q=Explain_Access_Reviews)
- [Access Packages](ca://s?q=Explain_Access_Packages)
- [B2B Collaboration](ca://s?q=Explain_Azure_AD_B2B)
