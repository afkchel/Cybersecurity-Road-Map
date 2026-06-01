# Enterprise Network Topologies

Network topology refers to the physical or logical layout of a network. Understanding these architectures is essential for effective network design, planning, and troubleshooting.

---

## 1. Star Topology (Hub-and-Spoke)
The most common topology used in modern local area networks (LANs).

* **Design:** All devices connect to a single **central networking component**.
* **Implementation:** In an Ethernet network, an **Ethernet switch** acts as the central hub. All "spokes" (devices) must communicate through this switch to reach each other.
* **Pros:** Easy to manage and scale; failure of one cable only affects that specific device.
* **Cons:** The central switch is a single point of failure.

## 2. Mesh Topology
A design where devices or locations are interconnected via multiple redundant paths.

* **Design:** One node connects to another over more than one network connection.
* **Usage:** Commonly seen in **Wide Area Networks (WANs)** to ensure remote sites stay connected.
* **Redundancy:** If one link fails, traffic is rerouted through an alternate path.
* **Load Balancing:** Traffic can be split across multiple links to improve performance.

## 3. Spine and Leaf Architecture
A two-tier architecture optimized for modern data centers to provide high-speed, low-latency communication.

* **The Spine:** The top-tier switches that connect to all leaf switches. Spines do not connect to each other.
* **The Leaf:** The switches that connect to end devices (servers) and to all spine switches. Leafs do not connect to each other.
* **Performance:** Any device in the data center is always exactly **one switch hop** (two switches total) away from any other device.
* **Top-of-Rack (ToR) Switching:** A common deployment where a leaf switch is placed at the top of every physical rack, keeping cabling self-contained within that rack.

## 4. Point-to-Point Topology
A direct, dedicated connection between exactly two endpoints.

* **Design:** A single point connected to a single point.
* **WAN Usage:** Historically common with T1 or T3 dedicated leased lines.
* **LAN Usage:** Often used to connect two buildings on a campus via a direct fiber or wireless link.

## 5. Hybrid Architecture
The reality of large enterprise environments where multiple topologies are used together.

* **Design:** A combination of different architectures (e.g., a Star network for the office, a Mesh for the WAN, and Spine and Leaf for the Data Center).
* **Purpose:** Allows the network to meet different requirements for cost, performance, and redundancy across different departments or locations.

---

## Summary Table

| Topology | Key Feature | Best For... | Redundancy |
| :--- | :--- | :--- | :--- |
| **Star** | Centralized switch | Standard Office LANs | Low (Central point) |
| **Mesh** | Multiple redundant paths | WANs / Critical links | Very High |
| **Spine & Leaf** | Two-tier, low latency | Data Centers | High |
| **Point-to-Point** | Dedicated 1-to-1 link | Building-to-Building | None |
| **Hybrid** | Mixed topologies | Large Enterprises | Varies |

> [!IMPORTANT]
> **Top-of-Rack (ToR)** switching simplifies cabling within a rack but increases costs as the data center grows, because every new rack requires its own dedicated switch.
