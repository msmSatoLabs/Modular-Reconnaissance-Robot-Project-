# Adaptive Modular Search & Rescue Robot Prototype (OCSEF)

**Honorable Mention — Orange County Science & Engineering Fair (OCSEF)**

*Utilizing Electromagnetic Conductivity and Modular Integration of Coordinated Sensor Systems to Develop Adaptive 3D-Printed Robots for Advanced Search and Rescue Operations*

**Problem Statement:** Mitigate the risks and logistical challenges associated with search and rescue operations in hazardous and structurally compromised environments.

A modular robotic system designed as a **proof-of-concept** for search and rescue (SAR) operations. The project explores the design, prototyping, and testing of a ground chassis with terrain-adaptive suspension and a drone module for aerial reconnaissance — combining coordinated sensors, modularity, and electromagnetic docking.

Many existing SAR robots take a "jack of all trades, master of none" approach — integrating too many components to handle every scenario, which makes them bulky, inefficient, and often suboptimal for any single task. This robot instead adapts its configuration to the specific rescue environment: if terrain is impassable by ground, the drone module detaches for aerial reconnaissance; if aerial reconnaissance isn't needed, all power is directed to terrain navigation. This situational adaptability is intended to make the system more effective in real-world rescue operations.

📺 **See [MEDIA.md](MEDIA.md) for build photos and testing clips.**

<p align="center">
  <img width="66%" alt="Assembled search-and-rescue robot: ground chassis and drone module" src="https://github.com/user-attachments/assets/d462ab23-48e2-430b-90d6-ca2aeaa525f3" />
</p>
<p align="center"><em>Assembled search-and-rescue robot, ground chassis and drone module.</em></p>

> **Status:** Prototype completed and field-tested across rocky, sandy, and uneven terrain. Recognized with an Honorable Mention at OCSEF. As a proof-of-concept, it surfaced clear next steps around structural weight and part durability — documented below and driving the current redesign.

**Team:** Developed by a two-person team — Matthew Sato and Rohan Hablani — at Arnold O. Beckman High School (Teacher: Claudia Le). Sato led CAD, mechanical part design, manufacturing, and assembly (chassis, suspension, planetary gear pods, docking hardware). Hablani led sensor selection/integration and onboard programming (Raspberry Pi/Arduino, FFT sensor calibration, detection software).

---

## Contents

