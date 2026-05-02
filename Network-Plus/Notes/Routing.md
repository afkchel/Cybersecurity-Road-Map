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
