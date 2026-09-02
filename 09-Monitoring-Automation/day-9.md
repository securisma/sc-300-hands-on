# Day‑9 — Monitoring, Logs & Automation

## 📌 Overview
Day‑9 focuses on **Monitoring**, **Log Analytics**, **Workbooks**, and **Automation** in Microsoft Entra ID.  
You will configure diagnostic settings, send logs to Log Analytics, build a workbook, create alerts, and automate responses using Graph API or PowerShell.

This is essential for SC‑300 and real‑world identity operations.

---

## 1. Verify Prerequisites
Before starting:

- You must have:
  - A **Log Analytics Workspace**
  - A **Subscription** with permissions
  - Entra ID P1/P2 features enabled
- Ensure test users exist:
  - `lab-user1`
  - `lab-user2`
- Ensure previous days (CA, PIM, Access Packages, Reviews) generated sign‑ins.

**Reference:**  
- [Entra Monitoring](ca://s?q=Explain_Entra_Monitoring)

---

## 2. Create a Log Analytics Workspace

### **Steps**
1. Go to **Azure Portal → Log Analytics workspaces → Create**
2. Configure:
   - **Name:** `entra-lab-law`
   - **Region:** Same as your tenant (EU recommended)
   - **Pricing tier:** Pay‑as‑you‑go (lab friendly)
3. Create workspace

### **Expected Behavior**
Workspace is ready to ingest Entra ID logs.

---

## 3. Enable Entra ID Diagnostic Settings

### **Steps**
1. Go to **Azure Portal → Microsoft Entra ID → Diagnostic settings**
2. Create a new diagnostic setting:
   - **Name:** `entra-logs-to-law`
3. Enable the following logs:
   - **SignInLogs**
   - **AuditLogs**
   - **ProvisioningLogs**
   - **RiskyUsers**
   - **RiskySignIns**
4. Destination:
   - **Send to Log Analytics workspace**
   - Select `entra-lab-law`
5. Save

### **Expected Behavior**
Logs begin flowing into Log Analytics within minutes.

---

## 4. Query Logs Using KQL (Kusto Query Language)

### **Steps**
1. Go to **Log Analytics workspace → Logs**
2. Run queries:

#### **Sign‑in logs**
```kql
SigninLogs
| take 20
```

#### **Failed sign‑ins**
```kql
SigninLogs
| where ResultType != 0
| project UserPrincipalName, ResultType, ResultDescription, AppDisplayName, IPAddress
```

#### **Risky sign‑ins**
```kql
RiskySignIns
| project UserPrincipalName, RiskLevel, RiskEventTypes
```

### **Store Queries**
```
09-Monitoring-Automation/kql-queries.md
```

---

## 5. Create an Identity Monitoring Workbook

### **Steps**
1. Go to **Azure Portal → Monitor → Workbooks**
2. Click **New workbook**
3. Add sections:
   - **Sign‑in summary**
   - **Failed sign‑ins**
   - **Risky sign‑ins**
   - **Conditional Access outcomes**
4. Add KQL queries from Step 4
5. Save workbook as:
   - `entra-identity-monitoring`

### **Expected Behavior**
You now have a visual dashboard for identity operations.

---

## 6. Create Alerts for Identity Events

### **Steps**
1. Go to **Monitor → Alerts → Create alert rule**
2. Configure:
   - **Scope:** Log Analytics workspace
   - **Condition:** Custom log search
3. Example alert query:
```kql
SigninLogs
| where ResultType != 0
```
4. Alert logic:
   - Trigger when count > 5 in 10 minutes
5. Action group:
   - Email: `lab-admin@yourlab.onmicrosoft.com`
6. Save alert

### **Expected Behavior**
You receive alerts for abnormal sign‑in failures.

---

## 7. Automate Identity Operations (Graph API / PowerShell)

### **Option A — Graph API**
Use Graph API to automate identity tasks.

#### Example: List users
```http
GET https://graph.microsoft.com/v1.0/users
```

#### Example: Disable risky user
```http
POST https://graph.microsoft.com/v1.0/users/<id>/disableAccount
```

### **Option B — PowerShell**
Install module:
```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
```

#### Example: Get sign‑ins
```powershell
Get-MgAuditLogSignIn -Top 20
```

#### Example: Remove user from group
```powershell
Remove-MgGroupMember -GroupId <groupId> -DirectoryObjectId <userId>
```

### **Store Scripts**
```
09-Monitoring-Automation/graph-scripts.ps1
09-Monitoring-Automation/powershell-scripts.ps1
```

---

## 8. Export Monitoring Evidence

### **Steps**
1. Export:
   - Workbook JSON
   - KQL queries
   - Alert rules
   - Sample logs
2. Store in GitHub:

```
09-Monitoring-Automation/workbook.json
09-Monitoring-Automation/alerts.md
09-Monitoring-Automation/sample-logs.csv
```

---

## 9. Day‑9 Completion Checklist
- [ ] Log Analytics workspace created  
- [ ] Diagnostic settings enabled  
- [ ] KQL queries tested  
- [ ] Workbook created  
- [ ] Alerts configured  
- [ ] Graph API tested  
- [ ] PowerShell tested  
- [ ] Evidence exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Entra Monitoring](ca://s?q=Explain_Entra_Monitoring)
- [Graph API](ca://s?q=Explain_Microsoft_Graph_API)
- [KQL](ca://s?q=Explain_KQL)
