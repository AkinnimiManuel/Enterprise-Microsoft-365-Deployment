# OneDrive for Business

---

# Business Requirement

OneDrive for Business provides secure personal cloud storage for employees, enabling users to store, synchronize, access, and share files from anywhere. This phase validates OneDrive deployment within Probryx Technologies Ltd. and ensures users can securely manage their work files while maintaining organizational governance and compliance.

---

# Implementation Overview

This phase validates OneDrive for Business provisioning, reviews OneDrive administration settings, verifies personal storage, tests file synchronization, and confirms sharing functionality.

---

# Objectives

- Verify OneDrive deployment
- Review OneDrive Admin Settings
- Validate user OneDrive provisioning
- Upload files
- Test synchronization
- Test file sharing
- Validate collaboration
- Review storage allocation

---

# Prerequisites

Before beginning this phase, ensure:

- Microsoft 365 tenant configured
- Identity Management completed
- Licensing completed
- Exchange Online configured
- Microsoft Teams configured
- SharePoint Online configured
- Microsoft 365 Business Premium licenses assigned

---

# OneDrive Architecture

| Component | Purpose |
|------------|---------|
| OneDrive for Business | Personal Cloud Storage |
| SharePoint Online | Storage Platform |
| OneDrive Sync Client | Device Synchronization |
| Microsoft 365 Apps | Document Collaboration |
| Web Access | Browser-based File Access |

---

# OneDrive User Storage

| User | OneDrive Status |
|--------|----------------|
| Kolawole Ashipa | Provisioned |
| Stefan Akinnimi | Provisioned |
| Damilola Ogunwole | Provisioned |
| Nurudeen Ifagbemi | Provisioned |
| Jane Smith | Provisioned |
| Bob Philip | Provisioned |
| David Johnson | Provisioned |
| Sarah Wilson | Provisioned |
| Michael Brown | Provisioned |

---

# Configuration Steps

---

## Step 1 – Verify OneDrive Administration

Navigate to

Microsoft 365 Admin Center

↓

Admin Centers

↓

SharePoint

↓

More Features

↓

User Profiles

↓

Open OneDrive Administration

Verify OneDrive is available.

### Technical Explanation

OneDrive administration allows administrators to manage storage, sharing, synchronization, and retention settings.

### Screenshot

![](../screenshots/onedrive/01-onedrive-admin.png)

---

## Step 2 – Verify OneDrive Provisioning

Sign in as:

Jane Smith

Open:

Microsoft 365 Portal

↓

OneDrive

Verify personal storage has been provisioned.

### Technical Explanation

A OneDrive site is automatically created for licensed users when they first access OneDrive.

### Screenshot

![](../screenshots/onedrive/02-onedrive-provisioned.png)

---

## Step 3 – Upload Files

Upload sample documents to OneDrive.

Examples:

- HR Policy.docx
- Employee Handbook.pdf
- Recruitment Tracker.xlsx

### Technical Explanation

OneDrive provides secure cloud storage for business documents.

### Screenshot

![](../screenshots/onedrive/03-file-upload.png)

---

## Step 4 – Create Folders

Create folders to organize content.

Examples:

- HR Documents
- Policies
- Recruitment
- Templates

### Technical Explanation

Folders help users organize and manage business content effectively.

### Screenshot

![](../screenshots/onedrive/04-folders-created.png)

---

## Step 5 – Test File Sharing

Share a document with:

Bob Philip

Verify:

- Sharing invitation
- Access permissions
- File accessibility

### Technical Explanation

OneDrive supports secure file sharing while maintaining access controls.

### Screenshot

![](../screenshots/onedrive/05-file-sharing.png)

---

## Step 6 – Test Collaboration

Open a shared document.

Verify:

- Edit access
- Save changes
- Real-time collaboration

### Technical Explanation

OneDrive integrates with Microsoft 365 Apps to provide collaborative editing capabilities.

### Screenshot

![](../screenshots/onedrive/06-collaboration.png)

---

## Step 7 – Review Storage Allocation

Navigate to:

Microsoft 365 Admin Center

↓

Active Users

↓

Select User

↓

OneDrive

Review available storage.

### Technical Explanation

Storage allocation determines how much cloud storage is available to users.

### Screenshot

![](../screenshots/onedrive/07-storage-allocation.png)

---

## Step 8 – Review Sharing Policies

Navigate to:

SharePoint Admin Center

↓

Policies

↓

Sharing

Review:

- External Sharing
- Internal Sharing
- Link Settings

No changes are required during this phase.

### Technical Explanation

Sharing policies govern how users can share files internally and externally.

### Screenshot

![](../screenshots/onedrive/08-sharing-policies.png)

---

# Validation

| Validation | Expected Result | Status |
|------------|-----------------|:------:|
| OneDrive Provisioned | Success | ✅ |
| File Upload Successful | Success | ✅ |
| Folder Creation Successful | Success | ✅ |
| File Sharing Successful | Success | ✅ |
| Collaboration Successful | Success | ✅ |
| Storage Allocation Visible | Success | ✅ |

---

## Validation 1 – OneDrive Provisioning

Verify that the OneDrive site has been successfully provisioned.

### Screenshot

![](../screenshots/onedrive/validation/onedrive-provisioned.png)

---

## Validation 2 – File Upload

Verify files have been successfully uploaded.

### Screenshot

![](../screenshots/onedrive/validation/file-upload.png)

---

## Validation 3 – File Sharing

Verify the shared document can be accessed by the recipient.

### Screenshot

![](../screenshots/onedrive/validation/file-sharing.png)

---

## Validation 4 – Collaboration

Verify collaborative editing functionality.

### Screenshot

![](../screenshots/onedrive/validation/collaboration.png)

---

# Troubleshooting

| Issue | Resolution |
|--------|------------|
| OneDrive not provisioned | Access OneDrive and allow provisioning to complete |
| Upload failure | Verify network connectivity and storage availability |
| Sharing unavailable | Review sharing policies and permissions |
| Sync issues | Verify OneDrive Sync Client is signed in and operational |

---

# Lessons Learned

- OneDrive provides secure personal storage for employees.
- OneDrive and SharePoint Online work together to deliver cloud file services.
- File sharing and collaboration improve productivity.
- Storage and sharing policies help maintain organizational governance.
- OneDrive supports secure access from multiple devices and locations.

---

# Conclusion

OneDrive for Business was successfully validated for Probryx Technologies Ltd. Personal storage, file uploads, sharing, collaboration, and storage allocation were tested and confirmed. The implementation provides users with secure cloud storage while supporting collaboration and productivity across the Microsoft 365 environment.

---

# References

- Microsoft Learn – OneDrive for Business
- Microsoft 365 Admin Center
- SharePoint Admin Center

---

## Navigation

⬅️ Previous: [SharePoint Online](08-SharePoint.md)

🏠 Project Home: [../README.md](../README.md)

➡️ Next: Security Baseline