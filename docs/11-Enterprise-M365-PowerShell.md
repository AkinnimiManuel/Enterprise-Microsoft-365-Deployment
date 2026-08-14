# Enterprise Microsoft 365 PowerShell

This document contains PowerShell commands used to administer and automate the Microsoft 365 environment.

---

# 1. Setup

## Install Required Modules

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
Install-Module ExchangeOnlineManagement -Scope CurrentUser
Install-Module MicrosoftTeams -Scope CurrentUser
Install-Module PnP.PowerShell -Scope CurrentUser
```

## Connect to Microsoft Graph

```powershell
Connect-MgGraph -Scopes "User.ReadWrite.All","Group.ReadWrite.All","Directory.ReadWrite.All","LicenseAssignment.ReadWrite.All"
```

## Connect to Exchange Online

```powershell
Connect-ExchangeOnline
```

## Connect to Microsoft Teams

```powershell
Connect-MicrosoftTeams
```

## Connect to SharePoint Online

```powershell
Connect-PnPOnline -Url "https://probryx-admin.sharepoint.com" -Interactive
```

---

# 2. Identity Management

## Create User

```powershell
$passwordProfile = @{
    Password = "TemporaryPassword123!"
    ForceChangePasswordNextSignIn = $true
}

New-MgUser `
    -DisplayName "John Doe" `
    -GivenName "John" `
    -Surname "Doe" `
    -UserPrincipalName "john.doe@probryx.org" `
    -MailNickname "john.doe" `
    -AccountEnabled:$true `
    -PasswordProfile $passwordProfile
```

## Update User

```powershell
Update-MgUser `
    -UserId "john.doe@probryx.org" `
    -JobTitle "IT Support Specialist" `
    -Department "Technology" `
    -OfficeLocation "Head Office"
```

## Disable User

```powershell
Update-MgUser `
    -UserId "john.doe@probryx.org" `
    -AccountEnabled:$false
```

## Delete User

```powershell
Remove-MgUser `
    -UserId "john.doe@probryx.org"
```

## Reset Password

```powershell
$passwordProfile = @{
    Password = "NewTemporaryPassword123!"
    ForceChangePasswordNextSignIn = $true
}

Update-MgUser `
    -UserId "john.doe@probryx.org" `
    -PasswordProfile $passwordProfile
```

---

# 3. Licensing

## View Available Licenses

```powershell
Get-MgSubscribedSku |
    Select-Object SkuPartNumber, SkuId, ConsumedUnits
```

## Assign License

```powershell
$sku = Get-MgSubscribedSku |
    Where-Object {$_.SkuPartNumber -eq "O365_BUSINESS_PREMIUM"}

Set-MgUserLicense `
    -UserId "john.doe@probryx.org" `
    -AddLicenses @{SkuId = $sku.SkuId} `
    -RemoveLicenses @()
```

## Remove License

```powershell
$sku = Get-MgSubscribedSku |
    Where-Object {$_.SkuPartNumber -eq "O365_BUSINESS_PREMIUM"}

Set-MgUserLicense `
    -UserId "john.doe@probryx.org" `
    -AddLicenses @() `
    -RemoveLicenses @($sku.SkuId)
```

---

# 4. Security Groups

## Create Security Group

```powershell
New-MgGroup `
    -DisplayName "IT-Security-Group" `
    -Description "IT Department Security Group" `
    -MailEnabled:$false `
    -MailNickname "it-security-group" `
    -SecurityEnabled:$true
```

## Add Member

```powershell
$group = Get-MgGroup -Filter "displayName eq 'IT-Security-Group'"
$user = Get-MgUser -UserId "john.doe@probryx.org"

New-MgGroupMember `
    -GroupId $group.Id `
    -DirectoryObjectId $user.Id
```

## Remove Member

```powershell
$group = Get-MgGroup -Filter "displayName eq 'IT-Security-Group'"
$user = Get-MgUser -UserId "john.doe@probryx.org"

Remove-MgGroupMemberByRef `
    -GroupId $group.Id `
    -DirectoryObjectId $user.Id
```

---

# 5. Microsoft 365 Groups

## Create Microsoft 365 Group

```powershell
New-MgGroup `
    -DisplayName "IT Department" `
    -Description "IT Department Collaboration Group" `
    -MailEnabled:$true `
    -MailNickname "itdepartment" `
    -SecurityEnabled:$false `
    -GroupTypes @("Unified")
```

## Add Member

```powershell
$group = Get-MgGroup -Filter "displayName eq 'IT Department'"
$user = Get-MgUser -UserId "john.doe@probryx.org"

New-MgGroupMember `
    -GroupId $group.Id `
    -DirectoryObjectId $user.Id
```

---

# 6. Distribution Lists

## Create Distribution List

```powershell
New-DistributionGroup `
    -Name "DL-AllStaff" `
    -DisplayName "All Staff" `
    -Alias "dl-allstaff" `
    -PrimarySmtpAddress "dl-allstaff@probryx.org"
```

## Add Member

```powershell
Add-DistributionGroupMember `
    -Identity "DL-AllStaff" `
    -Member "jane.smith@probryx.org"
```

## Remove Member

```powershell
Remove-DistributionGroupMember `
    -Identity "DL-AllStaff" `
    -Member "jane.smith@probryx.org" `
    -Confirm:$false
