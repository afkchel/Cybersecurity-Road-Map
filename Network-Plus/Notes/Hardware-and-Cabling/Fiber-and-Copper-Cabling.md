# Optical Fiber and Copper Cabling

---

## Fiber Optic Networking
Fiber optics transmit data as **light pulses** through thin strands of glass or plastic.

### Construction of a Fiber Cable
* **Core:** The innermost part of the fiber where light travels.
* **Cladding:** A layer with a low reflective index that surrounds the core, reflecting light back into it (total internal reflection).
* **Buffer Coating:** An outer layer providing physical protection to the glass.
* **Ferrule:** The rigid tip of the connector that protects and aligns the fiber end-face.

### Transmission Types
| Feature | Multi-mode Fiber (MMF) | Single-mode Fiber (SMF) |
| :--- | :--- | :--- |
| **Distance** | Short range (up to ~2 km) | Long range (up to 100 km) |
| **Light Source** | Inexpensive LED | Laser or high-intensity LED |
| **Core Size** | Large (allows multiple "modes" of light) | Small (allows only one light path) |
| **Cost** | Lower cost for hardware | Higher cost for hardware |

### Key Advantages
* **Security:** Very difficult to tap without detection; does not emit RF signals.
* **Interference:** Completely immune to **Radio Frequency Interference (RFI)**.
* **Distance:** Signals degrade much slower than copper, allowing for kilometer-scale runs.

---

## Copper (Twisted Pair) Cabling
The most common cabling for LANs, using electrical signals over copper wire.

### The "Twist" Mechanics
* **Balanced Signaling:** Signals are sent as "Transmit +" and "Transmit -" to help the receiver cancel out noise.
* **Interference Mitigation:** At least one wire in the pair is always moving away from a source of interference.
* **Varying Twist Rates:** Different pairs within the same sheath are twisted at different rates to reduce **crosstalk** between them.

### Performance Standards
Cables are categorized by their ability to support specific data throughputs.
* **Category 5 (Cat 5):** The minimum requirement for **1000BASE-T** (Gigabit Ethernet).
* **IEEE 802.3:** The standards body that defines minimum cable categories for Ethernet speeds.

---

## Coaxial and Special Copper
* **Coaxial (RG-6):** Used primarily for cable modems and bringing internet into a data center. All layers share a common axis.
* **Twinaxial (Twinax):** Two conductors in one cable. Often used for **10G SFP+** connections.
    * **Pros:** Low cost and low latency.
    * **Cons:** Limited to short distances (approx. **5 meters**).

---

## Safety and Installation: The Plenum
The **Plenum** is the shared airspace between a drop ceiling and the actual ceiling (often used for air circulation).

### Fire Safety Ratings
* **PVC (Polyvinyl Chloride):** Standard cable jacket; releases toxic fumes and heavy smoke when burned. **Not for use in plenums.**
* **Plenum-Rated (FEP/Low-smoke PVC):** Designed to produce minimal smoke and no hazardous fumes.
* **Installation Note:** Plenum-rated cable is often less flexible and more expensive than standard PVC cable.

> [!IMPORTANT]
> Always check building codes. If the ceiling space shares air with the HVAC system (no dedicated ductwork), **plenum-rated** cable is legally required.
