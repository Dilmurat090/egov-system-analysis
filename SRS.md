# System Requirements Specification (SRS)
## E-Government Application Submission Portal

**Version:** 1.0  
**Author:** Sultan Dilmurat  
**Date:** June 2025  
**Status:** Draft

---

## 1. Introduction

### 1.1 Purpose
This document defines functional and non-functional requirements for an improved e-government portal focused on the application submission and tracking flow for citizens of Kazakhstan.

### 1.2 Scope
The system enables citizens to submit applications for government services (permits, certificates, social benefits), track their status, receive notifications, and retrieve issued documents — through a single unified web portal.

### 1.3 Definitions
| Term | Definition |
|---|---|
| Citizen | An authenticated end user interacting with the portal |
| Operator | A government employee processing submitted applications |
| SSO | Single Sign-On — unified authentication via IIN + EDS key |
| EDS | Electronic Digital Signature (Kazakhstan national standard) |
| IIN | Individual Identification Number |

---

## 2. Actors

| Actor | Description |
|---|---|
| Citizen | Submits applications, tracks status, retrieves documents |
| Operator | Reviews, approves or rejects applications |
| Supervisor | Monitors operator workload and SLA compliance |
| Notification Service | Sends SMS/email/push notifications |
| Identity Provider | Validates IIN + EDS during authentication |
| Document Storage | Stores and retrieves issued certificates and permits |

---

## 3. Functional Requirements

### 3.1 Authentication & Identity

| ID | Requirement |
|---|---|
| FR-01 | The system SHALL authenticate citizens using IIN + EDS key via a national Identity Provider |
| FR-02 | The system SHALL maintain an SSO session valid for 60 minutes across all service categories |
| FR-03 | The system SHALL display the citizen's full name and IIN after successful authentication |
| FR-04 | The system SHALL allow re-authentication without clearing in-progress application data |

### 3.2 Application Submission

| ID | Requirement |
|---|---|
| FR-05 | The system SHALL provide a searchable catalogue of all available government services |
| FR-06 | The system SHALL pre-fill application fields with citizen data retrieved from the Identity Provider |
| FR-07 | The system SHALL validate all required fields before allowing form submission |
| FR-08 | The system SHALL generate a unique Application ID upon successful submission |
| FR-09 | The system SHALL allow citizens to attach supporting documents (PDF, JPG; max 10 MB per file) |
| FR-10 | The system SHALL display an estimated processing time after submission |

### 3.3 Status Tracking

| ID | Requirement |
|---|---|
| FR-11 | The system SHALL display real-time application status (Submitted / In Review / Approved / Rejected) |
| FR-12 | The system SHALL provide a unified status dashboard for all active and past applications |
| FR-13 | The system SHALL display the name and contact of the assigned operator upon request |
| FR-14 | The system SHALL show a timestamped history of all status changes for each application |

### 3.4 Notifications

| ID | Requirement |
|---|---|
| FR-15 | The system SHALL send a confirmation notification (SMS + email) within 2 minutes of submission |
| FR-16 | The system SHALL notify the citizen at every status change via their preferred channel |
| FR-17 | The system SHALL allow citizens to configure notification preferences (SMS / email / push) |

### 3.5 Document Retrieval

| ID | Requirement |
|---|---|
| FR-18 | The system SHALL make issued documents available for download within 1 hour of approval |
| FR-19 | The system SHALL store issued documents for a minimum of 5 years |
| FR-20 | The system SHALL allow citizens to share a read-only document link with third parties |

---

## 4. Non-Functional Requirements

| ID | Category | Requirement |
|---|---|---|
| NFR-01 | Performance | The portal SHALL load any page within 3 seconds under a load of 1000 concurrent users |
| NFR-02 | Availability | The system SHALL maintain 99.5% uptime, with planned maintenance windows only between 01:00–04:00 |
| NFR-03 | Security | All data in transit SHALL be encrypted using TLS 1.2 or higher; citizen data at rest SHALL be encrypted using AES-256 |
| NFR-04 | Accessibility | The portal SHALL conform to WCAG 2.1 Level AA accessibility standards |
| NFR-05 | Scalability | The system architecture SHALL support horizontal scaling to handle a 5× increase in load without architectural changes |

---

## 5. Out of Scope

- Payment processing for government fees (separate subsystem)
- Internal operator workflow management beyond status updates
- Mobile native applications (web only)

---

## 6. AS-IS vs TO-BE Summary

| Pain Point (AS-IS) | Improvement (TO-BE) |
|---|---|
| Identity verification repeated at each service | Single SSO session across all services |
| No unified status dashboard | Centralised application tracking page |
| Notifications not sent after submission | Automated notification triggered on every status event |
| Documents stored per-service, not accessible centrally | Unified document storage with citizen access |
| Integration between services is point-to-point | Standardised REST API contracts between subsystems |
