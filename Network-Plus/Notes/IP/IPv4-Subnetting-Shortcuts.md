# IPv4 Subnetting Shortcuts

---

## Part 1: The Magic Number Method
The Magic Number method focuses on a specific calculation derived from the subnet mask to identify the size of address blocks.

*   **Identify the Interesting Octet**: Locate the octet in the subnet mask that is neither 0 nor 255.
*   **Calculate the Magic Number**: Subtract the decimal value of the interesting octet from 256.
    *   *Example*: If the mask is 255.255.240.0, the interesting octet is 240. The Magic Number is $256 - 240 = 16$.
*   **Find the Subnet ID**: Find the multiple of the Magic Number that is closest to (but not exceeding) the IP address value in that same octet.
*   **Calculate the Broadcast Address**: Use the formula: $\text{Subnet ID} + \text{Magic Number} - 1$.
*   **Usable Host Range**:
    *   **First Host**: Subnet ID + 1.
    *   **Last Host**: Broadcast Address - 1.

---

## Part 2: The Seven-Second Subnetting Method
This method relies on a pre-built reference chart to eliminate math, focusing on visual boundaries.

### The Reference Chart

| CIDR (Octet 2/3/4) | Subnet Mask | Addresses per Block |
| :--- | :--- | :--- |
| /9, /17, /25 | 128 | 128 |
| /10, /18, /26 | 192 | 64 |
| /11, /19, /27 | 224 | 32 |
| /12, /20, /28 | 240 | 16 |
| /13, /21, /29 | 248 | 8 |
| /14, /22, /30 | 252 | 4 |

### The Rules for Calculation
*   **Mask = 255**: Simply "bring down" the value from the IP address.
*   **Mask = 0**: 
    *   For the **Subnet ID**, bring down a 0.
    *   For the **Broadcast Address**, bring down 255.
*   **The Subnet Address**: Reference the chart to see the block sizes (e.g., blocks of 64) and determine which boundary the IP address falls into (e.g., 0, 64, 128, 192).
*   **The Broadcast Address**: Look at the chart to find where the *next* subnet begins; the broadcast address is exactly one number prior to that.
*   **Host Range**: Add 1 to the Subnet Address for the first host and subtract 1 from the Broadcast Address for the last host.
