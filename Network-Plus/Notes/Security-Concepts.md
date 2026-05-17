# Core IT Security Concepts

---

## 1. Data Categorization (States of Data)

Security policies and defense mechanisms vary depending on whether data is moving across a network or sitting on a storage medium.

### A. Data in Transit (Data in Motion)
* **Definition:** Any information moving across a wired or wireless network link.
* **Infrastructure Role:** Core infrastructure components (switches, routers) focus on forwarding this traffic efficiently rather than protecting it. 
* **Security Controls:**
    - **Monitoring:** Firewalls and Intrusion Prevention Systems (IPS) inspect stream payloads to block malicious behavior.
    - **Encryption:** Protocols like **TLS** (Transport Layer Security) and **IPsec** (Internet Protocol Security) prevent eavesdropping on the wire.

### B. Data at Rest
* **Definition:** Data stored statically on a physical medium, such as a hard drive, solid-state drive (SSD), or database storage array.
* **Security Controls:**
    - **Encryption:** Full Disk Encryption (FDE), folder-level encryption, or specific database column/row encryption.
    - **Access Control:** Operating system permissions and Access Control Lists (ACLs) that restrict which users can open a file.

---

## 2. Trust Architecture & Public Key Infrastructure (PKI)

Managing trust, encryption keys, and digital certificates at scale requires a structured management system.

* **Public Key Infrastructure (PKI):** The overarching framework of policies, hardware, software, and procedures used to create, manage, distribute, store, and revoke digital certificates and public keys.
* **Certificate Authority (CA):** A centralized trusted entity that digitally signs certificates for users, servers, or devices. Anything signed by a trusted CA is inherently trusted by the rest of the organization.
    - *Internal CA:* Built in-house (e.g., via Windows Domain Services) to sign certificates for internal corporate assets.
    - *Third-Party CA:* An independent external authority used for public internet trust (e.g., securing external websites).
* **Web of Trust:** A decentralized alternative to a hierarchical CA. Trust is distributed across individual peers who sign each other's keys. If User A trusts User B, and User B trusts User C, then User A can transitively trust User C.

---

## 3. Identity and Access Management (IAM)

IAM governs the lifecycle of user identities, authentication, authorization, and auditing to protect sensitive digital resources.

### A. Core Principles
* **Least Privilege:** The foundational security practice of giving users only the absolute minimum permissions necessary to perform their job functions, and nothing more. This mitigates the blast radius if an account is compromised.
* **Auditing:** Tracking and monitoring all access history logs to review exactly who accessed what data and when.

### B. Logical Access Restrictions
* **Role-Based Access Control (RBAC):** Permissions are tied to specific corporate roles (e.g., Shipping Clerk, Manager, VP) rather than individual accounts. In enterprise environments like Windows Active Directory, this is implemented using **Groups**. Users are dropped into a group, and the group inherits the permissions.
* **Geofencing:** Setting a virtual boundary around a real-world geographic area using location indicators (GPS, IP addresses, local Wi-Fi access point names). Access to highly sensitive applications or data is blocked if the user physically moves outside the geofenced zone.

---

## 4. Physical Security Controls

Logical security is useless without physical boundaries to prevent unauthorized hands-on access to infrastructure hardware.

* **Surveillance (CCTV / Closed Circuit Television):** Networked camera systems deployed across campuses to record video, track movement, and assist in post-incident investigations. Modern iterations integrate advanced features like motion detection, license plate reading, and facial recognition.
* **Door Locks & Electronic Access Control:**
    - *Conventional:* Physical mechanical keys and deadbolts.
    - *Electronic:* Keypads requiring a PIN or card readers detecting electronic tokens (**RFID Badges**).
    - *Biometric:* High-security entry scanners parsing unique physical human characteristics (fingerprints, handprints, or retina scans).
* **Multi-Factor Physical Authentication:** Combining multiple distinct categories of credentials at a single checkpoint—such as swiping an RFID badge (**something you have**) followed by a thumbprint scan (**something you are**).
