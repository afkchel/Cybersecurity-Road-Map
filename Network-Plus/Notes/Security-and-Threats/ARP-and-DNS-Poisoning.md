# Network Spoofing: ARP and DNS Poisoning Mechanics

---

## 1. The Core Concept of Spoofing

Spoofing occurs when a malicious actor or rogue device impersonates another entity on a network. By forging identity markers (such as IP addresses, MAC addresses, email domains, or caller IDs), 
attackers gain unauthorized access to data streams, credentials, and systems. 
Spoofing serves as a foundation for launching **on-path attacks**, where an adversary positions themselves transparently between two communicating nodes to monitor, capture, or alter data in transit.

---

## 2. Address Resolution Protocol (ARP) Poisoning

The Address Resolution Protocol (ARP) maps a known Layer 3 network address (IP) to a physical Layer 2 hardware address (MAC) within a local broadcast domain.

### A. The Standard Verification Flow
Because an IP address is a logical label, a workstation (e.g., `192.168.1.9`) must learn the hardware address of its local gateway router (`192.168.1.1`) before it can forward packets out to the internet.
1. **The Broadcast:** The host sends an in-band broadcast frame asking: *"Who has 192.168.1.1? Tell 192.168.1.9."*
2. **The Reply:** The true router hears the broadcast and replies directly with its physical hardware MAC address.
3. **The Cache:** The workstation saves this mapping into its temporary local **ARP cache** to prevent sending redundant broadcasts for subsequent packets.

### B. The Exploit Mechanism
The underlying structural vulnerability of ARP is that it is entirely **stateless and unauthenticated**. 
Systems will blindly accept and process an incoming ARP reply frame even if they never sent a matching request query.

```text
  [ Victim Host ] (192.168.1.9)
   │  Local ARP Cache State:
   │  192.168.1.1  ──► [ Attacker's MAC Address ]  (POISONED!)
   │
   ▼ All Outbound Internet Traffic
  [ Attacker Machine ] (192.168.1.14) ───► Relays Traffic ───► [ Legitimate Router ] (192.168.1.1)
```

1. **Unsolicited Exploitation:** An attacker at `192.168.1.14` crafts a malicious, unsolicited ARP response and fires it at the victim host.
2. **The Identity Lie:** The packet states: *"I am 192.168.1.1, and my physical location is [Attacker's MAC Address]."*
3. **Cache Overwrite:** The victim's operating system processes the packet and automatically overwrites its genuine gateway map with the attacker's hardware details.
4. **On-Path Position:** From this point forward, every packet the victim attempts to send out to the internet is physically routed straight to the attacker's network adapter.
The attacker logs the data and passes it along to the real gateway so neither the user nor the router realizes an interception is taking place.

---

## 3. Domain Name System (DNS) Poisoning

While ARP handles local hardware mappings, DNS translates human-readable web domains (e.g., `professormesser.com`) into routable public IP addresses. 
DNS poisoning (or cache poisoning) aims to corrupt this translation registry to redirect users to a fraudulent site.

### A. Local Override Priorities
Before an operating system ever transmits a query packet onto the wire to find a DNS server, it checks its internal **hosts file**.
The local hosts file serves as a hardcoded static dictionary that possesses a higher priority ranking than any external network-queried response. 
If a domain mapping is hardcoded there, external DNS responses are ignored.

### B. Vector 1: Server Target Compromise
An attacker hacks directly into a central DNS server and modifies its zone resource records. 
They change the baseline record for a legitimate domain to point to the IP address of an attacker-controlled landing page. 
Every subsequent client that queries that server receives the poisoned record and is funneled directly to a spoofed interface.

### C. Vector 2: On-The-Fly Interception
If the attacker cannot breach the DNS server itself, they can pair DNS poisoning with an on-path position (such as an active ARP poisoning layout).

1. **The Query Race:** The victim client sends a standard UDP name query toward the DNS server.
2. **The On-The-Fly Reply:** The on-path attacker intercepts the query packet in real time and uses their proximity to immediately forge a fake response payload back to the client.
3. **Cache Poisoning:** Because UDP is stateless, if the attacker's malicious response arrives at the client even a fraction of a second *before* the real server's response can cross the circuit,
the client accepts the fake packet, populates its local browser cache with the poisoned IP, and drops the real response when it finally arrives.
