# Authentication Frameworks and Identity Protocols

This document details the AAA security model, single sign-on mechanics, directory access structures, federated web protocols, and multi-factor authentication validation.

---

## 1. The AAA Security Framework

The Triple-A framework provides the structured foundation for managing system access, permission assignment, and security auditing.

* **Identification (Pre-AAA):** The public claim of an identity. This is public or easily guessable information, such as a cleartext username or email address.
* **Authentication (The First A):** The validation phase. The user must provide private verification data (such as a password or cryptographic token) to prove they are the entity they claim to be.
* **Authorization (The Second A):** The permission assignment phase. Once identity is verified, the system assigns specific access rights to directories, files, or network segments based on defined access control policies.
* **Accounting (The Third A):** The tracking and auditing phase. Consistently records session connection timelines, logouts, resource usage, and authentication failures for compliance and investigation.

---

## 2. Directory Services and Network Access Protocols

Enterprise networks centralize user validation profiles using dedicated communication protocols to scale access control.

### A. RADIUS (Remote Authentication Dial-In User Service)
* **Design Engine:** A central client/server protocol used to authenticate and authorize remote connections.
* **Deployments:** Widely implemented on modern networks to secure VPN concentrations, firewall admin portals, and wireless authentication via 802.1X link points.

### B. TACACS+ (Terminal Access Control Access-Control System)
* **Design Engine:** Originally built to control dial-up modems on ARPANET. It was heavily enhanced by Cisco and opened as a public standard in 1993.
* **Modern Deployment:** Primarily utilized for device administration access control on switches and routers, decoupling authentication from command authorization granularly.

### C. LDAP (Lightweight Directory Access Protocol)
* **Design Engine:** Based on the X.500 structural hierarchy standard, LDAP reads, writes, and queries a centralized network directory service database tree (e.g., Windows Active Directory, Apple OpenDirectory).
* **Structural Architecture:** Objects are organized contextually using attributes:
    - **Containers:** Structural nodes used to group resources (e.g., Organizing by Country, Company, or Department/Organizational Unit like `OU=Marketing`).
    - **Leaf Objects:** Individual end assets or users at the tip of the database hierarchy (e.g., a specific server name `CN=WIDGETWEB`).

---

## 3. Web Federation and Single Sign-On (SSO)

To prevent password fatigue and reduce security vulnerabilities, organizations abstract the authentication layer across independent web tools.

* **Single Sign-On (SSO):** A mechanism allowing a user to authenticate once and automatically gain valid access permissions across multiple applications. The session validity windows are time-bound, typically expiring after 24 hours.
* **SAML (Security Assertion Markup Language):** An open, XML-based standard designed to exchange authentication and authorization data between distinct domains.
    - **The Architectural Flow:**
        1. **The Client (Browser):** Requests a protected resource from a destination.
        2. **The Resource Server (Service Provider):** Lacks local session history for the client, so it redirects the client browser to an identity provider.
        3. **The Authorization Server (Identity Provider):** Authenticates the client (checking credentials against an LDAP or RADIUS backend) and hands an encrypted cryptographic token back to the browser.
        4. **Validation:** The client browser presents this validation token back to the target resource server, which verifies the signature and grants access.

---

## 4. Multi-Factor Authentication (MFA) and TOTP Mechanics

Multi-Factor Authentication hardens identity validation by demanding that a user provide proof from multiple independent classification buckets.

### A. The Core Factors of Authentication
1. **Something You Know:** Static cognitive text data (e.g., passwords, PIN codes, security answers).
2. **Something You Have:** A physical or digital token in your possession (e.g., smartcards, registered smartphones).
3. **Something You Are:** Biological biometrics (e.g., fingerprints, retina scans, facial signatures).
4. **Somewhere You Are:** Geographic telemetry verification (e.g., GPS coordinates, local wireless access point signatures).

### B. TOTP (Time-based One-Time Password) Algorithm
A secure implementation of the "something you have" classification factor, commonly used in authenticator applications (Google, Microsoft, Duo).

```text
┌────────────────────────┐                   ┌────────────────────────┐
│   Client Mobile App    │                   │ Authentication Server  │
├────────────────────────┤                   ├────────────────────────┤
│ Seed: [Shared Secret]  │                   │ Seed: [Shared Secret]  │
│ Clock: 19:25:30        │                   │ Clock: 19:25:30        │
└───────────┬────────────┘                   └───────────┬────────────┘
            │                                            │
            ▼                                            ▼
   Calculated Code:                             Calculated Code:
       [582914]  ═══════ Presented Code ══════►     [582914] (Match!)

```

* **The Generation Engine:** The token code appears to be randomized, but it is entirely deterministic based on a mathematical formula requiring two synchronized variables:
1. A unique **Shared Secret Key (Seed)** established ahead of time between the server and client app via a QR code.
2. The precise **Current Time of Day**, changing the tracking window payload value automatically every 30 seconds.


* **Dependency:** For the generated pseudo-random hash to match on both sides,
both the client app and the backend authentication server must synchronize their system clocks using a protocol like **NTP (Network Time Protocol)**.
This allows users to securely generate valid login keys completely offline.
