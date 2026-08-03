# Project Planning

## Project Information

**Project Name:** Enterprise Microsoft 365 Deployment

**Company:** Probryx Technologies Ltd.

**Domain:** probryx.org

**Project Type:** Enterprise Microsoft 365 Business Premium Deployment

**Project Owner:** Stefan Akinnimi

------------------------------------------------------------------------

# Company Overview

Probryx Technologies Ltd. is a fictional cybersecurity and cloud
consulting company providing Microsoft 365, cloud, cybersecurity and
managed IT services.

-   **Industry:** Cybersecurity & Cloud Consulting
-   **Employees:** 150
-   **Locations:** Lagos (HQ), Abuja, Remote Workforce

# Mission

To help organizations modernize, secure and optimize their IT
infrastructure through Microsoft cloud technologies and cybersecurity
best practices.

# Vision

To become one of Africa's leading cloud and cybersecurity consulting
firms.

# Business Requirements

## Identity

-   Centralized identity management
-   Single Sign-On (SSO)
-   Role-Based Access Control (RBAC)

## Communication

-   Corporate email
-   Shared mailboxes
-   Distribution lists
-   Shared calendars

## Collaboration

-   Microsoft Teams
-   SharePoint Online
-   OneDrive for Business
-   Microsoft 365 Groups

## Administration

-   User lifecycle management
-   Group management
-   License management
-   Administrative role delegation

## Security

-   Multi-Factor Authentication
-   Security baseline
-   SPF, DKIM and DMARC
-   Secure remote work

------------------------------------------------------------------------

# Project Scope

## Included

-   Microsoft Entra ID
-   Exchange Online
-   Microsoft Teams
-   SharePoint Online
-   OneDrive for Business
-   Microsoft 365 Groups
-   RBAC
-   Custom Domain Integration

## Excluded (Future Projects)

-   Microsoft Intune
-   Microsoft Defender XDR
-   Conditional Access
-   Microsoft Purview
-   Microsoft Sentinel
-   Hybrid Identity

------------------------------------------------------------------------

# Success Criteria

-   Domain verified
-   Tenant configured
-   Users created
-   Licenses assigned
-   Exchange operational
-   Teams operational
-   SharePoint operational
-   OneDrive operational
-   Baseline security implemented
-   Validation completed
-   Documentation completed

------------------------------------------------------------------------

# Departments

  Department                 Users
  ------------------------ -------
  Executive                      2
  Information Technology         4
  Human Resources                2
  Finance                        2
  Sales                          3
  Marketing                      2
  Customer Support               3

------------------------------------------------------------------------

# Naming Standards

-   **UPN:** firstname.lastname@probryx.org
-   **Display Name:** Firstname Lastname
-   **Employee ID:** PBX-0001
-   **Security Groups:** SG-Department-Role
-   **Microsoft 365 Groups:** M365-Department
-   **Distribution Lists:** DL-Department
-   **Shared Mailboxes:** info@, support@, hr@, finance@, sales@
-   **Teams:** Executive Leadership, IT Operations, HR, Finance, Sales,
    Marketing, Customer Support
-   **Devices (Future):** PBX-LAP-001, PBX-DESK-001, PBX-SRV-001

------------------------------------------------------------------------

# High-Level Architecture

``` text
Internet
   |
probryx.org
   |
Microsoft 365 Business Premium
   |
+-- Microsoft Entra ID
+-- Exchange Online
+-- Microsoft Teams
+-- SharePoint Online
+-- OneDrive for Business
```

------------------------------------------------------------------------

# Risks

-   DNS propagation delays
-   Trial license limitations
-   Service configuration errors

# Deliverables

-   Enterprise Microsoft 365 Tenant
-   Deployment Guide
-   Validation Report
-   Troubleshooting Guide
-   GitHub Repository
-   Video Walkthrough

**Status:** In Progress

## Navigation

🏠 Project Home: [../README.md](../README.md)

➡️ Next: [Domain Configuration](02-Domain-Configuration.md)
