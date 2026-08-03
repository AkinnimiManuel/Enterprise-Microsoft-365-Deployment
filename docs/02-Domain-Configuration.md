# Domain Configuration

## Executive Summary

This document describes the implementation of the custom domain **probryx.org** within Microsoft 365 Business Premium.

---

## Business Requirement

Probryx Technologies requires a professional custom domain for Microsoft 365 identities, email, Teams, SharePoint, and OneDrive.

---

## Objectives

- Verify domain ownership
- Configure DNS
- Enable Microsoft 365 services
- Set default domain
- Validate deployment

---

## Prerequisites

- Microsoft 365 Business Premium Tenant
- Global Administrator
- Domain ownership
- DNS access

---

## Implementation Overview

|Task|Status|
|---|:---:|
|Review default domain|✅|
|Add domain|✅|
|Verify ownership|✅|
|Configure DNS|✅|
|Validate|✅|

---

## Configuration Steps

### Step 1 - Review Existing Domain

Screenshot:

![](../screenshots/domain/01-default-domain.png)

### Step 2 - Add Custom Domain

![](../screenshots/domain/02-add-domain-1.png)
![](../screenshots/domain/02-add-domain-2.png)

### Step 3 - TXT Verification

![](../screenshots/domain/03-domain-verification-record.png)
![](../screenshots/domain/03-domain-verification-record-2.png)

### Step 4 - Domain Verified

![](../screenshots/domain/04-domain-verified.png)

### Step 5 - Configure DNS Records

|Record|Purpose|Screenshot|
|---|---|---|
|MX|Mail Routing|05-mx-record.png|
|TXT (SPF)|Email Authentication|06-spf-record.png|
|Autodiscover|Outlook|07-autodiscover.png|
|Enterprise Enrollment|Device Enrollment|08-enterprise-enrollment.png|
|Enterprise Registration|Device Registration|09-enterprise-registration.png|

![](../screenshots/domain/05-mx-record.png)

![](../screenshots/domain/06-spf-record.png)

![](../screenshots/domain/07-autodiscover.png)

![](../screenshots/domain/08-enterprise-enrollment.png)

![](../screenshots/domain/09-enterprise-registration.png)

![](../screenshots/domain/09-DKIM-Setup.png)

### All Records added to the cloudflare domain
![](../screenshots/domain/09-Records-added.png)

### Domain setup complete
![](../screenshots/domain/09-Domain-setup-complete.png)


### Step 6 - Domain Healthy

![](../screenshots/domain/10-domain-healthy.png)

### Step 7 - Default Domain

![](../screenshots/domain/11-default-domain.png)

### Step 8 - Verify User UPN

![](../screenshots/domain/12-user-upn-domain.png)

### Step 9 - Exchange Accepted Domain

![](../screenshots/domain/13-exchange-accepted-domain.png)

---

## Technical Explanation

Why These DNS Records Are Required

When adding a custom domain to Microsoft 365, DNS records verify domain ownership and direct Microsoft 365 services to work correctly.

TXT (Verification): Confirms you own the domain before it can be added to Microsoft 365.
MX: Routes incoming email to Exchange Online.
SPF (TXT): Authorizes Microsoft 365 to send email on behalf of your domain, helping prevent spoofing.
Autodiscover (CNAME): Automatically configures Outlook clients.
EnterpriseEnrollment (CNAME): Enables automatic Microsoft Intune device enrollment.
EnterpriseRegistration (CNAME): Supports Microsoft Entra ID device registration and Azure AD Join.
DKIM (CNAME): Digitally signs outgoing emails to improve security and deliverability.
DMARC (TXT): Specifies how to handle emails that fail authentication, protecting against phishing.

---

## Validation

- Domain verified ✅
- DNS configured ✅
- Domain healthy ✅
- Default domain changed ✅
- UPN updated ✅
- Exchange recognizes domain ✅

---

## Troubleshooting

|Issue|Cause|Resolution|
|---|---|---|
|Domain verification delay|DNS propagation|Wait and retry before it propagated|
---

## Lessons Learned

- All Reocords are important for effective Microsoft tennat.

---

## References

- Microsoft Learn - Microsoft 365 Custom Domains
- Microsoft Learn - Exchange Online DNS Records

## Navigation

⬅️ Previous: [Project Planning](01-Project-Planning.md)

🏠 Project Home: [../README.md](../README.md)

➡️ Next: [Tenant Configuration](03-Tenant-Configuration.md)