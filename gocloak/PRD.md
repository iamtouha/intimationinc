# Project Requirements Document (PRD)

**Project Name:** GoCloak  
**Prepared by:** Sajib Jahan  
**Date:** March 14, 2025

| Date       | Version | Prepared by | Checked by    |
| ---------- | ------- | ----------- | ------------- |
| 14/03/2025 | 1.0.0   | Sajib Jahan | Masihur Maruf |

---

## 1. Project Overview

GoCloak is a lightweight, high-performance alternative to Keycloak, written in Go. It offers authentication, authorization, and user management functionality for modern applications and services. The goal is to deliver a modular, scalable Identity and Access Management (IAM) solution with a web-based Admin Panel and REST APIs.

It is designed to be self-hosted and easy to deploy, with minimal setup and a focus on extensibility and performance. The primary audience includes developers and system administrators needing fine-grained control without the overhead of Java-based platforms.

**Keycloak overview:** [YouTube Video](https://www.youtube.com/watch?v=z8gxQr6LGG4)

### What GoCloak Will Look Like

A central IAM server with:

- A REST API for creating and managing realms, users, clients, and roles
- An Admin Panel to manage these visually (internal access only)
- A token service for OAuth2/OIDC-based login and access control
  - Optional login and registration UIs for end-users
  - A modular architecture for future expansion: external IdPs, MFA, audit logs, etc.

## 2. Product Features

### 2.1 Admin Panel (Internal Use)

- **Realm Management:** Create, manage, and delete realms.
- **User & Role Management:** Add, update, delete users; assign roles and permissions.
- **Client Management:** Register and manage client applications.
- **Audit Logs:** Track changes and actions within the system.
- **Security:** Role-based access control with a dedicated admin login system.

### 2.2 REST API (External Use)

- **Authentication:** OAuth2 and OIDC token endpoints.
- **User Management:** CRUD operations on users within realms.
- **Realm Management:** Create, update, and list realms via API.
- **Client Management:** Register and manage applications.
- **Roles & Permissions:** Manage roles and user-role assignments.

### 2.3 Authentication Flows

- **Password Grant:** Login via username/password.
- **Authorization Code Flow:** For secure web and mobile app authorization.
- **Implicit Flow:** For client-side applications that need direct tokens.

## 3. User Stories

### 3.1 As an administrator

- I want to manage realms to separate identity data.
- I want to manage users and assign roles for access control.
- I want to use audit logs for monitoring and security.

### 3.2 As a developer

- I want to integrate OAuth2/OIDC with GoCloak for app security.
- I want to manage users, roles, and clients via API.

### 3.3 As a system

- I want to support 100k concurrent users per realm.
- I want API responses under 200ms for scalability and performance.

## 4. Functional Requirements

### 4.1 Realms (Core IAM)

- Multi-tenancy via isolated realms.
- Per realm:

  - Clients.
  - Users, groups.
  - Roles, permissions.
  - Configurations (tokens, password policies).

### 4.2 REST API (Public Interface)

- Realm management (CRUD).
- User management (CRUD).
- Client application management (CRUD).
- Role assignment APIs.

### 4.3 Admin Panel (Internal Use)

- Manage realms, users, roles, clients.
- Access audit logs and metrics.
- No public REST API; use internal APIs or server-side rendering.

---

## 5. Non-Functional Requirements

- **Performance:** Support 100k concurrent sessions per realm (clustered).
- **Security:** HTTPS, CSRF protection, input validation.
- **Extensibility:** Pluggable external identity providers.
- **Portability:** Dockerized deployments.
- **Scalability:** Stateless services, horizontal scaling.

## 5. Milestones

| Milestone               | Dateline          |
| ----------------------- | ----------------- |
| BRD Approval            | April 15, 2025    |
| API Design Finalization | April 25, 2025    |
| MVP Development Start   | May 1, 2025       |
| MVP Complete            | July 10, 2025     |
| Internal Alpha Testing  | August 15, 2025   |
| Beta Release            | September 5, 2025 |
| Production Release      | October 1, 2025   |