- [Abstract](#abstract)
- [Background Research](#background-research)
- [Project Overview](#project-overview)
- [Target Specifications](#target-specifications)
- [Design Philosophy](#design-philosophy)
- [Engineering Solution & Architecture](#engineering-solution--architecture)
- [Materials & Cost Breakdown](#materials--cost-breakdown)
- [Procedures](#procedures)
- [Build & Testing Process](#build--testing-process)
- [Results & Data](#results--data)
- [Design Iterations](#design-iterations)
- [Key Engineering Challenges](#key-engineering-challenges)
- [Discussion](#discussion)
- [Conclusion](#conclusion)
- [Future Development](#future-development)
- [Reflection & Application](#reflection--application)
- [Project Timeline](#project-timeline)
- [Skills Demonstrated](#skills-demonstrated)
- [References](#references)
- [License](#license)

---

## Abstract

Each year, natural disasters cause over 60,000 casualties globally, with earthquakes, floods, and other hazards leading to substantial loss of life (World Health Organization, 2020). This project introduced a modular robotic system designed to enhance search and rescue (SAR) operations in hazardous environments where human responders face critical risks. The system accesses difficult terrain and confined spaces while collecting real-time environmental data, targeting tasks humans are often too slow or unable to handle safely.

Each module was designed with CAD/CAM: a ground-based chassis with suspension for terrain traversal, and a drone for reconnaissance. Both modules link via an electromagnetic connection and can travel together, in air or on land. Onboard sensors enable facial recognition, soft-sound detection, and movement tracking — critical data points for search and rescue. Testing data demonstrated the robot's ability to gather environmental information and perform tasks such as traversing uneven terrain and reaching elevated or obstructed locations where human responders would be less effective.

---

## Background Research

Search and rescue (SAR) operations face challenges that reduce efficiency and increase risk. Delays in locating victims drastically lower survival chances — survival in fire incidents drops from 75% to 28% after eight minutes, and in avalanche cases, chances fall from 92% to 30% after 35 minutes, approaching zero at two hours (Rauch et al., 2024). In mountain rescue operations, survival rate upon arrival of rescue teams is only 3.5% (Oshiro & Murakami, 2022). Rescue workers face high risk themselves, with trauma the leading cause of death and roughly 10% experiencing post-traumatic stress disorder (PMC, 2022).

<p align="center">
  <img width="66%" alt="Fig 1. Search and rescue helicopter" src="media/fig1-sar-helicopter.jpg" />
</p>
<p align="center"><em>Fig 1. Search and rescue helicopter (placeholder — source image from presentation not yet uploaded to repo).</em></p>

Current robotic SAR solutions struggle with terrain adaptability, high cost, and limited versatility, underscoring the need for a system that can navigate complex terrain, reduce rescuer risk, and improve SAR operations.

**Design criteria** — the system must be capable of:
- Navigating hazardous (e.g., toxic), elevated, and obstructed locations (confined/collapsed regions)
- Minimizing human intervention through autonomous data collection and hazard assessment
- Providing real-time environmental data (visual and sensor-based) to support rescue operations
- Withstanding extreme conditions while ensuring adaptability across diverse scenarios

**Design constraints:**
- Cost-effective, commercially available materials that still allow for widespread deployment potential
- Battery capacity limits operational time, requiring efficient energy management and recharging options
- Design must balance portability and functionality without excessive weight or bulk
- Testing must comply with safety regulations (FAA and local standards) and not interfere with others

---

## Project Overview

The development moved through three major design phases:

### 1. Initial Design Concept (Caltech M4-inspired)

Early concept combined aerial and ground locomotion into one unit, sharing a single battery between driving and flying. This "jack of all trades" approach limited flight time and hurt performance in both domains.

<p align="center">
  <img width="33%" alt="Early concept sketch: combined aerial-ground locomotion unit" src="https://github.com/user-attachments/assets/0b0c433c-c9c3-4324-b948-07eeff0f06b5" />
</p>
<p align="center"><em>Early concept sketch — combined aerial-ground locomotion unit. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="33%" alt="Early concept sketch: integrated propeller-wheel design" src="https://github.com/user-attachments/assets/862cbe90-e2a1-4213-a597-00bf147b056e" />
</p>
<p align="center"><em>Early concept sketch — integrated propeller-wheel design. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Early prototype iteration of the combined chassis-drone unit" src="https://github.com/user-attachments/assets/afe30da5-999b-4369-a589-cb968232d16b" />
</p>
<p align="center"><em>Early prototype iteration of the combined chassis-drone unit. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Early design with built-in propellers inside the wheels" src="https://github.com/user-attachments/assets/9a9b953c-cb70-4899-985d-2e321b29be0d" />
</p>
<p align="center"><em>Early design included built-in propellers inside the wheels, similar to Caltech's <a href="https://www.caltech.edu/about/news/new-bioinspired-robot-flies-rolls-walks-and-more">M4 robot</a>.</em></p>

### 2. Modular Multi-Robot Approach

Redesigned into three specialized robots: a car, a quadruped, and a drone. Integrating the quadruped proved too complex for the timeline, prompting further refinement.

<p align="center">
  <img width="66%" alt="Second iteration: three-robot modular concept" src="https://github.com/user-attachments/assets/ef1550b7-22bb-4f3c-ac2d-b031c644b8ce" />
</p>
<p align="center"><em>Second iteration — three-robot modular concept (car, quadruped, drone). (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="33%" alt="Quadruped module concept" src="https://github.com/user-attachments/assets/41f5edea-54b0-48dd-aa1a-2a9d8ff5253d" />
</p>
<p align="center"><em>Quadruped module concept, later dropped due to integration complexity. (Caption inferred from surrounding context — please verify.)</em></p>

### 3. Final Modular Prototype

Narrowed to car + drone, each purpose-built and dockable. This simplified the system while preserving combined functionality.

<p align="center">
  <img width="66%" alt="Final modular prototype: car and drone configuration" src="https://github.com/user-attachments/assets/56b2c632-443e-4ae2-b2d7-666a3e1d2897" />
</p>
<p align="center"><em>Final modular prototype — car and drone configuration. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="33%" alt="Final chassis assembly, side view" src="https://github.com/user-attachments/assets/ae7a85e9-8519-47f6-8cc7-605540c9b65c" />
</p>
<p align="center"><em>Final chassis assembly, side view. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Docking interface detail" src="https://github.com/user-attachments/assets/a8a0240a-e48e-4f79-b96b-590494d21161" />
</p>
<p align="center"><em>Docking interface detail. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Drone module attached to chassis via electromagnetic dock" src="https://github.com/user-attachments/assets/2e6b9860-916d-470f-ac26-a5d42a800c33" />
</p>
<p align="center"><em>Drone module attached to chassis via electromagnetic dock. (Caption inferred from surrounding context — please verify.)</em></p>

---

## Target Specifications

<div align="center">

| Specification             | Prototype Implementation                                   |
|----------------------------|:-------------------------------------------------------------|
| Application                | Search & rescue proof-of-concept                             |
| Ground speed               | ~1.0 m/s operational (up to ~1.7 m/s unloaded top speed)       |
| Chassis material           | PETG / PETG-CF (carbon fiber-infused plastic)                |
| Suspension                 | OGRC oil shock absorbers (multi-terrain)                     |
| Wheels                     | TPU + rubber                                                  |
| Drive motors (chassis)     | DC 300 RPM gearmotor (BEMONOC), 4×                             |
| Drone motors               | Brushless, quad propeller, 4×                                 |
| Chassis motor controller   | L298N Dual H-Bridge, 2×                                       |
| Drone motor controller     | 40A electronic speed controller (ESC), 4×                     |
| Electromagnetic docking    | Modular, wireless charging                                    |
| Sensors                    | Ultrasonic, IR/thermal camera, sound (FFT), force, environmental (gas/temperature) |
| Main controller            | Arduino Mega 2560 (chassis), Raspberry Pi 4 8GB / Ubuntu Linux (drone) |
| Battery                    | LiPo (4×) + 9V (2×)                                           |
| Camera                     | Infrared/thermal, Pi-compatible object recognition            |
| Fasteners                  | M3 & M5 screws + nuts                                          |
| CV joint                   | 177.8mm major, 4×                                              |
| Testing locations          | Local park, school, home                                       |

</div>

<p align="center">
  <img width="66%" alt="Assembled robot specification overview" src="https://github.com/user-attachments/assets/b3386e32-9cca-45df-a608-4c15a06aacd3" />
</p>
<p align="center"><em>Assembled robot, specification overview. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Chassis and drone modules, side by side" src="https://github.com/user-attachments/assets/93132a63-4a3b-4536-9777-8a8c42d2419b" />
</p>
<p align="center"><em>Chassis and drone modules, side by side. (Caption inferred from surrounding context — please verify.)</em></p>

---

## Design Philosophy

- **Adaptability:** Modular subsystems (chassis + drone) operate independently or combined, depending on the rescue scenario.
- **Manufacturability:** 3D-printed PETG/PETG-CF and off-the-shelf hardware, accessible for a school engineering lab.
- **Iterative Development:** Multiple redesign cycles targeting structural failures, particularly in the suspension and motor mounts.

<p align="center">
  <img width="66%" alt="Modular subsystem breakdown" src="https://github.com/user-attachments/assets/0176651f-dcb0-44d6-a7fd-224df04b25c9" />
</p>
<p align="center"><em>Modular subsystem breakdown — chassis and drone operating independently. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="3D-printed PETG/PETG-CF components" src="https://github.com/user-attachments/assets/18b7f62a-dab3-4bdf-be3b-f148c7f66baa" />
</p>
<p align="center"><em>3D-printed PETG/PETG-CF components prior to assembly. (Caption inferred from surrounding context — please verify.)</em></p>

---

## Engineering Solution & Architecture

The prototype integrates ultrasonic sensors for terrain mapping, a camera for real-time visual data, and additional environmental sensors to monitor conditions such as gas levels or temperature. These sensors let the robot navigate difficult terrain, access confined spaces, and gather data about its surroundings in scenarios where human responders would be inefficient or unable to operate. The CAD design emphasizes an integrated structure — each suspension arm attaches directly to the base, which houses electronics and facilitates docking.

<p align="center">
  <img width="66%" alt="Fig 2-6. Final CAD rendering and 3D-printed chassis" src="media/fig2-6-cad-chassis.jpg" />
</p>
<p align="center"><em>Fig 2–6. Final CAD rendering and 3D-printed chassis (placeholder — source images from presentation not yet uploaded to repo).</em></p>

### Ground-Based Chassis

Early designs with direct motor mounts failed — shafts bent or snapped under torque and impact. The chassis was redesigned around a planetary gear system to distribute load across multiple gears, trading some compactness for durability. CV joints and bearings handle power transmission and rotation.

<p align="center">
  <img width="66%" alt="Direct motor mount design, early iteration" src="https://github.com/user-attachments/assets/1b050f92-5261-4c66-afc5-398e476bace4" />
</p>
<p align="center"><em>Direct motor mount design, early iteration. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Planetary gear system integrated into chassis motor mount" src="https://github.com/user-attachments/assets/01cc31bc-ce2e-4d43-a5d2-fa148ffe99fe" />
</p>
<p align="center"><em>Planetary gear system integrated into chassis motor mount. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="CV joint and bearing assembly" src="https://github.com/user-attachments/assets/25dcd6f4-47c9-44f4-8ee5-9c5d5d830f48" />
</p>
<p align="center"><em>CV joint and bearing assembly for power transmission. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Chassis suspension assembly, close-up" src="https://github.com/user-attachments/assets/ae7d2a26-2ad1-4cb0-8c16-e282f1f8b87f" />
</p>
<p align="center"><em>Chassis suspension assembly, close-up. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Motor box assembly with planetary gear housing" src="https://github.com/user-attachments/assets/8bfbfd5d-9cb4-4b7d-b1ff-4e08c0c16f81" />
</p>
<p align="center"><em>Motor box assembly with planetary gear housing. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Wheel and CV joint connection" src="https://github.com/user-attachments/assets/3497c9a1-c978-433f-9d14-02a94913ce24" />
</p>
<p align="center"><em>Wheel and CV joint connection. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="33%" alt="Suspension arm, isolated view" src="https://github.com/user-attachments/assets/bd696f8b-01f6-41e3-bb23-786c174d18c9" />
</p>
<p align="center"><em>Suspension arm, isolated view. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Assembled chassis underside" src="https://github.com/user-attachments/assets/fd568181-77c4-40b3-9267-e55baadd7fb4" />
</p>
<p align="center"><em>Assembled chassis underside. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Fully assembled ground chassis" src="https://github.com/user-attachments/assets/45fad5c4-1471-4125-b71c-9dbe7780015b" />
</p>
<p align="center"><em>Fully assembled ground chassis. (Caption inferred from surrounding context — please verify.)</em></p>

### Drone Module

Quad brushless motors with propellers, a Pi-compatible camera, and an ultrasonic sensor make up the drone module, built for aerial scouting over debris and areas the chassis cannot reach. Electromagnetic docking enables modularity and wireless charging with the chassis.

---

## Materials & Cost Breakdown

<div align="center">

| Material (Main)              | Dimensions        | Quantity | Cost (Per Unit) | Cost (Total) | Use                              |
|-------------------------------|--------------------|----------|------------------|---------------|-----------------------------------|
| PETG-CF Filament               | 1.75 ± 0.03 mm     | ~1172 g  | $0.032/gram      | $37.50        | Main structural component         |
| Constant Velocity (CV) Joint   | 177.8 mm major     | 4        | $10.00/joint     | $40.00        | Chassis motor–wheel joint         |
| Arduino Mega R3 (2560)         | 101.5 × 53.5 mm    | 1        | $23.00/each      | $23.00        | Microcontroller for chassis       |
| Raspberry Pi 4 (8GB RAM)       | 65 × 30 × 5 mm     | 1        | $35.00/each      | $35.00        | Microcontroller for drone         |
| M3 & M5 Screws + Nuts          | 6–16, 30–50 mm     | ~50      | $0.35/each       | $17.50        | Connections between parts         |
| L298N Motor Drivers            | 55 × 60 × 30 mm    | 2        | $3.47/each       | $6.95         | DC motor control                  |
| DC 300 RPM Motors              | 66 × 19 mm         | 4        | $15.88/each      | $63.52        | Thrust for chassis wheels         |
| Infrared/Thermal Cameras       | 26.5 × 32 mm       | 2        | $13.00/each      | $26.00        | Visual/spatial recognition        |
| OGRC Oil Shock Absorber        | 115 mm (open)      | 4        | $6.41/each       | $25.65        | Multi-terrain suspension          |
| Electromagnets                 | 30 × 22 mm         | 4        | $11.99/each      | $47.96        | Chassis–drone connection          |
| 40A Motor Controller (ESC)     | 72 × 24 mm         | 4        | $9.99/each       | $39.96        | Drone motor control               |
| Brushless Motors               | 28 × 24 mm         | 4        | $9.99/each       | $39.96        | Thrust for drone propellers       |
| LiPo & 9V Batteries            | ~50 × 50 mm total  | 4, 2     | $6.50 / $2.37    | $30.74        | Power for all components          |
| **Total prototype cost**       |                    |          |                  | **~$433.74**  |                                    |

</div>

<p align="center">
  <img width="33%" alt="Assembly section with materials in view" src="ocsef/4A39E4E3-4553-47E2-8F7E-667A52397530.JPG"/>
</p>
<p align="center"><em>Assembly section with materials in view.</em></p>

---

## Procedures

### 3D Printing (Bambu Lab P1S; Bambu Studio)

1. **Slicer settings:** layer height, speed, infill, and acceleration adjusted for PETG-CF. Multiple iterations were run to reach the final print quality.
2. **Post-processing:** supports removed and printed parts sanded, ensuring smooth edges and a functional fit for assembly.

<p align="center">
  <img width="66%" alt="Fig 7-8. Slicer settings and print bed pre-planning" src="media/fig7-8-slicer-settings.jpg" />
</p>
<p align="center"><em>Fig 7–8. Slicer settings and print bed pre-planning (placeholder — source images from presentation not yet uploaded to repo).</em></p>

### CAD (Onshape, 2025) — Chassis and Drone Design

1. **Motor box:** designed for adequate electronics clearance; 3D printed and fitted with securely installed DC motors.
2. **Suspension arms:** emphasis on material strength and articulation, hinged from the motor box.
3. **Platform construction:** designed to support sensors and electronics, mounted securely to the top of the motor box.
4. **Electromagnet integration:** slotted fit integrated into the platform for wireless docking strength.
5. **Drone body:** built using the chassis electromagnets as a template, allowing drone docking with the chassis.
6. **Drone arm construction:** optimized for strength, integrating securely with the body and brushless motors.

### Electrical (Arduino IDE; Linux/Ubuntu for Raspberry Pi 4)

1. **DC motors:** wired to motor controllers (9V) and the Arduino, with a shared ground system to avoid electrical conflicts.
2. **Sensors:** ultrasonic, sound, and additional sensors wired via digital, 5V, and ground pins, with connections verified.
3. **Brushless motors:** wired to 40A motor controllers and LiPo batteries, with direct power routed to the Pi.
4. **Verification:** additional sensors (e.g., camera) wired to the Pi, with all circuits checked for shorts before operation.

---

## Build & Testing Process

### CAD & 3D Printing

Designed in Onshape, printed with school equipment. Bulky parts and tight tolerances in early layouts drove several redesign passes to improve alignment and fit.

<p align="center">
  <img width="66%" alt="OnShape CAD model of the chassis" src="https://github.com/user-attachments/assets/9d023fa4-b840-4818-9a73-b365da0d3fcd" />
</p>
<p align="center"><em>Onshape CAD model of the chassis. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="3D print in progress on the Bambu Lab P1S" src="https://github.com/user-attachments/assets/1f2e843e-37ab-44cc-a543-a1332eb0baad" />
</p>
<p align="center"><em>3D print in progress on the Bambu Lab P1S. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Printed PETG-CF components after support removal" src="https://github.com/user-attachments/assets/754fad82-50c8-4a0a-bf3c-90ff18ef8fae" />
</p>
<p align="center"><em>Printed PETG-CF components after support removal. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="66%" alt="Post-processed and sanded chassis parts" src="https://github.com/user-attachments/assets/f7dcb00d-eda2-47a0-84ba-3d59ef7d9eb7" />
</p>
<p align="center"><em>Post-processed and sanded chassis parts, ready for assembly. (Caption inferred from surrounding context — please verify.)</em></p>

### Mechanical & Electrical Assembly

Metal fasteners and bearings are used throughout for durability. Planetary gears are integrated for torque distribution, and the PCB, sensors, Arduino, and Raspberry Pi are assembled and wired.

<p align="center">
  <img width="66%" alt="Wiring the Arduino Mega and motor drivers" src="https://github.com/user-attachments/assets/9be08430-5f53-49dc-adb7-1fa2a313e460" />
</p>
<p align="center"><em>Wiring the Arduino Mega and motor drivers. (Caption inferred from surrounding context — please verify.)</em></p>

<p align="center">
  <img width="33%" alt="Raspberry Pi 4 and sensor wiring, close-up" src="https://github.com/user-attachments/assets/4979b255-1dcc-4112-aaa6-852ae7a3a988" />
</p>
<p align="center"><em>Raspberry Pi 4 and sensor wiring, close-up. (Caption inferred from surrounding context — please verify.)</em></p>

### Testing

Evaluated on rocky, sandy, and uneven terrain to assess suspension stability and obstacle traversal. The drone was tested for flight stability and docking reliability — the electromagnetic interface worked, with refinement still needed for consistency. Sensor calibration using FFT methods improved detection accuracy, and data was collected via accelerometers, force sensors, and battery monitors.

---

## Results & Data

Testing showed the robot capable of speeds around 17 m/s, though it was operated closer to 10 m/s for terrain crossing to balance speed and maneuverability. This balance ensured effective traversal across rugged landscapes while maintaining stability. The variable suspension system was central to this adaptability, allowing the robot to successfully navigate diverse obstacles such as stationary logs, uneven rocky surfaces, and loose terrain.

Adjustments made over the course of testing included refining the suspension for better shock absorption, optimizing motor control for smoother acceleration, and fine-tuning sensor integration for more accurate environmental data collection. Sensor data was equally critical — Fast Fourier Transform (FFT) analysis was used on sound sensor data to identify frequencies associated with distress sounds or movement, and ultrasonic data was used to gauge distances.

<div align="center">

| Motor Output Speed | Ratio | Measured Output Speed | Observed Torque |
|---------------------|-------|-------------------------|-------------------|
| 600                 | 1:2   | 265                     | Low               |
| 400                 | 1:2   | 187                     | Low–Medium        |
| 300                 | 1:2   | 148                     | Medium            |

</div>

<p align="center">
  <img width="66%" alt="Field test results overview" src="https://github.com/user-attachments/assets/132262a9-637f-4f6c-a8bc-bdf11408f4da" />
</p>
<p align="center"><em>Field test results overview. (Caption inferred from surrounding context — please verify.)</em></p>

**Summary of results:**
- Traversed varied rough terrain (rocky, sandy, uneven) at ground speeds up to ~17 m/s, operated at ~10 m/s for stability.
- Modular docking and wireless charging demonstrated between chassis and drone in field tests.
- Real-time sensor feedback for obstacle and hazard detection, using FFT-calibrated signal processing.
- Recognized with an Honorable Mention at OCSEF, with judge feedback centered on scope ("too ambitious") and structural bulk — directly shaping the redesign priorities below.

---

## Design Iterations

Many revisions were made to arrive at the final design; the major iterations are described here.

- **Suspension assembly (n=2 → later iterations):** The early suspension iteration had poor integration with the motor mount — while moving, the chassis transferred significant load to the platform because the suspension sat on top of it. This was corrected in later revisions by integrating the suspension and motor mount into a single combined system.
- **Motor–CV connector (n=1):** The original motor-to-CV joint connector would snap its connection under load.
- **Motor box assembly (n=4 → n=5):** The final motor box iteration eliminated the snapping failure by switching to a planetary gear system, enabling a custom gear ratio while allowing for indirect mounting.
- **Platform mount (n=3):** An intermediate platform mount design preceded the final integrated version.

<p align="center">
  <img width="33%" alt="Fig 14. Old platform mount (n=3)" src="media/fig14-old-platform-mount.jpg" />
</p>
<p align="center"><em>Fig 14. Old platform mount (n=3) (placeholder — source image from presentation not yet uploaded to repo).</em></p>

<p align="center">
  <img width="66%" alt="Fig 9, 12. Old suspension assembly and motor-CV connector iterations" src="media/fig9-12-old-iterations.jpg" />
</p>
<p align="center"><em>Fig 9 (left). Old (n=2) suspension assembly iteration that did not meet criteria. Fig 12 (right). Old (n=1) motor-CV connector iteration (placeholder — source image from presentation not yet uploaded to repo).</em></p>

<p align="center">
  <img width="66%" alt="Fig 10, 11, 13. New motor box iterations" src="media/fig10-13-new-motor-box.jpg" />
</p>
<p align="center"><em>Fig 10–11. New (n=4) motor box iteration. Fig 13. New (n=5) motor box assembly iteration, integrating the planetary gear system (placeholder — source images from presentation not yet uploaded to repo).</em></p>

**Structural testing (qualitative, three trials per condition):**

<div align="center">

| # | Obstacle | Cracks | Location |
|---|----------|--------|----------|
| 1–3   | No  | No (0)   | Top    |
| 4–6   | Yes | Yes (3)  | Top    |
| 7–9   | No  | No (0)   | Bottom |
| 10–12 | Yes | No (0)   | Bottom |

</div>

<p align="center">
  <img width="33%" alt="Structural crack testing" src="media/fig-crack-testing.jpg" />
</p>
<p align="center"><em>Structural crack testing across obstacle trials (placeholder — source image from presentation not yet uploaded to repo).</em></p>

---

## Key Engineering Challenges

- **Suspension Integration:** Early direct motor mounts snapped under load; the planetary gear redesign resolved the torque failures at the cost of added size.
- **Sensor Calibration:** FFT-based calibration meaningfully improved detection accuracy but required iterative fine-tuning.
- **Docking & Power:** The electromagnetic docking system worked and enabled wireless charging, though it drew significant power and needs further reliability testing.

---

## Discussion

Data collected from testing demonstrated the effectiveness of the modular robotic system in search and rescue (SAR) scenarios. The robot consistently reached speeds of approximately 17 m/s but was optimized to 10 m/s for stable terrain traversal. Its variable suspension successfully adapted to diverse obstacles, including stationary logs and uneven rocky surfaces, highlighting its capability to navigate hazardous environments where traditional systems struggle. Integration of ultrasonic sensors and cameras provided real-time environmental data, improving victim detection and situational awareness.

Key trends indicated that modular adaptability enhanced performance across multiple conditions, reinforcing the advantages of reconfigurable robotics in SAR applications. Potential sources of error included sensor calibration inconsistencies and terrain variation, which could affect navigation precision. Compared to existing SAR technologies, the prototype demonstrated stronger terrain adaptability and environmental awareness, reducing responder risk and improving efficiency — consistent with findings emphasizing the importance of sensor integration and modularity in disaster-response robotics (ResearchGate, n.d.; PMC, 2022).

The project validated its hypothesis, confirming the potential for robotic assistance in SAR operations. Current robotic solutions face critical limitations in terrain adaptability, high cost, and restricted versatility — limitations that delay response times and increase risk to both victims and rescuers. This underscores the importance of continued development in this space.

---

## Conclusion

- The solution to the identified problem was a modular robotic system designed to enhance search and rescue (SAR) operations in hazardous environments — capable of navigating difficult terrain, accessing confined spaces, and gathering real-time environmental data, improving response efficiency and safety. The results validated the proposed hypothesis.
- The results are explained by the robot's modular design and adaptive reconfiguration capabilities, allowing it to navigate complex terrain and collect environmental data in scenarios where human responders would be ineffective or too slow.
- This work has broad potential applications in SAR operations during natural disasters such as earthquakes, floods, and fires, as well as environmental monitoring in hazardous locations and use in military or industrial sectors requiring autonomous operation in high-risk environments.

---

## Future Development

- **Structural redesign:** lighter, stronger, less bulky chassis and mounts.
- **Streamlined integration:** simplified electronics packaging for improved reliability.
- **AI/automated control:** smarter hazard and victim detection.
- **Battery optimization:** explore solar or kinetic energy harvesting.
- **New attachments:** flood/fire-specific modules, additional sensing.
- **Extended testing:** evaluation in more demanding environments to explore and expand operational limits.
- **Expanded modularity:** research into additional modules for more specialized rescue operations.

---

## Reflection & Application

This project highlighted the potential of modular robots to transform search and rescue (SAR) operations. The ability to rapidly adapt and navigate hazardous environments could be key to saving lives in critical situations where every second counts. Reconfigurable systems that reach victims in confined spaces or on difficult terrain have the potential to improve survival rates while minimizing risk to rescuers.

By reducing response times and safeguarding those who risk their lives to help others, this kind of technology could serve as a meaningful tool in life-or-death situations. Emergency responders, search and rescue teams, and organizations such as FEMA and the Red Cross stand to benefit from a tool offering flexibility and efficiency where current systems fall short.

<p align="center">
  <img width="33%" alt="Fig 15. Zoomed in chassis CAD" src="media/fig15-zoomed-chassis-cad.jpg" />
</p>
<p align="center"><em>Fig 15. Zoomed-in chassis CAD (placeholder — source image from presentation not yet uploaded to repo).</em></p>

Though the project has come a long way, it remains an early-stage prototype. Future development with access to more industry-grade resources and facilities could enable more robust testing, along with a user-friendly interface for non-experts to deploy in emergencies. Potential applications extend beyond SAR into environmental monitoring, industrial inspection, and military fields.

---

## Project Timeline

**Concept & Design** — Identified the need for rapid SAR deployment and terrain adaptability; designed the initial chassis, drone, and docking system.

**Prototyping & Iteration** — Printed, assembled, and tested multiple versions, with frequent redesigns to improve robustness.

**Integration & Field Testing** — Combined modules and tested at school, home, and a local park; documented structural, sensor, and battery performance.

---

## Skills Demonstrated

- CAD & mechanical design of a planetary suspension system
- 3D printing and hands-on assembly
- Sensor integration and FFT calibration
- Modular hardware/electronics development
- Iterative engineering and troubleshooting

---

## References

**Project documentation:**
- OCSEF_LOG.pptx — engineering log: assembly process, structural challenges, planetary gear integration, sensor/motor experimentation.
- OCSEF.docx — project summary: design rationale, technical details, constraints, build/test procedures, evaluation.
- Design inspiration: [arXiv:1910.00093](https://arxiv.org/pdf/1910.00093)
- Reference hardware: [Open Robot Actuator Hardware](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware)

**Cited sources:**
- Heggie, T. W., & Amundson, M. E. (2009). Dead men walking: search and rescue in US National Parks. *Wilderness & Environmental Medicine, 20*(3), 244–249. https://doi.org/10.1580/08-WEME-OR-299R.1
- Heggie, T. W., & Heggie, T. M. (2009). Search and rescue trends associated with recreational travel in US national parks. *Journal of Travel Medicine, 16*(1), 23–27. https://doi.org/10.1111/j.1708-8305.2008.00269.x
- Milani, M., Roveri, G., Falla, M., Dal Cappello, T., & Strapazzon, G. (2023). Occupational accidents among search and rescue providers during mountain rescue operations and training events. *Annals of Emergency Medicine, 81*(6), 699–705. https://doi.org/10.1016/j.annemergmed.2022.12.015
- Oshiro, K., & Murakami, T. (2022). Causes of death and characteristics of non-survivors rescued during recreational mountain activities in Japan between 2011 and 2015: a retrospective analysis. *BMJ Open, 12*(2), e053935. https://doi.org/10.1136/bmjopen-2021-053935
- Rauch, S., Brugger, H., Falk, M., Zweifel, B., Strapazzon, G., Albrecht, R., & Pietsch, U. (2024). Avalanche survival rates in Switzerland, 1981–2020. *JAMA Network Open, 7*(9), e2435253. https://doi.org/10.1001/jamanetworkopen.2024.35253
- World Health Organization. (2020). Natural disasters and casualty statistics.
- PMC. (2022). Post-traumatic stress and injury risk among search and rescue personnel.
- ResearchGate. (n.d.). Sensor integration and modularity in disaster-response robotics.

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
