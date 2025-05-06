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

---

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

---

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

---

## 4. Functional Requirements

### 4.1 Realms (Core IAM Functionality)

The system must support **multi-tenancy via Realms**, where each realm represents an isolated identity space (users, clients, roles, etc.).

**Features:**

- Create, update, delete, and retrieve realms
- Each realm maintains its own:

  - Clients (apps that authenticate)
  - Users and groups
  - Roles and permissions
  - Configurations (token settings, password policies, etc.)

### 4.2 REST API (External Use – Public IAM Interface)

Expose RESTful endpoints so that external applications and services can integrate with GoCloak as their authentication and authorization provider.

**Features:**

- **Realm Management:** APIs to create, update, delete, and retrieve realms.
- **User Management:** APIs to create, update, delete, and retrieve users per realm.
- **Client Management:** APIs to register, update, and delete client applications.
- **Role Management:** APIs to assign roles to users.

### 4.3 Admin Panel (Internal Only)

The admin panel is **internal-facing** and allows system admins to:

- View and manage all realms and their configurations
- View users and roles per realm
- Manage client applications
- View audit logs and metrics

> 🔒 No public REST API is needed for the admin panel. It can directly interact with backend services via internal APIs or server-side rendering.

---

## 5. Non-Functional Requirements

- **Performance:** Should be able to handle 100k concurrent user sessions per realm using cluster
- **Security:** Enforce HTTPS, CSRF protection in admin panel, input validation
- **Extensibility:** Pluggable provider model for external identity integrations
- **Portability:** Dockerized deployment
- **Scalability:** Horizontal scalability using stateless services

---

## 6. Milestones

| Milestone               | Dateline          |
| ----------------------- | ----------------- |
| BRD Approval            | April 15, 2025    |
| API Design Finalization | April 25, 2025    |
| MVP Development Start   | May 1, 2025       |
| MVP Complete            | July 10, 2025     |
| Internal Alpha Testing  | August 15, 2025   |
| Beta Release            | September 5, 2025 |
| Production Release      | October 1, 2025   |
