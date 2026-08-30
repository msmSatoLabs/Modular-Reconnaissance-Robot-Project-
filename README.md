# Adaptive Modular Search & Rescue Robot Prototype (OCSEF)

**Honorable Mention — Orange County Science & Engineering Fair (OCSEF)**

A modular robotic system designed as a **proof-of-concept** for search and rescue (SAR) operations. This project explores the design, prototyping, and testing of a ground chassis with terrain-adaptive suspension and a drone module for aerial reconnaissance — combining coordinated sensors, modularity, and electromagnetic docking.

📺 **See [MEDIA.md](MEDIA.md) for build photos and testing clips.**

<p align="center">
  <img width="66%" alt="Assembled modular chassis, top view" src="ocsef/B17090F1-A2D6-41B9-A585-FACF8B59D7A4.JPG"/>
</p>

> **Status:** Prototype completed and field-tested across rocky, sandy, and uneven terrain. Recognized with an Honorable Mention at OCSEF. As a proof-of-concept, it surfaced clear next steps around structural weight and part durability — documented below and driving the current redesign [1][2].

**Team:** Built with one partner. I led **CAD, mechanical part design, and assembly** (chassis, suspension, planetary gear pods, docking hardware). My partner led **sensor selection/integration and onboard programming** (Raspberry Pi/Arduino, FFT sensor calibration, detection software).

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

1. **Initial Design (Caltech M4-inspired):** Early concept combined aerial and ground locomotion into one unit, sharing a single battery between driving and flying. This "jack of all trades" approach limited flight time and hurt performance in both domains [2].
2. **Modular Multi-Robot Approach:** Redesigned into three specialized robots — car, quadruped, drone. Integrating the quadruped proved too complex for the timeline, prompting further refinement [2].
3. **Final Modular Prototype:** Narrowed to car + drone, each purpose-built and dockable. This simplified the system while preserving combined functionality [2].

<p align="center">
  <img width="66%" alt="SAR statistics visualized" src="ocsef/FE6210AB-C3C4-46F8-AA01-328C51ADBF15.JPG"/>
</p>

---

## Target Specifications

<div align="center">

| Specification            | Prototype Implementation                       |
|---------------------------|:------------------------------------------------|
| Application               | Search & rescue proof-of-concept                |
| Max ground speed          | ~10 m/s                                         |
| Chassis material          | PETG-CF (carbon fiber-infused plastic)          |
| Suspension                | Planetary gear, metal CV shafts                 |
| Wheels                    | TPU + rubber                                    |
| Drive motors (chassis)    | DC gearmotor (BEMONOC)                          |
| Drone motors               | Brushless, quad propeller                       |
| Chassis motor controller  | L298N Dual H-Bridge                             |
| Drone motor controller    | Electronic speed controllers (ESCs)             |
| Electromagnetic docking   | Modular, wireless charging                      |
| Sensors                   | Ultrasonic, IR camera, sound, force              |
| Main controller           | Raspberry Pi 4 (Ubuntu Linux), Arduino          |
| Battery                   | LiPo                                            |
| Camera                    | Pi-compatible IR + object recognition           |
| Fasteners                 | M3–M6 screws/nuts, metal & nylon                |
| Bearings                  | Uxcell 10x15x4mm                                |
| Testing locations         | Local park, school, home                        |

</div>

<p align="center">
  <img width="33%" alt="Drone module vertical demonstration" src="ocsef/A0CDC6F8-A694-4190-BF56-B56F8F83567E.JPG"/>
</p>

---

## Design Philosophy

- **Adaptability:** Modular subsystems (chassis + drone) operate independently or combined [2].
- **Manufacturability:** 3D-printed PETG-CF and off-the-shelf hardware, accessible for a school engineering lab [2].
- **Iterative Development:** Multiple redesign cycles targeting structural failures, particularly in the suspension and motor mounts [1][2].

