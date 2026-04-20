# 🔬 Lab: The Protocol Hunter — Real-World Traffic Analysis

This lab demonstrates how common protocols (**DNS, HTTP, TLS**) operate at the Transport Layer (Layer 4) and confirms their well-known port numbers using **Wireshark**.

## 🎯 Objective
To capture and analyze network traffic to verify:
1. The use of **UDP Port 53** for DNS queries.
2. The use of **TCP Port 80/443** for Web traffic.
3. The **TCP 3-Way Handshake** process (Connection-Oriented communication).

---

## 🛠️ Step 1: DNS Analysis (UDP Port 53)

**Action:** Perform a DNS lookup for `google.com` using the terminal(`nslookup google.com` command) and filter for DNS traffic in Wireshark.

<img width="1919" height="618" alt="image" src="https://github.com/user-attachments/assets/91e7811d-fa74-4165-9c78-6e13ee34890c" />


**Technical Discovery:**
*   **Protocol:** UDP (User Datagram Protocol).
*   **Source Port:** 62143 (Ephemeral).
*   **Destination Port:** **53** (Well-known DNS port).
*   **Observation:** The communication is connectionless; a single request is followed by a single response.

---

## 🛠️ Step 2: Web Traffic Analysis (TCP Port 80/443)

### HTTP

**Action:** Access a website (http://neverssl.com/) and identify the port numbers used in the Transmission Control Protocol header.

<img width="1787" height="859" alt="image" src="https://github.com/user-attachments/assets/b9d0d78a-2bd9-4470-aff0-5a5e0c13afaa" />


**Technical Discovery:**
*   **Protocol:** TCP (Transmission Control Protocol).
*   **Destination Port:** **80** (HTTP).
*   **Encryption:** I observed clear text. Using HTTP on port 80, I could read the headers and host information directly from the packet payload.

### HTTPS

**Action:** Access a website (https://www.youtube.com/) and identify the port numbers used in the Transmission Control Protocol header.

<img width="1729" height="728" alt="image" src="https://github.com/user-attachments/assets/02d122e7-5714-47c6-8618-e00be93b88c2" />


**Technical Discovery:**
*   **Protocol:** TCP (Transmission Control Protocol).
*   **Source Port(reply):** **443** (HTTPS).
*   **Encryption:** I observed encrypted data. Using HTTPS on port 443, the payload was protected by the TLS protocol, making the actual content unreadable in the packet capture.
---

## 🛠️ Step 3: The TCP 3-Way Handshake


**Action:** 
To isolate the connection establishment process, I performed the following steps:
1.  Started a new Wireshark capture and applied the display filter `tcp.flags.syn == 1` to identify new session attempts.
2.  Navigated to `example.com` in a web browser to generate fresh traffic.
3.  Located the initial **[SYN]** packet sent from my IP (`192.168.31.154`) to the destination on **Port 443**.
4.  Right-clicked the packet and selected **Follow > TCP Stream** to view the entire chronological exchange between the client and the server.

<img width="1125" height="73" alt="image" src="https://github.com/user-attachments/assets/76ae6b60-02a2-420a-8956-8e08c3ee70c7" />

**Technical Discovery:**
*   **The Handshake Sequence:** 
    - **Packet 113 [SYN]:** Connection request from Client to Server.
    - **Packet 120 [SYN, ACK]:** Server response acknowledging the request.
    - **Packet 121 [ACK]:** Final acknowledgement from Client, establishing a "Connection-Oriented" session.

**Conclusion:** This confirms the **Connection-Oriented** nature of TCP, ensuring both devices are ready before data transfer begins.

---

## 💡 Lab Takeaways
*   **Socket Identification:** Confirmed that every connection is a combination of `IP + Protocol + Port`.
*   **Reliability:** Observed the overhead of TCP (handshakes/ACKs) compared to the "fire and forget" nature of UDP.
*   **Port Consistency:** Verified that standard services strictly follow the IANA well-known port assignments (80, 443, 53).

---
