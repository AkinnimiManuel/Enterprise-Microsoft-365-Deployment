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
![](../../Screenshots/identity/01-entra-overview.png)

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
![](../../Screenshots/identity/02-create-users.png)

## Step 3 – Populate User Properties
Configure:
- Department
- Job title
- Office
- Usage location
- Manager
- Phone

Screenshot:
![](../../Screenshots/identity/03-user-properties.png)

## Step 4 – Assign Licenses
Assign Microsoft 365 Business Premium.

Screenshot:
![](../../Screenshots/identity/04-license-assignment.png)   

![](../../Screenshots/identity/04-license-assignment-1.png)

![](../../Screenshots/identity/04-license-assignment-2.png)

All Users Created
![](../../Screenshots/identity/02-create-users-1.png)

## Step 5 – Administrative Roles
Identity → Roles and administrators

Assign:
- Global Administrator
- User Administrator
- Exchange Administrator
- Teams Administrator
- SharePoint Administrator

Screenshot:
![](../../Screenshots/identity/05-admin-roles.png)

## Step 6 – Authentication Methods
Entar ID - Authentication Methods

Review:
- Microsoft Authenticator
- FIDO2
- SMS
- Temporary Access Pass

Screenshot:
![](../../Screenshots/identity/06-auth-methods.png)

## Step 7 – Self-Service Password Reset
Entra ID → Password reset

Enable SSPR.

Screenshot:
![](../../Screenshots/identity/07-sspr.png)


## Step 8 – Guest Users
Identity → External Identities

Document guest access strategy.

Screenshot:
![](../../Screenshots/identity/08-guest-users.png)

![](../../Screenshots/identity/08-guest-users-1.png)

## Step 9 – User Lifecycle
Document Joiner / Mover / Leaver process.

###Joiner 

```mermaid
flowchart TD
    A[HR Request] --> B[Create User Account]
    B --> C[Assign Microsoft 365 License]
    C --> D[Assign Groups & Roles]
    D --> E[Configure MFA & SSPR]
    E --> F[Provide Temporary Password]
    F --> G[User Signs In]
    G --> H[Identity Provisioned ✅]
```

Screenshot:
![](../../Screenshots/identity/09-user-lifecycle.png)

### Mover 

```mermaid
flowchart TD
    A[Manager/HR Request] --> B[Review New Role]
    B --> C[Update User Profile]
    C --> D[Update Department]
    D --> E[Update Manager]
    E --> F[Remove Old Group Memberships]
    F --> G[Assign New Groups & Roles]
    G --> H[Review License Requirements]
    H --> I[Validate User Access]
    I --> J[Identity Updated ✅]
```

Screenshot:
![](../../Screenshots/identity/09-user-lifecycle-1.png)

### Leaver

```mermaid
flowchart TD
    A[HR Termination Notice] --> B[Block User Sign-In]
    B --> C[Reset Password]
    C --> D[Remove Administrative Roles]
    D --> E[Remove Microsoft 365 License]
    E --> F[Convert Mailbox to Shared Mailbox]
    F --> G[Remove Group Memberships]
    G --> H[Archive/Delete Account]
    H --> I[Identity Deprovisioned ✅]
```

Block sign-in/disable account
![](../../Screenshots/identity/09-user-lifecycle-2.png)

Remove Group membership
![](../../Screenshots/identity/09-user-lifecycle-3.png)

Remove License
![](../../Screenshots/identity/09-user-lifecycle-4.png)

           ┌──────────────┐
           │   Joiner     │
           │  Onboarding  │
           └──────┬───────┘
                  │
                  ▼
        Identity Created
                  │
                  ▼
      Active Employee Account
                  │
        ┌─────────┴─────────┐
        ▼                   ▼
   Role Change          Department Change
      (Mover)               (Mover)
        │                   │
        └─────────┬─────────┘
                  ▼
       Updated Identity & Access
                  │
                  ▼
          Employment Ends
                  │
                  ▼
              Leaver
                  │
                  ▼
      Account Disabled & Archived


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

## Validation 1 (User Sign in)
- User sign-in
![](../../Screenshots/identity/10-validation-user-sign-in.png)

MFA Set up requets
- MFA works
![](../../Screenshots/identity/10-validation-MFA.png)

