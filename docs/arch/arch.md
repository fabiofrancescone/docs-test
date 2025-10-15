This section provides a technical overview of Carbonio’s architecture, outlining the core components, their responsibilities, and how they interact. Understanding the architecture is essential for designing, deploying, and scaling your Carbonio environment effectively.

---

## System Overview

Carbonio is built on a **modular, service-oriented architecture**. Each service can run on a separate server or be consolidated depending on your deployment size and requirements.

---

## Core Components

!!! info "📨 Mailstore (Mailbox Server)"
    - Stores user mailbox data: emails, folders, filters, preferences  
    - Handles delivery, indexing, search  
    - Integrates with LDAP for authentication

!!! info "📡 MTA (Mail Transfer Agent)"
    - Based on Postfix  
    - Manages inbound/outbound email  
    - Integrates anti-spam and anti-virus filtering

!!! info "🌐 Proxy Server"
    - Acts as a frontend for IMAP/SMTP/HTTP(S)  
    - Load-balances internal traffic  
    - Handles TLS termination and secure access

!!! info "🧑‍💼 Admin UI"
    - Web interface for managing domains, accounts, settings  
    - Supports role-based access control  
    - Includes dashboards and wizards

!!! info "🔧 CLI & API Layer"
    - Command-line tools for automated or scripted management  
    - REST APIs for integration with external systems and dashboards

!!! info "📁 File & Collaboration Services"
    - Document sharing and collaborative editing  
    - Supports file versioning and permission controls

!!! info "📅 Calendar & Contacts"
    - Shared calendars, address books, and scheduling tools  
    - Supports CalDAV and CardDAV protocols

---

## Supporting Services

!!! info "🔐 LDAP Directory"
    - Provides centralized user authentication and directory services  
    - Supports internal and external directories (e.g., Active Directory)

!!! info "🦠 Antivirus & Antispam"
    - ClamAV and SpamAssassin integration  
    - Customizable filtering policies

!!! info "🗂️ Zextras Services"
    - Extends Carbonio with:
        - Backup & Restore  
        - Mobile Sync (ActiveSync)  
        - Real-time Chat & Video  
        - Multi-tenancy

---

## Deployment Topologies

!!! info "Single-node"
    All components on one server. Suitable for testing and small installations.

!!! info "Multi-node"
    Services distributed across multiple servers for improved performance and reliability.

!!! info "High-availability"
    Redundant services with load balancing and failover to ensure service continuity.

!!! info "Cloud-native"
    Deployments using containers or orchestration platforms (e.g., Docker, Kubernetes).

---

## Summary

Carbonio’s architecture is designed for flexibility, security, and scalability. Whether deployed on a single server or a multi-node cluster, its modular design allows you to adapt the system to your organization's size and requirements.

→ [Continue to Installation & Setup](../inst/inst.md)

