# Wireless Encryption Standards 

## 1. Core Wireless Security Goals
Because wireless signals travel through open air, three primary security mechanisms are used to protect sensitive data:

* **Authentication**: Verifies that only authorized users (via username/password, MFA, or certificates) can join the network.
* **Confidentiality**: Uses **Encryption** to ensure that even if a signal is intercepted, the data cannot be read by unauthorized parties.
* **Integrity**: Uses a **Message Integrity Check (MIC)** to verify that the information received is exactly what was originally sent and has not been altered in transit.

---

## 2. Evolution of Encryption Protocols

### WEP (Wired Equivalent Privacy)
* **Status**: **Obsolete / Insecure**.
* **History**: The original 802.11 security standard.
* **Vulnerability**: Severe cryptographic flaws were discovered early on, allowing it to be cracked easily with modern tools.

### WPA (Wi-Fi Protected Access)
* **Status**: **Legacy / Stopgap**.
* **History**: Created as a temporary replacement for WEP.
* **Design**: Designed to run on the same older hardware as WEP but provided a much-needed security boost while the industry finalized the next standard.

### WPA2 (Wi-Fi Protected Access v2)
* **Status**: **Standard / Widely Used**.
* **History**: Introduced in 2004 as the long-term replacement for WEP/WPA.
* **Block Cipher Mode**: **CCMP** (Counter Mode with Cipher Block Chaining Message Authentication Code Protocol).
    * **Encryption**: Uses **AES** (Advanced Encryption Standard).
    * **Integrity**: Uses **CBC-MAC**.

### WPA3 (Wi-Fi Protected Access v3)
* **Status**: **State-of-the-Art**.
* **History**: Introduced in 2018 to provide enhanced security for modern networks.
* **Block Cipher Mode**: **GCMP** (Galois Counter Mode Protocol).
    * **Encryption**: Continues to use **AES** for confidentiality.
    * **Integrity**: Uses **GMAC** (Galois Message Authentication Code), which is more efficient and capable than CBC-MAC.

---

## 3. Comparison Summary Table

| Protocol | Implementation | Cipher Mode | Encryption | Integrity Check |
| :--- | :--- | :--- | :--- | :--- |
| **WEP** | Original Standard | N/A | RC4 | CRC-32 |
| **WPA** | Stopgap | TKIP | RC4 | Michael |
| **WPA2** | Mainstream (2004) | **CCMP** | **AES** | **CBC-MAC** |
| **WPA3** | Modern (2018) | **GCMP** | **AES** | **GMAC** |

---

## 4. Implementation Best Practices
* **Upgrade Hardware**: Whenever possible, upgrade older devices to support WPA3.
* **Avoid WEP**: Never use WEP on a modern network; it provides almost no protection against determined attackers.
* **Use the Highest Standard**: Always configure your access points to use the highest level of security supported by your client devices (WPA3 > WPA2).
