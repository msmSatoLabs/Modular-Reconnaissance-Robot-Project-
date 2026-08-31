# Adaptive Modular Search & Rescue Robot Prototype (OCSEF)

**Honorable Mention — Orange County Science & Engineering Fair (OCSEF)**

A modular robotic system designed as a **proof-of-concept** for search and rescue (SAR) operations. This project explores the design, prototyping, and testing of a ground chassis with terrain-adaptive suspension and a drone module for aerial reconnaissance — combining coordinated sensors, modularity, and electromagnetic docking.

Many existing SAR robots take a “jack of all trades, master of none” approach—trying to integrate too many components to handle every possible scenario, which makes them bulky, inefficient, and often suboptimal for any single task. This robot takes a modular approach, meaning it adapts its configuration to the specific rescue environment. If the terrain is impassable by ground, the drone module can detach for aerial reconnaissance. If aerial reconnaissance isn't needed, all power can be directed to terrain navigation. This situational adaptability makes it more effective in real-world rescue operations.

<p align="center">
  <img width="1127" height="782" alt="full robot" src="https://github.com/user-attachments/assets/d462ab23-48e2-430b-90d6-ca2aeaa525f3" />
</p>

> **Status:** Prototype completed and field-tested across rocky, sandy, and uneven terrain. Recognized with an Honorable Mention at OCSEF. As a proof-of-concept, it surfaced clear next steps around structural weight and part durability — documented below and driving the current redesign [1][2].

**Team:** Built with one partner. I led **CAD, mechanical part design, manufacturing, and assembly** (chassis, suspension, planetary gear pods, docking hardware). My partner led **sensor selection/integration and onboard programming** (Raspberry Pi/Arduino, FFT sensor calibration, detection software).

---

## Contents

