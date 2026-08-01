# Identity Management

> **Project:** Enterprise Microsoft 365 Deployment  
> **Company:** Probryx Technologies Ltd.

---

# 1. Executive Summary
This document describes the complete enterprise identity implementation for Probryx Technologies Ltd.

# 2. Business Requirement
Implement a secure, scalable Microsoft Entra ID identity platform following Zero Trust and least privilege principles.

# 3. Objectives
- Enterprise identity design
- Naming standards
- User provisioning
- Administrative roles
- Authentication methods
- Password policies
- SSPR
- Guest users
- Validation

# 4. Prerequisites
- Business Premium tenant
- probryx.org verified
- Global Administrator

# 5. Enterprise Identity Design

## Departments
| Department | Code |
|---|---|
| Executive | EXE |
| IT | IT |
| HR | HR |
| Finance | FIN |
| Sales | SAL |
| Operations | OPS |

## Naming Standards

| Item | Standard |
|---|---|
| UPN | firstname.lastname@probryx.org |
| Display Name | Firstname Lastname |
| Mail Nickname | firstnamelastname |

## Administrative Accounts
- global.admin@probryx.org
- identity.admin@probryx.org
- exchange.admin@probryx.org
- teams.admin@probryx.org
- sharepoint.admin@probryx.org
- helpdesk.admin@probryx.org

# 6. Implementation Steps

## Step 1 – Review Entra Overview
Navigate: Identity → Overview

Screenshot:
![](../screenshots/identity/01-entra-overview.png)

## Step 2 – Create Users
Identity → Users → New user

Created users for every department.

users created:
- Stefan Akinnimi (IT Administrator - Global Administrator)
- Jane Smith (HR Manager)
- David Johnson (Finance)
- Sarah Wilson (Sales)
- Michael Brown (Operations)

Screenshot:
![](../screenshots/identity/02-create-users.png)

## Step 3 – Populate User Properties
Configure:
- Department
- Job title
- Office
- Usage location
- Manager
- Phone

Screenshot:
![](../screenshots/identity/03-user-properties.png)

## Step 4 – Assign Licenses
Assign Microsoft 365 Business Premium.

Screenshot:
![](../screenshots/identity/04-license-assignment.png)   

![](../screenshots/identity/04-license-assignment-1.png)

![](../screenshots/identity/04-license-assignment-2.png)

All Users Created
![](../screenshots/identity/02-create-users-1.png)

## Step 5 – Administrative Roles
Identity → Roles and administrators

Assign:
- Global Administrator
- User Administrator
- Exchange Administrator
- Teams Administrator
- SharePoint Administrator

Screenshot:
![](../screenshots/identity/05-admin-roles.png)

## Step 6 – Authentication Methods
Entar ID - Authentication Methods

Review:
- Microsoft Authenticator
- FIDO2
- SMS
- Temporary Access Pass

Screenshot:
![](../screenshots/identity/06-auth-methods.png)

## Step 7 – Self-Service Password Reset
Entra ID → Password reset

Enable SSPR.

Screenshot:
![](../screenshots/identity/07-sspr.png)


## Step 8 – Guest Users
Identity → External Identities

Document guest access strategy.

Screenshot:
![](../screenshots/identity/08-guest-users.png)

![](../screenshots/identity/08-guest-users-1.png)

## Step 9 – User Lifecycle
Document Joiner / Mover / Leaver process.

Joiner 

Screenshot:
![](../screenshots/identity/09-user-lifecycle.png)

Mover 

Screenshot:
![](../screenshots/identity/09-user-lifecycle-1.png)

Leaver

Block sign-in/disable account
![](../screenshots/identity/09-user-lifecycle-2.png)

Remove Group membership
![](../screenshots/identity/09-user-lifecycle-3.png)

Remove License
![](../screenshots/identity/09-user-lifecycle-4.png)
# 7. Technical Explanation
Explain:
- Least privilege
- RBAC
- MFA
- SSPR
- Naming standards
- Identity lifecycle
- External identities

# 8. Validation
- User sign-in
- License assigned
- MFA works
- Password reset works
- Admin roles verified
- Guest invitation tested

# 9. Troubleshooting
| Issue | Resolution |
|---|---|
| Cannot create user | Verify Global Admin |
| License unavailable | Check subscription |
| MFA prompt missing | Review Authentication Methods |
| SSPR unavailable | Review Password Reset configuration |

# 10. Lessons Learned
- Identity planning reduces future administration effort.
- Least privilege improves security.
- Consistent naming improves manageability.

# 11. References
- Microsoft Learn – Microsoft Entra ID
- Microsoft Learn – Authentication Methods
- Microsoft Learn – SSPR
- Microsoft Learn – RBAC

# Change Log
|Version|Date|Author|
|---|---|---|
|1.0|YYYY-MM-DD|Emmanuel Stefan Akinnimi|
