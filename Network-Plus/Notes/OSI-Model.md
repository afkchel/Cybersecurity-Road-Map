# OSI Model

The **Open Systems Interconnection (OSI) model** is a conceptual framework used to understand network interactions in seven layers.

---

## 🏗️ The 7 Layers

### 1. Physical Layer
- **Function:** Signaling, cabling, and binary transmission.
- **Essentially:** [Ethernet cables](Network-Plus/Notes/Ethernet-Standards.md), hubs, and fiber optics.

### 2. Data Link Layer
- **Function:** Physical addressing and Media Access Control (MAC).
- **Essentially:** The switching layer (Frames).

### 3. Network Layer
- **Function:** Routing, IP addressing, and fragmenting data.
- **Essentially:** IP addresses, ICMP, and Routers (Packets).

### 4. Transport Layer
- **Function:** End-to-end communication and error recovery.
- **Essentially:** TCP (Transmission Control Protocol) and UDP (User Datagram Protocol).

### 5. Session Layer
- **Function:** Communication management between devices (Start, Stop, Restart).
- **Essentially:** Control protocols and tunneling.

### 6. Presentation Layer
- **Function:** Data representation, compression, and encryption.
- **Essentially:** Application encryption like SSL/TLS.

### 7. Application Layer
- **Function:** Network process to application. Where users interact with the network.
- **Protocols:** [HTTP, HTTPS, FTP, SSH, SMTP, DNS, DHCP, POP3.](./Common-Ports.md)
- **Essentially:** The interface we see (Data).

---

## 🧠 Mnemonics for Memorization


| Direction | Mnemonic |
| :--- | :--- |
| **Bottom to Top (1-7)** | **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way |

---

## 🛠️ Practical Implementation (Wireshark Analysis)

<img width="1155" height="252" alt="image" src="https://github.com/user-attachments/assets/52d57ea7-ce4b-4e52-869a-dce3db63d9db" />

To verify these layers, I performed a packet capture during a simple web request(ping 1.1.1.1 in cmd):
1. **Physical:** Ethernet perfomance capture(frame data length).
2. **Data Link:** Source and Destination **MAC Addresses**.
We can check if GigaByteTech indeed has a MAC address by comparing it to the physical address which we can identify with the ipconfig /all cmd command

<img width="676" height="456" alt="image" src="https://github.com/user-attachments/assets/01e93bfa-17c5-4bd8-a55f-e246c49cf91c" />

4. **Network:** Source and Destination **IP Addresses**, ICMP.

---
