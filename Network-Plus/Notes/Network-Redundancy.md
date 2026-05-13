# Network Redundancy

---

## 1. Active-Passive Configuration

Active-Passive is a high-availability deployment where one device performs all networking tasks while the other remains in a standby state.

* **Operational Mechanism:** The two devices communicate constantly to monitor each other's status.
* **Failover Process:** If the primary (active) device fails due to power loss or software crash, the secondary (passive) device detects the outage and automatically takes over as the primary.
* **Synchronization Requirements:**
* **Identical Configuration:** Both devices must have exactly the same settings.
* **Stateful Updates:** Real-time data, such as session tables and routing tables, must be synchronized so the passive device can resume traffic flows without interruption.

---

## 2. Active-Active Configuration

In an Active-Active setup, both devices are operational and processing network traffic simultaneously.

* **Resource Utilization:** This allows the organization to utilize the full computing power of both devices rather than leaving one idle.
  - **Traffic Distribution:** Different data flows are distributed across both active devices.
  - **Failure Handling:** Since both units are already active, the failure of one does not require a formal "failover" transition; the remaining unit simply absorbs the total load.

---

## 3. Design and Engineering Considerations

Implementing redundancy requires careful architectural planning to avoid connectivity issues.

* **Configuration Management:** Any change made to the primary device must be immediately copied to the secondary unit to ensure consistency.
* **Traffic Engineering (Active-Active):** This configuration is more complex and requires specific engineering to track asymmetrical data flows (e.g., traffic exiting one device but returning through another).
* **Visibility:** Redundancy should be mapped out visually to understand the communication path between the internet provider, firewalls, and internal resources like web servers.

---

## 4. Summary of Redundancy Models

| Feature | Active-Passive | Active-Active |
| --- | --- | --- |
| **Device Utilization** | One active, one idle (standby). | Both devices process traffic. |
| **Complexity** | Relatively simple to configure. | High; requires detailed flow design. |
| **Performance** | Performance is limited to one device. | Combined performance of both devices. |
| **Failover Behavior** | Passive device must switch to active mode. | Surviving device continues existing load. |
