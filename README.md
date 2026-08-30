# OCSEF Modular Search & Rescue Robot

## Project Overview

**Title:** Utilizing Electromagnetic Conductivity and Modular Integration of Coordinated Sensor Systems to Develop Adaptive 3D-Printed Robots for Advanced Search and Rescue Operations

**Goal:**  
The project aims to mitigate risk and improve efficiency in search and rescue operations by developing a modular robotic system capable of autonomous navigation and robust sensor integration. By combining ground and aerial modules, real-time data collection and hazard detection are achieved, ultimately increasing victim survival rates and reducing risks for human rescuers [2].

---

## Motivation & Background

Search and rescue operations often encounter drastic declines in survival rates with delays. For example, survival during fire incidents drops from 75% to 28% after eight minutes, and avalanche rescues fall from 92% to 30% after 35 minutes [2]. Current methods put rescuers at risk and are frequently inefficient, emphasizing the urgent need for adaptive robotic SAR tools.

---

## Technical Summary

- **Ground chassis:** Terrain-adaptive, suspension with planetary gear for efficient torque transfer and durability [1][2].
- **Drone module:** Provides aerial reconnaissance. Can dock/charge via an electromagnetic system.
- **Sensors:** Ultrasonic, camera (IR-capable), sound detection with FFT calibration [2].
- **Processing:** Raspberry Pi 4 (Ubuntu Linux) + Arduino IDE [2].
- **Integration:** Modular, detachable via electromagnetic docking. Real-time data transmission.

---

## Materials & Components

| Component                | Details                                         |
|--------------------------|-------------------------------------------------|
| Chassis & Drone Frame    | PETG-CF (carbon fiber–infused plastic; 3D print)|
| Wheels                   | TPU + Rubber                                    |
| Drive Shafts             | Metal CVD (x4)                                  |
| Shocks                   | Metal (x4)                                      |
| Motors                   | DC Gearmotor (BEMONOC 25GA370, x4 + drone x4)   |
| Motor Controllers        | L298N Dual H-Bridge (x2)                        |
| Microcontrollers         | Arduino, Raspberry Pi 4                         |
| Electromagnets           | 4 units                                         |
| Bearings                 | Uxcell 10x15x4mm                                |
| Screws/Nuts/Bolts        | M3/M4/M6, nylon, cap nuts                       |
| Breadboard, Sensors      | Multiple                                        |
| Batteries                | LiPo (x2)                                       |
| Pi Camera                | Infrared/automatic switching (x2)               |
| Tools                    | Screwdrivers, pliers, drill                     |

---

## Device Specification

- Ground module max speed: 10 m/s [2]
- Suspension: planetary gear system, indirect mounting [1][2]
- Drone: quad motors, camera, ultrasonic, sound sensors
- Modular docking: electromagnetic, wireless charging
- Real-time sensor and camera feedback
- Designed and printed at Beckman High School

---

## Build Process

**1. CAD & 3D Printing:**  
Design in OnShape, print parts in PETG-CF for durability and UV resistance. Modular slots for drone docking and suspension.

**2. Mechanical & Electronic Assembly:**  
Motors/suspension integrated using metal hardware. Planetary gear system implemented for load and torque distribution [1][2]. Electromagnetic dock added for secure module connection.

**3. Sensor Integration:**  
Ultrasonic, Pi camera (IR mode), and sound sensors mounted. Encoder wires connected to Arduino; FFT for sensor calibration [2].

**4. Testing:**  
- Ground module: varied terrain, stability/speed.
- Drone: confined space, wind resistance.
- Docking: reliability/load strength tested with force sensor.
- Battery life, wireless charging, and photo-recognition assessed [2].

**5. Data Collection:**  
Acceleration (accelerometer), sensor feedback, electromagnetic mount strength, battery consumption, charging efficiency [2].

---

## Project Results

- Stable terrain traversal up to 10 m/s; effective shock absorption [2]
- Accurate hazard/victim detection through sensors [2]
- Modular adaptability: ground/aerial, docking is robust [2]
- Efficiency and durability improved by planetary gear system [1][2]
- FFT sensor calibration enhanced accuracy [2]

---

## Future Directions

- AI for hazard/victim detection  
- Longer battery life, solar/kinetic harvesting  
- Specialized modules for rescues in water/fire/underground  
- Testing in real disaster scenarios [2]

---

## Images

Below are project images formatted for centered display.  
**Horizontally-dominant images:** 2/3 width  
**Vertically-dominant images:** 1/3 width

---

<div align="center">
  <img src="ocsef/B17090F1-A2D6-41B9-A585-FACF8B59D7A4.JPG" width="66%">
  <br> <em>Assembled modular chassis, top view</em>
</div>

<div align="center">
  <img src="ocsef/4A28B365-6B12-4048-ABA2-2F07FB40368E.JPG" width="33%">
  <br> <em>Planetary gear pod (vertical orientation)</em>
</div>

<div align="center">
  <img src="ocsef/7F12A415-A654-4338-AEDE-8F55B8269564.JPG" width="66%">
  <br> <em>Chassis integration phase</em>
</div>

<div align="center">
  <img src="ocsef/85BC9C84-5A49-4E60-B4FA-F81EA42378C2.JPG" width="66%">
  <br> <em>Drone docking demonstration</em>
</div>

<div align="center">
  <img src="ocsef/4A39E4E3-4553-47E2-8F7E-667A52397530.JPG" width="33%">
  <br> <em>Assembly detail (vertical orientation)</em>
</div>

<!-- Repeat for all relevant images in your ocsef folder -->

---

## References

- OCSEF_LOG.pptx [1]
- OCSEF.docx [2]
- GitHub Source: https://github.com/open-dynamic-robot-initiative/open_robot_actuator_hardware  
- Project Paper: https://arxiv.org/pdf/1910.00093

---

## License

Include your preferred open-source license or statement here.

---

### Notes

- Adjust image paths if necessary, depending on your GitHub repo structure.
- Add or remove images and captions as needed for your final layout.

---
