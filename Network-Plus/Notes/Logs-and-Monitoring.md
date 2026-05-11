# Network Logs and Monitoring

## 1. Flow Analysis with NetFlow
NetFlow provides metadata summaries of network traffic without capturing raw packets. This is essential for understanding application usage and identifying top talkers.

* **Architecture:**
    * **NetFlow Probe:** Captures raw packets and compiles them into flow statistics.
    * **NetFlow Collector:** A central database that gathers data from multiple probes.
    * **Report Generator:** Visualizes data into charts (e.g., Top 10 Conversations, Top Applications like SSL or SQL).
* **Use Case:** Identifying bandwidth spikes and mapping application traffic by port number.

## 2. Centralized Logging (Syslog & SIEM)

* **Syslog Protocol:** The industry standard for transferring log files from switches, routers, and firewalls to a central server.
    * **Facility Code:** Identifies the program or source that created the log.
    * **Severity Level:** Categorizes the urgency (e.g., Informational, Warning, Critical).
* **SIEM (Security Information and Event Management):**
    * **Aggregation:** Rolls up logs from diverse sources into a single dashboard.
    * **Forensics:** Allows administrators to "go back in time" to track authentication events (e.g., tracing a brute force attempt").
    * **Alerting:** Triggers alarms based on real-time anomalies or failed authentication patterns.

## 3. Deep Packet Inspection (Protocol Analyzers)
When metadata is insufficient, protocol analyzers are used to view the exact bits and bytes of a conversation.

* **Tools:** Software like Wireshark (Protocol Analyzer).
* **Packet Capture:**
    * **Port Mirroring (SPAN):** A switch configuration that sends a copy of traffic from one port to a monitoring device.
    * **Network Tap:** A physical hardware device inserted between two points to capture traffic.
* **Use Case:** Troubleshooting slow applications or identifying unknown, suspicious traffic.

## 4. Performance Baselines
A **Network Performance Baseline** is a historical record of what "normal" looks like on the network.

* **Utility:** During troubleshooting, the baseline is used to compare current utilization against a standard workday.
* **Granularity:** Baselines can be established for the entire network or for individual critical devices.

## 5. Automation via APIs
Managing hundreds of devices manually via SSH is inefficient.

* **API Integration:** Allows central management stations to communicate with devices in their native language via scripts or programs.
* **Benefit:** Enables one-click configuration changes and automated data queries across the entire infrastructure, bypassing the manual command-line interface.
