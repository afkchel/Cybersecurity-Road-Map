# IPv6, SLAAC and NDP

Notes on the mechanisms IPv6 uses for automatic addressing and network communication.

---

## 1. Stateless Address Autoconfiguration (SLAAC)

In IPv6, a device can assign itself a routable IP address without the need for a central DHCP server.

* **Definition:** A process where a device creates its own unique IPv6 address to communicate on the network.
* **Benefits:**
  - No DHCP server management is required.
  - No manual tracking of IP or MAC addresses.
  - No lease times or expirations to monitor.

---

## 2. Neighbor Discovery Protocol (NDP)

NDP is a foundational IPv6 protocol that replaces the Address Resolution Protocol (ARP) used in IPv4.

* **Multicast vs. Broadcast:** Unlike ARP, which uses broadcasts, NDP uses multicast to find other devices, making communication significantly more efficient and less disruptive to the network.
* **Key Functions:**
  - Finding other devices on the local network.
  - Identifying local routers.
  - Detecting duplicate addresses.

---

## 3. Router Identification Features

NDP allows workstations to find their local gateways and learn about the network environment through two primary message types:

* **Router Solicitation (RS):**
  - The workstation sends a multicast message asking if any routers are present on the local subnet.
  - 
* **Router Advertisement (RA):**
  - Routers respond to RS messages with a direct advertisement.
  - Routers can also send **unsolicited RAs** periodically to all devices.
  - **Information Provided:** RAs contain the 64-bit prefix, prefix length, DNS settings, and other configuration parameters.

---

## 4. The SLAAC Address Creation Process

To generate a complete 128-bit routable address, an IPv6 device follows these steps:

* **Step 1: Determine the Subnet:**
  - The device uses NDP (Router Solicitation) to ask for the 64-bit IPv6 subnet prefix from a local router.


* **Step 2: Generate the Interface ID:**
  - The device creates the remaining 64 bits (the Interface ID) using one of two methods:
    1. **Modified EUI-64:** Taking the MAC address and inserting `ff:fe` in the middle.
    2. **Randomization:** Generating a random 64-bit value for privacy.

* **Step 3: Duplicate Address Detection (DAD):**
  - Before using the address, the device uses NDP to check the rest of the network to ensure no other station is already using that specific address.
  - 
---

## 5. Comparison Summary

| Feature | IPv4 | IPv6 |
| --- | --- | --- |
| **Address Resolution** | ARP (Broadcast) | NDP (Multicast) |
| **Self-Configuration** | APIPA (Non-routable) | SLAAC (Routable) |
| **Conflict Check** | Gratuitous ARP | DAD (Duplicate Address Detection) |
| **Router Discovery** | Manual or DHCP | NDP (Solicitation/Advertisement) |
