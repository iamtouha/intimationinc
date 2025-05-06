# Business Requirements Document (BRD)

**Project Name:** GoCloak  
**Prepared by:** Sajib Jahan  
**Date:** March 10, 2025

| Date       | Version | Prepared by | Checked by    |
| ---------- | ------- | ----------- | ------------- |
| 10/03/2025 | 1.0.0   | Sajib Jahan | Masihur Maruf |

---

## 1. Project Overview

GoCloak is a lightweight, high-performance alternative to Keycloak, written in Go, designed to offer authentication, authorization, and user management functionality for modern applications and services. The goal is to deliver a modular, scalable Identity and Access Management (IAM) solution with a web-based Admin Panel and REST APIs to manage realms and other identity-related entities.

The system will be self-hosted and easy to deploy, with a minimal setup and a focus on extensibility and performance. It targets developers and system administrators who need fine-grained control over authentication and authorization infrastructure without the overhead of Java-based platforms.

**Keycloak Overview:** [YouTube link](https://www.youtube.com/watch?v=z8gxQr6LGG4)

**What GoCloak Will Look Like**

- A Central IAM server with:

  - A **REST API** for creating and managing realms, users, clients, and roles
  - An **Admin Panel** to manage these visually (only internal access)
  - A **token service** for OAuth2/OIDC-based login and access control

- **Optional login and registration UIs** for end-users
- A modular architecture for future expansion: external IdPs, MFA, audit logs, etc.

---

## 2. Business Objectives

- Provide a robust identity management system that supports multiple realms (multi-tenancy).
- Offer a web-based Admin Panel to simplify management tasks.
- Deliver RESTful endpoints for external service integration and automation.
- Ensure high performance and ease of deployment with Go-based architecture.
- Enable extensibility to support custom flows, identity providers, and integrations.

---

## 3. Scope

### In Scope

- REST API service to manage:

  - Realms (create, update, delete, list)
  - Clients and client secrets
  - Users and groups
  - Roles and permissions
  - Authentication flows

- Admin Panel for:

  - Realm management
  - User & group management
  - Role assignments
  - Audit logs

- Secure storage of credentials (e.g., bcrypt/argon2)
- JWT-based token issuance and validation
- OAuth2 and OpenID Connect support
- Basic multi-factor authentication (MFA) setup
- Admin login and user login UIs
- Dockerized deployment for easy setup

### Out of Scope (Initial Release)

- Social login integrations
- External identity provider federation
- SAML support
- Complex customizable authentication flows

---

## 6. Stakeholders

| Role                 | Team                   |
| -------------------- | ---------------------- |
| Product Owner        | Intimationinc Team     |
| Backend Engineering  | IAM API Team           |
| Frontend Engineering | Admin Panel UI Team    |
| DevOps               | Infrastructure Team    |
| QA                   | Quality Assurance Team |

---

## 7. Milestones

| Milestone               | Deadline          |
| ----------------------- | ----------------- |
| BRD Approval            | April 15, 2025    |
| API Design Finalization | April 25, 2025    |
| MVP Development Start   | May 1, 2025       |
| MVP Complete            | July 10, 2025     |
| Internal Alpha Testing  | August 15, 2025   |
| Beta Release            | September 5, 2025 |
| Production Release      | October 1, 2025   |

---

## 8. Risks & Mitigations

| Risk                                | Mitigation                              |
| ----------------------------------- | --------------------------------------- |
| High initial development complexity | MVP will limit features to essentials   |
| Admin UI becoming overly complex    | Focus on UX and modular components      |
| Security vulnerabilities            | Penetration testing and audit reviews   |
| Scalability under load              | Load testing and stateless architecture |

---

## 9. Success Metrics

- Achieve 90% test coverage on API and Admin Panel.
- Maintain <200ms average API response time under load.
- Deploy successfully with 3+ realms, each with 1000+ users.
- Positive usability and performance feedback from early testers.
