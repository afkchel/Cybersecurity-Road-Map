# IPv4 Addressing and Configuration

Internet Protocol version 4 (IPv4) is the standard for logical addressing at **OSI Layer 3 (Network Layer)**. It provides the unique identifier necessary for devices to communicate across a network.

---

## 1. The Structure of an IPv4 Address
An IPv4 address is a **32-bit** value, usually represented in **dotted-decimal notation**.

* **Octets:** The address is divided into four groups of 8 bits each (4 octets).
* **Bytes:** Since 8 bits = 1 byte, an IPv4 address is **4 bytes** long.
* **Maximum Value:** The highest decimal value for any single octet is **255** (binary `11111111`).
* **Example:** `192.168.1.165`

## 2. Critical Configuration Components
To communicate on a network, a device typically requires three key pieces of information:

| Component | Purpose |
| :--- | :--- |
| **IP Address** | The unique logical identifier for the device. |
| **Subnet Mask** | Defines which part of the IP is the Network ID and which is the Host ID. Used locally to determine if a destination is on the same subnet. |
| **Default Gateway** | The IP address of the local router. Traffic destined for outside the local subnet is sent here. |

---

## 3. Automated Addressing Methods
### DHCP (Dynamic Host Configuration Protocol)
The modern standard for automated configuration. A server automatically provides the IP, mask, and gateway when a device connects.

### APIPA (Automatic Private IP Addressing)
A "link-local" fallback mechanism used when a DHCP server is unavailable.
* **Range:** `169.254.0.1` to `169.254.255.254`
* **Limitation:** Traffic is **non-routable**; you can talk to local neighbors but cannot access the Internet.
* **Mechanism:** Uses ARP (Address Resolution Protocol) to ensure the chosen address isn't already in use.

---

## 4. Special Address Ranges
* **Loopback Address:** `127.0.0.1` through `127.255.255.254`. Used to test the local IP stack.
* **Reserved Addresses:** `240.0.0.1` through `254.255.255.254` (Class E). Set aside for future use or testing.
* **Virtual IP (VIP):** An address not tied to a physical adapter, often used for virtual machines or internal router references.

---

## 5. Private Addressing (RFC 1918)
Because IPv4 addresses are limited, specific ranges were set aside for internal use. These are **non-routable** on the public internet and require **NAT (Network Address Translation)** to communicate externally.

| Class | Private Range | CIDR | Total Addresses |
| :--- | :--- | :--- | :--- |
| **Class A** | `10.0.0.0` – `10.255.255.255` | `/8` | 16,777,216 |
| **Class B** | `172.16.0.0` – `172.31.255.255` | `/12` | 1,048,576 |
| **Class C** | `192.168.0.0` – `192.168.255.255` | `/16` | 65,536 |

> [!IMPORTANT]
> **RFC 1918** is the standard that defines these private ranges. If you see an address starting with 10.x or 192.168.x, you are looking at an internal private network address.
