# Network Troubleshooting and Solutions

## 1. Network Discovery and Information Gathering

When starting a troubleshooting session with no initial data, use discovery protocols and scanning techniques to build a map of the network.

### **Discovery Protocols:**
* **LLDP (Link Layer Discovery Protocol):** An open standard for switch-level discovery.
* **CDP (Cisco Discovery Protocol):** Cisco’s proprietary version of link-layer discovery.
### **Scanning Methods:**
* **Ping Scans:** Identifying devices that are currently active and responding on the network.
* **Port Scans:** Identifying open services and applications on specific devices.
* **SNMP (Simple Network Management Protocol):** Querying devices for specific performance and configuration data.

## 2. Traffic Flow and Forensic Analysis

Detailed analysis allows for a frame-by-frame or packet-by-packet understanding of network activity.

### **Firewall Logs**

These logs provide a wealth of data for every traffic flow, including:

* **Timestamps:** Pinpointing exactly when a connection occurred.
* **Protocols and Ports:** Identifying if the traffic was TCP, UDP, and which application port was used.
* **Source and Destination:** Identifying the Client IP and Server IP involved in the communication.
* **Data Volume:** Measuring exactly how many bytes were transferred.
* **Utility:** Storing this information over long periods enables detailed historical reporting and security forensics.

## 3. Availability and Performance Monitoring

Monitoring ensures that infrastructure remains operational and efficient.

### **Availability Status**
* **An "Up/Down" metric** 
* **Performance Metrics:** Using SNMP, NetFlow, or software agents to track:
* **Network Utilization:** Identifying if links are saturated.
* **Error Rates:** Detecting hardware or configuration issues causing packet drops.
* **Alerting:** Integrating these statuses into automated alarms (email, helpdesk tickets) to ensure rapid response to outages.

## 4. Configuration and Firmware Management

Maintaining backups and tracking changes is critical for disaster recovery and security.

* **Version Control:** Configuration files are often specific to certain firmware versions.
* **Downgrades:** If a router OS is updated, older configuration files may not load without first downgrading the firmware to the matching version.

### **Configuration Integrity:**
* **Standardization:** Comparing configuration files across identical devices (e.g., 10 identical web servers) to ensure consistency.
* **Change Control:** Monitoring configuration files for unauthorized changes and generating alerts if the established "gold" configuration is modified without approval.
* **Storage:** Always keep a repository of both current configuration backups and previous firmware/software versions.
