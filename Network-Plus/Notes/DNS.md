# Domain Name System (DNS) 

---

## 1. DNS Hierarchy and Structure
DNS is organized into a hierarchical, distributed database. This structure ensures that no single server is responsible for every name on the internet.

* **Root Level:** Represented by a single dot (.). There are 13 root server clusters globally that direct queries to the appropriate Top-Level Domains.
* **Top-Level Domains (TLDs):**
    - **Generic TLDs:** .com, .org, .net, etc.
    - **Country Code TLDs:** .us, .ca, .uk, etc.
* **Fully Qualified Domain Name (FQDN):** The complete domain name for a specific host (e.g., `www.professormesser.com`).

---

## 2. DNS Server Roles and Lookups
To maintain uptime and efficiency, DNS uses different server types and lookup methods.

* **Primary vs. Secondary Servers:**
    - **Primary DNS:** The authoritative source where configuration changes and updates are made.
    - **Secondary DNS:** Receives read-only updates (zone transfers) from the primary server for redundancy.
* **Forward vs. Reverse Lookups:**
    - **Forward Lookup:** Providing a name to receive an IP address.
    - **Reverse Lookup:** Providing an IP address to receive the associated hostname.
* **Authoritative vs. Non-Authoritative:**
    - **Authoritative:** The primary source for the zone's data.
    - **Non-Authoritative:** A server providing an answer from its cache (may be outdated).
* **Time to Live (TTL):** A setting in the DNS record that determines how many seconds a non-authoritative server is allowed to cache the information before requesting a fresh copy.

---

## 3. DNS Resource Records (RR)
The DNS configuration file contains specific records used for various network functions.

* **SOA (Start of Authority):** Located at the top of the file; contains zone serial numbers and refresh/retry timers.
* **A and AAAA Records:**
    - **A Record:** Maps a hostname to an **IPv4** address.
    - **AAAA Record:** Maps a hostname to an **IPv6** address.
* **CNAME (Canonical Name):** An alias that points one hostname to another hostname (e.g., `ftp` pointing to `server1`).
* **MX (Mail Exchanger):** Specifies the mail server responsible for receiving email for the domain.
* **NS (Name Server):** Lists the authoritative DNS servers for the zone.
* **PTR (Pointer):** Used in reverse lookup zones to map an IP address to a hostname.
* **TXT (Text):** Stores human or machine-readable text used for:
    - **SPF (Sender Policy Framework):** Lists authorized mail servers to prevent spoofing.
    - **DKIM (Domain Keys Identified Mail):** Stores public keys to verify digital signatures on emails.

---

## 4. DNS Resolution and Caching
When a client (resolver) requests a name, the process follows a recursive path if the data is not already cached.

* **Recursive Query Process:**
    - The local DNS server queries a **Root Server**.
    - The Root Server points to a **TLD Server** (.com).
    - The TLD Server points to the **Authoritative Server** for the domain.
    - The Authoritative Server provides the IP, which is then cached locally for future use.
* **Local Name Resolution:** Utilizing a **hosts file** (`windows/system32/drivers/etc/hosts`) to bypass DNS servers for specific manual mappings.

---

## 5. DNS Security and Encryption
Standard DNS sends data in cleartext. Several protocols have been developed to secure and private the process.

* **DNSSEC (Domain Name System Security Extensions):**
    - Adds digital signatures to DNS records.
    - Verifies that the response is authentic and has not been modified.
    - *Note: Does not encrypt the query; data is still visible to eavesdroppers.*
* **DoT (DNS over TLS):**
    - Encrypts DNS traffic over **TCP port 853**.
    - Uses similar protocols to web encryption to ensure privacy.
* **DoH (DNS over HTTPS):**
    - Encrypts DNS traffic within standard HTTPS packets over **TCP port 443**.
    - Blends in with regular web traffic, making it difficult to block or monitor.
