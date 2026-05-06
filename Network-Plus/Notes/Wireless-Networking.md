# 📶 Wireless Networking Standards & Technologies

---

## 🌐 Wi-Fi Standards (IEEE 802.11)
All wireless networking standards are managed by the **IEEE** (802.11 committee). To ensure devices from different manufacturers work together, the **Wi-Fi Alliance** tests and certifies products with the official Wi-Fi logo.

### 📊 Wi-Fi Generations Comparison


| Generation | IEEE Standard | Frequencies | Max Theoretical Speed |
| :--- | :--- | :--- | :--- |
| **Wi-Fi 7** | 802.11be | 2.4 / 5 / 6 GHz | 40+ Gbps |
| **Wi-Fi 6 / 6E**| 802.11ax | 2.4 / 5 / 6 GHz | 9.6 Gbps |
| **Wi-Fi 5** | 802.11ac | 5 GHz | 6.9 Gbps |
| **Wi-Fi 4** | 802.11n | 2.4 / 5 GHz | 600 Mbps |
| **Legacy** | 802.11a/b/g | 2.4 / 5 GHz | 11 - 54 Mbps |

*Note: Newer standards increase throughput by using more antennas (MIMO) and wider channels.*

---

## 📱 Mobile Cellular Networks

### 4G LTE (Long Term Evolution)
*   **Technology:** A convergence of GSM and CDMA standards into a single global standard.
*   **Standard LTE:** Supports download rates of approx. **150 Mbps**.
*   **LTE Advanced (LTE-A):** Improved version supporting up to **300 Mbps**.

### 5G (Fifth Generation)
*   **Performance:** Significantly higher throughput compared to 4G. 
*   **Speed:** Real-world speeds often range from **100–900 Mbps**, with a theoretical goal of **10 Gbps**.
*   **Impact:** Enabling the expansion of **IoT (Internet of Things)** by removing bandwidth constraints and allowing more cloud-based data processing.

---

## 🛰️ Non-Terrestrial Networking (Satellite)
Used for remote locations where traditional cable or fiber is unavailable.

*   **Latency (Delay):**
    - **Traditional Satellite:** High latency (approx. **250ms up / 250ms down**), resulting in a half-second round trip.
    - **Modern (e.g., Starlink):** Aiming for lower latency (approx. **20ms - 40ms**).
*   **Speeds:** Commonly provides **100 Mbps down / 5 Mbps up**. (*Most satellite connections are asymmetric, meaning the Download speed (data to user, e.g., 100 Mbps) is significantly higher than the Upload speed (data from user, e.g., 5 Mbps) due to the power limitations of the ground-based transmitter.*)
*   **Challenges:**
    - **Line of Sight:** Requires an unobstructed path to the satellite.
    - **Rain Fade:** Heavy thunderstorms can cause signal degradation or complete loss of connectivity.

---

## 💡 Key Terminology
*   **IEEE 802.11:** The family of standards for Wireless Local Area Networks (WLAN).
*   **Interoperability:** The ability of different systems/devices to work together (certified by Wi-Fi Alliance).
*   **Rain Fade:** Signal interference caused by environmental factors like rain or snow.

---

## Wireless Network Modes

* Infrastructure Mode: Devices connect to a central Access Point (AP).
* IBSS (Independent Basic Service Set): Also known as ad hoc mode.
* Devices communicate directly with each other without an access point.
   * Commonly used for initial configuration of IoT devices (e.g., smart lights, door locks).

## 2. Service Set Identifiers

* SSID (Service Set Identifier): The human-readable name of the wireless network (e.g., "SGC1").
* BSSID (Basic Service Set Identifier): The hardware (MAC) address of a specific access point (e.g., 60:3D:26:11:22:33). This differentiates APs sharing the same SSID.
* ESSID (Extended Service Set Identifier): Used when multiple access points share the same SSID across a large area. This allows for seamless roaming as a user moves through a building.

## 3. Network Access & Authentication

* Captive Portal: A web page that appears when first connecting to a network.
* Requires users to agree to terms or provide authentication (username/password).
   * Uses a centralized access table to track authenticated devices for a set duration (e.g., 24 hours).

## 4. Wireless Security Modes

* Open System: No security, no encryption, no authentication.
* OWE (Opportunistic Wireless Encryption): Provides encryption but prevents direct communication between wireless devices on the same network.
* Personal / PSK (Pre-Shared Key): Everyone uses the same password (e.g., a coffee shop password).
* Enterprise / 802.1x:
* Uses individual credentials (unique usernames and passwords).
   * Centralized management: if an employee leaves, their specific access is disabled.
* Legacy/Modern Standards: Supports WEP, WPA, WPA2, and WPA3.

## 5. Antennas

* Omnidirectional:
* Distributes signal evenly in all directions.
   * Best for placement in the center of a room or home.
* Directional (Implicit): Mentioned as a potential alternative for specific layouts, such as when an AP is placed in the corner of a building.
