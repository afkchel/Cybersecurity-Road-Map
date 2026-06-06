# Non-Repudiation: Verifying Cryptographic Integrity and Origin

Non-repudiation is a foundational pillar of modern information security and cryptography. 
It ensures that when data is transmitted to a third party, the recipient has undeniable proof of the data's integrity and its origin. 
This creates a high assurance of authenticity, legally and technically preventing a sender from falsely denying that they originated the transaction.

---

## 1. Proof of Integrity

Proof of integrity provides a guarantee that any data received is accurate, consistent, and identical to the original version transmitted by the sender. 

* **The Mechanics of Hashing:** Cryptographic integrity relies heavily on hashing algorithms. A hashing function evaluates a raw plaintext payload and outputs a fixed,
short string of characters often referred to as a **message digest** or a **digital fingerprint**.
* **The Sensitivity Factor:** Because a hash acts as a unique data signature, even the slightest alteration to the underlying file will yield a radically different output.
* **Limitations of Standalone Hashes:** While a standard hash is exceptional at confirming that a file has not been altered or corrupted in transit, it operates independently of identity.
It proves that the payload matches the original digest, but it cannot verify *who* generated or sent the file.

---

## 2. Proof of Origin

To overcome the limitations of standalone hashing, security architectures implement proof of origin. This layer introduces authentication to validate the true creator or sender of a message.

* **Asymmetric Key Pairing:** Proof of origin relies on public key cryptography, which splits security parameters into an mathematically linked key pair: a **private key** and a **public key**.
* **Key Scoping Boundaries:**
  - **The Private Key:** Kept strictly confidential and known exclusively to the sender. No other node or individual possesses a copy.
  - **The Public Key:** Publicly accessible and freely distributed to anyone on the network.

---

## 3. The Digital Signature Pipeline

A **digital signature** successfully combines proof of integrity and proof of origin to establish non-repudiation. 
When an administrator signs an asset, a complex cryptographic pipeline takes place beneath the surface.

```
[ Sender: Alice ]
 1. Plaintext ("You're hired, Bob") ---> Run through Hashing Algorithm ---> Message Digest (Hash)
 2. Message Digest (Hash) ------------> Encrypted with Alice's Private Key ---> Digital Signature
 3. Plaintext + Digital Signature ----> Bundled and transmitted over the network

[ Recipient: Bob ]
 1. Digital Signature ---------------> Decrypted with Alice's Public Key ----> Extracted Sender Hash
 2. Received Plaintext --------------> Run through Hashing Algorithm -------> Manually Generated Hash
 3. Validation Check: Does Extracted Sender Hash == Manually Generated Hash? 
    - If YES: Data has zero changes (Integrity) AND could only come from Alice (Origin).
```