<p align="center">
  <img width="66%" alt="Chassis integration phase" src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG"/>
</p>

---

## Architecture & Structural Engineering

### Ground-Based Chassis

- Early designs with direct motor mounts failed — shafts bent or snapped under torque and impact [1].
- Redesigned around a planetary gear system to distribute load across multiple gears, trading some compactness for durability [1].
- CV joints and bearings handle power transmission and rotation.

<p align="center">
  <img width="33%" alt="Planetary gear pod (vertical orientation)" src="ocsef/4A28B365-6B12-4048-ABA2-2F07FB40368E.JPG"/>
</p>

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

### Mechanical & Electrical Assembly

- Metal fasteners and bearings throughout for durability.
- Planetary gears integrated for torque distribution [1].
- PCB, sensors, Arduino, and Raspberry Pi assembled and wired.

<p align="center">
  <img width="66%" alt="Sensor mount and wiring" src="ocsef/E6C2E789-D521-4209-8E83-BA2DF915C60C.JPG"/>
</p>

### Testing

- Evaluated on rocky, sandy, and uneven terrain to assess suspension stability and obstacle traversal [1].
- Drone tested for flight stability and docking reliability — the electromagnetic interface worked, with refinement still needed for consistency [2].
- Sensor calibration using FFT methods improved detection accuracy [2].
- Data collected via accelerometers, force sensors, and battery monitors [2].

<p align="center">
  <img width="66%" alt="Drone docking demonstration" src="ocsef/85BC9C84-5A49-4E60-B4FA-F81EA42378C2.JPG"/>
</p>

---

## Key Engineering Challenges

- **Suspension Integration:** Early direct motor mounts snapped under load; the planetary gear redesign resolved the torque failures at the cost of added size [1].
- **Sensor Calibration:** FFT-based calibration meaningfully improved detection accuracy but required iterative fine-tuning [2].
- **Docking & Power:** The electromagnetic docking system worked and enabled wireless charging, though it drew significant power and needs further reliability testing [2].

<p align="center">
  <img width="66%" alt="Chassis, planetary pods, assembly" src="ocsef/492F5B14-A730-4B9D-9CEE-6A882FFA2FEE.JPG"/>
</p>

---

## Results

- **Traversed varied rough terrain** (rocky, sandy, uneven) at ground speeds up to ~10 m/s.
- **Modular docking and wireless charging demonstrated** between chassis and drone in field tests.
- **Real-time sensor feedback** for obstacle and hazard detection, using FFT-calibrated signal processing.
- **Recognized with an Honorable Mention at OCSEF**, with judge feedback centered on scope ("too ambitious") and structural bulk — directly shaping the redesign priorities below.

<p align="center">
  <img width="66%" alt="Chassis integration, top-down" src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG"/>
</p>

---

## Future Development

- **Structural redesign:** lighter, stronger, less bulky chassis and mounts.
- **Streamlined integration:** simplified electronics packaging for improved reliability.
- **AI/automated control:** smarter hazard and victim detection.
- **Battery optimization:** explore solar or kinetic energy harvesting.
- **New attachments:** flood/fire-specific modules, additional sensing [2].

<p align="center">
  <img width="66%" alt="Future modular attachment planning" src="ocsef/A7AC316B-0769-4655-AE26-0070581A88D2.JPG"/>
</p>

---

## Project Timeline

**Concept & Design** — Identified the need for rapid SAR deployment and terrain adaptability [2]; designed the initial chassis, drone, and docking system [1].

**Prototyping & Iteration** — Printed, assembled, and tested multiple versions, with frequent redesigns to improve robustness [1][2].

**Integration & Field Testing** — Combined modules and tested at school, home, and a local park; documented structural, sensor, and battery performance [2].

<p align="center">
  <img width="33%" alt="Project collaborators and workspace" src="ocsef/3D04DFF2-302E-4154-96CE-2302DD2F556F.JPG"/>
</p>

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
