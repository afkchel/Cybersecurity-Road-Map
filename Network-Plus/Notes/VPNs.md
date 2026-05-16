# Virtual Private Networks (VPNs) Architecture and Routing

The implementation types, client configurations, and traffic routing mechanisms for Virtual Private Network (VPN) environments.

---

## 1. The VPN Concentrator
A VPN acts as an encryption/decryption engine designed to aggregate and secure incoming network connections over public infrastructure.

* **Functionality:** It encrypts cleartext data prior to transit across an untrusted network (e.g., the Internet) and decrypts the incoming cryptographic payloads at the destination.
* **Deployment Options:**
    - **Hardware-Based:** Specialized appliances built into or deployed alongside modern firewall infrastructures to leverage dedicated cryptographic processing power.
    - **Software-Based:** Service applications deployed directly onto an existing server instance.

---

## 2. VPN Implementation Models
Organizations use different architecture frameworks based on deployment scale and endpoint locations.

* **Client-to-Site VPN (Remote Access):**
    - Connects an individual mobile endpoint back to a centralized corporate network.
    - Requires endpoint software initialization, either manually handled by the user or dynamically triggered via an **Always-On** policy on system startup.
* **Site-to-Site VPN:**
    - Connects entire physical infrastructures together securely (e.g., establishing a persistent bridge between a branch office and headquarters).
    - Typically executed at the firewall level on both perimeters as an unyielding, persistent connection.
    - Transmissions between endpoints occur completely transparently to internal network hosts.
* **Clientless VPN:**
    - Provides individual user-to-site tunnels without requiring dedicated workstation endpoint clients.
    - Natively functions inside modern browsers utilizing **HTML5** and its integrated **Web Cryptography API** via standard HTTPS.

---

## 3. Tunneling and Traffic Routing Policies
Network administrators control routing performance and corporate resource security through specific logical boundary definitions.

### A. Full Tunneling
All outbound traffic originating from the client machine is encapsulated and forced directly through the secure VPN link.

* **Mechanism:** Even public, non-corporate traffic (e.g., generic web browsing) is forwarded to the enterprise concentrator, decrypted, and then sent out through the corporate internet perimeter.
* **Pros:** Enforces maximum corporate security policy control over all traffic vectors.
* **Cons:** Consumes significant corporate internet bandwidth and increases performance overhead due to hair-pinning routes.

### B. Split Tunneling
Outbound traffic is systematically divided at the client endpoint based on the destination network segment.

* **Mechanism:** - Traffic destined for corporate applications is routed directly through the encrypted VPN tunnel to the concentrator.
    - Public third-party traffic (e.g., generic cloud services, video streaming) completely bypasses the tunnel and exits directly out of the user's local internet path.
* **Pros:** Conserves corporate network bandwidth, eliminates latency overhead on non-work traffic, and increases localized browser pathing efficiencies.
* **Cons:** Exposes the remote host to untrusted public networks while simultaneously maintaining an open tunnel into the core corporate infrastructure.

---

## 4. Redundancy Architecture Comparison

| Feature | Full Tunneling | Split Tunneling | Clientless (HTML5) |
| :--- | :--- | :--- | :--- |
| **Corporate Bandwidth Impact** | High (All traffic routed through HQ) | Low (Only enterprise traffic routed through HQ) | Low (Scoped to specific web portals) |
| **Client Software Requirement** | Dedicated Local Client App | Dedicated Local Client App | Standard Web Browser Only |
| **Security Control Scope** | Universal across host machine | Scoped strictly to corporate traffic | Scoped strictly to the browser session |
| **Primary Deployment Use Case** | Highly regulated industries | Distributed standard workspaces | Temporary or third-party contractor access |
