# Software-Defined Networking (SDN) & SD-WAN 

## 1. The Virtualization Challenge
The primary challenge in modern networking is transitioning physical hardware functions (routers, switches, firewalls) into virtualized environments. 
To achieve this, networking components are broken down into three distinct functional "planes".
By creating software versions of these planes, networking can be deployed almost anywhere in a virtual environment with increased functionality.

---

## 2. The Three Planes of Networking
Networking devices are categorized into three layers based on their specific roles.

| Plane | Also Known As | Primary Function | Examples |
| :--- | :--- | :--- | :--- |
| **Data Plane** | Infrastructure Layer | The "heavy lifting"; handles actual data forwarding. | Trunking, Encrypting, NAT, Forwarding traffic. |
| **Control Plane** | Control Layer | Determines where data should go by referencing tables. | Routing tables, Switching tables, NAT tables. |
| **Management Plane** | Application Layer | Allows administrators to manage and configure the device. | SSH, Web-based consoles, Management front ends. |

---

## 3. Software-Defined WAN (SD-WAN)
SD-WAN stands for **Software-Defined Networking in a Wide Area Network**. 
It was specifically designed to handle the complexities of cloud-based environments where applications no longer reside in a single central data center.

### Key Characteristics of SD-WAN:
*   **Application Aware**: The network can identify which application is being used (e.g., email vs. database) and route it to the closest specific service provider.
*   **Zero-Touch Provisioning**: Allows remote routers and switches to update themselves automatically without user intervention whenever a service location changes.
*   **Transport Agnostic**: Designed to work over any connection type, including high-speed fiber, 5G, or DSL.
*   **Central Policy Management**: Policies are configured on one central console and pushed out to all SD-WAN routers automatically.

---

## 4. Evolution of Connectivity
### Traditional WAN
In the past, remote sites connected via a static WAN link to a centralized data center where all email, applications, and databases were stored.

### Modern SD-WAN
Today, services are spread across various cloud providers globally. 
SD-WAN allows remote sites to access the data center for internal resources while connecting 
**directly** to cloud-based services for email or web applications, optimizing the path for each specific task.
