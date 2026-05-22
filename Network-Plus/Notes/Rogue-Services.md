# Rogue Infrastructure Services and On-Path Network Attacks

---

## 1. Rogue Dynamic Host Configuration Protocol (DHCP) Servers

The Dynamic Host Configuration Protocol (DHCP) automatically assigns IP addresses, subnet masks, default gateways, and DNS server parameters to endpoints joining a network.

### The Vulnerability
The legacy DHCP standard operates completely without built-in security features. 
A client workstation simply broadcasts a request onto the local network segment, and its operating system will process the **first response that returns**, regardless of its origin.

```text
  [ Client Workspace ] ────── (DHCP Broadcast Request) ──────┐
         │                                                   │
         ▼ (Races a response back to the client)             ▼
  [ Rogue DHCP Server ]                                [ Legitimate DHCP Server ]
  "Use IP 192.168.1.50"                                "Use IP 10.0.0.14"
  "Use Gateway [Attacker's IP]" (POISONED!)
```

### The Security Impact
An unauthorized or misconfigured rogue DHCP server can drop malicious or incorrect parameters into local host configurations:
* **Network Exhaustion / DoS:** Handing out IP schemes that match existing resources, creating IP address duplication conflicts, or assigning unroutable gateways that completely break internet connectivity.
* **On-Path Redirection:** Setting the rogue server's own IP address as the default gateway. This routes all outbound user traffic directly through the attacker's machine before it reaches the real router.

### Enforcement Defenses
* **DHCP Snooping:** A Layer 2 switch feature that monitors inbound DHCP traffic. Administrators explicitly flag switch interfaces as either **trusted** (connected to legitimate corporate DHCP servers)
or **untrusted** (user-facing access ports). If a DHCP server response frame attempts to enter an untrusted access port, the switch drops the packet and blocks the rogue server.
* **Active Directory Authorization:** Enterprise directory service engines can validate a DHCP server's authorization status against a central directory,
forcing unauthorized instances to shut down their assignment pools.
* **Remediation Strategy:** If a rogue DHCP server compromises a segment,
you must physically or logically disconnect the rogue hardware from the switch fabric, and then execute a network-wide IP lease renewal sequence (`ipconfig /renew`) across all affected clients.

---

## 2. Rogue Access Points and Wireless Evil Twins

Wireless entry extensions introduce unique security challenges because radio frequencies expand corporate perimeters beyond physical facility walls.

### A. Rogue Access Points (APs)
* **The Mechanism:** An employee plugs a cheap retail wireless router or access point into an open Ethernet wall jack to expand corporate Wi-Fi coverage or use a personal device. 
* **The Threat:** Even if installed without malicious intent, this sets up a rogue access point that bypasses corporate perimeter defenses and access controls. If the personal AP uses weak or no security settings, anyone in physical proximity can slip onto the private corporate network.
* **Software Rogue APs:** Modern operating systems include internet connection sharing features that allow an insider to turn their workstation's
wireless card into a software-driven access point, projecting an unmonitored wireless footprint.
* **Enforcement Defenses:**
    - **802.1X / Network Access Control (NAC):** Implementing 802.1X forces switches to demand rigorous device or user authentication *before* opening a port to pass traffic. If an unauthorized rogue AP is plugged in, the port remains locked.
    - **Wireless Site Audits:** Regularly scanning the corporate airwaves using a wireless analyzer to identify unknown radio frequency signatures.

### B. The Wireless Evil Twin Attack
An **Evil Twin** is an explicit, weaponized rogue access point configured by an attacker to impersonate an authentic local hotspot.

```text
  [ Legitimate AP ] (SSID: "Coffee_Shop" | Signal: Low)
  
  [ Wireless Victim ] ─── (Connects to Strongest Signal) ───► [ Wireless Evil Twin ]
                                                               (SSID: "Coffee_Shop" | Signal: MAX)
                                                               (Captures cleartext logs)
```

* **Impersonation:** The attacker sets up a hotspot with the exact same SSID (network name), security configuration profiles, and web captive portals as a trusted network (such as a corporate campus or public shop Wi-Fi).
* **Signal Overpowering:** The attacker increases the transmission power of their radio antennas.
Because client devices naturally lock onto the strongest available signal for a given SSID, nearby workstations drop their connections to the real network and automatically associate with the evil twin.

---

## 3. The On-Path Network Attack Profile

Rogue DHCP servers and wireless evil twins are common methods used to establish an **On-Path Attack** (historically called a *Man-in-the-Middle* attack).

```text
┌──────────────┐               ┌──────────────────┐               ┌──────────────┐
│  Client Host │ ─────────────►│ Attacker Node    ├──────────────►│ Target Site  │
│              │◄──────────────┤ (On-Path Layer)  │◄──────────────┤              │
└──────────────┘               └──────────────────┘               └──────────────┘
                                • Reads Private Data
                                • Modifies Payloads
```

* **The Trap:** The attacker positions themselves directly in the middle of a live communication stream. They receive data from a source node, inspect or alter the payload contents, and then pass the traffic along to the legitimate destination.
* **Transparency:** Both communicating endpoints believe they are talking directly to each other, completely unaware that an intermediary is controlling the connection path.
* **Associated On-Path Vectors:** - ARP Poisoning
    - Session Hijacking
    - DNS Poisoning
    - HTTPS Spoofing
    - Wi-Fi Eavesdropping

### The Ultimate Mitigation: Cryptographic Encrypted Payloads
While network-level controls like DHCP snooping and 802.1X protect local corporate infrastructure, the most effective defense against on-path data collection across untrusted public networks is **end-to-end encryption**.

By forcing all traffic through an active **Virtual Private Network (VPN)** and requiring strict **HTTPS** transport layer security across web sessions,
the payload data is scrambled before it ever hits the wire. Even if a user connects to an evil twin or a rogue router, the on-path interceptor only captures unreadable encrypted blocks, keeping credentials and private sessions secure.
