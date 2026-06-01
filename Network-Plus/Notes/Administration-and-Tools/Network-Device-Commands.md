# Network Device Commands: Table Verification, Interface Analysis, and Hardware Metrics

---

## 1. Multi-Vendor Command Standardization

While different manufacturers use slight variations in command syntax, the underlying technology remains uniform across major enterprise vendors.

* **Concept Continuity:** Learning the functional mechanics behind network commands on one vendor's platform makes transitioning to another manufacturer's equipment straightforward.
* **Output Uniformity:** Diagnostic outputs report nearly identical structural data types (such as port mappings, status counters, and errors) across hardware ecosystems, allowing administrators to adapt quickly.

---

## 2. Layer 2 Forwarding Table Analysis

Switches use an internal **MAC address table** to track the locations of network nodes. 
This table maps learned source physical MAC addresses directly to the specific hardware port indexes where they were detected.

* **Command:** `show mac-address-table`
* **Diagnostic Use Cases:** * **Traffic Flooding Investigation:** Helps determine why unicast frames are flooding out of every port instead of being delivered over a single point-to-point connection.
* **Capacity Constraints:** Verifies whether the switch fabric has reached its maximum entry limit, which stops it from learning new device addresses.

---

## 3. Layer 3 Routing Table Diagnostics

Routers build paths across networks by tracking destination subnets, metric costs, next-hop coordinates, and exit interfaces inside a local routing table.

* **Command:** `show route`
* **Path Assessment Protocol:** Administrators use this command on each router across a network path to trace how data moves from one endpoint to another.
* **Prefix Matching:** When routing a packet, the router evaluates all entries to find a **more specific route** (a tighter subnet mask match) that applies to the packet's destination IP address.

### Routing Table Codes and Attributes:

* **Abbreviations Index:** The top of the output contains an abbreviation key that details how each route entry was added to the table.
* **`C` (Connected Route):** Indicates a local network that is directly attached to one of the router's physical or logical interfaces.
* **`R` (RIP Protocol Route):** Indicates a dynamic path learned via the Routing Information Protocol.

#### Routing Entry Output Structure:

```
[Prefix / Mask] ---> via [Next-Hop IP Address] ---> out [Physical Exit Interface]
Example: 1.0.0.0/8 via 20.20.0.2 on Serial3/0

```

---

## 4. Physical Port State and Link Error Analysis

The health, capacity, and duplex states of a physical link can be analyzed using a single interface status query.

* **Command:** `show interface`
* **Syntax Breakdown Example (`FastEthernet 0/0`):** Indicates a **100-Mbps** Fast Ethernet port located on slot index 0 at port position 0.
* **Dual 'Up' Status Evaluation:**
  - **Interface is Up:** Confirms the physical layer (Layer 1) hardware is receiving a valid electrical or optical signal.
  - **Line Protocol is Up:** Confirms data link layer (Layer 2) framing communications are working properly.


* **Physical Properties Tracked:** Displays the maximum transmission unit (**MTU**),
interface encapsulation types, hardware media type (e.g., RJ45 copper), speed configurations, and full-duplex versus half-duplex parameters.
* **Performance Error Counters:** Tracks real-time frame transmission drops and physical-layer corruption, including **CRC (Cyclic Redundancy Check) errors**,
input/output anomalies, and total broadcast packet counts.

---

## 5. Volatile Configuration Management

Network appliances use plain-text files to manage global operating parameters, port bindings, and security rules.

* **Command:** `show running-config` (or `show config` depending on the platform)
* **Active State Inspection:** Displays the configuration file currently active in the device's volatile memory.
* **File Attributes:** Captures structural metadata—such as file size (e.g., 830 bytes), software version numbers, and management timestamps—along with inline port IP address assignments and subnet masks.
* **Live Adjustments:** Modifications made via the command line update the active configuration immediately, allowing administrators to re-run the command to verify changes.

---

## 6. Infrastructure Address Resolution Logs

Like client operating systems, enterprise switches and routers maintain an internal Address Resolution Protocol cache to resolve logical network addresses to local physical endpoints.

* **Command:** `show arp`
* **Data Fields Returned:** Lists the active layer 3 protocol, destination IP address, hardware MAC address, and the local interface index where the resolution pair was identified.
* **Infrastructure Mapping:** Helps verify whether an upstream device can see and resolve a specific neighbor's physical MAC address.

---

## 7. Logical VLAN Mapping

Switches segregate broadcast domains using Virtual Local Area Networks (VLANs) to group ports logically regardless of their physical location.

* **Command:** `show vlan`
* **VLAN Database Indexing:** Displays a structured table containing all active VLAN IDs, alphanumeric names, status attributes, and their assigned physical switch ports.
* **Default Identification:** Highlights which ports remain in the default VLAN profile and which interfaces have been explicitly assigned to isolated custom VLAN segments.

---

## 8. Power over Ethernet (PoE) Wattage Monitoring

Modern edge switches distribute electrical power alongside data traffic over standard twisted-pair copper cables to run devices like IP phones, cameras, and wireless access points.

* **Command:** `show power`
* **PoE Administrative Fields:** Lists all physical ports, states whether PoE power delivery is enabled or disabled per interface, and displays real-time wattage draw metrics.
* **Capacity Calculations:** Tracks total power delivery capacity to help administrators determine if the switch has enough power remaining to support new devices.

### Power Allocation Calculation Example:

$$\text{Total PoE Power Capacity Pool: } 370\text{ Watts}$$

$$\text{Active Infrastructure Power Draw: } 40\text{ Watts}$$

$$\text{Remaining Available Power Margin: } 330\text{ Watts}$$

*With a 330-watt headroom margin remaining, the switch has sufficient capacity to power additional PoE endpoints without overloading its power supply.*