```

---

# 7. Shared Mailboxes

## Create Shared Mailbox

```powershell
New-Mailbox `
    -Shared `
    -Name "IT Support" `
    -DisplayName "IT Support" `
    -Alias "itsupport" `
    -PrimarySmtpAddress "itsupport@probryx.org"
```

## Grant Full Access

```powershell
Add-MailboxPermission `
    -Identity "itsupport@probryx.org" `
    -User "stefan.akinnimi@probryx.org" `
    -AccessRights FullAccess `
    -InheritanceType All
```

## Grant Send As

```powershell
Add-RecipientPermission `
    -Identity "itsupport@probryx.org" `
    -Trustee "stefan.akinnimi@probryx.org" `
    -AccessRights SendAs `
    -Confirm:$false
```

---

# 8. Exchange Online

## Verify Mailbox

```powershell
Get-EXOMailbox `
    -Identity "john.doe@probryx.org"
```

## Grant Mailbox Full Access

```powershell
Add-MailboxPermission `
    -Identity "john.doe@probryx.org" `
    -User "stefan.akinnimi@probryx.org" `
    -AccessRights FullAccess `
    -InheritanceType All
```

## Grant Send As

```powershell
Add-RecipientPermission `
    -Identity "john.doe@probryx.org" `
    -Trustee "stefan.akinnimi@probryx.org" `
    -AccessRights SendAs `
    -Confirm:$false
```

## Create Mail Flow Rule

```powershell
New-TransportRule `
    -Name "External Email Warning" `
    -FromScope NotInOrganization `
    -ApplyHtmlDisclaimerText "External email - use caution when opening links or attachments." `
    -ApplyHtmlDisclaimerLocation Prepend
```

---

# 9. Microsoft Teams

## Create Team

```powershell
New-Team `
    -DisplayName "IT Department" `
    -Description "IT Department Collaboration Team" `
    -Visibility Private
```

## Add Member

```powershell
Add-TeamUser `
    -GroupId "<TEAM-ID>" `
    -User "john.doe@probryx.org"
```

## Create Channel

```powershell
New-TeamChannel `
    -GroupId "<TEAM-ID>" `
    -DisplayName "Projects" `
    -Description "IT Projects and Activities" `
    -MembershipType Standard
```

## List Teams

```powershell
Get-Team
```

---

# 10. SharePoint Online

## Connect to SharePoint

```powershell
Connect-PnPOnline `
    -Url "https://probryx-admin.sharepoint.com" `
    -Interactive
```

## Create Team Site

```powershell
New-PnPSite `
    -Type TeamSite `
    -Title "IT Department" `
    -Alias "ITDepartment" `
    -Owners "stefan.akinnimi@probryx.org"
```

## Create Document Library

```powershell
Connect-PnPOnline `
    -Url "https://probryx.sharepoint.com/sites/ITDepartment" `
    -Interactive

New-PnPList `
    -Title "IT Documentation" `
    -Template DocumentLibrary
```

## Add Site Member

```powershell
Add-PnPGroupMember `
    -Identity "IT Department Members" `
    -LoginName "john.doe@probryx.org"
```

---

# 11. Administration

## Export Users

```powershell
Get-MgUser -All |
    Select-Object DisplayName,
        UserPrincipalName,
        JobTitle,
        Department,
        AccountEnabled |
    Export-Csv ".\users.csv" -NoTypeInformation
```

## List Users

```powershell
Get-MgUser -All |
    Select-Object DisplayName,
        UserPrincipalName,
        JobTitle,
        Department,
        AccountEnabled |
    Format-Table -AutoSize
```

## Search Sign-In Logs

```powershell
Get-MgAuditLogSignIn -Top 50 |
    Select-Object CreatedDateTime,
        UserDisplayName,
        UserPrincipalName,
        AppDisplayName,
        IpAddress,
        Status
```

## Search Directory Audit Logs

```powershell
Get-MgAuditLogDirectoryAudit -Top 50 |
    Select-Object ActivityDateTime,
        ActivityDisplayName,
        Category,
        Result
```

---

# 12. Verification Commands

## Verify User

```powershell
Get-MgUser `
    -UserId "jane.smith@probryx.org"
```

## Verify Security Group

```powershell
Get-MgGroup `
    -Filter "displayName eq 'IT-Security-Group'"
```

## Verify Distribution List

```powershell
Get-DistributionGroup `
    -Identity "DL-AllStaff"
```

## Verify Shared Mailbox

```powershell
Get-EXOMailbox `
    -Identity "itsupport@probryx.org"
```

## Verify Teams

```powershell
Get-Team
```

## Verify SharePoint Sites

```powershell
Get-PnPTenantSite
```

---

# PowerShell Automation Principles

- Use least-privilege permissions.
- Test commands before production use.
- Avoid hard-coded passwords.
- Use variables for reusable values.
- Validate the result of administrative operations.
- Store reusable scripts in source control.
- Use automation for repetitive administrative tasks.

---

# Conclusion

PowerShell provides a repeatable method for administering the Microsoft 365 environment.

The commands documented here cover:

- Microsoft Entra ID
- Users
- Groups
- Licensing
- Exchange Online
- Shared Mailboxes
- Distribution Lists
- Microsoft Teams
- SharePoint Online
- Reporting
- Audit Logs

These commands form the foundation for future Microsoft 365 automation and Infrastructure-as-Code practices.