# 📢 Lab: The Local Shout — Analyzing Broadcast & ARP

This lab demonstrates how the **Broadcast (One-to-All)** communication type works in an IPv4 environment and how the **Address Resolution Protocol (ARP)** uses it to discover physical MAC addresses.

## 🎯 Objective
To observe the transition from a **Broadcast** request to a **Unicast** response by forcing the system to perform a fresh ARP discovery.

---

## 🛠️ Step 1: Clearing the ARP Cache

**Action:** 
To see the broadcast in action, I had to force my PC to "forget" known devices. I opened the Command Prompt as an **Administrator** and ran `arp -d *`. 
This command clears the ARP table, ensuring the next network request triggers a fresh discovery process.

## 🛠️ Step 2: Capturing the Broadcast (ARP Request)

**Action:**
I started a Wireshark capture with the filter `eth.addr == ff:ff:ff:ff:ff:ff` (the Layer 2 Broadcast address).

<img width="1898" height="205" alt="image" src="https://github.com/user-attachments/assets/2cac0c2a-44c0-4bb6-9309-ce631f918d71" />


**Technical Discovery:**
*   **Destination MAC:** `ff:ff:ff:ff:ff:ff` (**Broadcast**).
*   **Protocol:** ARP (Address Resolution Protocol).
*   **The Message:** *"Who has 192.168.31.1? Tell 192.168.31.154"*
*   **Observation:** Every device in my local network segment received this frame, but only the owner of the IP address(the router) responded.

---

## 🛠️ Step 3: The Unicast Response (ARP Reply)

**Action:**
I analyzed the response from the router to see how the communication type changed from Broadcast to Unicast.

<img width="1062" height="109" alt="image" src="https://github.com/user-attachments/assets/976ff805-6222-4fde-98be-7c62783408c5" />


**Technical Discovery:**
*   **Destination MAC:** `74:56:3c:d8:9d:d2`(My specific PC's MAC).
*   **The Message:** *"192.168.31.1 is at 04:67:61:cf:cd:c8"(The router's MAC Address)*
*   **Observation:** The response is a **Unicast (One-to-One)** communication. The router replies directly to my machine, providing its hardware address to complete the mapping.

---

## 💡 Key Takeaways

1.  **Broadcast Necessity:** In IPv4, Broadcast is essential for initial discovery. My PC couldn't send data to the router's IP without first "shouting" to find its MAC address.
2.  **L2 vs. L3 Mapping:** This lab proves that **Layer 3 (IP)** cannot function without **Layer 2 (MAC)** addressing. ARP acts as the bridge between these layers.
3.  **Efficiency:** While the request was sent to everyone (**One-to-All**), the reply was sent only to me (**One-to-One**), demonstrating efficient use of network resources once the destination was identified.
