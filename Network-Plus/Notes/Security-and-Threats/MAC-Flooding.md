# MAC Address Tables and MAC Flooding 

---

## 1. Foundation: The Media Access Control (MAC) Address

A Media Access Control (MAC) address is the unique 48-bit (6-byte) hardware identifier burned into the Read-Only Memory (ROM) of a Network Interface Card (NIC). 

### Address Architecture
* **Format:** Typically written in hexadecimal notation separated by colons, hyphens, or periods (e.g., `8C:2D:AA:4B:98:A7`).
* **Organizationally Unique Identifier (OUI):** The first 3 bytes define the specific manufacturer of the network adapter.
* **Network Interface Controller Specific Value:** The last 3 bytes act as a unique hardware serial number assigned by the manufacturer.

---

## 2. The Dynamic Switching Learning Process

Switches use MAC addresses to make intelligent, targeted forwarding decisions, ensuring that traffic moves only between talking endpoints rather than being shouted to the entire network.

```text
Sam (1000:1111:1111) ───[Sends Frame to Server]───► [ Port F0/1 ] Switch
                                                            │
                                                     Dynamic Learning:
                                           ┌────────────────────────────────┐
                                           │  MAC Table:                    │
                                           │  1000:1111:1111  ──► Port F0/1 │
                                           └────────────────────────────────┘
```

1. **Inbound Examination:** When a frame enters an interface, the switch inspects its **Source MAC Address**.
2. **Table Population:** If the source MAC is missing from its internal MAC address table, the switch creates a map matching that MAC address to the physical incoming interface.
3. **Directed Forwarding:** When a subsequent frame arrives, the switch looks up its **Destination MAC Address** in the table:
    - **Known Destination:** The switch forwards the frame *only* out of the corresponding mapped port. Devices on other ports never receive this traffic.
    - **Unknown Destination (Unicast Flooding):** If the destination address is missing from the table, the switch copies and sends the frame out of **every active interface** (except the source port) to guarantee it reaches its target.
4. **Cache Aging (Timeout):** MAC table maps are temporary. To keep the database accurate as devices move, entries automatically age out and are deleted after a typical idle threshold of **five minutes (300 seconds)**.

---

## 4. Weaponization: The MAC Flooding Attack

The underlying intelligence of a switch relies entirely on its ability to maintain an accurate MAC address table. However, this table has a **finite storage capacity** hardcoded into the switch hardware specification.

### The Attack Mechanism
An attacker uses an automated attack tool to blast thousands of malicious, entirely randomized source MAC addresses into a single switch port.

```text
  [ Attacker ] ══════ (Floods Millions of Fake Source MACs) ══════► [ Port F0/4 ] Switch
                                                                          │
                                                                   MAC Table State:
                                                                ┌────────────────────┐
                                                                │ [FAKE MAC 1]  F0/4  │
                                                                │ [FAKE MAC 2]  F0/4  │
                                                                │ [CAM Table Full!]  │
                                                                └─────────┬──────────┘
                                                                          │
                                                                          ▼
                                                                Switch Drops to "Hub Mode"
                                                                (Floods ALL traffic to ALL ports)
```

1. **Table Exhaustion:** The switch processes these incoming fake frames and fills all available memory storage slots with fake MAC address maps.
2. **Degradation to Hub Mode:** Once the MAC table is completely saturated, legitimate new host maps cannot be saved.
3. **Universal Unicast Flooding:** Because the switch cannot find genuine destination MAC addresses in its full table, it must revert to its fallback behavior: it treats *every single packet* as an unknown destination and floods all traffic out of **every active port**.

### The Exploit Objective
By crashing the switch's intelligent forwarding engine, the network fabric drops back into an inefficient, insecure "hub" operational state. The attacker can now run a packet sniffer to easily capture private data streams crossing the switch, even if that traffic was never originally addressed to their machine.

---

## 5. Defense: Implementing Port Security

Modern enterprise switches feature dedicated Layer 2 protection capabilities to neutralize volume-based address flooding.

* **Port Security:** An administrative configuration that limits the number of unique hardware addresses a switch interface is permitted to dynamically learn.
* **Baseline Enforcement:** By setting a strict upper threshold (e.g., allowing a maximum of 2 or 3 distinct MAC addresses on an employee desktop interface), the switch will immediately drop additional fake frames and block the flooding tool from overwhelming the shared CAM memory pool.
