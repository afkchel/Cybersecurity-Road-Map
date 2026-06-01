# Configuration Management

## 1. The Production Baseline
The **Production Configuration** is the verified standard for every device in the live environment. It is not merely a collection of settings but a comprehensive state that includes:
* **Hardware & Firmware:** Specific versions currently certified for use.
* **Device Drivers:** Verified versions for compatibility and stability.
* **Software Versions:** Standardized builds to ensure consistent behavior.

## 2. Configuration Control Methods

To maintain stability, the following methods are used to protect and verify system states:

### 2.1 Pre-Change Backups
**Standard Operating Procedure (SOP):** Never commit a change without a fallback point.
* **File-Based:** Copy critical configuration files (e.g., `config.cfg`) before editing.
* **Snapshots:** In Virtual Machine (VM) environments, utilize snapshots to save the entire system state (RAM, Disk, Config) at a specific point in time for near-instant reversal.

### 2.2 Golden Configurations (Baselines)
A **Golden Configuration** is the "Master Copy" that represents the ideal, certified state of a device or application.
* **Integrity Checks:** Regularly compare production settings against the Golden Config.
* **Reconciliation:** If a mismatch is found:
    1.  Revert the production environment to match the baseline.
    2.  *OR* Update the baseline if the production change is the new approved standard.

## 3. The Change Management Lifecycle

No modification should be made in "Production" without following these four pillars:

| Phase | Description |
| :--- | :--- |
| **Plan** | Define the scope, identify affected systems, and develop a rollback plan. |
| **Test** | Perform changes in a lab environment. Do not use production to "see how it runs." |
| **Inform** | Notify stakeholders of the change window and potential impact. |
| **Document** | Record every change from initial installation through the current state. |

## 4. Application Scope Documentation
Documentation must include:
* **Server Configurations:** OS settings and app binaries.
* **Network Path:** Firewall rules, load balancer settings, and routing tables.
* **Workstation Settings:** Client-side requirements and local configurations.

## 5. Disaster Recovery Readiness
In the event of a total system failure, documentation is the roadmap to reconstruction. Having a record of every change made since the initial "Day 0" installation is the only way to ensure the system is rebuilt to the exact state it was in before the disaster.
