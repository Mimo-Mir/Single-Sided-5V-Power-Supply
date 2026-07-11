# Single-Sided 5V Regulated Power Supply

A compact **single-sided 5V regulated linear power supply** designed using **KiCad 9** and built around the **LM7805 voltage regulator**.

This project was developed as part of my PCB design learning journey to gain hands-on experience with the complete hardware development workflow—from schematic capture and PCB layout to electrical verification, 3D visualization, Gerber generation, and project documentation.

In addition to PCB design, this project demonstrates the basic design principles of a regulated linear power supply, including rectification, filtering, voltage regulation, and component selection.

---

# Project Preview

## PCB Layout

![PCB Layout](Docs/pcb-layout.png)

## 3D View (Front)

![3D Front](Docs/pcb-3d-front.png)

## 3D View (Back)

![3D Back](Docs/pcb-3d-back.png)

## Schematic

![Schematic](Docs/schematic.png)

---

# About This Project

The primary objective of this project was to learn professional PCB design using **KiCad 9** while designing a simple regulated power supply suitable for educational and low-power embedded applications.

Although the electrical circuit is based on the widely used **LM7805 linear voltage regulator**, the project focuses on understanding the complete PCB development process, including:

- Electronic schematic design
- Component selection
- Footprint assignment
- PCB layout
- Manual routing
- Electrical verification
- Manufacturing file generation
- Hardware project documentation
- Version control using Git and GitHub

The completed board is designed as a **single-sided through-hole PCB**, making it easy to assemble, inspect, and understand for students, beginners, and electronics hobbyists.

---

# Design Objectives

The project was developed with the following objectives:

- Design a functional regulated 5V power supply using the LM7805.
- Practice schematic capture using KiCad 9.
- Learn proper footprint assignment.
- Design a manufacturable single-sided PCB.
- Perform ERC (Electrical Rules Check) and DRC (Design Rules Check).
- Generate fabrication-ready Gerber files.
- Document the complete design process professionally.
- Understand the importance of power supply filtering and voltage regulation.

---

# Features

- Single-sided PCB design
- Through-hole components (easy to solder)
- Regulated 5V DC output using LM7805
- Full-wave bridge rectifier
- Large input smoothing capacitor
- LM7805 datasheet-recommended bypass capacitors
- Power indicator LED
- Manual PCB routing
- Ground copper pour
- ERC verified
- DRC verified
- 3D PCB visualization
- Manufacturing-ready Gerber files
- Complete GitHub documentation

---

# Design Specifications

| Parameter | Value |
|-----------|-------|
| Input Supply | 9V AC Transformer |
| Rectifier | Full-Wave Bridge Rectifier |
| Output Voltage | 5V DC |
| Maximum Output Current | **500 mA** |
| Voltage Regulator | LM7805 |
| Main Filter Capacitor (C1) | **3300 µF** |
| Input Bypass Capacitor (C2) | **0.33 µF** |
| Output Bypass Capacitor (C3) | **0.1 µF** |
| PCB Type | Single-Sided |
| Mounting Style | Through-Hole (THT) |
| PCB Design Software | KiCad 9 |
| Routing | Manual |
| Ground Plane | Copper Pour |
| Manufacturing Files | Gerber |

---

# Design Assumptions

The following assumptions were used during the design of this project:

- Input supplied from a **9V AC transformer**.
- Maximum continuous output current of **500 mA**.
- Ambient operating temperature of approximately **25°C**.
- Intended for low-power embedded systems and educational applications.
- Designed as a linear regulated power supply where efficiency is secondary to simplicity and ease of understanding.

These assumptions are important because component selection, filtering, thermal performance, and regulator operation depend on the expected load conditions.

---

# Project Overview

The circuit converts a **9V AC input** into a regulated **5V DC output** through four main stages:

## 1. AC to DC Rectification

A full-wave bridge rectifier converts the incoming AC voltage into pulsating DC.

---

## 2. Input Filtering

A **3300 µF electrolytic capacitor (C1)** smooths the rectified voltage by reducing ripple before it reaches the voltage regulator.

