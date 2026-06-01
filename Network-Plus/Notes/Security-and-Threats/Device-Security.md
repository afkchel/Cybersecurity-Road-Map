# Device Security and Interface Hardening

---

## 1. Port Security and Network Sockets

Every network service running on a computer opens a specific **port number** (ranging from 0 to 65,535). These ports act as entry points into that system.

* **The Risk:** Leaving unused network services running keeps unnecessary ports open, creating accidental entry holes that attackers can exploit.
* **Firewall Controls:** Firewalls should be used to restrict access to open ports, letting you choose exactly which internal or external devices can connect to them.
* **Discovery Scanning:** To find out which hidden ports are open on a machine, administrators use third-party tools like **Nmap**.
Nmap scans a system and lists every port advertised to the network, allowing you to identify and shut down unneeded services.

---

## 2. Managing Default Credentials

Many network components—including switches, routers, and firewalls—ship from the factory with a standard set of default usernames and passwords.

* **The Vulnerability:** Keeping default credentials active means anyone who knows them can log in. These default accounts frequently grant full administrative access, giving an outsider total control over the device.
* **Public Databases:** Information sites like **routerpasswords.com** maintain public databases of default credentials for almost every major hardware vendor, making it easy for attackers to find them.
* **Hardening Rule:** Administrators must change factory-default usernames and passwords the very first time they log into a new device.

---

## 3. Switchport Security Controls

Because you cannot physically watch every Ethernet jack in a building, network switches include built-in features to prevent unauthorized hardware from plugging into the network.

### A. MAC Address Port Security

Port security prevents an attacker from unplugging a legitimate device and connecting their own computer into that same switch port. It tracks connections using the device's **MAC address** (the physical hardware address of the network interface card).

* **Configuration:** You configure the switch port with the specific MAC address allowed to use it, or limit the maximum number of unique MAC addresses that the port can learn.
* **Violation Action:** If an unapproved device plugs in, port security triggers. By default, the switch will immediately **disable (shut down) the interface** and send an alert to the network administrator.

### B. Interface Disabling Best Practice

Open Ethernet jacks in public spaces (like break rooms or conference rooms) should be administratively **disabled** on the switch when they are not actively needed. While this requires more effort to turn the ports back on when requested, it keeps outsiders from plugging in and instantly joining the network.

### C. Network Access Control (NAC) and 802.1X

For advanced protection, organizations use Network Access Control (NAC), usually implemented as the **802.1X** standard. 
This requires user or machine authentication (username and password) before the switch port opens to pass any data traffic.

### D. MAC Filtering and Obscurity

MAC filtering limits network access to a pre-approved list of hardware addresses.
However, this is considered **security through obscurity** because MAC addresses can be easily captured from the air or wire and changed via software settings. 
If an attacker spoofs an approved MAC address, they can easily bypass the filter.

---

## 4. Centralized Key Management Systems

Modern IT environments use hundreds of authentication details, certificates, and encryption keys that require active oversight.

* **Centralization:** A **Key Management System (KMS)** provides a single management console to create, track, and control cryptographic keys and certificates across local and cloud environments.
* **SSL/TLS Certificates:** The software manages SSL keys for web servers, tracking their expiration dates so administrators can renew them before they expire or revoke them if compromised.
* **SSH Keys:** The system logs SSH keys used to access Linux servers, showing exactly which users are authenticating to which devices.
* **Reporting:** Centralized tracking allows administrators to generate access logs and usage reports to ensure corporate keys are not being misused.
