# Interface Configurations and Optimization Reference

## 1. Physical Layer Settings
When connecting a device to a switch or router, the physical link parameters must be synchronized between both sides of the cable.

*   **Speed**: The transmission rate of the connection (e.g., 10 Mbps, 100 Mbps, 1 Gbps, or 10 Gbps). Both sides must be configured identically, or the link will fail to establish (no link light).
*   **Duplex**: 
    *   **Full Duplex**: Simultaneous two-way communication.
    *   **Half Duplex**: One-way communication at a time.
*   **Mismatch Consequences**: If speed is mismatched, the link fails. If duplex is mismatched, the link will function but suffer from extreme performance degradation and collisions under heavy load.

---

## 2. IP Configuration Essentials
Once the physical link is stable, the interface requires valid Layer 3 settings, typically assigned by a network administrator.

*   **IP Address**: The unique identifier for the device on the network.
*   **Subnet Mask**: Defines the boundaries of the local network.
*   **Default Gateway**: The IP address of the router used to reach external networks.
*   **DNS Settings**: Required for resolving hostnames to IP addresses.
*   **Validation**: Incorrect masks or gateways will prevent communication with devices outside the local subnet.

---

## 3. Link Aggregation (LAG)
Link Aggregation, also known as **Port Bonding** or **LAG**, allows multiple physical interfaces to be combined into a single logical link.

*   **Increased Throughput**: Combining four 1 Gbps links results in 4 Gbps of total throughput.
*   **Loop Prevention**: Instead of seeing four individual connections (which could cause a loop), the switch treats them as one large pipe.
*   **LACP (Link Aggregation Control Protocol)**: A protocol that automatically handles the configuration and "handshake" between two switches to bond the ports.

---

## 4. MTU and Jumbo Frames
The **Maximum Transmission Unit (MTU)** defines the largest size packet or frame that can be sent across a network without fragmentation.

*   **Standard Ethernet Frame**: Default size is **1,500 bytes**.
*   **Fragmentation**: If a packet is too large for a link, it is broken into smaller pieces, which adds overhead and slows down communication.
*   **Jumbo Frames**:
    *   Increases the MTU up to **9,000 or 9,216 bytes**.
    *   **Efficiency**: One jumbo frame can carry the payload of approximately six standard frames, reducing the CPU load on routers and switches.
    *   **Critical Requirement**: **Every device** in the data path (source, destination, and all intermediate switches/routers) must support and be configured for jumbo frames. If one device does not support them, the frames will be dropped.