This larger capacitor was selected to improve ripple performance for the intended **500 mA maximum output current**.

---

## 3. Voltage Regulation

An **LM7805 linear voltage regulator** provides a stable **5V DC output** over a range of load conditions.

The regulator includes internal:

- Current limiting
- Thermal shutdown
- Safe operating area protection

making it suitable for educational and low-power applications.

---

## 4. High-Frequency Decoupling

To improve regulator stability, two ceramic bypass capacitors are placed close to the LM7805:

- **0.33 µF (C2)** at the regulator input
- **0.1 µF (C3)** at the regulator output

These capacitor values follow the recommendations provided in the LM7805 datasheet and help suppress high-frequency noise while improving transient response.

---

# Components Used

| Component | Quantity | Purpose |
|-----------|:-------:|---------|
| LM7805 Voltage Regulator | 1 | Regulates the output to a stable 5V DC |
| Bridge Rectifier | 1 | Converts AC input into pulsating DC |
| 3300 µF Electrolytic Capacitor (C1) | 1 | Smooths the rectified voltage and reduces ripple |
| 0.33 µF Ceramic Capacitor (C2) | 1 | LM7805 input bypass capacitor for stability |
| 0.1 µF Ceramic Capacitor (C3) | 1 | LM7805 output bypass capacitor for stability |
| 330 Ω Resistor | 1 | Limits LED current |
| 2-Pin Screw Terminal | 2 | Input and output power connections |

---

# Why These Components?

### LM7805

The LM7805 is a widely used linear voltage regulator capable of providing a regulated **5V output** with minimal external components. It also includes built-in thermal shutdown and current limiting, making it an excellent choice for beginner-friendly power supply designs.

---

### Bridge Rectifier

The bridge rectifier converts the incoming **9V AC** into pulsating DC, allowing the regulator to operate from a transformer-based AC supply.

---

### 3300 µF Electrolytic Capacitor

The large electrolytic capacitor significantly reduces ripple voltage after rectification.

For the intended **500 mA load**, a higher capacitance improves voltage smoothing and helps maintain sufficient input voltage for proper LM7805 regulation.

---

### 0.33 µF and 0.1 µF Ceramic Capacitors

These capacitors are placed close to the regulator input and output pins to improve high-frequency filtering and regulator stability.

Their values follow the recommendations provided in the LM7805 datasheet.
---

### Screw Terminals

The screw terminals provide secure and reusable connections for both the AC input and regulated DC output.

# Electrical Design Considerations

Although this project was primarily created to learn PCB design, several engineering considerations were incorporated to improve the reliability and stability of the power supply.

The design follows the typical architecture of a linear regulated power supply:

```text
9V AC
   │
Bridge Rectifier
   │
3300 µF Filter Capacitor
   │
0.33 µF Bypass Capacitor
   │
LM7805 Voltage Regulator
   │
0.1 µF Bypass Capacitor
   │
5V DC Output
```

Each stage performs a specific function to convert the AC input into a clean and regulated 5V DC output.

---

# Design Calculations

## 1. Rectified DC Voltage

The circuit is designed to operate from a **9V AC transformer**.

The peak voltage after rectification can be approximated as:

**Vpeak = VAC × √2**

For a 9V AC input:

```
Vpeak ≈ 9 × 1.414
      ≈ 12.7 V
```

After accounting for the voltage drop across the bridge rectifier (approximately 1.4V), the capacitor charges to approximately:

```
VDC ≈ 11.3 V
```

This provides sufficient input voltage for the LM7805 to regulate the output to 5V.

---

## 2. Input Filter Capacitor Selection

After rectification, the voltage contains ripple.

A large electrolytic capacitor stores energy between the peaks of the rectified waveform, reducing ripple voltage before the regulator.

For this design, a **3300 µF capacitor** was selected.

Compared to smaller values, the larger capacitance provides:

- Lower ripple voltage
- Improved load regulation
- Better support for the intended 500 mA load
- Increased stability during transient current demands

---

## 3. Bypass Capacitors

Two ceramic capacitors are used near the LM7805.

### Input Capacitor (C2)

Value:

```
0.33 µF
```

Purpose:

