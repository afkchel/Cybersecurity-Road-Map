# 🔑 Common Network Protocols and Well-Known Ports

---

## 📂 File Transfer Protocols


| Protocol | Port | Transport | Description |
| :--- | :--- | :--- | :--- |
| **FTP** | 20, 21 | TCP | **File Transfer Protocol.** Port 21 is for control/commands; Port 20 is for data transfer. Non-encrypted. |
| **SFTP** | 22 | TCP | **Secure FTP.** Uses SSH to provide fully encrypted file transfers and file management. |
| **TFTP** | 69 | UDP | **Trivial FTP.** A very simple, "barebones" protocol with no authentication. Used for quick config transfers. |

---

## 💻 Remote Access & Console


| Protocol | Port | Transport | Description |
| :--- | :--- | :--- | :--- |
| **SSH** | 22 | TCP | **Secure Shell.** Encrypted console access for remote device management. |
| **Telnet(outdated)** | 23 | TCP | **Telecommunication Network.** Remote console access, but sends all data (including passwords) in **clear text**. |

---

## 🌐 Web & Email Services


| Protocol | Port | Transport | Description |
| :--- | :--- | :--- | :--- |
| **HTTP** | 80 | TCP | **Hypertext Transfer Protocol.** Standard web browsing, non-encrypted. |
| **HTTPS** | 443 | TCP | **HTTP Secure.** Web browsing encrypted via SSL/TLS. |
| **SMTP** | 25, 587 | TCP | **Simple Mail Transfer Protocol.** Used for server-to-server email transfer. Port 587 is used for encrypted (TLS) transfer. |
| **IMAP** | 143 | TCP | **Internet Message Access Protocol.** Used for receiving and managing email inboxes. |

---

## 🏗️ Infrastructure & Management


| Protocol | Port | Transport | Description |
| :--- | :--- | :--- | :--- |
| **DNS** | 53 | UDP/TCP | **Domain Name System.** Translates domain names to IP addresses. UDP for queries; TCP for large transfers. |
| **DHCP** | 67, 68 | UDP | **Dynamic Host Configuration Protocol.** Automatically assigns IP addresses, subnet masks, and gateways to devices. |
| **NTP** | 123 | UDP | **Network Time Protocol.** Synchronizes clocks across all network devices (critical for logs). |
| **SNMP** | 161, 162 | UDP | **Simple Network Management Protocol.** Port 161 for querying devices; Port 162 for "Traps" (proactive alerts). |
| **Syslog** | 514 | UDP | **System Log.** Standard protocol for consolidating log files from diverse devices to a central server (SIEM). |

---

## 🗄️ Directory & Windows Services


| Protocol | Port | Transport | Description |
| :--- | :--- | :--- | :--- |
| **LDAP** | 389 | TCP | **Lightweight Directory Access Protocol.** Used to query databases of users and devices (Active Directory). |
| **LDAPS** | 636 | TCP | **LDAP over SSL.** Secure, encrypted version of LDAP. |
| **SMB** | 445 | TCP | **Server Message Block.** Windows standard for file/printer sharing and authentication (also known as CIFS). |

---
