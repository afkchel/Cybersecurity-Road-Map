# Network Address Translation (NAT) and Port Address Translation (PAT)

## 1. The Purpose of NAT
With approximately **20 to 30 billion devices** connected to the internet and only **4.29 billion available IPv4 addresses**, the industry has completely exhausted the list of available public subnets. 
**Network Address Translation (NAT)** allows organizations to use a limited number of public IP addresses to communicate with the billions of devices on the internet.

---

## 2. Private vs. Public Addressing 
Private IP addresses are defined by **RFC 1918** and are not routable on the public internet. They are used internally within homes and businesses to conserve public address space.

| Private Range | Typical Use Case |
| :--- | :--- |
| **10.0.0.0 – 10.255.255.255** | Large enterprise networks. |
| **172.16.0.0 – 172.31.255.255** | Mid-sized internal networks. |
| **192.168.0.0 – 192.168.255.255** | Home networks and small offices. |

---

## 3. How NAT Works
When an internal device (source) wants to communicate with an external server (destination), the NAT-configured router performs the following steps:

1.  **Identification**: The router recognizes the source IP is an internal private address (e.g., `10.10.20.50`).
2.  **Translation**: The router modifies the source IP address to a **public IP address** from its available pool (e.g., `94.1.1.1`).
3.  **Forwarding**: The packet is sent to the public destination (e.g., a web server).
4.  **Reverse Translation**: When the web server responds to the public IP, the router references its translation table to change the destination back to the original internal private IP.

---

## 4. PAT (Port Address Translation)
Standard NAT translates one private IP to one public IP, which is inefficient for large numbers of users. 
**Port Address Translation (PAT)**, also known as **NAT Overload**, allows thousands of internal devices to share a single public IP address.

### The PAT Process:
*   **IP + Port**: The router tracks both the internal IP address and a unique **source port number** for each transaction.
*   **Translation Table**: The router maps a private address (e.g., `10.10.20.50:3233`) to a public address with a unique port (e.g., `94.1.1.1:1055`).
*   **Concurrency**: Multiple users can use the same public IP (`94.1.1.1`) simultaneously because the router differentiates them by assigning each user a different port number (e.g., `94.1.1.1:1055`, `94.1.1.1:1056`, etc.).

---

## 5. Summary of Benefits
*   **Address Conservation**: Allows thousands of devices to access the internet using a single public IP address.
*   **Security**: Internal private IP addresses are never exposed directly to the public internet.
*   **Flexibility**: Organizations can change their internal IP scheme without needing to request new public addresses from an ISP.
