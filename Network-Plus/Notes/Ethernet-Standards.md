# 🔌 Ethernet Standards

Ethernet is the global standard for wired networking, managed and documented by the **IEEE** (Institute of Electrical and Electronics Engineers) under the **802.3 committee**.

---

## 🏗️ The Ethernet Naming Formula

The IEEE uses a specific naming convention to describe the speed, technology, and media used in each standard. You can break down almost any Ethernet name using this formula:

**[Speed] + [Signal Type] + [Medium/Distance]**

### 1. Speed
The first number represents the data rate:
*   **10 / 100 / 1000:** Measured in Megabits per second (e.g., 1000 = 1 Gbps).
*   **10G / 40G / 100G:** Measured in Gigabits per second.

### 2. Signal Type (BASE)
*   **BASE** stands for **Baseband**.
*   **Definition:** This means a single frequency is used to send data over the cable (occupying the entire bandwidth). This is the opposite of *Broadband*, which uses multiple frequencies simultaneously.

### 3. Medium / Distance (The Suffix)
The letter at the end identifies the physical cable type or wavelength:
*   **-T:** Twisted-pair copper (e.g., Cat5e, Cat6).
*   **-S:** Short wavelength fiber optic (e.g., SX = Short wavelength).
*   **-L:** Long wavelength fiber optic (e.g., LX = Long wavelength).
*   **-X:** Often refers to specific local area network (LAN) fiber standards.

---

## 📊 Common Ethernet Standards Comparison


| Standard | Speed | Media Type | Distance/Note |
| :--- | :--- | :--- | :--- |
| **1000BASE-T** | 1 Gbps | Twisted-pair Copper | Standard Gigabit Ethernet |
| **10GBASE-T** | 10 Gbps | Twisted-pair Copper | High-speed copper (Cat6a) |
| **1000BASE-SX** | 1 Gbps | Fiber Optic (Multimode) | Short wavelength light |
| **10GBASE-SR** | 10 Gbps | Fiber Optic (Multimode) | Short range 10G fiber |

---

## 💡 Key Takeaways
*   **Interoperability:** Because of the IEEE 802.3 standards, any compliant device can connect to any Ethernet network regardless of the manufacturer.
*   **Media Diversity:** Ethernet is flexible; it can run over cheap copper cables for short distances or expensive fiber optics for long distances.
*   **Naming Accuracy:** While names give a good idea of the tech, the IEEE notes that they don't always perfectly correlate to all technical details. To understand a standard fully, the technical documentation must be reviewed.

---
