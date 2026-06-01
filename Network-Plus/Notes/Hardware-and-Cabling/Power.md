# IT Power and Electrical Systems

## 1. Electrical Units of Measurement
Understanding how electricity is measured is essential for calculating power requirements and ensuring safety.

| Unit | Abbreviation | Analogy | Description |
| :--- | :---: | :--- | :--- |
| **Ampere (Amp)** | **A** | Hose Diameter | The rate of electrons moving past a point (Current). |
| **Voltage (Volt)** | **V** | Water Pressure | The electrical "pressure" flowing through a wire. |
| **Watt (Watt)** | **W** | Total Water Flow | The total amount of power being used. |

**Calculation**: `Volts (V) x Amps (A) = Watts (W)`
*Example: A device on a 120V source drawing 0.5A uses 60 Watts.*

---

## 2. Power Types: AC vs. DC

### Alternating Current (AC)
* **Symbol**: Wavy line (representing frequency).
* **Usage**: Ideal for long-distance distribution; the type of power found in wall outlets.
* **Standards**:
    * **US/Canada**: 110–120V at 60 Hz.
    * **Europe**: 220–240V at 50 Hz.

### Direct Current (DC)
* **Symbol**: Solid line over dashed lines.
* **Usage**: Used by internal electrical components (CPUs, motherboards). Current moves in a single direction at a constant voltage.
* **Conversion**: Power supplies (internal or "bricks" on a cord) convert the AC from the wall into the DC required by the device.

---

## 3. Uninterruptible Power Supplies (UPS)
A UPS provides backup power via batteries during an outage and protects against power quality issues.

### Common Power Issues
* **Brownout**: A drop in voltage.
* **Surge**: A spike in voltage.

### UPS Types
1. **Offline / Standby**: Only kicks in when power fails. There is a small "gap" in power that may cause sensitive devices to reboot.
2. **Line-Interactive**: Adjusts internal voltage to compensate for brownouts without switching fully to battery.
3. **Online / Double-Conversion**: The device always runs off the battery, which is constantly charged. This provides the highest level of protection with zero transfer time.

---

## 4. Power Distribution Units (PDU)
A PDU is more than just a power strip; in a data center, it is an intelligent management device.
* **Form Factor**: Usually rack-mountable.
* **Management**: Often includes an Ethernet port and a web server.
* **Remote Control**: Allows administrators to remotely monitor power usage or "power cycle" (reboot) a specific device by toggling an individual outlet.

---

## 5. Electrical Safety
* **Disconnect First**: Always unplug a device before working on internal components.
* **Capacitor Danger**: Some components (like CRT monitors and laser printers) store a lethal charge in **capacitors** even after being unplugged.
* **Grounding**: Never connect yourself to a ground wire or any part of an electrical system that could potentially become energized.