MFA Added successfully ✅
![](../../Screenshots/identity/10-validation-MFA.-added.png)

Jane Smith signed in successfully ✅
Maibox Active 

![](../../Screenshots/identity/10-validation-user-sign-in-successful.png)

## Validation 2 (Password Resets)
- Password reset works
![](../../Screenshots/identity/10-validation-password-reset.png)

![](../../Screenshots/identity/10-validation-password-reset-done.png)

## Validation 3 (Admin Role Verification)

- Admin roles verified
Jane Smith (User Administrator)

The following validation tests were performed to verify that the delegated **User Administrator** role was functioning as expected while enforcing Microsoft Entra ID Role-Based Access Control (RBAC) and the principle of least privilege.

---

#### User Provisioning

**Objective**

Verify that a User Administrator can successfully create a new user account.

**Procedure**

1. Signed in as **Jane Smith** (`jane.smith@probryx.org`).
![](../../Screenshots/identity/10-validation-jane-smith-entra-role.png)

2. Navigated to **Microsoft Entra Admin Center** → **Identity** → **Users**.
3. Selected **New User (Bob Philip)**.
4. Created a test user account.

**Expected Result**

The User Administrator should be able to create standard user accounts.

**Actual Result**

The test user account was created successfully without requiring Global Administrator privileges.

**Status**

✅ Passed

**Screenshot**

![](../../Screenshots/identity/10-validation-bob-philip-user-created.png)

![](../../Screenshots/identity/10-validation-bob-philip-user-created-1.png)

---

#### Password Reset

**Objective**

Verify that a User Administrator can reset the password of a standard user.

**Procedure**

1. Signed in as **Jane Smith**.
2. Selected an existing user account.
3. Chose **Reset Password**.
4. Generated a temporary password.

**Expected Result**

The User Administrator should be able to reset passwords for supported user accounts.

**Actual Result**

The password reset operation completed successfully, confirming delegated password management functionality.

**Status**

✅ Passed

**Screenshot**

![](../../Screenshots/identity/10-validation-reset-password.png)

---

#### Role-Based Access Control (Least Privilege)

**Objective**

Verify that the User Administrator role cannot perform actions reserved for higher privileged administrative roles.

**Procedure**

1. Signed in as **Jane Smith**.
2. Attempted to perform an administrative action outside the scope of the User Administrator role (for example, assigning the **Global Administrator** role).
3. The add assignments button should be greyed out

**Expected Result**

Access should be denied because the operation requires higher administrative privileges.

**Actual Result**

Microsoft Entra ID denied the operation, confirming that Role-Based Access Control (RBAC) and the principle of least privilege were correctly enforced.

**Status**

✅ Passed

**Screenshot**

![](../../Screenshots/identity/10-validation-RBAC.png)

---

## Validation Summary

| Validation Test   | Expected Result                   | Actual Result             | Status |
| ----------------- | --------------------------------- | ------------------------- | :----: |
| User Provisioning | User account created successfully | Successful                |    ✅   |
| Password Reset    | Password reset completed          | Successful                |    ✅   |
| RBAC Enforcement  | Privileged action denied          | Access denied as expected |    ✅   |

## Conclusion

The validation activities confirmed that the Microsoft Entra ID identity environment was successfully configured and operating as intended. User accounts were provisioned correctly, and a newly created user was able to sign in successfully, verifying the onboarding process. Multi-Factor Authentication (MFA) was successfully configured and enforced, demonstrating an additional layer of identity protection. Password reset functionality was validated through both administrative password reset and user authentication scenarios, confirming effective identity recovery capabilities.

Role-Based Access Control (RBAC) was also successfully validated. The **User Administrator** account was able to perform delegated identity management tasks, including creating new user accounts and resetting user passwords, while being prevented from performing privileged actions outside its assigned role, such as assigning role to users as a user admin. This confirms that the principle of least privilege was correctly implemented and that administrative permissions were appropriately restricted.

Overall, the validation results demonstrate that the identity management configuration provides a secure, well-governed, and enterprise-ready Microsoft Entra ID environment that aligns with Microsoft security best practices and establishes a solid foundation for subsequent phases of the Enterprise Microsoft 365 Deployment project.


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
|1.0|2026-08-01|Stefan Akinnimi|
