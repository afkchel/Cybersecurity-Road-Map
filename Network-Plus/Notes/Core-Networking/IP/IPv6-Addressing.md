# IPv6 Addressing

## 1. The Necessity of IPv6
The transition from IPv4 to IPv6 is driven by the exhaustion of the IPv4 address space. 
While IPv4 supports approximately 4.29 billion addresses, current estimates suggest there are over 20 billion connected devices. 

*   **Address Limit**: We have hit the limit for available IPv4 addresses.
*   **NAT Constraints**: While Network Address Translation (NAT) has extended the life of IPv4, certain applications prefer to avoid it, and it adds complexity to network communication.
*   **Massive Space**: IPv6 provides a 128-bit address space, allowing for a virtually unlimited number of unique addresses.

---

## 2. IPv6 Address Structure
An IPv6 address is 128 bits in length, significantly larger than the 32-bit IPv4 address.

*   **Format**: Addresses are written in hexadecimal values and separated by colons (e.g., `fe80::5d18:652:6ffd:8f52`).
*   **Sections**: An address consists of eight 16-bit sections.
*   **Size**: Each section is two bytes (two octets) in length, totaling 16 bytes for the entire address.



---

## 3. Compression Rules
To make 128-bit addresses easier to read and write, two primary compression rules are applied:

*   **Leading Zeros**: You can remove leading zeros from any group within the address.
*   **Double Colons (::)**: One or more contiguous groups of all-zero sections can be replaced with a single double colon. This can only be done **once** per address to avoid ambiguity.

### Compression Example:
*   **Original**: `2601:04C3:4002:BE00:0000:0000:0000:0066`
*   **Remove Leading Zeros**: `2601:4C3:4002:BE00:0:0:0:66`
*   **Apply Double Colon**: `2601:4C3:4002:BE00::66`

---

## 4. Migration and Compatibility Technologies
Because IPv4 and IPv6 cannot communicate directly, several "stopgap" measures are used to bridge the gap during the long-term transition to a pure IPv6 environment.

| Technology | Description | Use Case |
| :--- | :--- | :--- |
| **Dual-Stack** | Running IPv4 and IPv6 simultaneously on the same interface. | Most common modern method; applications choose the protocol they prefer. |
| **Tunneling** | Encapsulating one protocol inside the other (e.g., 6to4 or 4in6). | Used to send traffic across a network that doesn't support the native protocol. |
| **NAT64** | A specialized router translates between IPv6 and IPv4 addresses. | Allows IPv6-only clients to communicate with IPv4-only servers. |
| **DNS64** | Works with NAT64 to synthesize IPv6 addresses from IPv4 DNS records. | Essential for redirecting clients to the NAT64 translation router. |



---

## 5. Tunneling Protocols (Legacy)
*   **6to4 Addressing**: Sends IPv6 traffic over IPv4 networks but does not support NAT and requires specialized relay routers. It is no longer common and has been removed from modern Windows versions.
*   **4in6 Tunneling**: Sends IPv4 traffic across an existing IPv6 network. Like 6to4, this is now unusual in modern enterprise environments.