- [Project Overview](#project-overview)
- [Target Specifications](#target-specifications)
- [Design Philosophy](#design-philosophy)
- [Architecture & Structural Engineering](#architecture--structural-engineering)
- [Materials & Components](#materials--components)
- [Build & Testing Process](#build--testing-process)
- [Key Engineering Challenges](#key-engineering-challenges)
- [Results](#results)
- [Future Development](#future-development)
- [Project Timeline](#project-timeline)
- [Skills Demonstrated](#skills-demonstrated)
- [References](#references)
- [License](#license)

---

## Project Overview

This robot aims to improve SAR efficiency by autonomously navigating dangerous terrain and providing real-time hazard/victim detection. Survival rates in disasters drop quickly (e.g., fire survival falls from 75% to 28% in eight minutes), and current SAR robots are often inefficient, costly, or insufficiently adaptable [2]. Our prototype uses accessible hardware and modular design to address these gaps.

The development moved through three major design phases:

1. **Initial Design Concept(Caltech M4-inspired):** Early concept combined aerial and ground locomotion into one unit, sharing a single battery between driving and flying. This "jack of all trades" approach limited flight time and hurt performance in both domains [2].

<img width="515" height="745" alt="image" src="https://github.com/user-attachments/assets/0b0c433c-c9c3-4324-b948-07eeff0f06b5" />
<img width="603" height="837" alt="image" src="https://github.com/user-attachments/assets/862cbe90-e2a1-4213-a597-00bf147b056e" />
<img width="580" height="441" alt="image" src="https://github.com/user-attachments/assets/afe30da5-999b-4369-a589-cb968232d16b" />

<img width="1000" height="667" alt="image" src="https://github.com/user-attachments/assets/9a9b953c-cb70-4899-985d-2e321b29be0d" />
*early design included built-in propellers inside the wheels, similar to Caltech's M4 Robot (https://www.caltech.edu/about/news/new-bioinspired-robot-flies-rolls-walks-and-more)*

2. **Modular Multi-Robot Approach:** Redesigned into three specialized robots which included a car, quadruped, and a drone. Integrating the quadruped proved too complex for the timeline, prompting further refinement [2].
<img width="513" height="391" alt="image" src="https://github.com/user-attachments/assets/ef1550b7-22bb-4f3c-ac2d-b031c644b8ce" />
<img width="552" height="586" alt="image" src="https://github.com/user-attachments/assets/41f5edea-54b0-48dd-aa1a-2a9d8ff5253d" />



3. **Final Modular Prototype:** Narrowed to car + drone, each purpose-built and dockable. This simplified the system while preserving combined functionality [2].

<img width="1047" height="541" alt="image" src="https://github.com/user-attachments/assets/56b2c632-443e-4ae2-b2d7-666a3e1d2897" />

<img width="517" height="582" alt="image" src="https://github.com/user-attachments/assets/ae7a85e9-8519-47f6-8cc7-605540c9b65c" />
<img width="320" height="125" alt="image" src="https://github.com/user-attachments/assets/a8a0240a-e48e-4f79-b96b-590494d21161" />
<img width="535" height="290" alt="image" src="https://github.com/user-attachments/assets/2e6b9860-916d-470f-ac26-a5d42a800c33" />



---

## Target Specifications

<div align="center">

| Specification             | Prototype Implementation                        |
|---------------------------|:------------------------------------------------|
| Application               | Search & rescue proof-of-concept                |
| Max ground speed          | ~1.0 m/s                                         |
| Chassis material          | PETG/PETG-CF (carbon fiber-infused plastic)     |
| Suspension                | RC car shock springs                            |
| Wheels                    | TPU + rubber                                    |
| Drive motors (chassis)    | DC gearmotor (BEMONOC)                          |
| Drone motors              | Brushless, quad propeller                       |
| Chassis motor controller  | L298N Dual H-Bridge                             |
| Drone motor controller    | Electronic speed controllers (ESCs)             |
| Electromagnetic docking   | Modular, wireless charging                      |
| Sensors                   | Ultrasonic, IR camera, sound, force             |
| Main controller           | Raspberry Pi 4 (Ubuntu Linux), Arduino          |
| Battery                   | LiPo                                            |
| Camera                    | Pi-compatible IR + object recognition           |
| Fasteners                 | M3–M6 screws/nuts, metal & nylon                |
| Bearings                  | Uxcell 10x15x4mm                                |
| Testing locations         | Local park, school, home                        |

</div>
<img width="1132" height="683" alt="image" src="https://github.com/user-attachments/assets/b3386e32-9cca-45df-a608-4c15a06aacd3" />

<img width="1068" height="677" alt="image" src="https://github.com/user-attachments/assets/93132a63-4a3b-4536-9777-8a8c42d2419b" />


---

## Design Philosophy

- **Adaptability:** Modular subsystems (chassis + drone) operate independently or combined, depending on the situation [2].
- **Manufacturability:** 3D-printed PETG/PETG-CF and off-the-shelf hardware, accessible for a school engineering lab [2].
- **Iterative Development:** Multiple redesign cycles targeting structural failures, particularly in the suspension and motor mounts [1][2].

<img width="1436" height="887" alt="image" src="https://github.com/user-attachments/assets/0176651f-dcb0-44d6-a7fd-224df04b25c9" />
<img width="967" height="786" alt="image" src="https://github.com/user-attachments/assets/18b7f62a-dab3-4bdf-be3b-f148c7f66baa" />


---

## Architecture & Structural Engineering

### Ground-Based Chassis

- Early designs with direct motor mounts failed — shafts bent or snapped under torque and impact [1].
- Redesigned around a planetary gear system to distribute load across multiple gears, trading some compactness for durability [1].
- CV joints and bearings handle power transmission and rotation.

<img width="635" height="607" alt="image" src="https://github.com/user-attachments/assets/1b050f92-5261-4c66-afc5-398e476bace4" />

<img width="1242" height="742" alt="image" src="https://github.com/user-attachments/assets/01cc31bc-ce2e-4d43-a5d2-fa148ffe99fe" />
<img width="1002" height="722" alt="image" src="https://github.com/user-attachments/assets/25dcd6f4-47c9-44f4-8ee5-9c5d5d830f48" />
<img width="577" height="502" alt="image" src="https://github.com/user-attachments/assets/ae7d2a26-2ad1-4cb0-8c16-e282f1f8b87f" />
<img width="632" height="605" alt="image" src="https://github.com/user-attachments/assets/8bfbfd5d-9cb4-4b7d-b1ff-4e08c0c16f81" />

<img width="390" height="352" alt="image" src="https://github.com/user-attachments/assets/3497c9a1-c978-433f-9d14-02a94913ce24" />
<img width="497" height="518" alt="image" src="https://github.com/user-attachments/assets/bd696f8b-01f6-41e3-bb23-786c174d18c9" />
<img width="622" height="465" alt="image" src="https://github.com/user-attachments/assets/fd568181-77c4-40b3-9267-e55baadd7fb4" />
<img width="853" height="655" alt="image" src="https://github.com/user-attachments/assets/45fad5c4-1471-4125-b71c-9dbe7780015b" />

### Drone Module

- Quad brushless motors with propellers, Pi-compatible camera, ultrasonic sensor.
- Built for aerial scouting over debris and areas the chassis can't reach.
- Electromagnetic docking enables modularity and wireless charging with the chassis [2].

---

## Materials & Components

| Item              | Qty | Details                            |
|-------------------|-----|-------------------------------------|
| PETG-CF           | -   | Frame, chassis, drone (3D-printed)  |
| TPU + rubber      | 4   | Wheels                              |
| Metal CVD shaft   | 4   | Drive transmission                  |
| Metal shocks      | 4   | Suspension                          |
| Chassis motors    | 4   | DC gearmotor (BEMONOC)              |
| Drone motors      | 4   | Brushless                           |
| Chassis motor controller | 2 | L298N Dual H-Bridge              |
| Drone motor controller   | 1 | ESC (multi-channel)               |
| Battery           | 2   | LiPo                                |
| Camera            | 2   | Pi-compatible, IR auto-switch       |
| Ultrasonic sensor | 2+  | Obstacle/victim detection           |
| Sound sensor      | 1   | FFT calibration                     |
| Force sensor      | 1+  | Docking/load testing                |
| Bearings          | -   | Uxcell 10x15x4mm                    |
| Screws/nuts       | -   | M3/M4/M6, metal/nylon               |
| Breadboard        | -   | Sensor/electronics integration      |
| Electromagnet     | 4   | Docking                             |

<p align="center">
  <img width="33%" alt="Assembly section with materials in view" src="ocsef/4A39E4E3-4553-47E2-8F7E-667A52397530.JPG"/>
</p>

---

## Build & Testing Process

### CAD & 3D Printing

- Designed in Onshape, printed with school equipment [2].
- Bulky parts and tight tolerances in early layouts drove several redesign passes to improve alignment and fit [1][2].
<img width="611" height="392" alt="image" src="https://github.com/user-attachments/assets/9d023fa4-b840-4818-9a73-b365da0d3fcd" />
<img width="1277" height="842" alt="image" src="https://github.com/user-attachments/assets/1f2e843e-37ab-44cc-a543-a1332eb0baad" />
<img width="867" height="755" alt="image" src="https://github.com/user-attachments/assets/754fad82-50c8-4a0a-bf3c-90ff18ef8fae" />
<img width="1966" height="1362" alt="image" src="https://github.com/user-attachments/assets/f7dcb00d-eda2-47a0-84ba-3d59ef7d9eb7" />


### Mechanical & Electrical Assembly

- Metal fasteners and bearings throughout for durability.
- Planetary gears integrated for torque distribution [1].
- PCB, sensors, Arduino, and Raspberry Pi assembled and wired.

<img width="4032" height="2268" alt="image" src="https://github.com/user-attachments/assets/9be08430-5f53-49dc-adb7-1fa2a313e460" />
<img width="2268" height="4032" alt="image" src="https://github.com/user-attachments/assets/4979b255-1dcc-4112-aaa6-852ae7a3a988" />



### Testing

- Evaluated on rocky, sandy, and uneven terrain to assess suspension stability and obstacle traversal [1].
- Drone tested for flight stability and docking reliability — the electromagnetic interface worked, with refinement still needed for consistency [2].
- Sensor calibration using FFT methods improved detection accuracy [2].
- Data collected via accelerometers, force sensors, and battery monitors [2].
---

## Results

- **Traversed varied rough terrain** (rocky, sandy, uneven) at ground speeds up to ~10 m/s.
- **Modular docking and wireless charging demonstrated** between chassis and drone in field tests.
- **Real-time sensor feedback** for obstacle and hazard detection, using FFT-calibrated signal processing.
- **Recognized with an Honorable Mention at OCSEF**, with judge feedback centered on scope ("too ambitious") and structural bulk — directly shaping the redesign priorities below.

<img width="797" height="686" alt="image" src="https://github.com/user-attachments/assets/132262a9-637f-4f6c-a8bc-bdf11408f4da" />

---

## Future Development

- **Structural redesign:** lighter, stronger, less bulky chassis and mounts.
- **Streamlined integration:** simplified electronics packaging for improved reliability.
- **AI/automated control:** smarter hazard and victim detection.
- **Battery optimization:** explore solar or kinetic energy harvesting.
- **New attachments:** flood/fire-specific modules, additional sensing [2].


---

## Project Timeline

**Concept & Design** — Identified the need for rapid SAR deployment and terrain adaptability [2]; designed the initial chassis, drone, and docking system [1].

**Prototyping & Iteration** — Printed, assembled, and tested multiple versions, with frequent redesigns to improve robustness [1][2].

**Integration & Field Testing** — Combined modules and tested at school, home, and a local park; documented structural, sensor, and battery performance [2].

---

## Skills Demonstrated

- CAD & mechanical design of a planetary suspension system
- 3D printing and hands-on assembly
- Sensor integration and FFT calibration
- Modular hardware/electronics development
- Iterative engineering and troubleshooting

---

## References

- OCSEF_LOG.pptx — engineering log: assembly process, structural challenges, planetary gear integration, sensor/motor experimentation [1]
- OCSEF.docx — project summary: design rationale, technical details, constraints, build/test procedures, evaluation [2]
- Design inspiration: [arXiv:1910.00093](https://arxiv.org/pdf/1910.00093)
- Reference hardware: [Open Robot Actuator Hardware](https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware)

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
