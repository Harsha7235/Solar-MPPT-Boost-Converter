Solar MPPT Boost Converter — 24 V Output
A hardware-oriented solar power conversion project involving the schematic design and PCB layout of an Arduino-assisted boost-converter stage. The design was created in KiCad and is intended to step up a lower DC input from a solar source to a nominal 24 V output.
Project status: Schematic and PCB design/fabrication work completed by the project author. The screenshots show the circuit schematic and routed PCB layout. Do not interpret the nominal output label as proof of a regulated 24 V output under every input/load condition; measured performance data should be added after testing.

Repository name
Solar-MPPT-Boost-Converter
Repository description
KiCad schematic and PCB design for an Arduino-assisted solar MPPT boost-converter prototype with a nominal 24 V output.
Project overview
The project combines a boost-converter power stage with a microcontroller-based control/monitoring arrangement. The visible schematic contains an Arduino Nano, an INA219 current/voltage-monitoring IC, an inductor, a Schottky power diode, a MOSFET switching device, input/output capacitors, and supporting gate/feedback components.

The intended system-level workflow is:
1. Accept a DC input from a solar source.
2. Use a boost power stage to raise the input voltage.
3. Use the Arduino-based control arrangement for the intended MPPT/control logic.
4. Monitor electrical quantities through the INA219 interface.
5. Provide a nominal 24 V output at the output connector.
Important: The supplied screenshots establish the circuit and PCB design elements, but do not show the complete MPPT firmware, a solar-panel test setup, calibration procedure, closed-loop control results, or measured efficiency. Add those details only when they are implemented and verified.
Hardware visible in the schematic
Reference / component	Value or part marking shown	Intended role
A1	Arduino Nano (V3.x footprint)	Microcontroller platform for control and monitoring
U1	INA219AD	I²C-based voltage/current/power monitoring
L1	220 µH	Boost-converter energy-storage inductor
D1	MBR1060	Schottky rectifier in the boost power stage
Q1	P30N06L	MOSFET switching device
C1, C2	470 µF	Bulk input/output filtering capacitors (confirm exact net placement from the schematic)
C3, C4	100 nF	High-frequency bypass/decoupling capacitors
R1	10 Ω	Gate-series resistor as drawn
R2	100 kΩ	Gate pull-down resistor as drawn
J1	2-pin connector	Input connection as labelled in the schematic
J2	2-pin connector	Output connection labelled VOUT_24V / GND
J3	2-pin connector	Additional board connection; verify its final intended use from the netlist


Part numbers and values above are transcribed from the provided schematic image. Confirm the exact manufacturer datasheets, pinouts, voltage/current ratings, capacitor polarity, and connector functions before applying power.
Design files
Upload the native KiCad project files to this repository so that the design can be inspected and edited:
- *.kicad_pro — KiCad project
- *.kicad_sch — schematic
- *.kicad_pcb — PCB layout
- fabrication/ — Gerber files, drill files, and fabrication notes (if generated)
- images/ — schematic and PCB screenshots
- firmware/ — Arduino source code (if available)
The screenshots alone are not a substitute for the editable KiCad source files or manufacturing outputs.
Design workflow
1. Schematic capture: Place the power-stage, sensing, controller, passive components, and connectors in KiCad.
2. Electrical connections: Connect the boost stage, sensing interface, controller pins, input, and output nets.
3. PCB placement: Arrange the components on the board while considering power-path length, switching-node area, grounding, and component accessibility.
4. Routing: Route the power and signal connections in the PCB editor. The supplied board image shows routed copper and the component footprints.
5. Fabrication preparation: Generate and inspect Gerber/drill outputs and verify the board against the schematic before manufacturing.
6. Bring-up and testing: Test with a current-limited bench supply and suitable load before connecting a solar panel or valuable equipment.
Power-electronics design considerations
A boost converter can produce an output voltage higher than its input, but the actual output depends on the input range, switching frequency, duty cycle, inductor, diode, MOSFET, load, feedback method, and losses.

For a practical MPPT implementation, document and validate:
- Solar-panel voltage/current operating range.
- MPPT algorithm used (for example, Perturb and Observe or Incremental Conductance), if implemented.
- PWM frequency and duty-cycle limits.
- Voltage/current sensing calibration and sampling rate.
- Output-voltage regulation method and over-voltage protection.
- Input undervoltage, output overcurrent, thermal, and short-circuit protection.
- Inductor saturation current, MOSFET safe operating area, diode rating, capacitor ripple-current rating, and PCB copper-current capacity.
The ideal continuous-conduction boost relationship is:
\[
V_{out} = \frac{V_{in}}{1-D}
\]
where D is the switch duty cycle. This is an ideal relationship, not a measured performance claim; real designs have losses and operating limits.
Safety and validation
This is a switching power-electronics circuit. Incorrect wiring, component polarity, PCB clearance, grounding, or control settings can damage hardware or cause burns/fire.

Before powering the board:
- Check the schematic-to-PCB consistency and run KiCad ERC and PCB DRC.
- Inspect solder joints, component orientation, connector polarity, and MOSFET/diode pinouts.
- Verify there are no shorts between input, output, and ground.
- Confirm the voltage ratings of all capacitors and semiconductors exceed the maximum possible circuit voltage with suitable margin.
- Start with a current-limited bench supply and a dummy load.
- Increase input voltage and load gradually while monitoring the MOSFET, diode, inductor, and capacitors for heating.
- Measure input voltage/current, output voltage/current, ripple, and efficiency before describing the converter as tested or regulated.
Do not connect the board directly to a battery, panel, or load until the design has passed these checks.
Results
The currently supplied project evidence is the KiCad schematic and PCB layout screenshots. Add a measured-results table here after bench testing:
Parameter	Measured result
Solar/DC input voltage range	To be measured
Input current	To be measured
Output voltage under load	To be measured
Output current / load	To be measured
Switching frequency	To be confirmed
Efficiency	To be measured
Output ripple	To be measured
Thermal performance	To be measured


Suggested repository structure
Solar-MPPT-Boost-Converter/
├── README.md
├── kicad/
│   ├── project.kicad_pro
│   ├── project.kicad_sch
│   └── project.kicad_pcb
├── fabrication/
│   ├── gerber/
│   └── drill/
├── firmware/
├── images/
│   ├── schematic.png
│   └── pcb-layout.png
└── docs/
    └── test-results.md
Author
P.Harsha Vardhan Reddy
B.Tech
AI & DS(CPS_S)
Amrita Vishwa Vidyapeetham, Coimbatore 

Designed and fabricated as a hands-on project in solar power electronics, embedded control, and PCB design.
