# Network Types

## 1. Infrastructure Mode
This is the most common wireless configuration, used in almost all home and office environments.
* **Centralized Control**: All wireless devices communicate through a central **Access Point (AP)**.
* **Wired Integration**: The AP typically connects to a wired switch, bridging the wireless and wired parts of the network.
* **Client Isolation**: A security feature in many infrastructure networks that prevents wireless clients from communicating with each other, allowing them only to talk to the AP and the internet.

---

## 2. Ad Hoc Mode (IBSS)
Formally known as **Independent Basic Service Set (IBSS)**, this is a decentralized network type.
* **Peer-to-Peer**: Devices communicate directly with one another without the need for a central access point.
* **IoT Provisioning**: Often used as a temporary connection to set up **Internet of Things (IoT)** devices. You connect to the device via Ad Hoc to "hand off" your home Wi-Fi credentials, after which the device switches to Infrastructure mode.
* **Temporary Connectivity**: Useful for quick file transfers between two laptops when no network infrastructure is available.

---

## 3. Wireless Mesh
A mesh network consists of multiple access points that work together to blanket a large area with a single seamless signal.
* **Interconnectivity**: Unlike standard extenders, mesh APs communicate with each other to determine the best path for data.
* **Self-Healing**: If one node in the mesh fails or moves, the network automatically recalculates the path to maintain connectivity for all remaining devices.
* **Scalability**: New nodes can be added easily to extend the "fabric" of the network into dead zones.

---

## 4. Point-to-Point (Bridge)
This mode is used to connect two specific points over a distance, acting as a wireless replacement for a physical cable.
* **Building-to-Building**: Common for connecting two separate offices or homes that are within line-of-sight.
* **Specialized Hardware**: Requires access points that support bridging mode and often utilizes **directional antennas** (like Yagi or Parabolic) to focus the signal.
* **Configuration**: Requires manual adjustment of power output and frequency to ensure a stable link over long distances while complying with local regulations.

---

## Summary Comparison Table

| Network Type | Central AP? | Best Use Case | Primary Benefit |
| :--- | :--- | :--- | :--- |
| **Infrastructure** | Yes | Homes & Offices | High management and stability |
| **Ad Hoc** | No | IoT Setup / Direct file swap | No hardware required |
| **Mesh** | Yes (Multiple) | Large homes / Dead zones | Self-healing and easy coverage |
| **Point-to-Point** | Yes (Bridge) | Connecting two buildings | Replaces long-distance cabling |
