# Spanning Tree Protocol (STP) 

## 1. The Problem: Layer 2 Loops
When multiple switches are connected with redundant links without a loop-prevention mechanism, an **Ethernet loop** occurs.
*   **No TTL**: Unlike IP packets (Layer 3), Ethernet frames (Layer 2) have no mechanism to count how many times they have been seen or to expire.
*   **Broadcast Storms**: Frames loop infinitely, adding more traffic until the switch capacity is overwhelmed, crashing the network within seconds.
*   **Resolution**: While physically disconnecting a cable fixes the loop, an automated software solution is required for enterprise reliability.

---

## 2. IEEE 802.1D (STP)
The **Spanning Tree Protocol (STP)** is the standard (802.1D) designed to identify and prevent loops by strategically disabling redundant paths.

### Port States
STP moves interfaces through several states to ensure the network topology is understood before traffic flows:
*   **Blocking**: The port is disabled from forwarding traffic to prevent a loop.
*   **Listening**: The switch clears existing tables and identifies other switches on the network.
*   **Learning**: The switch populates its MAC address table but does not yet forward data.
*   **Forwarding**: The port is fully operational, sending and receiving data.
*   **Disabled**: The port is administratively turned off and does not participate in STP.

### Port Roles
*   **Root Port (RP)**: The specific interface on a switch that provides the best path to the **Root Bridge**.
*   **Designated Port (DP)**: Any other port authorized to forward traffic that is not a Root Port.
*   **Blocked Port**: A redundant port that has been disabled by STP to break a physical loop.

---

## 3. 802.1W (Rapid STP)
**Rapid Spanning Tree Protocol (RSTP)** is the modern evolution of the standard.
*   **Convergence Speed**: The original 802.1D standard can take **30 to 50 seconds** to recover from a link failure. RSTP reduces this "convergence" time to approximately **6 seconds**.
*   **Backwards Compatibility**: RSTP is fully compatible with original STP, allowing mixed-hardware environments to function together.
*   **Operation**: RSTP uses the same fundamental logic as STP but utilizes specific shortcuts to transition ports to forwarding states much faster.

---

## 4. STP in Action: Failover
If a primary link in the network fails:
1.  Spanning Tree recognizes the loss of connectivity.
2.  The protocol clears the old topology and "re-learns" the network.
3.  Previously **Blocked Ports** are transitioned to a **Forwarding** state to provide a new path to the destination.
4.  This process ensures the network remains reachable without human intervention or creating a new loop.
