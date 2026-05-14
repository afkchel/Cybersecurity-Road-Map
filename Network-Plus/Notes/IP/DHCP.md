# DHCP and Automatic IP Addressing

---

## 1. Evolution of Automatic Addressing

Historically, IPv4 settings such as IP addresses, subnet masks, and DNS settings had to be configured manually on every device. To scale this, automated protocols were developed:

* **BOOTP (Bootstrap Protocol):** The original protocol for automatic configuration, which lacked the ability to recognize when an IP address was no longer in use.
* **DHCP (Dynamic Host Configuration Protocol):** The modern enhancement of BOOTP that provides automatic address configuration and manages the availability of IP addresses as devices join or leave the network.

---

## 2. The DORA Process

DHCP follows a standardized four-step sequence to assign an IP address to a client:

* **Discover (D):** The client sends a broadcast packet (`255.255.255.255`) from source `0.0.0.0` to find available DHCP servers.
* **Offer (O):** The DHCP server responds with an offered IP address configuration.
* **Request (R):** The client requests the specific IP address offered by the server.
* **Acknowledgment (A):** The server confirms the configuration, and the client begins using the address.

---

## 3. Technical Specifications

DHCP operations rely on the User Datagram Protocol (UDP) and specific port assignments:

* **Client Port:** UDP 68.
* **Server Port:** UDP 67.
* **Traffic Type:** Communication typically starts as a broadcast to ensure reachability on the local subnet since the client does not yet have an IP address.

---

## 4. DHCP Across Subnets (Relay/Helper)

Because routers do not transmit broadcast frames, a client cannot normally reach a DHCP server located on a different subnet.

* **DHCP Helper / DHCP Relay:** A router functionality that allows DHCP traffic to traverse subnets.
* **Mechanism:**
  - The router receives a local broadcast "Discover" message from a client.
  - The router converts the broadcast into a **Unicast** communication directed to the specific IP of the remote DHCP server.
  - The response from the server is sent back to the router via unicast, and the router relays it back to the client as a local broadcast.

* **Benefit:** This allows organizations to centralize DHCP servers and distribute them for redundancy across the enterprise.

# DHCP Server Configuration and Management

---

## 1. DHCP Scopes and Pools

A DHCP server manages IP addresses through defined logical groupings.

* **DHCP Scope:** A specific range or "pool" of IP addresses defined for a particular subnet.
* **Contiguous Pools:** Typically, an administrator defines a starting and ending address (e.g., .1 through .100) to be handed out.
* **Scope Settings:** In addition to the IP range, a scope includes:
  - Subnet masks.
  - Exclusions (addresses within the range that should not be assigned).
  - Lease durations.
  - Default gateways and DNS server addresses.

---

## 2. Address Reservations

For devices that must maintain a consistent IP address (like printers or servers), manual configuration is often replaced by **Address Reservations**.

* **Mechanism:** The administrator creates a table in the DHCP server pairing a device's **MAC address** with a specific **IP address**.
* **Benefits:**
  - Provides "Static DHCP" or "IP Reservations" without having to visit each physical device.
  - Allows central management of all fixed IP addresses in one interface.

* **Scalability:** Changes to settings (like a new DNS server) can be updated in the DHCP server once, rather than manually on every static device.

---

## 3. The DHCP Lease Process

DHCP addresses are not permanent; they are "leased" for a specific time frame determined by the administrator.

* **Dynamic Reassignment:** If a device leaves the network and its lease expires, the address returns to the pool for use by other devices.
* **MAC Tracking:** DHCP servers often "remember" MAC addresses. If a device returns and its previous IP is still available, the server will preferentially assign the same address.
* **Lease Release:** When a system is properly turned off, it can "release" the IP back to the pool immediately.

---

## 4. Lease Timers (T1 and T2)

Clients do not wait for the entire lease to expire before attempting to stay on the network.

* **T1 Timer (Renewal):**
* Triggers at **50%** of the lease duration.
* The client attempts to communicate with the **original** DHCP server to renew the lease.


* **T2 Timer (Rebinding):**
* Triggers at **87.5% (7/8)** of the lease duration.
* If the original server is unavailable, the client attempts to renew with **any available** DHCP server on the network.

---

## 5. DHCP Options

DHCP can deliver much more than just basic IP and gateway information through specialized fields.

* **Function:** Separate fields used to configure specific TCP/IP settings.
* **Capacity:** There are 254 usable, numbered options available.
* **Common Examples:**
  - **Option 129:** Voice Over IP (VoIP) Call Server IP.
  - **Option 135:** HTTP Proxy settings.

* **Compatibility:** Not all DHCP servers support every option; administrators must verify that their specific server software can distribute the required numbered option.
