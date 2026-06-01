# ARP vs. NDP Lab
---

## Lab Environment and Tooling

This lab is built and executed entirely within the **Cisco Packet Tracer** emulation platform. 
The software provides a simulated network sandbox that models network interface cards, media links, and switch backplane logic. 
This allows us to configure devices, run protocols, and capture the resulting ARP and NDP table outputs exactly as they would appear on real physical network hardware.

---

## 1. Objective

To construct a local network segment and analyze how IPv4 (ARP) and IPv6 (NDP) map network-layer IP addresses to the same physical hardware MAC address.

---

## 2. Topology and Equipment Layout

<img width="714" height="156" alt="image" src="https://github.com/user-attachments/assets/a888a3b5-2c41-4eb0-bc39-8ea4d6986e88" />

* **End Devices:** 2 PCs (labeled **PC1** and **PC2**)
* **Switching Fabric:** 1 Cisco Catalyst 2960 Switch
* **Media:** 2 Copper Straight-Through Cables

### Connections:

* **PC1** (FastEthernet0) Connected to **Switch** (FastEthernet0/1)
* **PC2** (FastEthernet0) Connected to **Switch** (FastEthernet0/2)

---

## 3. Interface Addressing Matrix

### PC1 Configuration

<img width="1052" height="359" alt="image" src="https://github.com/user-attachments/assets/339dbd52-1755-44f6-beb7-bb148fa26b9f" />

* **IPv4 Address:** `192.168.1.10`
* **Subnet Mask:** `255.255.255.0`
* **IPv6 Address:** `2001:db8::10`
* **Prefix Length:** `64`

### PC2 Configuration

<img width="879" height="370" alt="image" src="https://github.com/user-attachments/assets/47224ec6-7954-48f2-b2c4-0ea996480c3d" />

* **IPv4 Address:** `192.168.1.20`
* **Subnet Mask:** `255.255.255.0`
* **IPv6 Address:** `2001:db8::20`
* **Prefix Length:** `64`

---

## 4. Part 1: IPv4 Address Resolution Protocol (ARP) Execution

<img width="439" height="398" alt="image" src="https://github.com/user-attachments/assets/b4cb7abe-3a46-4b5a-8546-fdc21593d797" />

1. Access the **Command Prompt** on **PC1**.
2. Query the initial IPv4 address resolution table:
```cmd
arp -a

```


*Output: No ARP Entries Found.*
3. Initiate an ICMPv4 Echo Request from PC1 to PC2:
```cmd
ping 192.168.1.20

```


4. Re-query the IPv4 address resolution table to capture the learned mapping:
```cmd
arp -a

```



### Captured Data Output:

```text
Internet Address      Physical Address      Type
192.168.1.20          0010.119b.b2cd        dynamic

```

---

## 5. Part 2: IPv6 Neighbor Discovery Protocol (NDP) Execution

<img width="542" height="299" alt="image" src="https://github.com/user-attachments/assets/f131f631-df6a-4ff8-b850-160941959c15" />

1. Remain in the **PC1 Command Prompt**.
2. Query the initial IPv6 neighbor cache table:
```cmd
netsh interface ipv6 show neighbors

```


*Output: None*
3. Initiate an ICMPv6 Echo Request from PC1 to PC2:
```cmd
ping 2001:db8::20

```


4. Re-query the IPv6 neighbor cache table to capture the learned mapping:
```cmd
netsh interface ipv6 show neighbors

```



### Captured Data Output:

```text
Interface FastEthernet0: FastEthernet

Internet Address                             Physical Address    Type
-------------------------------------------------------------------------
2001:db8::20                                 0010.119b.b2cd      Permanent

```

---

## 6. Data Analysis and Lab Findings

By comparing the experimental data captured in Part 1 and Part 2, the following network behaviors are confirmed:

* **Protocol Independence:** IPv4 utilizes broadcast-based Address Resolution Protocol (ARP) functions, while IPv6 replaces this with multicast-based Neighbor Discovery Protocol (NDP) actions.
* **Hardware Binding Resolution:** Despite running different network-layer protocols, the logical IPv4 destination (`192.168.1.20`) and the logical IPv6 destination (`2001:db8::20`) both resolve to the exact same physical hardware MAC layer identifier: `0010.119b.b2cd`.
* **Conclusion:** This data proves that changing the network-layer protocol version does not alter the underlying hardware interface requirements; both operational stacks exist purely to discover the same physical hardware address needed to move data across the local switch fabric.
