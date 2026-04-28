# IPv4 Subnet Masks and CIDR Notation

Since 1993, the networking world has moved away from rigid address classes to **Classless Inter-Domain Routing (CIDR)**. This allows for flexible subnet sizes that are not restricted to 8, 16, or 24 bits.

---

## 1. What is a Subnet Mask?
A subnet mask is a 32-bit value used to divide an IP address into two parts:
1.  **Network Portion:** Identifies the specific network or subnet.
2.  **Host Portion:** Identifies the specific device on that network.

### The Rule of Contiguity
A valid subnet mask **must** consist of a contiguous series of 1s on the left, followed by a contiguous series of 0s on the right.
* **Valid:** `11111111.11111111.11110000.00000000`
* **Invalid:** `11111111.00000000.11111111.00000000` (The 1s are not contiguous)

---

## 2. CIDR Block Notation
CIDR notation (e.g., `/24`) is a shorthand way to express the number of "1" bits in a subnet mask.

| Decimal Mask | Binary Representation (simplified) | CIDR |
| :--- | :--- | :--- |
| **255.0.0.0** | 8 ones, 24 zeros | `/8` |
| **255.255.0.0** | 16 ones, 16 zeros | `/16` |
| **255.255.255.0** | 24 ones, 8 zeros | `/24` |
| **255.255.255.192** | 26 ones, 6 zeros | `/26` |

---

## 3. The "Magic Table" for Mask Conversion
Within a single octet, there are only 9 possible decimal values for a subnet mask:

| Number of 1s | Binary | Decimal Value |
| :--- | :--- | :--- |
| 0 | `0000 0000` | **0** |
| 1 | `1000 0000` | **128** |
| 2 | `1100 0000` | **192** |
| 3 | `1110 0000` | **224** |
| 4 | `1111 0000` | **240** |
| 5 | `1111 1000` | **248** |
| 6 | `1111 1100` | **252** |
| 7 | `1111 1110` | **254** |
| 8 | `1111 1111` | **255** |

---

## 4. Conversion Examples

### Example A: Convert `/20` to Decimal
1.  **Count the 1s:** 20 bits total.
2.  **Fill Octets:** * 1st Octet: 8 bits (`255`)
    * 2nd Octet: 8 bits (`255`)
    * 3rd Octet: 4 bits remaining (`240` from chart)
    * 4th Octet: 0 bits remaining (`0`)
3.  **Result:** `255.255.240.0`


### Example B: Convert `255.255.255.224` to CIDR
1.  **Count the 1s:**
    * `255` = 8 bits
    * `255` = 8 bits
    * `255` = 8 bits
    * `224` = 3 bits (from chart)
2.  **Sum:** $8 + 8 + 8 + 3 = 27$.
3.  **Result:** `/27`

---

## 5. Network vs. Host Bits
The CIDR notation tells you exactly how much space is available for devices:
* **Network Bits:** The CIDR number ($n$).
* **Host Bits:** $32 - n$.
* **Formula for Hosts:** $2^{(32-n)} - 2$ (We subtract 2 for the Network and Broadcast addresses).

**Example for `/26`:**
* **Network Bits:** 26
* **Host Bits:** 6
* **Total Hosts:** $2^6 - 2 = 62$ usable IP addresses.

---

> [!TIP]
> While **Windows** usually expects the **Decimal Mask** (255.255.255.0), **Routers and Switches** almost always prefer **CIDR Notation** (/24).
