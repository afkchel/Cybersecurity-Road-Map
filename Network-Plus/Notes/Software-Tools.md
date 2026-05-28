# Software Diagnostic Tools: Protocol Analysis, Active Mapping, and Discovery Protocols

---

## 1. Protocol Analyzers and Frame Decodes

When troubleshooting network performance issues or application delays, administrators use **protocol analyzers** to capture and inspect raw data.

* **Functionality:** A protocol analyzer captures data frames moving across a wired or wireless network link and decodes the binary traffic into a structured, human-readable format.
* **Deployment Options:** Packet capture capabilities are often built directly into the software of switches,
routers, or firewalls. This allows engineers to view the data locally or export the capture to a file for deeper analysis.
* **Wireshark Analysis:** Exported capture files can be opened in specialized analyzers like **Wireshark**.
Wireshark parses the data to show detailed protocol decodes and trace the entire conversation across the network.
* **Historical Analysis:** In large enterprise networks, administrators often capture and save all network packets to disk.
This archive allows them to quickly search through historical records to analyze past security or performance events.

---

## 2. Active Network Mapping via Nmap

**Nmap (Network Mapper)** is an active scanning utility used to discover network hosts, identify open ports, and map infrastructure assets.

### A. Active Query Logic
Unlike passive packet sniffer tools, Nmap performs an **active scan**. 
It transmits targeted queries directly to a specific destination host or across an IP address range and analyzes the responses to determine the state of the remote device.

### B. Information Gathered by Nmap
Without needing to log into the target system, an active Nmap scan can discover:
* Active hosts within a designated subnet range.
* **Open Port Numbers:** Identifies which transport layer coordinates are listening for connections.
* **Operating System Details:** Detects the type and version of the OS running on the remote device.
* **Application Services:** Identifies the specific type and version of the service running on an open port.
* **Scripting Engine Extensibility:** Features an embedded scripting engine that allows engineers to write custom scripts to extend Nmap's scanning and validation capabilities.

### C. Subnet Asset Discovery and Rogue Detection
Nmap is a powerful tool for finding unauthorized or rogue hardware on an organization's network. 
When scanning within a shared local subnet, **Nmap can interact using just Layer 2**. This direct local connectivity makes it difficult for a rogue device to hide its presence from the scan.

### D. Reference Port Identifications
An Nmap scan against a typical server (such as IP `10.1.10.222`) may reveal several open ports. Standard port mappings from the scan data include:
* **Port 22:** Secure Shell (SSH) management access.
* **Port 80:** Hypertext Transfer Protocol (HTTP) unencrypted web traffic.
* **Port 443:** Hypertext Transfer Protocol Secure (HTTPS) encrypted web traffic.
* **Port 548:** Apple Filing Protocol (AFP) file sharing service.
* **Port 2049:** Network File System (NFS) storage access protocol.

If an administrator discovers open ports that are unexpected, they must perform additional research to identify what services are running on those ports.

---

## 3. Infrastructure Discovery Protocols (CDP and LLDP)

When managing a patch panel or wiring closet, 
it can be difficult to tell what devices are plugged into a switch port or which VLANs they belong to just by looking at the hardware.
Administrators use neighbor discovery protocols to gather this information automatically.

```
+---------------------------------------------------------------------------------+
|                          Neighbor Discovery Protocols                           |
|  (Gather native VLANs, interface names, and device profiles without logging in) |
+---------------------------------------------------------------------------------+
                                  |
         +------------------------+------------------------+
         |                                                 |
         v                                                 v
+-------------------------------+                 +-------------------------------+
| Cisco Discovery Protocol (CDP)|                 |Link Layer Discovery Protocol  |
| - Cisco Proprietary           |                 |  (LLDP)                       |
| - Version 2 Detail Reports    |                 | - Industry Standard           |
| - Hardware-Specific Bindings  |                 | - Vendor-Neutral Support      |
+-------------------------------+                 +-------------------------------+
```

---

## 4. Bandwidth and Performance Validation

Validating internet connection speeds and available bandwidth requires consistent testing methodologies.

### A. Pre- and Post-Configuration Baselining
When making modifications to a network, administrators should perform speed tests **both before and after applying the configuration update**. 
Comparing these pre- and post-change measurements allows them to verify whether the update successfully improved performance, degraded throughput, or had no effect.

### B. Time-of-Day Variations
Bandwidth availability fluctuates based on total network utilization. 
Tests run during the middle of a standard workday often yield lower performance results because many active users are sharing the same path. 
In contrast, tests run during off-hours typically show higher available bandwidth.

### C. Speed Test Site Selection
Internet speed test platforms measure throughput by sending data over a link and tracking the upload and download times. However, testing platforms can vary significantly:
* **Distance Constraints:** Test sites located far away can introduce external routing delays and geographic latency that distort results.
* **Capacity Limits:** Some third-party speed test sites may have their own bandwidth constraints, which can lead to inaccurate performance statistics.
* **ISP-Hosted Testing Sites:** For the most accurate measurement of a local link's performance,
administrators should use testing platforms hosted directly by their local Internet Service Provider (such as Xfinity or AT&T).
These sites isolate the test to the provider's local network, removing outside variables.
* **Recommended Third-Party Alternatives:** If an ISP-hosted option is unavailable, reliable independent testing choices include **Fast.com**, **SpeedOf.Me**, **speedtest.net**, and **testmy.net**.
