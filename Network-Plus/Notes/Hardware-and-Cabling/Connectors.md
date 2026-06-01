# Fiber Optic Connector Types

In fiber optic networking, selecting the correct connector is essential for ensuring a secure and efficient physical connection. Connectors vary by size, locking mechanism, and density.

---

## 1. SC Connector (Subscriber Connector)
Commonly known as the **Square Connector** or **Standard Connector**.

* **Design:** A square-shaped housing that uses a simple **push-pull** locking mechanism.
* **Security:** Snaps into place and requires a pull on the connector body to unlock, preventing accidental disconnection.
* **Usage:** Frequently used in data centers. Often combined into pairs (duplex) for transmit and receive functions.

## 2. LC Connector (Local Connector)
Also referred to as a **Lucent Connector** or **Little Connector**.

* **Design:** Smaller than the SC connector, making it ideal for high-density environments. It features a **locking clip** on the top (similar to an RJ-45 Ethernet plug).
* **Security:** To remove it, you must depress the clip to release the lock.
* **Usage:** Popular for modern networking equipment where space is at a premium. Like the SC, it is often used in duplex pairs.

## 3. ST Connector (Straight Tip)
Characterized by its unique round shape and metal housing.

* **Design:** Uses a **bayonet-style** connector. 
* **Security:** You must push the connector into the interface and give it a **slight twist** to lock it. This ensures it will not be dislodged unless the twist is reversed.
* **Features:** Includes a protective **ferrule** to shield the fiber tip. It is highly resistant to being accidentally pulled out.

## 4. MPO Connector (Multi-fiber Push On)
Designed specifically for high-density applications and "big pipe" connections.

* **Design:** A single connector that contains **12 individual fibers** within one cable.
* **Branding:** Often referred to as an **MTP** (a brand name by Corning).
* **Security:** Uses a push-pull locking mechanism similar to the SC connector.
* **Visibility:** All 12 fibers can be seen as tiny dots at the end of the connector when light is passed through them.

---

## Connector Summary Table

| Connector | Name | Form Factor | Locking Mechanism | Typical Fiber Count |
| :--- | :--- | :--- | :--- | :--- |
| **SC** | Subscriber | Square/Standard | Push-Pull | 1 (often paired) |
| **LC** | Local | Small | Clip/Tab | 1 (often paired) |
| **ST** | Straight Tip | Round | Bayonet (Twist) | 1 |
| **MPO** | Multi-fiber Push On | Rectangular | Push-Pull | 12 |

> [!NOTE]
> Locking mechanisms are critical in server racks. With a high volume of cables, these locks prevent accidental dislodgment during maintenance or cable management.

# Copper and Coaxial Connectors

Network connectivity relies on a variety of copper-based connectors, each designed for specific cabling types, signal requirements, and mechanical stability.

---

## 1. Registered Jacks (RJ)
These are the most common connectors used for twisted-pair copper cabling.

### RJ11 (Registered Jack 11)
* **Design:** A 6-position housing, typically using only **2 conductors** (6P2C).
* **Usage:** Primarily used for **analog telephones** and **DSL (Digital Subscriber Line)** internet connections.
* **Size:** Smaller and narrower than the RJ45.

### RJ45 (Registered Jack 45)
* **Design:** An 8-position housing using all **8 conductors** (8P8C).
* **Usage:** The industry standard for **Ethernet** networking (LAN).
* **Size:** Slightly larger and wider than the RJ11 to accommodate the additional wire pairs.

---

## 2. Coaxial Connectors
Coaxial cables use different connectors depending on whether the application is consumer broadband or professional networking.

### F-Connector
* **Design:** A threaded connector that screws onto the interface.
* **Signal:** Uses the solid central copper wire of the coaxial cable as the conductor.
* **Usage:** Standard for **cable modems**, cable television, and **DOCSIS** (Data Over Cable Service Interface Specification) connections.

### BNC Connector
* **Design:** A **Bayonet** connector (named after Neill-Concelman).
* **Locking Mechanism:** A "push and twist" lock that prevents accidental removal.
* **Usage:** Frequently used for **WAN connections**, professional video, and laboratory equipment.
* **Benefit:** Very secure; requires a deliberate untwist to disconnect, making it ideal for high-vibration or critical environments.

---

## Summary Comparison Table

| Connector | Cable Type | Pins/Conductors | Key Feature | Primary Application |
| :--- | :--- | :--- | :--- | :--- |
| **RJ11** | Twisted Pair | 6P2C | Small form factor | Analog Phone / DSL |
| **RJ45** | Twisted Pair | 8P8C | Wide form factor | Ethernet (LAN) |
| **F-Type** | Coaxial | 1 (Solid Core) | Threaded screw | Cable Modem / DOCSIS |
| **BNC** | Coaxial | 1 (Solid Core) | Bayonet Twist-Lock | WAN / Video / Secure Coax |

> [!NOTE]
> While RJ11 and RJ45 look similar, an RJ11 can physically fit into an RJ45 port, but it will not function correctly for Ethernet and can potentially damage the pins of the RJ45 jack.
