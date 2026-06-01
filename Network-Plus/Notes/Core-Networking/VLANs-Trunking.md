# Virtual LANs (VLANs) and Trunking 

## 1. The Concept of a VLAN
A **Local Area Network (LAN)** is a group of devices residing in the same **broadcast domain**. Traditionally, separate broadcast domains required separate physical switches, which was expensive and inefficient. 

**Virtual Local Area Networks (VLANs)** allow multiple broadcast domains to exist on the same physical switch. 
*   **Separation**: Devices on different VLANs cannot communicate directly without a router, even if plugged into the same switch.
*   **Identification**: VLANs are defined by **numbers** (e.g., VLAN 10, VLAN 20).
*   **Efficiency**: Consolidates hardware, reduces power consumption, and saves rack space.

---

## 2. VLAN Trunking (802.1Q)
When VLANs need to span across multiple switches, a **Trunk** is used. Instead of running a separate cable for every single VLAN, a single physical link (an **802.1Q trunk**) carries traffic for all of them.

### Frame Tagging
To keep traffic organized on a trunk, the switch adds a **12-bit VLAN tag** to the standard Ethernet frame. 
*   **The Tag**: Inserted after the Source MAC address.
*   **Capacity**: Supports up to **4,094** unique VLANs.
*   **The Process**: The sending switch adds the tag; the receiving switch reads the tag, removes it, and forwards the "clean" frame to the correct destination port.

### Native VLANs
A **Native VLAN** is a specific configuration where traffic is sent across a trunk **without a tag**. 
*   Used for administrative traffic (management, notifications) or devices that do not support 802.1Q tagging.
*   **Requirement**: The Native VLAN ID must match on both ends of the trunk to avoid errors.

---

## 3. Layer 3 Switching
While traditional (Layer 2) switches forward traffic based on MAC addresses, a **Layer 3 Switch** can also make forwarding decisions based on **IP addresses**.

*   **SVI (Switched Virtual Interface)**: A virtual internal interface that allows the switch to route traffic between different VLANs.
*   **Benefit**: Combines the high speed of a switch with the routing intelligence of a router in one device, though it may lack some advanced features of a standalone router.

---

## 4. Voice and Data Integration
Modern enterprise networks often run **Voice over IP (VoIP)** and data over the same physical Ethernet cable.

*   **VLAN Separation**: To prevent "bursty" computer data from interrupting sensitive voice calls, phones are placed on a **Voice VLAN** and computers on a **Data VLAN**.
*   **Daisy-Chaining**: Most VoIP phones have an internal switch. You plug the phone into the wall, and the computer into the back of the phone. The single cable back to the switch acts as a mini-trunk to keep the voice and data traffic separate.
