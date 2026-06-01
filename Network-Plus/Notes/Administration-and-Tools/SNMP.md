# SNMP (Simple Network Management Protocol)

## 1. Protocol Fundamentals
SNMP is a standardized protocol used to monitor and manage network devices (switches, routers, servers, firewalls) regardless of the manufacturer.

* **NMS (Network Management Station):** The central console that queries devices.
* **Agent:** The software running on the network device that responds to queries.
* **Polling (UDP 161):** The NMS actively asks the device for data at regular intervals.
* **Traps (UDP 162):** The device proactively sends an unsolicited alert to the NMS when a threshold is met (e.g., high error rate).

## 2. Data Structure: MIBs and OIDs
Data on a device is organized in a hierarchical database.

* **MIB (Management Information Base):** The central database of all manageable parameters on a device.
* **OID (Object Identifier):** A unique numerical path (e.g., `.1.3.6.1.2.1.11.28.0`) that points to a specific variable in the MIB.
    * **Standard MIBs:** Identical across all vendors (e.g., MIB-II).
    * **Custom MIBs:** Specific to a manufacturer; require importing a MIB file to the NMS for translation.
* **MIB Walker:** A tool used to query every possible OID on a device to discover available data points.

## 3. Version Comparison & Security

| Version | Security Mechanism | Encryption | Recommendation |
| :--- | :--- | :--- | :--- |
| **SNMPv1** | Community String (Cleartext) | None | **Legacy only.** Do not use in production. |
| **SNMPv2c** | Community String (Cleartext) | None | Efficient for large data, but insecure. |
| **SNMPv3** | User/Password Hashing | **Full Encryption** | **Standard.** Required for all secure environments. |

## 4. Community Strings (v1/v2c)
If v3 is unavailable, the following naming standards apply:
* **Read-Only (RO):** Used for monitoring only (default: `public` - **MUST BE CHANGED**).
* **Read-Write (RW):** Allows the NMS to change device settings (default: `private` - **HIGH RISK**).
* **Trap String:** Dedicated string for unsolicited alerts.
