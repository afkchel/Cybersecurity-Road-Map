# Wireless Infrastructure Architecture: Frequencies, Attenuation, and Security

---

## 1. Frequency Band Dynamics and Channel Planning

Wireless networks operate within shared, finite radio spectrum blocks. Managing these resources effectively requires careful channel distribution to avoid interference.

### A. The Single-Speaker Constraint
Wireless communication media requires that only a single device transmits on a specific frequency at any given microsecond. 
When multiple access points (APs) or client nodes broadcast simultaneously on overlapping frequencies, they create destructive RF interference, 
which significantly reduces network throughput.

### B. Spectrum Bands Comparison

| Frequency Band | Non-Overlapping Channels (North America) | Interference Characteristics & Capacity |
| :--- | :--- | :--- |
| **2.4 GHz** | **3 Channels** (Typically Channel 1, 6, and 11) | High susceptibility to overlapping interference in busy areas due to the limited number of clean channels. |
| **5 GHz** | **Many more frequencies available** | Greater capacity and a better chance of isolating a channel free from neighboring interference. |
| **6 GHz** | **Massive expansion of available frequencies** | Significantly reduces frequency conflicts and interference issues. |

### C. Overlapping Channel Mismatches
Deploying access points on arbitrary channels within the 2.4 GHz spectrum introduces performance issues. For example, 
if two valid AP footprints are centered on non-overlapping channels **6** and **11**, manually configuring a new third AP on **channel 8** creates a destructive overlap. 
Channel 8 bleeds directly into the frequencies used by both channel 6 and channel 11, degrading the performance and throughput of all devices within that radio range.
In this scenario, the new AP should be assigned to the remaining non-overlapping option, **channel 1**.

### D. Throughput Optimization Best Practices
* **Disable Legacy Support:** Access points frequently include backward compatibility options to support older, low-speed wireless standards.
If all production hardware on the segment supports modern protocols, **administrators should disable legacy support**.
Enabling backward compatibility introduces overhead that slows down the wireless network and reduces overall efficiency.
* **Output Power Tuning:** High-power APs can create interference across a wide area. If an access point covers a small room but its output power is set to maximum,
it can cause interference for neighboring APs. Reducing the output power provides adequate local coverage while minimizing interference with adjacent cells.
* **Load Distribution:** Splitting a dense client pool across multiple physical access points that are spaced apart and locked to distinct, non-overlapping channels
distributes the load and ensures optimal performance.

---

## 2. Signal Attenuation and Physical Layer Corrections

As radio signals travel through the air away from an access point, their strength naturally decreases. This weakening is called **attenuation**.

### A. Antenna Modification and Gain Metrics
Administrators use several physical layer adjustments to counter the effects of attenuation:
* **Transmit Power Control:** Increasing the output power on the access point can expand its coverage footprint, provided the hardware supports this feature.
* **High-Gain External Antennas:** Adding an external high-gain antenna focuses the signal, increasing the access point's ability to transmit across
larger distances without requiring more electrical input power.

### B. Coaxial Cable Attenuation Risks
When connecting external antennas to an access point using coaxial cables, administrators must account for internal signal loss:
* **High-Frequency Attenuation:** Coaxial cables introduce signal loss that increases at higher frequencies.
* **Cable Run Management:** Technicians should **limit the length of coaxial cable runs** between the access point and the antenna to prevent losing too much signal before transmission.
* **Physical Damage Checks:** Coaxial cables must be regularly inspected for damage, creases, or splits, which can leak RF energy and cause link failure.

---

## 3. Site Surveys and Heat Map Telemetry

To ensure adequate coverage and minimize interference from neighboring organizations, administrators must routinely assess the local RF environment.

* **Environmental Frequency Mapping:** Performing site surveys allows administrators to identify what frequencies neighboring businesses are using.
For example, if a neighbor uses only the 2.4 GHz and 5 GHz bands, the 6 GHz spectrum remains completely open for deployment.
* **Heat Map Generation:** Technicians generate visual heat maps by walking through a facility with a Wi-Fi analyzer.
The analyzer records signal quality at specific physical locations and plots the data using a color gradient:
  * **Bright Colors:** Represent strong signal coverage and optimal link quality.
  * **Cool Colors:** Represent weak signal coverage, indicating areas where access points may need to be added or repositioned.
* **Periodic Assessment:** Because surrounding networks change constantly as neighbors add or modify hardware, administrators should perform **multiple site surveys throughout the year**
to discover new interference sources.

---

## 4. Wireless Security and Client Roaming Dynamics

### A. Client Disassociation Denial of Service (DoS) Attacks
Older wireless networks are vulnerable to targeted Denial of Service attacks that exploit unprotected management frames:
* **The Vulnerability:** In older versions of the 802.11 standard, Layer 2 management frames are unencrypted and unauthenticated.
* **The Attack Mechanism:** An attacker can forge and broadcast spoofed **client disassociation frames**, forcing target devices to continuously disconnect and reconnect,
or preventing them from establishing a stable connection entirely.
* **Discovery and Mitigation:** Administrators can detect this attack by using an **802.11 packet capture device** to look for abnormal volumes of disassociation frames in the wireless traffic.
To stop these attacks permanently, the wireless infrastructure should be upgraded to the latest 802.11 standards, which include protected management frames.

### B. Enterprise SSID Deployment and Seamless Roaming
Organizations can extend a wireless network across a large building or campus by configuring multiple access points with the exact same **Service Set Identifier (SSID)**.
* **The Roaming Experience:** A shared SSID allows client devices to move from one access point to another without losing network connectivity.
* **Configuration Requirements:** For roaming to be seamless, **all participating access points must share identical configurations**,
including matching security protocols and encryption settings. If a user roams to an AP with mismatched security parameters,
the connection will drop completely, and the user will be forced to manually authenticate again.
