# 🔬 Lab: Analyzing and Verifying the DHCP DORA Process

This project documents the live capture, analysis, and verification of the Dynamic Host Configuration Protocol (DHCP) four-step **DORA** transaction sequence using Wireshark.

---

## 1. Executive Summary

This lab demonstrates how a workstation dynamically obtains an IP address. 
By clearing active leases and capturing network traffic,
this lab provides clear packet-level proof of how an address is requested, offered, and assigned within a local network.

---

## 2. Network Topology & Addressing Schema

### A. Topology

```text
  ┌────────────────────────┐                    ┌────────────────────────┐
  │     Client Host        │                    │      DHCP Server       │
  │ MAC: 74:56:3c:d8:9d:d2 │◄─── Switched ─────►│  MAC: 04:67:61:cf:cd:c8│
  │  IP: 192.168.31.154    │        Link        │  IP:  192.168.31.1     │
  └────────────────────────┘                    └────────────────────────┘

```

### B. Forcing a Fresh DHCP Sequence

By default, computers remember their old settings and take a shortcut to renew them. To capture the full **DORA** sequence, we use two Windows commands to force the computer to start from scratch:

```cmd
:: 1. Disconnect: Drop the current IP and reset to 0.0.0.0
ipconfig /release

:: 2. Reconnect: Force a brand-new DORA broadcast sequence
ipconfig /renew

```

#### What These Commands Do:

1. **`ipconfig /release`** This tells the computer to give up its current IP address (`192.168.31.154`) and send a **Release** packet to the router. The computer's IP drops to `0.0.0.0`, completely disconnecting it from the network.
2. **`ipconfig /renew`** With the computer's network identity wiped, this command forces it to find a router from scratch. It wakes up the network card and instantly triggers the **DORA** process to pull down a fresh network configuration.

---

## 3. Captured Traffic & Empirical Analysis

The packet capture shows every step the computer and router take to negotiate and finalize the IP address lease.

<img width="875" height="143" alt="image" src="https://github.com/user-attachments/assets/17f65fe6-7181-4149-9f16-f05adab01c4d" />


---

### Packet-by-Packet Analysis

#### 0. The Lease Release (Packet #951)

* **What's happening:** The computer tells the router it is giving up its current IP address.
* **Details:** Sent as a direct unicast packet from `192.168.31.154` to the gateway (`192.168.31.1`). This clears out the old settings so the computer is completely unconfigured, forcing a brand-new DORA sequence instead of a quick renewal.

#### 1. D - DHCP Discover (Packet #1045)

* **What's happening:** The computer shouts out into the network to find a DHCP server.
* **Details:** Since the computer doesn't have an IP address yet, it uses `0.0.0.0` as the source and sends a broadcast packet to `255.255.255.255` on UDP port 67.
* **Tracking ID:** It creates a unique **Transaction ID (`0x120661d1`)** so it can tell which responses belong to this specific request.

<img width="1098" height="275" alt="image" src="https://github.com/user-attachments/assets/fe70ed58-d93d-4604-b99c-c078c8dda22e" />

#### 2. O - DHCP Offer (Packet #1107)

* **What's happening:** The router hears the request and offers an IP address.
* **Details:** The router (`192.168.31.1`) looks at the transaction ID and sends a packet back to the client, proposing `192.168.31.154` as its new IP address. This packet also includes basic subnet rules and lease times.

<img width="1002" height="726" alt="image" src="https://github.com/user-attachments/assets/73ac3dbb-b547-4e40-a54c-4bc7005a9650" />


#### 3. R - DHCP Request (Packet #1108)

* **What's happening:** The computer says, "Yes, I'll take that IP address."
* **Details:** Even though it picked an address, the computer still doesn't officially own it yet, so it keeps its source as `0.0.0.0` and sends another broadcast to `255.255.255.255`. Broadcasting this step lets the main router know its offer was accepted, while telling any other DHCP servers on the network that they can release their offers.

<img width="1131" height="141" alt="image" src="https://github.com/user-attachments/assets/17057c05-7287-4591-b09a-16c318184769" />

#### 4. A - DHCP Acknowledgment (Packet #1109)

* **What's happening:** The router finalizes the deal and confirms the settings.
* **Details:** The router sends a final confirmation to `192.168.31.154`. This packet contains the actual network configuration settings the computer needs to work—like the subnet mask, default gateway, and DNS servers. The computer applies these settings and is now fully connected.

<img width="1105" height="657" alt="image" src="https://github.com/user-attachments/assets/101fd618-9643-46f9-a32c-6384090577df" />

---

## 4. Conclusion

By tracking the Transaction ID `0x120661d1` from start to finish, this lab provides clear, raw proof of how DHCP operates. The packet capture proves that even when a computer has no IP identity at all, it can use local broadcast packets to safely find a server and pull down its network settings.
