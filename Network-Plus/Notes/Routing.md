# Routing

## 1. Routing Fundamentals
A router's primary responsibility is to forward traffic between different IP subnets. This process involves several key steps:

*   **Identification**: The router identifies the destination IP address for all incoming packets.
*   **Table Examination**: It examines its routing table to determine the "best route" for that packet.
*   **Direct Delivery**: If the destination is on a subnet directly connected to the router, it sends the packet directly to that local subnet.
*   **Next Hop**: If the destination is remote, the router identifies the **Next Hop** (the IP address of the next router in line) and forwards the traffic out the corresponding interface.

> **Note**: If a router cannot find a matching entry or a "next hop" for a destination IP in its table, the traffic is discarded.

---

## 2. Directly Connected vs. Remote Routes
Routers automatically recognize subnets that are physically connected to their interfaces.

*   **Directly Connected**: These routes are added to the routing table automatically as soon as an interface is configured with an IP and brought online.
*   **Remote Routes**: Routers have no inherent knowledge of networks "behind" other routers. These must be added either manually (Static) or automatically (Dynamic).

---

## 3. Static Routing
**Static Routing** is the manual configuration of routes by a network administrator. 

### Advantages:
*   **Low Overhead**: Unlike dynamic protocols, static routes do not consume CPU cycles or memory for background processing.
*   **Simplicity for Small Networks**: It is a quick and effective way to manage routing for simple environments.
*   **Ideal for Stub Networks**: Perfect for remote sites (stub networks) that only have a single connection to the rest of the network or internet.
*   **Security**: Since there are no dynamic routing updates being sent or received, it is considered more secure.

### Disadvantages:
*   **Scalability**: Manually configuring routes in hundreds or thousands of routers is time-consuming and prone to human error.
*   **No Redundancy**: Static routes do not automatically reroute traffic if a link goes down; changes must be made manually.
*   **Management**: Any change to the physical network topology requires the administrator to log into every affected router to update the tables.

---

## 4. Configuration Logic
To configure a static route, an administrator must provide the destination network, the subnet mask, and the address of the next router.

**Example Command Logic:**
If an administrator wants Router 1 to reach the `10.10.20.0/24` network by sending it to Router 2 (IP `10.10.40.2`), the logic is:
> *"If destination matches `10.10.20.0/24`, then send to next hop `10.10.40.2`."*

Once this is configured, the router no longer discards that traffic and successfully forwards it to the next router for delivery.

# Dynamic Routing

## 1. Overview of Dynamic Routing
Dynamic routing allows routers to automatically discover network paths and update their routing tables without manual intervention from a network administrator. Unlike static routing, which requires manual configuration for every route, dynamic routing protocols handle the discovery and maintenance of routes in real-time.

### Key Benefits:
*   **Automation**: Routers automatically identify new routes when a device is added and remove routes when a device goes offline.
*   **Scalability**: Significantly easier to manage in large environments with tens or hundreds of routers compared to static routing.
*   **Real-time Updates**: Changes to the network infrastructure are shared across all routers automatically.

### Trade-offs:
*   **Overhead**: Requires additional CPU and memory resources on the router to process updates and calculate paths.
*   **Initial Complexity**: Requires initial planning and configuration of the specific protocol used.

---

## 2. How Dynamic Routing Works
Routers use a specialized process to maintain an accurate map of the network:
1.  **Listening**: Routers listen for routing updates on the local subnet sent by other routers, often via multicast.
2.  **Informing**: Routers send their own updates to nearby neighbors to share the routes they currently know.
3.  **Interpreting**: Upon receiving an update, a router determines if the new information provides a better or secondary path based on the protocol’s specific criteria.
4.  **Convergence**: When the network changes, routers inform all other routers to ensure the entire network has a synchronized view of the infrastructure.

---

## 3. Common Dynamic Routing Protocols

### EIGRP (Enhanced Interior Gateway Routing Protocol)
*   **Type**: Often considered a hybrid or advanced distance-vector protocol.
*   **Cisco-Centric**: Originally proprietary to Cisco; most commonly found in Cisco-based environments.
*   **Performance**: Features fast convergence (the speed at which it reacts to changes) and built-in loop prevention.
*   **Efficiency**: Sends updates with minimal network traffic to preserve bandwidth.

### OSPF (Open Shortest Path First)
*   **Type**: Link-state protocol.
*   **Standardization**: An open, non-proprietary standard used across many different hardware manufacturers.
*   **Cost-Based**: Determines the best route based on the "cost" of a link, which is typically associated with throughput (speed) and link availability.
*   **Autonomous Systems (AS)**: Typically used within a single organization's network where they have complete control over the infrastructure.

### BGP (Border Gateway Protocol)
*   **Type**: External Gateway Protocol / Path-vector.
*   **Scope**: The protocol used to connect different autonomous systems together; it is the fundamental routing protocol of the internet.
*   **Design**: Specifically designed to handle the massive task of dynamically updating routes across the entire global internet.
*   **External Routing**: Used when an organization needs to route traffic to external sites or between different internet service providers.

---

## 4. Comparison Summary

| Protocol | Scope | Best Suited For | Selection Criteria |
| :--- | :--- | :--- | :--- |
| **EIGRP** | Internal (IGP) | Cisco-heavy enterprise networks | Feasible distance and metrics |
| **OSPF** | Internal (IGP) | Multi-vendor enterprise networks | Link speed and availability (Cost) |
| **BGP** | External (EGP) | Connecting to the internet or other organizations | Path attributes and policies |

# Routing Technologies

## 1. Routing Table
A router's primary job is to evaluate incoming traffic, determine the destination, and forward it to the appropriate interface based on its knowledge of the network. To make these decisions, routers—as well as workstations and servers—maintain a **routing table**.

*   **Destination Subnet**: The IP range the packet is trying to reach.
*   **Next Hop**: The IP address of the next router in the path toward the destination.
*   **Outgoing Interface**: The physical or virtual port the router uses to send the traffic.
*   **Directly Connected**: If a subnet is physically attached to a router, it is automatically added to the table with a code (usually "C").

---

## 2. Route Selection (Tie-Breaking)
When a router has multiple paths to the same destination, it follows a specific hierarchy to choose the best route:

### I. Longest Prefix Match (Specificity)
The router first compares the destination IP to the subnet IDs and prefix lengths in the table. The **most specific route** (the one with the longest prefix length, such as `/32` over `/24`) is always preferred.

### II. Administrative Distance (AD)
If multiple routes have the same prefix length but come from different sources, the router uses **Administrative Distance** to rate the trustworthiness of the source. A lower AD is preferred.

| Source | Administrative Distance (Cisco) |
| :--- | :--- |
| **Connected Interface** | 0 |
| **Static Route** | 1 |
| **EIGRP** | 90 |
| **OSPF** | 110 |
| **RIP** | 120 |
| **DHCP Default Route** | 254 |
| **Unknown** | 255 |

### III. Routing Metrics
If the same protocol provides multiple paths to the same location, it uses a **Metric** to break the tie. Metrics are internal values specific to a protocol (e.g., RIP uses "hop count") and cannot be compared across different protocols.

---

## 3. High Availability and Virtualization
Modern networks use virtualization to provide redundancy.

*   **FHRP (First Hop Redundancy Protocol)**: Provides a **Virtual IP (VIP)** address shared between an active and standby router. If the active router fails, the standby router takes over the VIP seamlessly so end users don't lose their default gateway.
*   **Subinterfaces**: A single physical interface separated into multiple virtual interfaces. This allows a single "trunk" cable to handle multiple VLANs, each with its own IP address and routing table entries.
