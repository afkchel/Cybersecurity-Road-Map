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
