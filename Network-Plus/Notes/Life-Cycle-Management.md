# Life-Cycle Management (LCM) Standard Operating Procedure

## 1. Product Life-Cycle Stages

| Term | Definition | Impact |
| :--- | :--- | :--- |
| **End of Life (EOL)** | The manufacturer stops marketing or selling the product and will no longer add new features. | Plan and budget for replacement; security patches may still be available. |
| **End of Support (EOS)** | The manufacturer ceases all support, including critical security patches and bug fixes. | **High Security Risk.** Device must be replaced or isolated immediately. |

## 2. Patch & Update Management

Software and firmware require constant maintenance to close security holes and improve stability.

### 2.1 Operating System (OS) Updates
* **Recurring Schedule:** Most OS updates (Windows, Linux, Mobile) follow a monthly release cycle.
* **Out-of-Band Updates:** Emergency patches released outside the normal schedule, usually to address **Zero-Day** vulnerabilities.
* **Configuration Changes:** Updates may include changes to password complexity, minimum lengths, and built-in firewall rules.

### 2.2 Firmware Management
Firmware is the embedded software running on purpose-built hardware (routers, printers, IoT).
* **Documentation:** Always maintain a repository of firmware binaries.
* **Fallback Plan:** Before any upgrade, ensure a "back-out" plan exists to revert to the previous version if the update fails.
* **Vendor Reliability:** Be aware that hardware manufacturers may be slow to patch firmware (e.g., the Trane thermostat vulnerability took nearly two years to fully patch).

## 3. Change Management Process

All modifications to the computing environment must be managed to ensure uptime and accountability.

1.  **Request:** Submit a formal change request for any modification (switch upgrades, firewall rules, etc.).
2.  **Window:** Perform changes only during defined maintenance windows to minimize user impact.
3.  **Documentation:** Track and monitor all changes in a centralized system.
4.  **Rollback:** Every change must have a predefined process for rolling back if stability is compromised.

## 4. Service Requests & Support

Ongoing lifecycle support is managed through a centralized **Process Tracking System** (Help Desk).
* **Triage:** Incoming tickets are prioritized based on severity.
* **Resolution:** Technicians resolve the issue and document the fix.
* **Closure:** Tickets are closed only after verification of service restoration.

## 5. Decommissioning & Disposal

The final stage of the life-cycle ensures that sensitive data does not leave the organization.

* **Sanitization:** All storage media must be wiped (sanitized) using approved software methods.
* **Physical Destruction:** If a device cannot be sanitized, it must be physically destroyed.
* **Legal Hold:** Certain data may be subject to legal requirements for storage.
* **Proper Disposal:** Do not dispose of hardware in normal trash.
