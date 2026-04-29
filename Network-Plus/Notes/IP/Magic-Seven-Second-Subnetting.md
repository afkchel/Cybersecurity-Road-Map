# Magic Seven-Second Subnetting

This guide combines the logic of the **Magic Number** method and the efficiency of the **Seven-Second Subnetting** shortcut to help you calculate IPv4 boundaries without complex binary math[cite: 1, 3].

---

## 1. The Core Concept
Subnetting is the process of splitting a network into smaller, manageable pieces[cite: 3]. While binary conversion is the traditional method, shortcuts allow you to determine the **Subnet ID**, **Broadcast Address**, and **Usable Host Range** using simple addition and subtraction[cite: 1, 3].

---

## 2. The Seven-Second Subnetting Chart
Before starting any calculation, create this reference table. It eliminates the need for real-time math during an exam[cite: 3].

| CIDR (Octet 2/3/4) | Subnet Mask (Decimal) | Number of Networks | Addresses per Block |
| :--- | :--- | :--- | :--- |
| /9, /17, /25 | 128 | 2 | 128 |
| /10, /18, /26 | 192 | 4 | 64 |
| /11, /19, /27 | 224 | 8 | 32 |
| /12, /20, /28 | 240 | 16 | 16 |
| /13, /21, /29 | 248 | 32 | 8 |
| /14, /22, /30 | 252 | 64 | 4 |

> [!NOTE]
> To build this chart quickly:
> * **Networks:** Start at 2 and double the number (2, 4, 8...)[cite: 3].
> * **Addresses:** Start at 128 and divide by 2 (128, 64, 32...)[cite: 3].
> * **Masks:** Perform 256 minus the Address value (the Magic Number logic)[cite: 1, 3].

---

## 3. The 4-Step Calculation Process

### Step 1: Identify the "Interesting" Octet
Look at the subnet mask. The "Interesting Octet" is the one that is **not** 0 and **not** 255[cite: 1].
* If the mask is **255**, it is a "copy-down" octet—simply bring the IP address value down to your result[cite: 1, 3].
* If the mask is **0**, it is a "zero-out" octet—set the Subnet ID value to 0 and the Broadcast value to 255[cite: 1, 3].

### Step 2: Determine the Subnet ID (Network Address)
Find the block size (Number of Addresses) for your interesting octet in the chart[cite: 3].
* Look at the IP address value in that octet[cite: 1, 3].
* Identify which block that number fits into (e.g., in a block size of 64, the number 88 fits into the block starting at 64)[cite: 3].
* The start of that block is your **Subnet ID**[cite: 1, 3].

### Step 3: Determine the Broadcast Address
Use the Magic Number formula:
* **Broadcast = Subnet ID + Magic Number - 1**[cite: 1].
* Alternatively, look at your chart: the broadcast address is the number immediately preceding the start of the *next* block[cite: 3].

### Step 4: Define the Usable Host Range
* **First Usable Host:** Subnet ID + 1[cite: 1, 3].
* **Last Usable Host:** Broadcast Address - 1[cite: 1, 3].

---

## 4. Example Calculation
**Target:** `165.245.12.88/26`

1.  **Convert Mask:** A `/26` is `255.255.255.192`[cite: 3].
2.  **Interesting Octet:** The 4th octet (`192`)[cite: 1, 3].
3.  **Magic Number/Block Size:** $256 - 192 = 64$ addresses[cite: 1, 3].
4.  **Find the Block:** IP octet is `88`. Block boundaries are 0, 64, 128. `88` falls in the **64** block[cite: 3].
5.  **Subnet ID:** `165.245.12.64`[cite: 3].
6.  **Broadcast:** $64 + 64 - 1 = 127$. Result: `165.245.12.127`[cite: 1, 3].
7.  **Usable Range:** `165.245.12.65` to `165.245.12.126`[cite: 3].
