# Zero Trust & SASE (Secure Access Service Edge) 

## 1. The Zero Trust Philosophy
Traditionally, network security focused on protecting the **edges** (perimeter) of the network. 
While this controlled entry and exit, it left the internal network vulnerable because once a user was inside, everything was accessible. 
**Zero Trust** is a holistic approach where every user, device, and application is inherently untrusted, regardless of their location.

### Core Principles:
*   **Verify Explicitly**: Always authenticate and authorize based on all available data points.
*   **Least Privilege Access**: Users are only granted the specific rights and permissions required to perform their job.
*   **Assume Breach**: Constantly monitor the network for threats as if an attacker is already present.

---

## 2. Adaptive Identity
In a Zero Trust environment, authentication is not just about a username and password; it uses **Adaptive Identity** to evaluate risk in real-time.

| Factor | Description |
| :--- | :--- |
| **User Context** | Considers who the user is (e.g., long-term employee vs. a new vendor). |
| **Geographic Location** | Checks if the login attempt is coming from a local area or an unusual country. |
| **Connection Risk** | Evaluates the IP address and the type of connection (e.g., VPN vs. public Wi-Fi). |
| **Behavioral Patterns** | Flags logins occurring at unusual times of day. |

---

## 3. Authorization and Least Privilege
Once identity is verified, the system determines what the user can access.
*   **Role-Based Access**: A help desk member may view a database, while a manager can modify it.
*   **Device Trust**: Additional permissions may be granted if the user is on a company-provided laptop with a verified certificate.
*   **Risk Mitigation**: Administrative access is limited because if an admin account is infected with malware, the malware gains full access to the entire system.

---

## 4. SASE (Secure Access Service Edge)
As users and applications move outside the traditional office, **SASE** (pronounced "sassy") provides a secure mechanism for communication regardless of location. 
SASE is often described as a **Next-Generation VPN** that moves security into the cloud, closer to the application data.

### SASE Architecture Components:
*   **Network as a Service**: Provides routing and Quality of Service (QoS).
*   **Security as a Service**: Includes Firewall as a Service (FWaaS), DNS security, and Zero Trust Network Access (ZTNA).
*   **The SASE Client**: Software installed on the user device that automatically manages secure connections without user intervention.

### Benefits of SASE:
*   **Location Independent**: Works for corporate offices, home offices, and mobile field users.
*   **Seamless Security**: Security is built into the process, so users don't have to manually turn it on or off.
*   **Cloud-Native**: Specifically designed to secure access to Software as a Service (SaaS) and public cloud applications.