- Filters high-frequency noise
- Improves regulator stability
- Recommended by the LM7805 datasheet

---

### Output Capacitor (C3)

Value:

```
0.1 µF
```

Purpose:

- Prevents high-frequency oscillation
- Improves transient response
- Reduces output noise
- Recommended by the LM7805 datasheet

Both capacitors are placed as close as possible to the regulator pins to maximize their effectiveness.

---

# Thermal Considerations

The LM7805 is a **linear voltage regulator**, meaning excess voltage is dissipated as heat.

The power dissipated by the regulator can be estimated using:

```
P = (Vin − Vout) × Iout
```

Assuming:

- Input voltage ≈ 11.3V DC
- Output voltage = 5V
- Maximum output current = 500 mA

```
P = (11.3 − 5) × 0.5

P ≈ 3.15 W
```

A power dissipation of approximately **3 W** can cause the regulator to become hot during continuous operation.

For sustained operation at the maximum rated current, a suitable heatsink is recommended to maintain safe operating temperatures.

---

# Why a Linear Regulator?

Several voltage regulation methods are available, including switching regulators and linear regulators.

For this project, the **LM7805** was selected because it offers:

- Simple circuit design
- Minimal external components
- Low cost
- High reliability
- Excellent educational value

Although switching regulators provide much higher efficiency, the LM7805 is easier to understand and is commonly used when learning basic power supply design.

---

# PCB Design Workflow

The PCB was developed using the same workflow commonly followed in professional PCB design.

The complete process consisted of:

1. Creating the schematic.
2. Selecting appropriate components.
3. Assigning footprints.
4. Importing the schematic into the PCB editor.
5. Arranging components for efficient routing.
6. Manually routing all traces.
7. Creating a ground copper pour.
8. Running ERC and DRC verification.
9. Inspecting the PCB using KiCad's 3D Viewer.
10. Generating Gerber files for fabrication.

Following this workflow helped ensure that the design was electrically correct, manufacturable, and well documented.

---

# 1. Schematic Design

The project began by creating the complete circuit schematic in **KiCad 9**.

During this stage:

- All electronic components were selected.
- Electrical connections were completed.
- Power symbols were added.
- Net labels were used where appropriate.
- Component values were assigned.
- Electrical connectivity was verified.

A clean schematic is the foundation of a reliable PCB design and helps reduce errors during later stages of development.

---

# 2. Footprint Assignment

Each schematic symbol was assigned an appropriate physical footprint before PCB layout.

The selected footprints match standard through-hole components, making assembly straightforward for beginners.

The assigned footprints include:

- TO-220 package for the LM7805
- Through-hole electrolytic capacitors
- Ceramic disc capacitors
- LED
- Resistors
- Screw terminals
- Bridge rectifier

Correct footprint assignment ensures that the physical components fit properly during PCB assembly.

---

# 3. Component Placement

Once the PCB was created from the schematic, components were arranged before routing.

The placement process focused on:

- Keeping related components close together.
- Minimizing unnecessary trace lengths.
- Placing bypass capacitors close to the LM7805.
- Improving routing efficiency.
- Maintaining adequate spacing for soldering and inspection.

Proper placement significantly simplified the routing process and improved the overall appearance of the PCB.

---

# 4. Manual Routing

Because the PCB is single-sided, all traces were manually routed on one copper layer.

Manual routing provided better control over:

- Trace length
- Routing clarity
- Component accessibility
- Manufacturing simplicity

Several component placements were adjusted during routing to achieve a clean and practical layout.

The final routing avoids unnecessary bends and keeps the board easy to understand for educational purposes.

# 5. Ground Copper Pour

After completing the routing, a **Ground (GND) Copper Pour** was added across the PCB.

Using a ground plane offers several advantages:

- Reduces unused copper areas.
- Improves grounding throughout the board.
- Simplifies ground routing.
- Can slightly improve heat distribution.
- Provides a cleaner and more professional PCB layout.

After creating the copper pour, the filled zones were updated to ensure all ground connections were electrically connected.

---

# 6. Electrical Rules Check (ERC)

Before PCB layout, an **Electrical Rules Check (ERC)** was performed.

