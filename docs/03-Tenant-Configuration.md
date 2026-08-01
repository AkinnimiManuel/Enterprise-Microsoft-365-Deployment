# Tenant Configuration

> **Project:** Enterprise Microsoft 365 Deployment  
> **Company:** Probryx Technologies Ltd.  
> **Phase:** Tenant Configuration  
> **Environment:** Microsoft 365 Business Premium

---

# 1. Executive Summary

This document describes the initial configuration of the Microsoft 365 tenant for Probryx Technologies Ltd. The objective of this phase is to prepare the tenant for enterprise deployment by configuring organizational settings, reviewing administrative portals, validating tenant health, and documenting the baseline configuration before user provisioning begins.

---

# 2. Business Requirement

Probryx Technologies requires a properly configured Microsoft 365 tenant that reflects the organization's identity and provides a stable foundation for identity management, collaboration, messaging, and security.

A correctly configured tenant ensures consistency, simplifies administration, and prepares the environment for future projects such as Microsoft Intune, Zero Trust Security, and Hybrid Identity.

---

# 3. Objectives

- Configure organizational information
- Verify Microsoft 365 subscription
- Configure organization profile
- Review organization settings
- Configure release preferences
- Review service health
- Review Message Center
- Verify available admin centers
- Review Security Defaults
- Document the tenant baseline

---

# 4. Prerequisites

- Microsoft 365 Business Premium
- Global Administrator account
- Custom domain successfully configured
- Internet connectivity

---

# 5. Implementation Overview

| Task | Status |
|------|:------:|
| Microsoft 365 Admin Center Reviewed | ✅ |
| Organization Profile Configured | ✅ |
| Company Branding Reviewed | ⌛ |
| Organization Information Verified | ✅ |
| Organization Settings Reviewed | ✅ |
| Release Preferences Configured | ✅ |
| Service Health Reviewed | ✅ |
| Message Center Reviewed | ✅ |
| Admin Centers Reviewed | ✅ |
| Security Defaults Reviewed | ✅ |

---

# 6. Configuration Steps

---

## Step 1 – Review Microsoft 365 Admin Center

Navigate to:

Microsoft 365 Admin Center

Review:

- Dashboard
- Navigation menu
- Tenant information
- Subscription

### Screenshot

![](../Screenshots/tenant/01-admin-center-home.png)

### Subscription
![](../Screenshots/tenant/01-admin-center-home.png)


---

## Step 2 – Configure Organization Profile

Navigate to:

Settings

↓

Org Settings

↓

Organization Profile

### Screenshot


![](../Screenshots/tenant/02-organization-profile.png)

---

## Step 3 – Company Branding

Navigate to

Microsoft Entra Admin Center

↓

Identity

↓

Company Branding

Review or configure

- Company Name
- Banner Logo
- Square Logo
- Background Image
- Sign-in Text

If branding assets are unavailable, document this for future implementation.

### Screenshot

```
../screenshots/tenant/03-company-branding.png
```

![](../Screenshots/tenant/03-company-branding.png)

---

## Step 4 – Organisation Information

Verify:

- Tenant Name
- Tenant ID
- Initial Domain
- Custom Domain
- Subscription

### Screenshot

### Organisation Information
![](../Screenshots/tenant/04-org-information.png)

### Custom Domains
![](../Screenshots/tenant/04-org-information-2.png)

### Billing Information 
![](../Screenshots/tenant/04-org-information-3.png)

---

## Step 5 – Organization Settings

Review available organizational settings.

Examples include:

- Calendar
- Microsoft Loop
- Viva
- User-owned Apps
- Self-service Purchase

No changes are required unless necessary.

### Screenshot

![](../Screenshots/tenant/05-org-settings.png)

### Calendar Settings
![](../Screenshots/tenant/05-calendar-org-settings.png)

### User owned app settings
![](../Screenshots/tenant/05-user-owned-app-org-settings.png)

### User purchase settings
![](../Screenshots/tenant/05-self-service-purchase-org-settings.png)


The organization settings were reviewed to understand the tenant's default configuration and identify settings that may require modification in future deployment phases. No changes were made during this phase because the objective was to establish a documented baseline.
---

## Step 6 – Configure Release Preferences

Navigate to

Settings

↓

Org Settings

↓

Release Preferences

Recommended:

Standard Release

Reason:

Provides production stability while avoiding preview features.

### Screenshot

```
../screenshots/tenant/06-release-preferences.png
```

![](../Screenshots/tenant/06-release-preferences.png)

---

## Step 7 – Review Service Health

Navigate to

Health

↓

Service Health

Review:

- Active Incidents
- Advisories
- Current Service Status

### Screenshot

![](../Screenshots/tenant/07-service-health.png)

---

## Step 8 – Review Message Center

Navigate to

Health

↓

Message Center

Review:

- Upcoming Changes
- Feature Releases
- Planned Maintenance

### Screenshot

![](../Screenshots/tenant/08-message-center.png)

---

## Step 9 – Review Security Defaults

Navigate to

Microsoft Entra Admin Center

↓

Identity

↓

Overview

↓

Properties

↓

Manage Security Defaults

Record the current configuration.

This project only documents the current state.

Advanced security configuration will be completed during Project 3.

### Screenshot

![](../Screenshots/tenant/9-security-defaults.png)


---

# 7. Technical Explanation

## Why configure the Organization Profile?

The organization profile identifies the Microsoft 365 tenant and provides business information used across Microsoft services.

---

## Why review Service Health?

Service Health enables administrators to monitor outages, advisories, and service degradation that may affect users.

---

## Why review Message Center?

The Message Center communicates upcoming Microsoft changes, feature releases, maintenance events, and retirement notices.

---

## Why configure Release Preferences?

Release Preferences determine how quickly users receive new Microsoft 365 features.

Standard Release is generally recommended for production environments.

---

## Why review Security Defaults?

Security Defaults provide a baseline level of protection including Multi-Factor Authentication and legacy authentication blocking.

---

# 8. Validation

| Validation Item | Status |
|-----------------|:------:|
| Organization Profile Configured | ✅ |
| Organization Information Verified | ✅ |
| Company Branding Reviewed | ✅ |
| Organization Settings Reviewed | ✅ |
| Release Preferences Configured | ✅ |
| Service Health Reviewed | ✅ |
| Message Center Reviewed | ✅ |
| Admin Centers Accessible | ✅ |
| Security Defaults Documented | ✅ |

---

# 9. Troubleshooting

| Issue | Cause | Resolution |
|------|------|-----------|
| Company branding unavailable | Branding assets not prepared | Configure after branding is created |

---

# 10. Lessons Learned

- A Microsoft 365 tenant should be configured before creating users.
- Organization settings establish consistency across Microsoft services.
- Service Health and Message Center should be monitored regularly.
- Standard Release provides a stable production experience.
- Documenting the baseline simplifies future troubleshooting and audits.

---

# 11. References

- Microsoft Learn – Microsoft 365 Admin Center
- Microsoft Learn – Microsoft Entra ID
- Microsoft Learn – Organization Settings
- Microsoft Learn – Service Health
- Microsoft Learn – Message Center

---

# Change Log

| Version | Date | Author | Description |
|----------|------|--------|-------------|
| 1.0 | 2026-07-30 | Emmanuel Stefan Akinnimi | Initial Tenant Configuration |

---