# Core Security Technologies, Cyber Risk, and Deception Frameworks

---

## 1. Deception Frameworks (Honeypots and Honeynets)

Rather than fighting automated attack programs blindly, defensive teams deploy intentionally vulnerable assets to observe threat techniques, scripts, and lateral movement in real time.

* **Honeypot:** A single isolated decoy asset (e.g., a virtual server, data file, or mock application) placed on a network with no legitimate production value. Any interaction with a honeypot is immediately flagged as suspicious.
* **Honeynet:** A complex, interconnected network of honeypots mimicking a real corporate enterprise topology. 
    - **Components:** Contains virtual workstations, decoy file servers, network-attached storage (NAS) devices, proxy pools, routers, and mock firewalls.
    - **Purpose:** Tracks an adversary's lateral movement patterns (e.g., pivoting from an compromised entry workstation over to a central network share) to map their playbook without risking live production infrastructure.

---

## 2. The Cyber Risk Lifecycle

Every security decision made within an organization is driven by calculating, managing, and mitigating operational risk.

```text
┌────────────────┐      Takes Action      ┌───────────────┐      Weaponizes      ┌─────────────────┐
│  Threat Agent  │ ─────────────────────► │    Threat     │ ───────────────────► │     Exploit     │
└────────────────┘                        └───────┬───────┘                      └────────┬────────┘
                                                  │                                       │
                                                  │ Impacts                               │ Breaches
                                                  ▼                                       ▼
                                          ┌───────────────┐                      ┌─────────────────┐
                                          │     Risk      │                      │  Vulnerability  │
                                          └───────────────┘                      └─────────────────┘
```

* **Risk:** The baseline exposure to harm or danger. It is the calculated probability and business impact of an adverse event occurring during organizational shifts (e.g., deploying new software, changing port configurations).
* **Vulnerability:** A specific weakness, architectural flaw, or misconfiguration inside an operating system, network protocol, or application code layer (e.g., unpatched buffer overflows or hardcoded credentials).
* **Exploit:** The action, piece of code, or script used by an attacker to weaponize a vulnerability. Executing an exploit is the mechanism that converts a passive code weakness into an active system breach.
* **Threat:** Any potential force, entity, or circumstance capable of exploiting a vulnerability to cause harm.
    - *Intentional Threats:* External malicious hackers, automated exploit scripts, insider threat actors.
    - *Accidental Threats:* Disasters like facility fires, hardware structural failures, or localized flooding.

---

## 3. The Core Pillars of Security: The CIA Triad

To counteract threats, information technology systems measure their defensive stance using three fundamental principles. This is occasionally referred to as the **AIC Triad** to prevent naming confusion with the US intelligence agency.

### A. Confidentiality (C)
* **Objective:** Assuring that sensitive data is restricted from unauthorized viewing or interception.
* **Enforcement Mechanisms:** Robust access control lists (ACLs), strict user authentication workflows, and strong data-at-rest/data-in-transit encryption protocols (such as AES, TLS, and IPsec).

### B. Integrity (I)
* **Objective:** Guaranteeing that data remains completely accurate, unaltered, and untampered with throughout its entire creation, transmission, and storage lifecycle.
* **Enforcement Mechanisms:** Hashing mechanisms (SHA-256) and cryptographic **Digital Signatures** applied directly to files or data streams to instantly catch unauthorized changes or manipulation.

### C. Availability (A)
* **Objective:** Ensuring that all underlying infrastructure, computing systems, and data repositories remain completely functional and accessible to authorized personnel whenever needed.
* **Strategic Balance:** Defensive configurations (such as aggressive firewall blocks or restrictive software access profiles) must be balanced carefully so they do not inadvertently break, delay, or slow down access for legitimate operators trying to do their jobs.