ERC verifies the logical correctness of the schematic by checking for issues such as:

- Missing electrical connections
- Unconnected pins
- Incorrect power connections
- Missing power flags
- Electrical rule violations

Any reported issues were reviewed and corrected before continuing with the PCB layout.

Running ERC helped ensure that the schematic accurately represented the intended electrical circuit.

---

# 7. Design Rules Check (DRC)

After completing the PCB layout, a **Design Rules Check (DRC)** was performed.

Unlike ERC, which validates the schematic, DRC checks the physical PCB layout.

The following items were verified:

- Trace clearances
- Minimum spacing between pads
- Track width violations
- Overlapping footprints
- Board outline integrity
- Manufacturing rule compliance

Passing DRC provides confidence that the PCB is suitable for fabrication.

---

# 8. 3D Verification

Before generating manufacturing files, the PCB was inspected using **KiCad's 3D Viewer**.

The 3D inspection was used to verify:

- Component orientation
- Footprint placement
- Silkscreen readability
- Mechanical appearance
- Overall board layout

This step helps identify placement or orientation issues that may not be obvious in the 2D PCB editor.

---

# 9. Gerber File Generation

The final stage of the project was generating the manufacturing files required for PCB fabrication.

The generated files include:

- Top Copper Layer
- Bottom Copper Layer
- Top Silkscreen
- Bottom Silkscreen
- Top Solder Mask
- Bottom Solder Mask
- Edge Cuts
- Drill Files
- Gerber Job File

