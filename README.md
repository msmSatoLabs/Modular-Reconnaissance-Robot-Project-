# Adaptive Modular Search & Rescue Robot for OCSEF

A custom-engineered, modular robotic system developed for search and rescue operations. The project explores the design, manufacturing, and integration of coordinated sensor and actuator subsystems—combining a terrain-adaptive chassis and aerial drone—capable of autonomous navigation, real-time hazard/victim detection, and modular deployment in disaster environments [2].

<p align="center">
  <img width="66%" alt="Assembled modular chassis, top view" src="ocsef/B17090F1-A2D6-41B9-A585-FACF8B59D7A4.JPG"/>
</p>

> **Current status:** Mechanical and electrical assembly complete; ground and aerial modules fully integrated and tested for terrain traversal, sensor functionality, and electromagnetic docking. The system achieves up to 10 m/s ground speed and robust modularity for dynamic SAR scenarios [2].
---
## Project Overview

The OCSEF robot is a **modular SAR system** designed for rapid deployment in hazardous environments, incorporating both ground and aerial mobility.  
Survival rates in disasters decline rapidly—for example, fire incident survival drops from 75% to 28% after eight minutes; avalanche rescue odds fall from 92% to 30% after 35 minutes [2].  
Existing SAR robots are often expensive, limited by terrain adaptability, and lack real-time modularity. Our solution is an accessible, adaptable, and robust system focused on practical engineering and testing [2].

<p align="center">
  <img width="66%" alt="Motivation: SAR statistics visualized" src="ocsef/FE6210AB-C3C4-46F8-AA01-328C51ADBF15.JPG"/>
</p>

---
### Target Specifications

<div align="center">

| Specification                | Design Target / Implementation                |
|------------------------------|:---------------------------------------------|
| Application                  | Search & rescue                              |
| Max ground speed             | 10 m/s                                       |
| Chassis material             | PETG-CF (carbon fiber-infused plastic)        |
| Suspension                   | Indirect planetary gear, metal CV shafts      |
| Wheels                       | TPU + rubber                                 |
| Drone motors                 | Brushless, quad                              |
| Electromagnetic docking      | Modular, wireless charging                   |
| Sensors                      | Ultrasonic, IR camera, FFT sound, force      |
| Main controller              | Raspberry Pi 4 (Ubuntu Linux), Arduino IDE   |
| Battery                      | LiPo                                         |
| Camera                       | Pi-compatible IR + object recognition        |
| Fasteners                    | M3–M6 screws/nuts, metal & nylon             |
| Bearings                     | Uxcell 10x15x4mm                             |
| Testing                      | Local park, school, home                     |

</div>

<p align="center">
  <img width="33%" alt="Drone subsystem; vertical demonstration" src="ocsef/A0CDC6F8-A694-4190-BF56-B56F8F83567E.JPG"/>
</p>

---
# Design Philosophy

The project is guided by several core goals:
### Adaptability
Modular design allows the robot to reconfigure for specific rescue needs. Detachable drone and chassis offer ground & aerial navigation [2].

### Toughness & Manufacturability
Designed and printed with accessible tools and materials (PETG-CF, 3D printing, modular hardware). Suspension and drive use planetary gears for durability and torque distribution [1][2].

### Real-time Data Collection
Sensor-rich platform gathers hazard and victim information autonomously, relaying live data to SAR teams [2].

### Cost-effectiveness
Uses readily available components and 3D printing to lower cost, enabling wider deployment [2].

### Engineering Iteration
Frequent redesign and testing (CAD → 3D print → assembly → test → improve) led to robust planetary suspension, reliable sensor integration, and repeatable modularity [1][2].

<p align="center">
  <img width="66%" alt="Chassis integration phase" src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG"/>
</p>

---
# System Architecture

## Ground-Based Chassis
- **Terrain-adaptive suspension:** Refined from initial helical design, now uses planetary gears—high torque, reduced wear, increased durability; indirect motor mounting avoids shaft failure [1].
- **Modular slot:** For drone docking; integrates electromagnets + wireless charging.
- **Motors:** DC geared, encoder feedback via Arduino.
- **Sensors:** Ultrasonic angled for obstacle/victim detection; IR camera for night/thermal hazards; sound sensors processed with FFT.

<p align="center">
  <img width="33%" alt="Planetary gear pod (vertical orientation)" src="ocsef/4A28B365-6B12-4048-ABA2-2F07FB40368E.JPG"/>
</p>

## Aerial Drone Module
- **Quad motors and propellers** for vertical lift.
- **IR/visible camera** for reconnaissance.
- **Electromagnet docking:** Secure, power-efficient integration [2].
- **Independent battery, controller, sensors** for separate operation.

---
# Reduction & Power Transmission

Original helical motor mount failed under torque; direct mounting led to shaft snapping and poor torque distribution.  
Switch to planetary gear system distributes load across multiple gears, enabling compact and efficient torque transfer for high-speed ground navigation [1].

<p align="center">
  <img width="66%" alt="Build Process: Sensor mount and wiring" src="ocsef/E6C2E789-D521-4209-8E83-BA2DF915C60C.JPG"/>
</p>

---
# Materials & Components

