# Day‑12 — Identity Automation Pipeline (GitHub Actions + Microsoft Graph)

## 📌 Overview
Day‑12 focuses on building an **Identity Automation Pipeline** using:
- GitHub Actions  
- Microsoft Graph API  
- PowerShell  
- Secure secrets  
- Automated identity tasks  

This transforms your SC‑300 lab into a real DevSecOps identity workflow.

---

## 1. Prerequisites

Before starting:

- GitHub repository created  
- GitHub Actions enabled  
- App Registration created (Day‑5)  
- Client secret stored securely  
- Microsoft Graph permissions granted  
- PowerShell installed locally  

**Reference:**  
- [Microsoft Graph](ca://s?q=Explain_Microsoft_Graph_API)

---

## 2. Create an Automation App Registration

### **Steps**
1. Go to **Entra admin center → Applications → App registrations → New registration**
2. Configure:
   - **Name:** `Lab-Automation-App`
   - **Supported account types:** Single tenant
3. Create a **client secret**
4. Add **API permissions**:
   - Microsoft Graph → Application → `User.Read.All`
   - Microsoft Graph → Application → `Group.ReadWrite.All`
5. Grant **admin consent**

### **Store Metadata**
```
12-Automation-Pipeline/app-info.md
```

---

## 3. Store Secrets in GitHub

### **Steps**
1. Go to **GitHub → Repo → Settings → Secrets → Actions**
2. Add:
   - `TENANT_ID`
   - `CLIENT_ID`
   - `CLIENT_SECRET`

### **Expected Behavior**
GitHub Actions can authenticate to Microsoft Graph securely.

---

## 4. Create GitHub Actions Workflow

Create file:

```
.github/workflows/identity-automation.yml
```

### **Workflow Example**
```yaml
name: Identity Automation

on:
  workflow_dispatch:

jobs:
  run-automation:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install PowerShell
        uses: PowerShell/PowerShell@v2

      - name: Run Identity Script
        run: pwsh ./automation/identity-script.ps1
        env:
          TENANT_ID: ${{ secrets.TENANT_ID }}
          CLIENT_ID: ${{ secrets.CLIENT_ID }}
          CLIENT_SECRET: ${{ secrets.CLIENT_SECRET }}
```

### **Store Workflow**
```
12-Automation-Pipeline/identity-automation.yml
```

---

## 5. Create PowerShell Automation Script

Create folder:

```
automation/
```

Create file:

```
automation/identity-script.ps1
```

### **Example Script**
```powershell
# Authenticate to Graph
Connect-MgGraph -TenantId $env:TENANT_ID -ClientId $env:CLIENT_ID -ClientSecret $env:CLIENT_SECRET

# List users
$users = Get-MgUser -All
$users | Select-Object DisplayName, UserPrincipalName

# Example: Remove inactive guest users
$guests = $users | Where-Object { $_.UserType -eq "Guest" }
foreach ($guest in $guests) {
    Write-Output "Removing guest: $($guest.DisplayName)"
    Remove-MgUser -UserId $guest.Id
}
```

### **Store Script**
```
12-Automation-Pipeline/identity-script.ps1
```

---

## 6. Add Automated Identity Tasks

### **Examples**
- Disable risky users  
- Remove inactive guest users  
- Export sign‑in logs  
- Rotate secrets  
- Enforce group membership  
- Auto‑assign app roles  
- Auto‑revoke sessions  

Document tasks:

```
12-Automation-Pipeline/tasks.md
```

---

## 7. Test the Automation Pipeline

### **Steps**
1. Go to **GitHub → Actions**
2. Run workflow manually
3. Validate:
   - Authentication  
   - Script execution  
   - Graph API calls  
   - Identity changes in Entra ID  

### **Store Evidence**
```
12-Automation-Pipeline/run-output.md
```

---

## 8. Add Scheduled Automation

Modify workflow:

```yaml
on:
  schedule:
    - cron: "0 */6 * * *"   # Every 6 hours
```

### **Use Cases**
- Continuous guest cleanup  
- Continuous risky user remediation  
- Continuous group enforcement  
- Continuous log export  

---

## 9. Day‑12 Completion Checklist
- [ ] Automation App Registration created  
- [ ] Graph permissions granted  
- [ ] GitHub secrets stored  
- [ ] GitHub Actions workflow created  
- [ ] PowerShell automation script created  
- [ ] Identity tasks automated  
- [ ] Pipeline tested  
- [ ] Evidence exported  
- [ ] GitHub folder updated  

---

## 🔗 Helpful Deep‑Dive Links
- [Microsoft Graph](ca://s?q=Explain_Microsoft_Graph_API)
- [PowerShell Graph Module](ca://s?q=Explain_Microsoft_Graph_PowerShell)
- [Identity Governance](ca://s?q=Explain_Access_Packages)
- [Zero Trust](ca://s?q=Explain_Zero_Trust_Architecture)
