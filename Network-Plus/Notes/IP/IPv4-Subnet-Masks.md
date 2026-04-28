# IPv4 Subnet Masks, CIDR, and VLSM Calculations

Since 1993, the networking world has moved away from rigid address classes to **Classless Inter-Domain Routing (CIDR)** and **Variable-Length Subnet Masking (VLSM)**. This allows administrators to create subnets of exactly the right size for their specific needs.

---

## 1. What is a Subnet Mask?
A subnet mask is a 32-bit value used to divide an IP address into two parts:
1.  **Network/Subnet Portion:** Identifies the specific network.
2.  **Host Portion:** Identifies the specific device on that network.

### The Rule of Contiguity
A valid subnet mask **must** consist of a contiguous series of 1s on the left, followed by a contiguous series of 0s on the right.
* **Valid:** `11111111.11111111.11110000.00000000` (/20)
* **Invalid:** `11111111.00000000.11111111.00000000` (Non-contiguous)

---

## 2. Variable-Length Subnet Masking (VLSM)
VLSM allows you to "borrow" bits from the host portion of a classful address to create multiple smaller subnets. Think of it as cutting a large pizza (a Class A/B/C network) into smaller, custom-sized slices.

### The Borrowing Concept
* **Network Bits:** The original bits assigned by the address class (A=8, B=16, C=24).
* **Subnet Bits ($s$):** The additional bits "borrowed" from the host section.
* **Host Bits ($h$):** The remaining bits used to identify devices.

---

## 3. The Core Formulas
Using the powers of 2, you can quickly calculate the dimensions of any network:

| To Find... | Formula | Description |
| :--- | :--- | :--- |
| **Number of Subnets** | $2^s$ | Where $s$ is the number of bits borrowed. |
| **Usable Hosts** | $2^h - 2$ | Where $h$ is host bits. Subtract 2 for Network & Broadcast IDs. |

---

## 4. Subnetting "Cheat Sheet" (The Magic Table)
Within a single octet, these are the only possible decimal values:

| 1s | Binary | Decimal | 1s | Binary | Decimal |
| :--- | :--- | :--- | --- | :--- | :--- | :--- |
| 1 | `10000000` | **128** | 5 | `11111000` | **248** |
| 2 | `11000000` | **192** | 6 | `11111100` | **252** |
| 3 | `11100000` | **224** | 7 | `11111110` | **254** |
| 4 | `11110000` | **240** | 8 | `11111111` | **255** |

---

## 5. Calculation Walkthroughs

### Scenario A: Class C Address with 2 bits borrowed
**IP:** `192.168.1.0/26`
* **Default Class C:** /24 (24 bits)
* **Borrowed ($s$):** 2 bits (26 - 24)
* **Hosts ($h$):** 6 bits (32 - 26)
* **Subnets:** $2^2 = 4$
* **Usable Hosts:** $2^6 - 2 = 62$

### Scenario B: Class B Address with 5 bits borrowed
**IP:** `172.16.0.0/21`
* **Default Class B:** /16 (16 bits)
* **Borrowed ($s$):** 5 bits (21 - 16)
* **Hosts ($h$):** 11 bits (32 - 21)
* **Subnets:** $2^5 = 32$
* **Usable Hosts:** $2^{11} - 2 = 2,046$

---

> [!TIP]
> **Why do we subtract 2?** The first address in any subnet is the **Network ID** (all host bits 0), and the last address is the **Broadcast ID** (all host bits 1). Neither can be assigned to a computer or router.
