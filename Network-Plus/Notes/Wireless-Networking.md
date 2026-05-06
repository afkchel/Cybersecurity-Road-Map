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

## Wireless Service Sets

*   **IBSS (Independent Basic Service Set)**: Also known as an **ad hoc connection**. This allows two devices to communicate directly with each other without an access point. This is common for setting up Internet of Things (IoT) devices, such as smart door locks.
*   **BSS (Basic Service Set)**: The standard wireless network where multiple devices connect to a single central access point.

---

## Wireless Identifiers
To manage and differentiate between networks and hardware, several identifiers are used:

*   **SSID (Service Set Identifier)**: The human-readable name of the wireless network (e.g., "SGC1") that appears when searching for available connections.
*   **BSSID (Basic Service Set Identifier)**: The unique hardware MAC address of a specific access point. This allows devices to differentiate between two different pieces of hardware that might be broadcasting the same network name.
*   **ESSID (Extended Service Set Identifier)**: Used when multiple access points across a large area share the same SSID. This allows a user to walk through a building and seamlessly "roam" from one access point to another without losing connectivity.

---

## 3. Network Access and Security
Accessing a wireless network often involves different authentication methods depending on the environment:

*   **Captive Portal**: A screen that appears when first connecting, requiring users to agree to terms or provide credentials before gaining internet access. These are common in public spaces like hotels or airports.
*   **Security Modes**:
    *   **Open System**: No security or authentication required.
    *   **Personal (PSK)**: Uses a **Pre-Shared Key** (password) that everyone on the network shares.
    *   **Enterprise (802.1X)**: Requires unique credentials (username and password) for every user, often tied to their organizational account.
    *   **OWE (Opportunistic Wireless Encryption)**: Allows a connection but prevents devices from communicating directly with each other on the same network.

---

## 4. Antennas and Signal Strength
The choice of antenna determines how the wireless signal is distributed:

*   **Omnidirectional**: Distributes the signal evenly in all directions. This is ideal for a central location in a home or office.
*   **Directional**: Focuses the signal in a specific direction to increase range or performance.
    *   **Yagi Antenna**: Very directional with high gain.
    *   **Parabolic Antenna**: Focuses signals into a single point, useful for long-distance links.
*   **Gain**: Measured in decibels (dB). A **3dB** increase effectively doubles the power of the signal.

---

## 5. Wireless Management
In large environments, access points are managed differently than standalone home routers:

*   **Autonomous Access Points**: Standalone devices that operate independently without additional software or hardware.
*   **Lightweight Access Points**: Hardware that relies on a central controller for its "intelligence" and configuration.
*   **Wireless LAN Controller (WLC)**: A central management station that provides a "single pane of glass" to monitor, configure, and report on the entire wireless infrastructure.
*   **CAPWAP**: The standard protocol used for the **control and provisioning of wireless access points** from a central controller.
