# Binary Math and Decimal Conversion

Binary calculation is a foundational skill for IP subnetting and networking.

---

## 1. Fundamentals of Binary
* **Bit:** The smallest unit of data, representing either a **0** or a **1**.
* **Byte:** A grouping of **8 bits**. 
* **Octet:** A common networking term for an 8-bit byte, used to emphasize the eight individual positions in an IP address segment.

## 2. The Binary Conversion Chart
To perform calculations, we use a chart based on the **powers of 2**. Starting from the right, each position doubles as you move to the left:

| $2^7$ | $2^6$ | $2^5$ | $2^4$ | $2^3$ | $2^2$ | $2^1$ | $2^0$ |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |

---

## 3. Binary to Decimal Conversion
To convert binary to decimal, align your binary string under the conversion chart and add the values of the columns where a "1" appears.

**Example: Convert `10000010` to Decimal**
1. Identify the '1's: They are in the **128** and **2** positions.
2. Add them: $128 + 2 = 130$.
3. **Result:** `130`

**Example: Convert `11111111` to Decimal**
1. Identify the '1's: Every position is active.
2. Add them: $128+64+32+16+8+4+2+1 = 255$.
3. **Result:** `255`

---

## 4. Decimal to Binary Conversion
To convert decimal to binary, determine which power-of-two values "fit" into your decimal total.

**Example: Convert `154` to Binary**
* Does **128** fit into 154? Yes. (Remainder: 26). Set bit to **1**.
* Does **64** fit into 26? No. Set bit to **0**.
* Does **32** fit into 26? No. Set bit to **0**.
* Does **16** fit into 26? Yes. (Remainder: 10). Set bit to **1**.
* Does **8** fit into 10? Yes. (Remainder: 2). Set bit to **1**.
* Does **4** fit into 2? No. Set bit to **0**.
* Does **2** fit into 2? Yes. (Remainder: 0). Set bit to **1**.
* Does **1** fit into 0? No. Set bit to **0**.

**Result:** `10011010`

---

## 5. Bit Scaling and Outcomes
The more bits you use, the more unique combinations (outcomes) you can represent. The number of outcomes is calculated as $2^n$ (where $n$ is the number of bits).

| Number of Bits | Possible Outcomes ($2^n$) | Decimal Range |
| :--- | :--- | :--- |
| 2 bits | 4 | 0 - 3 |
| 4 bits | 16 | 0 - 15 |
| 8 bits | 256 | 0 - 255 |
| 10 bits | 1,024 | 0 - 1,023 |

> [!TIP]
> Memorizing the doubling sequence (1, 2, 4, 8, 16, 32, 64, 128) is the most effective way to speed up your subnetting calculations.