These files are included in the **gerbers/** directory and are ready for submission to a PCB manufacturer.

---

# Testing

Although this project was primarily created as a PCB design learning exercise, the circuit was designed using standard linear power supply design practices.

The following electrical characteristics are expected:

| Parameter | Expected Value |
|-----------|---------------:|
| Input Voltage | 9V AC |
| Output Voltage | 5V DC |
| Maximum Output Current | 500 mA |
| Voltage Regulation | Approximately ±5% |
| Regulator | LM7805 |

Future revisions of the project may include measured performance data such as:

- Output voltage under different loads
- Ripple voltage measurements
- Thermal measurements of the LM7805
- Efficiency calculations
- Load regulation
- Line regulation

---

# Design Limitations

Like any engineering design, this project has certain limitations.

- Designed primarily for educational purposes.
- Intended for low-power embedded applications.
- Maximum recommended continuous output current is **500 mA**.
- Linear voltage regulators are less efficient than switching regulators.
- Excess input voltage is dissipated as heat by the LM7805.
- Continuous operation near maximum load requires an appropriate heatsink.

Understanding these limitations is an important part of engineering design and helps determine whether the circuit is suitable for a particular application.

---

# Repository Structure

The repository is organized to separate documentation, PCB design files, and manufacturing outputs.

```text
Single-Sided-5V-Power-Supply/
│
├── Docs/
│   ├── schematic.png
│   ├── pcb-layout.png
│   ├── pcb-3d-front.png
│   └── pcb-3d-back.png
│
├── gerbers/
│   ├── *.gbr
│   ├── *.drl
│   └── *.gbrjob
│
├── LICENSE
├── README.md
├── .gitignore
│
├── Single-Sided 5V Power Supply.kicad_pro
├── Single-Sided 5V Power Supply.kicad_sch
└── Single-Sided 5V Power Supply.kicad_pcb
```

---

# Results

This project successfully demonstrates the complete workflow involved in designing a simple regulated power supply PCB using KiCad.

Through this project I gained practical experience with:

- Electronic schematic design
- PCB layout techniques
- Component footprint assignment
- Manual PCB routing
- Ground plane implementation
- ERC verification
- DRC verification
- 3D PCB inspection
- Gerber generation
- Git version control
- GitHub project documentation

Although the electrical circuit itself is relatively simple, completing the entire hardware development workflow provided valuable practical experience that extends beyond circuit design alone.

# Challenges & Lessons Learned

Every hardware project presents unique challenges, and this project was no exception. While the electrical circuit is relatively simple, designing a manufacturable PCB and documenting the complete engineering workflow provided valuable practical experience.

## Challenges

### Learning the KiCad Workflow

One of the first challenges was understanding how each stage of PCB development connects together—from schematic capture to PCB layout, verification, and manufacturing.

Working through the complete workflow gave me a much better understanding of professional PCB development practices.

---

### Component Placement

Achieving a clean component placement required several iterations.

I learned that spending additional time arranging components before routing greatly simplifies PCB layout and results in a cleaner, more maintainable design.

---

### Single-Sided PCB Routing

Routing every connection on only one copper layer was one of the most challenging aspects of the project.

Because routing flexibility is limited on a single-sided PCB, I had to reposition components multiple times before reaching a layout that balanced functionality, manufacturability, and readability.

---

### Understanding Electrical Verification

Before this project, I had limited experience using ERC and DRC.

Through this design, I learned that:

- **ERC (Electrical Rules Check)** validates the schematic.
- **DRC (Design Rules Check)** validates the PCB layout.

Both are essential steps before manufacturing a PCB.

---

### Engineering Documentation

Another important lesson was learning that a good engineering project is not only about creating a working circuit but also about documenting the design decisions.

While improving this project, I expanded the documentation to include:

- Design assumptions
- Component selection
- Electrical design considerations
- Thermal analysis
- Design limitations

These additions make the project more useful for anyone reviewing or learning from the design.

---

# Lessons Learned

This project helped me develop practical experience with:

- PCB design using KiCad 9
- Electronic schematic capture
- Component footprint assignment
- Manual PCB routing
- Single-sided PCB design
- Ground copper pours
- ERC verification
- DRC verification
- 3D PCB inspection
- Gerber file generation
- Git version control
- GitHub project documentation
- Basic linear power supply design
- Engineering documentation

One of the biggest lessons I learned is that PCB design is an iterative engineering process.

Designing a reliable PCB requires much more than simply connecting components—it involves planning, verification, documentation, and continuous improvement.

---

# Future Improvements

Although this project successfully meets its educational objectives, several improvements could be made in future revisions.

Future versions may include:

- Reverse polarity protection using a protection diode or MOSFET.
- Input fuse for improved safety.
- Power switch.
- Mounting holes for enclosure installation.
- Improved silkscreen labels.
- Wider PCB traces for higher current capability.
- Larger copper areas around the voltage regulator for improved heat dissipation.
- Output test points for easier measurements.
- Thermal performance measurements under load.
- Ripple voltage measurements using an oscilloscope.
- Double-sided PCB version with optimized routing.
- Switching regulator version for higher efficiency.

These improvements would further increase the robustness and practical usability of the design.

---

# Skills Demonstrated

This project allowed me to develop and practice the following technical skills:

### Electronics

- Linear power supply design
- Bridge rectifier circuits
- Voltage regulation using LM7805
- Capacitor selection
- Basic thermal considerations

### PCB Design

- Schematic capture
- Footprint assignment
- PCB layout
- Manual routing
- Ground plane implementation
- Single-sided PCB design
- Design rule verification
- Manufacturing file generation

### Software

- KiCad 9
- Git
- GitHub

### Engineering Practice

- Hardware documentation
- Design verification
- Version control
- Project organization

---

# Tools Used

| Tool | Purpose |
|------|---------|
| KiCad 9 | Schematic Capture and PCB Design |
| Git | Version Control |
| GitHub | Project Hosting and Documentation |

---

# References

The following resources were used during the development of this project:

- LM7805 Voltage Regulator Datasheet
- KiCad 9 Official Documentation
- Basic Linear Power Supply Design References
- PCB Design Best Practices

---

# Acknowledgements

This project was completed as part of my ongoing journey to learn electronics and PCB design.

It provided valuable hands-on experience in the complete PCB development process, from schematic creation and PCB layout to verification, documentation, and manufacturing file generation.

The project also reinforced the importance of engineering documentation, design verification, and continuous improvement through technical feedback.

I look forward to applying these lessons to more advanced embedded systems, power electronics, and PCB design projects in the future.

---

# License

This project is licensed under the **MIT License**.

See the **LICENSE** file for more information.
