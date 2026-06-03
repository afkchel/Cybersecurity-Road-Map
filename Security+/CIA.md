# The CIA Triad: Core Security Objectives and Foundations

The CIA Triad serves as the foundational framework for information technology security. It defines three core objectives that must be balanced to secure computing environments, data, and infrastructure.

```
          Confidentiality
                /\
               /  \
              /    \
             /______\
  Integrity          Availability

```

---

## 1. Confidentiality

Confidentiality ensures that private or sensitive information is prevented from being accessed by unauthorized individuals. 
The primary challenge is making data available to the right users while strictly enforcing boundaries against others.

### Implementation Mechanisms:

* **Encryption:** Converts plain text into cipher text so that anyone intercepting the data in transit cannot discern any meaningful information.
* **Access Controls:** Restricts permission footprints based on job function.
* **Multi-Factor Authentication:** Requires additional verification credentials during login, hardening user accounts against unauthorized access.

---

## 2. Integrity

Integrity ensures that data remains unaltered, accurate, and valid. 
It provides a mechanism to verify that data received by a recipient matches exactly what was transmitted by the originator, guaranteeing that no mid-transit modifications occurred.

### Implementation Mechanisms:

* **Hashing:** The sender generates a fixed mathematical string based on the data payload. The recipient recalculates the hash using the same function; if the strings match, data integrity is verified.
* **Digital Signatures:** Takes a hash and encrypts it using an asymmetric encryption algorithm. This mathematical bond verifies both data integrity and the authentic identity of the sender.
* **Certificates:** Used to systematically identify devices or individuals, embedding trusted verification layers into data transfers.
* **Non-Repudiation:** Achieved when an organization possesses absolute proof of integrity, making it impossible for the originating party to deny sending the information.

---

## 3. Availability

Availability ensures that authorized personnel maintain consistent, uninterrupted access to systems and data whenever needed.

### Implementation Mechanisms:

* **Fault Tolerance:** Engineering infrastructure with redundant components so that if a single hardware part fails, a backup automatically handles the operations with minimal or zero disruption.
* **System Patching:** Keeping operating systems and applications consistently updated to fix vulnerabilities, close security exploits, and maximize baseline stability.
