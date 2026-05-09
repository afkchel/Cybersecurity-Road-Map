# Network Documentation 

## 1. Network Maps

Network maps are essential for visualizing the layout and connectivity of your infrastructure.

* **Physical Network Map**: Shows the actual physical layout, including cables, physical interfaces, and the specific hardware units.
* **Logical Network Map**: Provides a high-level view of how data flows, often grouping complex hardware into single locations (like a "cloud") to simplify the overview.
* **Rack Diagram**: A physical representation of a server rack as if you were standing in front of it. It helps technicians identify the exact Rack Unit (U) where a device is located.
* **Cable Map**: A diagram typically found in an IDF or MDF that shows the physical path of wires through the building (under floors or above ceilings). Each network drop is usually numbered to correlate with the patch panel.

---

## 2. Layered Documentation

Modern documentation often overlays multiple OSI layers to provide a complete picture:

* **Layer 1**: The physical interfaces and wires.
* **Layer 2**: MAC addresses and data link information.
* **Layer 3**: IP addresses associated with those physical and MAC addresses.

---

## 3. Asset Management

Tracking physical hardware is critical for both technical and financial operations.

* **Asset Tags**: Every device (laptops, routers, switches) should be labeled with a unique tag or barcode.
* **Asset Database**: A centralized database used to track ownership, physical location (via the assigned user), and warranty status.
* **Financial Tracking**: Asset tags help accounting departments track the depreciation of equipment over time.

---

## 4. IP Address Management (IPAM)

IPAM solutions provide a central console to plan and configure addressing schemes.

* **Tracking**: Maps specific users to IP addresses at specific dates and times, which is helpful for troubleshooting dynamic (DHCP) environments.
* **Planning**: Helps identify IP shortages or problems, allowing administrators to modify ranges for both IPv4 and IPv6.
* **Monitoring**: Consoles provide change logs, error logs, and utilization statistics.

---

## 5. Wireless Documentation

* **Site Survey**: A process used to identify all active access points and the frequencies they use, including those belonging to neighboring organizations.
* **Heat Map**: A visual representation of wireless signal propagation throughout a building, identifying areas of high or low signal strength.

---

## 6. Service Level Agreements (SLA)

An SLA is a contractual document between an organization and a service provider (like an ISP).

* **Uptime Requirements**: Defines the minimum level of service, such as "99.99% uptime."
* **Recovery Time**: May specify maximum allowed unscheduled downtime (e.g., no more than 4 hours) and the process for dispatching technicians or replacement hardware.