|Item            | Qty   | Details                               |
|----------------|-------|------------------------------------|
| PETG-CF 3D Print | varies | Frame, chassis, drone            |
| TPU + rubber     | 4     | Wheels                             |
| Metal CVD shaft  | 4     | Drive transmission                 |
| Metal shocks     | 4     | Suspension                         |
| Motors          | 8     | DC gearmotor (BEMONOC)             |
| Motor control   | 2     | L298N Dual H-Bridge                |
| Battery         | 2     | LiPo                               |
| Camera          | 2     | Pi-compatible, IR auto-switch      |
| Ultrasonic sensor| 2+    | Obstacle/victim detection          |
| FFT sound sensor | 1     | Sound analysis                     |
| Force sensor    | 1+    | Docking/load testing               |
| Bearings        | varies| Uxcell 10x15x4mm                   |
| Screws/nuts     | many  | M3/M4/M6, metal/nylon              |
| Breadboard      | varies| Sensor/electronics integration      |
| Electromagnet   | 4     | Docking                            |

<p align="center">
  <img width="33%" alt="Assembly section with materials in view" src="ocsef/4A39E4E3-4553-47E2-8F7E-667A52397530.JPG"/>
</p>

---
# Manufacturing & Assembly

## CAD & 3D Printing
- Designed in OnShape, printed in PETG-CF for UV resistance and strength [2].
- Drone and chassis manufactured at Beckman High School.

## Mechanical Assembly
- Parts affixed with metal screws, cap nuts, washers for durability and alignment.
- Bearings installed at all rotational joints for smooth motion.
- Planetary gear system integrated for power transmission [1].

## Electrical Integration
- Arduino and Pi control sensors, motors, and transmit real-time data [2].  
- Encoder wiring and sensor input routed via breadboard and connectors.

<p align="center">
  <img width="66%" alt="Drone docking demonstration" src="ocsef/85BC9C84-5A49-4E60-B4FA-F81EA42378C2.JPG"/>
</p>

---
# Engineering Challenges

### Suspension
Direct drive motor mounts were prone to snapping and torque failures, leading to switch to planetary gears.  
Planetary system provides stability and longer component life under impact [1].

### Sensor Calibration
Noise interference in ultrasonic and sound sensors addressed with FFT analysis for improved detection accuracy [2].

### Electromagnetic Docking
Critical balance of strength and power efficiency; designed to minimize battery drain and enable secure, repeatable module connection [2].

<p align="center">
  <img width="66%" alt="Chassis, planetary pods, mechanical assembly" src="ocsef/E6C2E789-D521-4209-8E83-BA2DF915C60C.JPG"/>
</p>

---
# Testing & Data Collection

- **Ground module:** Evaluated on rocky, sandy, and uneven terrain for stability and speed.
- **Drone:** Tested for flight stability, wind resistance, and autonomous docking.
- **Sensor performance:** Object and sound detection, IR/night vision, force evaluation for electromagnetic coupling.
- **Battery life:** Monitored during multi-mode operation.
- **Wireless charging:** Efficiency and reliability tested.

<p align="center">
  <img width="66%" alt="Subassembly: Chassis integration/top down" src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG"/>
</p>

---
# Results & Findings

- Robust terrain traversal, suspension absorbs shocks effectively up to 10 m/s [2].
- Real-time sensor feedback delivers accurate hazard and victim detection [2].
- Electromagnetic docking is reliable, with drone able to re-dock autonomously if detached [2].
- Modular adaptability allows flexible deployment in varying SAR scenarios.
- Cost-effective fabrication supports scalability and field deployment.

<p align="center">
  <img width="33%" alt="Assembly details; vertical orientation" src="ocsef/492F5B14-A730-4B9D-9CEE-6A882FFA2FEE.JPG"/>
</p>

---
# Future Development

- **Enhanced AI Integration:** Machine learning modules for automated hazard/victim detection.
- **Extended Battery Life:** Exploration of solar/kinetic energy harvesting.
- **New Attachments:** Water drones, IR cameras for fire/wildlife scenarios, ground rescue pods.
- **Real SAR Testing:** Collaboration with emergency response teams for deployment trials [2].

<p align="center">
  <img width="66%" alt="Future modular attachment planning" src="ocsef/A7AC316B-0769-4655-AE26-0070581A88D2.JPG"/>
</p>

---
# Project Timeline

## 1. Concept & Design
- Identified SAR needs and rapid survival drop-off [2].
- Designed modular platform using CAD modeling and planetary suspension [1][2].

## 2. Initial Prototyping
- Printed, assembled, and iterated through multiple chassis and drone designs [2].
- Developed electromagnetic docking and sensor arrays.

## 3. Integration & Assembly
- Mechanical-complete, electronics installed, system tested on multiple terrains.

## 4. Testing & Iteration
- Evaluated suspension, docking, sensor data, battery life, and modular adaptability.

<p align="center">
  <img width="33%" alt="Project collaborators and workspace" src="ocsef/3D04DFF2-302E-4154-96CE-2302DD2F556F.JPG"/>
</p>

---
# Skills Demonstrated

### Mechanical/Structural Engineering
* CAD & planetary gear design [1]
* Bearing and torque analysis
* Modular interface engineering

### Manufacturing
* FDM 3D printing, post-processing, assembly

### Electrical & Controls
* Arduino & Pi integration
* Sensor calibration (FFT)
* Electromagnetic actuation

### Robotics
* Terrain adaptive mobility
* Modular autonomous deployment
* Real-time SAR data collection

---
# Project Status

**Mechanical/Electrical prototype: COMPLETE**  
**Sensor & docking integration: COMPLETE**  
**Modular deployment: TESTED**  
**Experimental characterization: IN PROGRESS**  
**Field testing: IN PROGRESS**

---
# References

* OCSEF_LOG.pptx [1]
* OCSEF.docx [2]
* GitHub Source: https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware  
* Design Paper: https://arxiv.org/pdf/1910.00093

---
# License

Include your preferred open-source license or statement here.

---

**Media & video demonstration: See MEDIA.md for detailed deployment and field trial videos!**
