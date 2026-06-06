# The AAA Framework

The AAA Framework is composed of three sequential phases: **Authentication, Authorization, and Accounting**.

---

## 1. Core Phases of the AAA Framework

```
+----------------+       +------------------+       +-----------------+
| Identification | ----> |  Authentication  | ----> |  Authorization  |
| "I claim to be |       | "Prove you hold  |       | "What explicit  |
|  user 'Bob'"   |       |  the secrets"    |       |  privileges?"   |
+----------------+       +------------------+       +-----------------+
                                                             |
                                                             v
                                                    +-----------------+
                                                    |   Accounting    |
                                                    | "Continuous log |
                                                    |  of footprints" |
                                                    +-----------------+
```

### A. Identification
The process begins when a node or user asserts an identity. This is simply the claim of who a particular user is on a system, typically initiated by typing an unauthenticated alphanumeric username.

### B. Authentication
Authentication tests the claimed identity by forcing the user to provide a verified secret (such as a password) or additional authentication factors. 
This step matches the credentials against a secure directory database to prove that the entity truly is who they claim to be.

### C. Authorization
Once identity is verified, authorization determines the explicit boundaries of user access. 
It evaluates which departments, applications, directories, or assets the authenticated user is permitted to interact with (e.g., granting a shipping employee access to customer logistics 
databases while blocking access to the finance network).

### D. Accounting
Accounting acts as a continuous ledger that tracks what occurs during an active session. 
It maintains detailed log files documenting exactly when a user logs in, how much data is sent or received, what specific files are accessed, and the exact timestamp of their logout.

---

## 2. Centralized AAA Infrastructure

Managing local databases of usernames, passwords, and access privileges on hundreds or thousands of separate infrastructure devices across the globe does not scale. 
To streamline operations, networks deploy centralized architecture.

* **The Production Workflow:** When a remote user attempts to connect to an internal file server via a perimeter device (such as a VPN concentrator or firewall),
the gateway intercepts the request and prompts for user credentials.
* **Database Offloading:** The VPN concentrator does not store user databases locally. Instead,
it forwards the identification credentials over the network to a central **AAA server**.
* **Access Approval:** The centralized AAA server evaluates the request against its master user database.
If the credentials are valid, the AAA server returns an approval token back to the gateway device, which then permits the remote client to pass through and access internal file resources.

---

## 3. Cryptographic Device Authentication via Certificates

Unmanned hardware assets (such as field laptops or remote edge devices) cannot manually enter text passwords to gain network access, 
and storing plaintext passwords on remote endpoints creates a severe security risk. To authenticate these devices automatically, networks use digital certificates.

* **The Certificate Authority (CA):** A Certificate Authority is a dedicated device or software system responsible for issuing, signing, and managing cryptographic certificates within an organization.
* **The Device Certificate:** The CA generates a unique device certificate specifically for a target laptop.
This certificate is digitally signed by the Certificate Authority's own root key, creating an explicit cryptographic chain of trust.
* **Authentication Checking:** The signed certificate is deployed onto the client machine. When the laptop connects to a secure network gateway or device management engine,
the infrastructure validates the machine's authenticity by verifying that its certificate was legitimately signed by the trusted internal Certificate Authority.

---

## 4. Scalable Authorization and Abstraction Models

Directly mapping individual user accounts to individual rights and permissions creates massive administrative overhead that fails to scale. 

* **The Scaling Problem:** If an organization has hundreds of employees in a shipping department who each require access to dozens of separate databases,
tracking configurations, and labeling resources, manually configuring discrete permissions for every individual account creates a highly unstable administrative environment.
* **The Abstraction Solution:** To build scalable architectures, organizations insert an **authorization abstraction model** between the user pool and the infrastructure resources.
This cleanly separates user profiles from target applications or data directories.
* **Group-Based Abstraction:** Users and services are grouped together by shared organizational characteristics, roles, or attributes (e.g., adding all logistics personnel into a single group called `Shipping and Receiving`).
Instead of editing individual accounts, permissions to track shipments, generate shipping labels, and access customer contact lists are applied once directly to the group object. 
