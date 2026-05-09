# Home Network Discovery and Layered Mapping Lab

## Project Overview

The objective of this lab was to perform a complete discovery of a local area network (LAN), identify connected assets, and visualize the network architecture through a multi-layer logical map. 
This process simulates real-world **Asset Management** and **IP Address Management (IPAM)** procedures used in enterprise IT environments.

## Tools Used

* **Advanced IP Scanner**: Network discovery and port identification.
* **Xiaomi Home App**: Physical asset verification and IoT management.
* **MiWiFi Admin Interface**: Gateway analysis and connection type verification.
* **Microsoft Excel**: Database creation for IPAM and Asset Tagging.
* **Draw.io**: Logical network diagramming.

## Methodology

### Phase 1: Network Discovery

Conducted a scan of the local subnet. Given the netmask of `192.168.31.0/24`, the scan range was set to `192.168.31.1 - 192.168.31.254`.

<img width="805" height="334" alt="image" src="https://github.com/user-attachments/assets/4001fd6b-a80b-4b90-ad84-be308bfdfcd8" />

### Phase 2: Asset Identification & Verification

To move beyond generic manufacturer names, I performed an investigation:

* **Verification**: Correlated MAC addresses found in the scan with the **Xiaomi Home** application.
* **Discovery**: Successfully identified an "unknown" device at `.252` as a **Roborock S6 Pure** vacuum cleaner by matching the physical hardware MAC address.

<img width="591" height="1280" alt="image" src="https://github.com/user-attachments/assets/b7f0dc6f-1eff-4502-8e5a-20f7672606c4" />

### Phase 3: Data Documentation (IPAM)

I exported the raw scan data into a `.csv` format and enriched the data in Excel. I added custom columns to create a professional asset inventory:

* **User/Owner**: Assigned specific family members or roles (e.g., Infrastructure, Family, Leonid).
* **Asset Tags**: Created a standardized naming convention (e.g., `HOME-RTR-01`, `HOME-PHN-01`).
* **Connection Type**: Verified via the router admin page.

**Final Asset Table:**
<img width="1351" height="198" alt="image" src="https://github.com/user-attachments/assets/3c1bfc58-dcb8-4409-a427-a5fd0a3fe48b" />


### Phase 4: Layered Network Mapping

Using the gathered data, I designed a **Layered Network Map** in Draw.io. The map integrates three distinct layers of information:

1. **Layer 1 (Physical)**: Visualized connection mediums (Ethernet vs. Wi-Fi).
2. **Layer 2 (Data Link)**: Included unique MAC addresses for every node.
3. **Layer 3 (Network)**: Assigned static and dynamic IP addresses and identified the WAN DHCP connection.

<img width="929" height="791" alt="My Network drawio" src="https://github.com/user-attachments/assets/ab5ad86e-4268-4bde-9214-34a3620a4699" />

## Key Findings & Troubleshooting

* **Bottleneck Identified**: During the physical audit, the PC (`HOME-PC-01`) was found to be limited to **100 Mbps**. Further investigation revealed a **Category 5 (Cat 5)** Ethernet cable acting as a hardware bottleneck.
* **Spectrum Allocation**: Verified that high-bandwidth devices (Smartphones) are utilizing the **5GHz** band, while low-bandwidth IoT (Vacuum) utilizes the **2.4GHz** band for better range.
* **Security Architecture**: Confirmed the **Security System (Ajax)** is hardwired via Ethernet for maximum stability and reduced interference.

## Conclusion

This lab demonstrates the importance of network visibility. By documenting the "hidden" aspects of the network—such as MAC addresses and physical cable categories—I was able to identify performance bottlenecks and create a baseline for future troubleshooting.
