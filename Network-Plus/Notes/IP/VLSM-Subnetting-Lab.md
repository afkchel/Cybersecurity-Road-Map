# Lab: Enterprise IPv4 Subnetting & VLSM Design

## 1. Scenario Overview
The **Global-Tech Solutions** corporation has been assigned a single Class B private address block: **`172.16.0.0/16`**. As the Network Engineer, my task is to segment this space into efficient subnets to support various departments while minimizing address waste.

---

## 2. Charts Used
These reference tables were utilized to perform rapid calculations for masks and network boundaries.

### Subnet Mask Reference Table
| | | Masks | | Mask Value | Networks | Addresses |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| /1 | /9 | /17 | /25 | 128 | 2 | 128 |
| /2 | /10 | /18 | /26 | 192 | 4 | 64 |
| /3 | /11 | /19 | /27 | 224 | 8 | 32 |
| /4 | /12 | /20 | /28 | 240 | 16 | 16 |
| /5 | /13 | /21 | /29 | 248 | 32 | 8 |
| /6 | /14 | /22 | /30 | 252 | 64 | 4 |
| /7 | /15 | /23 | /31 | 254 | 128 | 2 |
| /8 | /16 | /24 | /32 | 255 | 256 | 1 |

### Network Address Subnet Boundaries
<img width="1384" height="171" alt="image" src="https://github.com/user-attachments/assets/e883286b-96f2-40ce-a7ea-176117043d6a" />

---

## 3. Subnetting Implementation

### A. Operations: 2,000 Hosts (Manual)
*   **Host bits calculation**: $2^{11} - 2 = 2,046$ usable hosts. $n = 11$ host bits.
*   **Binary Mask**: `11111111.11111111.11111000.00000000`
*   **CIDR**: `/21`
*   **Network IP**: `172.16.0.0`
*   **Mask**: `255.255.248.0`
*   **Broadcast**: `172.16.7.255`
*   **Usable Range**: `172.16.0.1 - 172.16.7.254`

### B. Marketing: 500 Hosts (Magic Number)
*   **Host bits calculation**: $2^9 - 2 = 510$ usable hosts. $n = 9$ host bits.
*   **CIDR**: $32 - 9 = /23$
*   **IP Starting Point**: `172.16.8.0` (First available after Operations).
*   **Mask**: `255.255.254.0`
*   **Magic Number**: $256 - 254 = 2$.
*   **Broadcast Calculation**: $8 + (2) - 1 = 9$ (in the 3rd octet).
*   **Network IP**: `172.16.8.0`
*   **Broadcast**: `172.16.9.255`
*   **Usable Range**: `172.16.8.1 - 172.16.9.254`

### C. Human Resources: 50 Hosts (Seven-Second Shortcut)
*   **Requirement**: 50 hosts.
*   **Chart Lookup**: Smallest block fitting 50 is **64** (CIDR **/26**).
*   **Network IP**: `172.16.10.0` (First available after Marketing).
*   **Mask**: `255.255.255.192`.
*   **Boundary**: Subnet Boundaries table shows next block at `.64`, so broadcast is `.63`.
*   **Usable Range**: `172.16.10.1 - 172.16.10.62`

### D. Site-to-Site WAN: 2 Hosts (Seven-Second Shortcut)
*   **Requirement**: 2 hosts.
*   **Chart Lookup**: Smallest block fitting 2 is **4** (CIDR **/30**).
*   **Network IP**: `172.16.10.64` (First available after HR).
*   **Mask**: `255.255.255.252`.
*   **Boundary**: Address table shows next block at `.68`, so broadcast is `.67`.
*   **Usable Range**: `172.16.10.65 - 172.16.10.66`

---

## 4. Final Addressing Plan Summary

| Subnet | Network IP | CIDR | Subnet Mask | Broadcast | Usable Range |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Operations** | `172.16.0.0` | `/21` | `255.255.248.0` | `172.16.7.255` | `.0.1 - .7.254` |
| **Marketing** | `172.16.8.0` | `/23` | `255.255.254.0` | `172.16.9.255` | `.8.1 - .9.254` |
| **HR** | `172.16.10.0` | `/26` | `255.255.255.192` | `172.16.10.63` | `.10.1 - .10.62` |
| **WAN** | `172.16.10.64` | `/30` | `255.255.255.252` | `172.16.10.67` | `.10.65 - .10.66` |
