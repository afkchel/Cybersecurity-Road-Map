### 🔍 Practical Lab: Observing DNS TTL Decay

#### Steps:
1. Ran `nslookup -debug google.com` twice with a 7-second interval.
2. Observed the **TTL (Time to Live)** value in the response.

<p align="center">
  <img src="https://github.com/user-attachments/assets/a5c0d7f1-efd4-4af5-ba46-bd039edfe77b" width="45%" />
  <img src="https://github.com/user-attachments/assets/5345d7fa-30c8-4b1a-b909-08f28f203837" width="45%" />
</p>

#### Analysis:
*   **DNS TTL is measured in seconds**, unlike IP TTL which uses hops.
*   In the first capture, the TTL was **128** seconds.
*   In the second capture (7 seconds later), the TTL dropped to **121** seconds.

**Conclusion:** This confirms that my local system is caching the DNS record. Once this timer hits **0**, my PC will discard the entry and perform a fresh recursive lookup to get an updated IP address.
