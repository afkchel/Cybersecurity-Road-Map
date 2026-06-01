# IPv4 Classful Subnetting

While modern networking uses Classless Inter-Domain Routing (CIDR), the traditional classful system remains the fundamental starting point for understanding how IP addresses are structured and how subnetting begins.

---

## 1. The Five IP Classes
The class of an IP address is determined by the value of its **first octet**.

| Class | First Octet Range | Default Subnet Mask | Network:Host Bits | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **A** | 1 – 127 | 255.0.0.0 | 8 : 24 | Very Large Networks |
| **B** | 128 – 191 | 255.255.0.0 | 16 : 16 | Medium/Large Networks |
| **C** | 192 – 223 | 255.255.255.0 | 24 : 8 | Small Networks |
| **D** | 224 – 239 | N/A | N/A | Multicast Groups |
| **E** | 240 – 255 | N/A | N/A | Reserved/Experimental |

---

## 2. Binary Identification
You can also identify the class by looking at the leading bits of the first octet:
* **Class A:** Starts with `0` (e.g., **0**xxx xxxx)
* **Class B:** Starts with `10` (e.g., **10**xx xxxx)
* **Class C:** Starts with `110` (e.g., **110**x xxxx)
* **Class D:** Starts with `1110`
* **Class E:** Starts with `1111`

---

## 3. The Four Critical Subnet Values
When calculating any subnet, you must identify these four specific addresses:

### A. Network Address
* **Definition:** The identifier for the entire subnet. It cannot be assigned to a host.
* **Calculation:** Set all **Host Bits** to **0**.
* **Example (Class C):** For `192.168.1.50`, the Network Address is `192.168.1.0`.

### B. First Usable Host
* **Definition:** The first IP in the range that can be assigned to a device (PC, Server, etc.).
* **Calculation:** **Network Address + 1**.
* **Example:** `192.168.1.1`.

### C. Network Broadcast Address
* **Definition:** The address used to communicate with every device on the subnet simultaneously.
* **Calculation:** Set all **Host Bits** to **1** (Decimal 255).
* **Example (Class C):** `192.168.1.255`.

### D. Last Usable Host
* **Definition:** The final IP in the range that can be assigned to a device.
* **Calculation:** **Broadcast Address - 1**.
* **Example:** `192.168.1.254`.

---

## 4. Calculation Example Walkthrough
**Target IP:** `172.16.88.200`

1. **Identify Class:** First octet is 172. **Class B**.
2. **Default Mask:** **255.255.0.0**.
3. **Split Portions:** Network = `172.16`, Host = `.88.200`.
4. **Calculations:**
    * **Network Address:** `172.16.0.0` (Host bits to 0)
    * **First Usable:** `172.16.0.1`
    * **Broadcast Address:** `172.16.255.255` (Host bits to 1)
    * **Last Usable:** `172.16.255.254`

---

> [!NOTE]
> Classless addressing (CIDR) allows us to ignore these fixed boundaries (8, 16, 24 bits) to create subnets of any size, but the math for finding the Network and Broadcast addresses remains the same.
