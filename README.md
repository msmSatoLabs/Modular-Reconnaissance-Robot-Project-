# Adaptive Modular Search & Rescue Robot Prototype (OCSEF)

A modular robotic system designed as a **proof-of-concept** for search and rescue (SAR) operations. This project explores the design, prototyping, and testing of a ground chassis with terrain-adaptive suspension and a drone module for aerial reconnaissance—combining coordinated sensors, modularity, and electromagnetic docking.  
**Note:** This is a prototype with room for improvement, especially regarding structural integrity and part design, which were found to be bulky and prone to weaknesses [1][2].

<p align="center">
  <img width="66%" alt="Assembled modular chassis, top view" src="ocsef/B17090F1-A2D6-41B9-A585-FACF8B59D7A4.JPG"/>
</p>

> **Status:** Prototype completed and tested in field conditions; provided useful insights but is not a final product. Structural weaknesses and bulky components highlighted the need for further refinement [1][2].

---

## Project Overview

This robot aims to improve SAR efficiency by autonomously navigating dangerous terrain and providing real-time hazard/victim detection. Survival rates in disasters drop quickly (e.g., fire survival falls from 75% to 28% in eight minutes), and current SAR robots are often inefficient, costly, or insufficiently adaptable [2].  
Our prototype uses accessible hardware and modular design to address these gaps.

<p align="center">
  <img width="66%" alt="SAR statistics visualized" src="ocsef/FE6210AB-C3C4-46F8-AA01-328C51ADBF15.JPG"/>
</p>

---

### Target Specifications

<div align="center">

| Specification           | Prototype Implementation                  |
|-------------------------|:------------------------------------------|
| Application             | Search & rescue proof-of-concept          |
| Max ground speed        | ~10 m/s                                   |
| Chassis material        | PETG-CF (carbon fiber-infused plastic)    |
| Suspension              | Planetary gear, metal CV shafts           |
| Wheels                  | TPU + rubber                              |
| Drone motors            | Brushless, quad propellers                |
| Electromagnetic docking | Modular, wireless charging                |
| Sensors                 | Ultrasonic, IR camera, sound, force       |
| Main controller         | Raspberry Pi 4 (Ubuntu Linux), Arduino    |
| Battery                 | LiPo                                      |
| Camera                  | Pi-compatible IR + object recognition     |
| Fasteners               | M3–M6 screws/nuts, metal & nylon          |
| Bearings                | Uxcell 10x15x4mm                          |
| Testing locations       | Local park, school, home                  |

</div>

<p align="center">
  <img width="33%" alt="Drone module vertical demonstration" src="ocsef/A0CDC6F8-A694-4190-BF56-B56F8F83567E.JPG"/>
</p>

---

# Design Philosophy

- **Adaptability:** Modular subsystems (chassis + drone) can operate independently or combined [2].
- **Manufacturability:** 3D-printed PETG-CF and available hardware, accessible for school engineering labs [2].
- **Iterative Development:** Multiple redesigns to address structural failures, especially in the suspension and motor mounts [1][2].
- **Room for Improvement:** Prototype bulkiness and mechanical weaknesses need further engineering cycles [1][2].

<p align="center">
  <img width="66%" alt="Chassis integration phase" src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG"/>
</p>

---

# Architecture & Structural Engineering

## Ground-Based Chassis

- Early designs with direct helical motor mounts failed: shafts bent/snapped under torque and impact [1].
- Planetary gear system added to distribute load across gears, improving durability but making the design bulkier [1].
- CV joints and bearings used for power transmission and rotation.

<p align="center">
  <img width="33%" alt="Planetary gear pod (vertical orientation)" src="ocsef/4A28B365-6B12-4048-ABA2-2F07FB40368E.JPG"/>
</p>

## Drone Module

- Quad motors with propellers, Pi-compatible camera, ultrasonic sensor.
- Designed for aerial scouting over debris and out-of-reach areas.
- Electromagnetic docking for modularity and wireless charging [2].

---

# Materials & Components

| Item             | Qty | Details                            |
|------------------|-----|-------------------------------------|
| PETG-CF          | -   | Frame, chassis, drone (3D-printed)  |
| TPU + rubber     | 4   | Wheels                              |
| Metal CVD shaft  | 4   | Drive transmission                  |
| Metal shocks     | 4   | Suspension                          |
| Motors           | 8   | DC gearmotor (BEMONOC)              |
| Motor controller | 2   | L298N Dual H-Bridge                 |
| Battery          | 2   | LiPo                                |
| Camera           | 2   | Pi-compatible, IR auto-switch       |
| Ultrasonic sensor| 2+  | Obstacle/victim detection           |
| Sound sensor     | 1   | FFT calibration                     |
| Force sensor     | 1+  | Docking/load testing                |
| Bearings         | -   | Uxcell 10x15x4mm                    |
| Screws/nuts      | -   | M3/M4/M6, metal/nylon               |
| Breadboard       | -   | Sensor/electronics integration      |
| Electromagnet    | 4   | Docking                             |

