# OSI Model

The **Open Systems Interconnection (OSI) model** is a conceptual framework used to understand network interactions in seven layers.

---

## 🏗️ The 7 Layers

### 7. Application Layer
- **Function:** Network process to application. This is where users interact with network applications.
- **Protocols:** HTTP, HTTPS, FTP, SSH, SMTP, DNS, DHCP, POP3
- **Essentially:** What we see

### 6. Presentation Layer
- **Function:** Data representation and encryption. Ensures that data is readable by the receiving system.
- **Essentially:** Application encryption SSL/TLS.

### 5. Session Layer
- **Function:** Communication between devices. Can start, stop, and restart them. 
- **Essentially:** Control, tunneling 

### 4. Transport Layer
- **Function:** Transporting data
- **Essentially:** TCP(Transmission control protocol), UDP(User Datagram protocol)

### 3. Network Layer
- **Function:** Routing, fragmenting data
- **Essentially:** IPs, ICMP

### 2. Data Link Layer
- **Function:** Physical addressing and MAC(Media Access Control).
- **Essentially:** The switching layer

### 1. Physical Layer
- **Function:** Signalling, cabling.
- **Essentially:** Ethernet 

---

## 🧠 Mnemonics for Memorization


| Direction | Mnemonic |
| :--- | :--- |
| **Top to Bottom (7-1)** | **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing |
| **Bottom to Top (1-7)** | **P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way |

---

## 🛠️ Practical Implementation (Wireshark Analysis)
To verify these layers, I performed a packet capture during a simple web request:
1. **Physical:** Signal captured via the Ethernet interface.
2. **Data Link:** Source and Destination **MAC Addresses** identified.
3. **Network:** Source and Destination **IP Addresses** identified.
4. **Transport:** **TCP Port 443** (HTTPS) used for session establishment.
5. **Application:** **TLS Handshake** and encrypted payload observed.
<img width="1155" height="252" alt="image" src="https://github.com/user-attachments/assets/52d57ea7-ce4b-4e52-869a-dce3db63d9db" />


---
*Created during Professor Messer's N10-009 Course study.*
