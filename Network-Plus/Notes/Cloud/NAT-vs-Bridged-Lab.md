# 🧪 Lab: Virtualization Networking Modes (NAT vs. Bridged)

This lab explores the practical implementation of **Network Function Virtualization (NFV)** and **Virtual Network Interface Cards (VNICs)** using a Type 2 Hypervisor.

## 🎯 Objective
To demonstrate how different networking modes in a virtualized environment affect connectivity, isolation, and Layer 3 addressing.

---

## 🛠️ Environment
- **Host OS:** Windows 10
- **Guest OS:** Ubuntu Linux (Virtual Machine)
- **Hypervisor:** Oracle VirtualBox (Type 2)

---

## 🔬 Phase 1: NAT Mode (Network Address Translation)

<img width="776" height="509" alt="image" src="https://github.com/user-attachments/assets/57764aa3-6a51-4ab8-ac73-c5269e341c76" />

In this mode, the Hypervisor creates a private internal network. The VM is isolated from the physical LAN and uses the Host's IP to access the internet.

### Configuration & Discovery
Running `ip address` inside the Ubuntu VM:
- **Interface:** `enp0s3`
- **MAC Address:** `08:00:27:a2:08:94`
- **IPv4 Address:** `10.0.2.15/24`

<img width="1024" height="433" alt="image" src="https://github.com/user-attachments/assets/276f1ce2-6f2f-461c-a946-779bcfc3beda" />

### Observations:
*   The `10.0.2.x` address is a private range assigned by the VirtualBox NAT engine.
*   The VM can access the internet, but the Host OS cannot reach the VM directly.

---

## 🔬 Phase 2: Bridged Mode

<img width="784" height="519" alt="image" src="https://github.com/user-attachments/assets/1bf88fac-4b5b-4e9c-a19b-35610cbd7c25" />

In this mode, the VNIC is bridged directly to the physical network adapter (WiFi/Ethernet). The VM becomes a peer to the Host OS on the physical network.

### Configuration & Discovery
After switching to **Bridged Adapter** in VirtualBox settings:
- **Interface:** `enp0s3`
- **MAC Address:** `08:00:27:a2:08:94` (Remains the same)
- **IPv4 Address:** `192.168.31.246/24`

<img width="1027" height="381" alt="image" src="https://github.com/user-attachments/assets/e8fc4aca-945f-447b-a5b0-ca08ffa4ad71" />

### Observations:
*   The IP address changed to the `192.168.31.x` range, assigned by the physical **Xiaomi router**.
*   The VM is now a visible node on the physical Local Area Network (LAN).

---

## 📊 Connectivity Test (The Proof)

To verify the isolation levels, I performed a `ping` test from the **Host (Windows)** to the **Guest (Ubuntu)**:

<p align="center">
  <img width="517" height="391" alt="image" src="https://github.com/user-attachments/assets/b86e7f90-94a7-49a8-94df-fe08ed43caf9" />
</p>

| Target IP | Mode | Status | TTL Result | Conclusion |
| :--- | :--- | :--- | :--- | :--- |
| **192.168.31.246** | **Bridged** | ✅ Success | `TTL=64` | VM is reachable as a network peer. |
| **10.0.2.15** | **NAT** | ❌ Failed | `Request timed out` | VM is isolated behind the Hypervisor. |

---

## 💡 Key Takeaways
1.  **Encapsulation & Layer 2:** Even when switching modes, the **MAC Address** remained constant, confirming the identity of the VNIC.
2.  **Layer 3 Addressing:** The switch from `10.x.x.x` to `192.x.x.x` demonstrates how DHCP functions differently in isolated vs. transparent virtual networks.
3.  **Security:** NAT mode provides a default layer of security by hiding the virtual instance from the external network, whereas Bridged mode allows full transparency.
4.  **TTL Awareness:** The `TTL=64` value in the successful ping response correctly identifies the target as a **Linux** machine, as per standard OS defaults.