<p align="center">
  <img width="33%" alt="Assembly section with materials in view" src="ocsef/4A39E4E3-4553-47E2-8F7E-667A52397530.JPG"/>
</p>

---

# Build & Testing Process

## CAD & 3D Printing

- Designed in OnShape, printed with school equipment [2].
- Bulky parts and difficult alignment exposed limitations in early layouts [1][2].

## Mechanical & Electrical Assembly

- Used metal fasteners and bearings for durability.
- Integrated planetary gears for torque distribution [1].
- Assembled PCB and sensors with Arduino and Raspberry Pi.

<p align="center">
  <img width="66%" alt="Sensor mount and wiring" src="ocsef/E6C2E789-D521-4209-8E83-BA2DF915C60C.JPG"/>
</p>

## Testing

- Evaluated on rocky, sandy, uneven terrain; found weaknesses in structural robustness [1].
- Drone tested for flight stability and docking reliability; electromagnetic interface worked but further refinement needed [2].
- Sensor calibration using FFT methods improved detection, but reliability varied [2].
- Data collected using accelerometers, force sensors, battery monitors [2].

<p align="center">
  <img width="66%" alt="Drone docking demonstration" src="ocsef/85BC9C84-5A49-4E60-B4FA-F81EA42378C2.JPG"/>
</p>

---

# Key Engineering Challenges

- **Suspension Integration:** Early mounts snapped under load; planetary gears reduced torque failures but increased size/bulk [1].
- **Sensor Calibration:** FFT methods increased accuracy but required fine-tuning [2].
- **Structural Design:** Bulky layouts and poor integration compromised durability; many parts need redesign for strength and space efficiency [1][2].
- **Docking/Energy:** Electromagnetic system worked, but was power hungry and could be unreliable under some conditions [2].

<p align="center">
  <img width="66%" alt="Chassis, planetary pods, assembly" src="ocsef/E6C2E789-D521-4209-8E83-BA2DF915C60C.JPG"/>
</p>

---

# Prototype Testing & Data Collected

- **Ground module:** Stable terrain traversal, but structural weaknesses under repeated impact [1].
- **Drone:** Docking and flight worked in small-scale field tests; further refinements needed [2].
- **Sensor feedback:** Real-time detection; accuracy varied, room for improvement [2].
- **Battery life:** Monitored, showed room for optimization [2].
- **Wireless charging:** Functional, but efficiency and integration could be improved [2].

<p align="center">
  <img width="66%" alt="Chassis integration, top-down" src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG"/>
</p>

---

# Results & Areas to Improve

- **Proof-of-concept:** Traversed rough terrain, managed modular docking, collected sensor data [2].
- **Limitations:** Structural integrity, component bulk, and sensor reliability need much refinement.  
- **Iterative Design Required:** Future versions must focus on reducing bulk, increasing strength, optimizing electronics, and extending battery life [1][2].

<p align="center">
  <img width="33%" alt="Assembly detail; vertical orientation" src="ocsef/492F5B14-A730-4B9D-9CEE-6A882FFA2FEE.JPG"/>
</p>

---

# Future Development

- **Structural Redesign:** Lighter, stronger, and less bulky chassis and mounts.
- **Advanced Integration:** Streamlined electronics and sensors for improved reliability.
- **AI/Automated Control:** Implement smarter hazard/victim detection.
- **Battery Optimization:** Explore solar/kinetic harvesting.
- **New Attachments:** Flood/fire modules, additional sensing [2].

<p align="center">
  <img width="66%" alt="Future modular attachment planning" src="ocsef/A7AC316B-0769-4655-AE26-0070581A88D2.JPG"/>
</p>

---

# Project Timeline

## Concept & Design
- Identified need for rapid SAR deployment and terrain adaptability [2]; designed initial chassis, drone, and docking system [1].

## Prototyping & Iteration
- Printed, assembled, and tested multiple versions; frequent redesigns to improve robustness and reduce failures [1][2].

## Integration & Field Testing
- Combined modules, tested in school/home/local park; documented structural, sensor, and battery performance [2].

<p align="center">
  <img width="33%" alt="Project collaborators and workspace" src="ocsef/3D04DFF2-302E-4154-96CE-2302DD2F556F.JPG"/>
</p>

---

# Skills Demonstrated

- CAD & mechanical design of planetary suspension
- 3D printing and hands-on assembly
- Sensor integration and FFT calibration
- Modular hardware/electronics development
- Iterative engineering and troubleshooting

---

# Project Status

**Prototype:** Built and tested; not deployment-ready  
**Major Issues:** Structural bulkiness, critical weakness under load, sensor consistency  
**Future Plans:** Redesign, optimize, further testing

---

# References

- OCSEF_LOG.pptx [1]
- OCSEF.docx [2]
- Design Paper: https://arxiv.org/pdf/1910.00093
- GitHub Source: https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware

---

# License

Include your preferred open-source license or statement here.

---

**See MEDIA.md for photos and testing clips!**
