# Hardware Optimization: Power over Ethernet and Transceiver Power Budgets

---

## 1. Power over Ethernet (PoE) Architecture

Power over Ethernet delivers electrical power alongside baseband data over a single twisted-pair copper cable, removing the need for separate electrical wiring for remote network devices.

### A. Power Sourcing Equipment (PSE) Layouts
* **Endspan:** A network architecture where power sourcing circuitry is built directly into the Ethernet switch ports.
* **Midspan:** A deployment configuration where a standard, non-PoE switch is paired with an inline standalone **power injector**. This midspan injector sits in the middle between the switch and the remote device to add electrical current to the line.

### B. PoE Standards Matrix
PoE configurations are defined by standard capacity limits that match different device power requirements:

| Standard Tier | Maximum DC Power Output | Maximum Current Rating | Typical Target Devices |
| :--- | :--- | :--- | :--- |
| **Original PoE** | **15.4 Watts** | 350 mA | Basic IP telephones, small wireless access points |
| **PoE+** | **25.5 Watts** | 600 mA | Larger smart phones, fixed security cameras |
| **PoE++ (Type 3)** | **51.3 Watts** | 600 mA | Laptops, cellular access points |
| **PoE++ (Type 4)** | **71.3 Watts** | 960 mA | High-draw Pan-Tilt-Zoom (PTZ) cameras, laptops |

> [!IMPORTANT]
> **Data Rate Support:** The PoE++ standard expands physical layer compatibility to support high-speed Ethernet standards, including **2.5-Gbps**, **5-Gbps**, and **10-Gbps** connections.

### C. Power Capacity Compatibility and Budgeting
* **Downstream Compatibility:** Power allocation compatibility does not scale upward. While a higher-tier PoE++ or PoE+ switch port can support a lower-draw legacy device, a PoE+ switch port cannot power a demanding PoE++ device.
* **Switch Wattage Ceilings:** Switches have a total maximum PoE power budget limit (e.g., **200 Watts** or **720 Watts**). Administrators must add up the maximum power draw of all connected devices to ensure the total remains under the total capacity of the switch to prevent power starvation issues.

---

## 2. Modular Transceiver Integration and Optical Power Budgets

Modular transceivers provide flexible physical interfaces for switching hardware. Maintaining reliable fiber links requires matching optical properties and calculating link loss budgets.

### A. Wavelength Verification
* **Matching Parameters:** Optical transceivers use specific light wavelengths to transmit data, such as **850 nanometers (nm)** or **1310 nanometers (nm)**. Operating wavelengths must match identically across the entire link and align with the correct fiber optic cable standard (multimode vs. single-mode).
* **Mismatch Symptoms:** Deploying mismatched wavelengths along an active link leads to signal loss, increased error counters, or a complete loss of overall network efficiency.
* **Physical Inspection Challenges:** Many transceivers look virtually identical from the outside. Because their tiny wavelength markings become hidden from view once inserted into a switch port, technicians must view interface data via the switch operating system or physically remove the transceiver to read its label.

### B. Optical Power Budget Calculations
To ensure that a light signal arrives with enough strength for the remote receiver to read it cleanly, administrators perform an optical power budget calculation.

* **Receiver Sensitivity Level:** The minimum usable signal strength an optical interface needs to cleanly receive and interpret incoming data payloads without corruption. This hardware ceiling is documented as a negative decibel per milliwatt value (e.g., **-17 dBm**).
* **The Mathematical Formula:**

  $$
  \text{Expected Received Power} =
  \text{Transmitter Output Power (dBm)} - \text{Total Medium Path Loss} $$
  
  $$
  \text{Total Medium Path Loss} =
  \text{Fiber Attenuation over Distance}
  +
  \text{Cumulative Losses from Connectors/Splices}
  $$

* **Link Integrity Validation:**
  * If the calculated *Expected Received Power* is closer to zero than the sensitivity threshold (e.g., a received power of **-14 dBm** on a transceiver rated for **-17 dBm**), the signal is strong enough and the link is valid.
  * If the calculated received power falls below the required threshold (e.g., a received power of **-20 dBm** on a transceiver rated for **-17 dBm**), the light is too faint, resulting in interface errors or total link failure.
