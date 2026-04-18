# Networking Functions


---

### CDN (Content Delivery Network)
*   **Function:** A distributed network of servers designed to provide data efficiently from a geographically close point.
*   **Essentially:** **Caching and Speed.** 
*   **How it works:** If you are in North America, you access a North American CDN server instead of a centralized server in Europe. This significantly reduces latency.

---

### VPN (Virtual Private Network)
*   **Function:** Creates a secure, encrypted tunnel over an insecure(public) network.
*   **VPN Concentrator:** An access device or firewall function designed for high-speed encryption/decryption for many users simultaneously.
---

### QoS (Quality of Service)
*   **Function:** Prioritizes specific applications or traffic types over others to ensure performance.
*   **Essentially:** **Traffic Shaping.**
*   **Mechanism:** Network admins can give high priority to real-time traffic (Voice/VoIP, Video) and lower priority to non-critical data (File transfers).
*   **Managed via:** Firewalls, Routers, Switches, and Qos devices.

---

### ⏳ TTL (Time to Live)

TTL acts as a "timer" or "safety switch" to prevent data from circulating indefinitely. Its definition changes based on the protocol:

#### 1. TTL in IP (Layer 3)
- **Measured in:** **Hops**.
- **Purpose:** **Loop Prevention.**
- **How it works:** Each router the packet passes through decreases the TTL by **1**. When TTL hits **0**, the packet is discarded.
- **Default values:** 
  - **Linux/MacOS:** 64 hops.
  - **Windows:** 128 hops.

  ### 🔬 Wireshark 

  As shown in the packet capture below, the **Time to Live (TTL)** field is an integral part of the **Internet Protocol version 4(IPv4)** header, confirming it operates at **Layer 3 (Network Layer)**.

  <img width="1113" height="372" alt="image" src="https://github.com/user-attachments/assets/29c4d44d-c994-42b8-9b50-85794abad341" />

  **Observations from the Capture:**
  *   **TTL Value:** 128 (This suggests the packet hasn't passed through any routers yet, because it is the default value for Windows).


    
- **Troubleshooting:** Routing loops can be identified using `tracert` (Trace Route).

#### 2. TTL in DNS
- **Measured in:** **Seconds**.
- **Purpose:** **Cache Management.**
- **How it works:** It tells your local machine how many seconds to keep a DNS record in its cache before asking the DNS server for an update.
- **Example:** A TTL of `300` means your PC "remembers" the IP for 5 minutes.

---

### Summary Table


|  | Protocol | Unit of Measure | Primary Goal |
| :--- | :--- | :--- | :--- |
| **CDN** | HTTP/HTTPS | Distance/Location | Reduce Latency |
| **VPN** | Multiple | Encryption | Secure Remote Access |
| **QoS** | Multiple | Priority Levels | Manage Bandwidth |
| **TTL** | IP | **Hops** | Stop Routing Loops |
| **TTL**| DNS | **Seconds** | Control Caching |
