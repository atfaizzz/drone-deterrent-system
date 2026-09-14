[Project code available on request: mail at faizabid32@gmail.com]
# Bird Deterrent System for Delivery Drones 

This repository contains the design, components, and logic for a **lightweight, AI-driven bird deterrent system** for autonomous delivery drones. The system proactively detects and repels birds using a combination of **computer vision, real-time onboard AI, and multi-modal deterrents** (audio, visual, motion). It is designed for drones operating in **challenging environments**, such as hilly or mountainous regions where bird attacks can threaten safe flight.

---

##  Key Features

- **Bird Detection using YOLOv4-tiny** on Raspberry Pi or Jetson Nano.
- **Real-time onboard inference** for detecting approaching birds.
- **Multi-modal deterrence** system: distress calls, strobe light, predator decoy, and evasive maneuvers.
- **Failsafe remote override** via LoRa or LTE.
- **Weatherproof and field-deployable** for outdoor delivery missions.
- Optimized for **low cost (< ₹50,000)** and **lightweight (< 1.5 kg)** integration.

---

##  System Overview

| Subsystem         | Description                                                                                                                                           |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Detection**     | Camera + YOLOv4-tiny model on embedded hardware (e.g., Raspberry Pi + Coral TPU).                                                                    |
| **Deterrence**    | Combines audio (bird distress/predator calls), visual (strobe LEDs), and physical decoy (predator head).                                             |
| **Evasion**       | On detection of imminent threat, autopilot executes aggressive maneuver (climb/spin/swerve) to avoid bird collision.                                 |
| **Autonomy**      | GPS-guided navigation using Pixhawk/ArduPilot with barometer, IMU, and optional SLAM/LiDAR-based obstacle avoidance.                                |
| **Communication** | LoRa or LTE-based failsafe remote control for manual override or emergency command input.                                                             |
| **Weatherproofing**| All electronics enclosed in IP-rated casings with conformal coating and passive thermal protection for outdoor conditions.                          |

---

## 📷 Bird Detection Pipeline

The system uses YOLOv4-tiny, a lightweight object detection model fine-tuned to identify birds in real time.

### Workflow:
1. Capture live video feed from forward-facing camera.
2. Run detection using YOLOv4-tiny on embedded board.
3. If bird detected:
   - Trigger deterrents.
   - Send alert to remote controller.
   - Optionally initiate evasive maneuver.

>  Real-time performance achieved on Raspberry Pi 4 + Coral TPU or Jetson Nano (~10-15 FPS).

---

## 🔊 Multi-Modal Deterrence System

| Mode     | Component                               | Functionality                                                                 |
|----------|------------------------------------------|--------------------------------------------------------------------------------|
| **Audio**  | Speaker + Amplifier                     | Emits distress and predator calls (e.g., hawk screech, crow alarm).           |
| **Light**  | High-intensity Strobe LEDs              | Flashes at 10–20 Hz to disorient and deter birds.                             |
| **Decoy**  | Predator head or silhouette             | Static/dynamic hawk decoy triggers instinctive fear response.                |
| **Motion** | Autopilot command via MAVLink          | Executes evasive maneuvers (e.g., vertical climb or swerve).                  |

All deterrents are **non-lethal, eco-friendly**, and combinable for increased effectiveness.

---

##  Hardware Architecture

### Detection Module (~170g)
- Raspberry Pi 4 or Jetson Nano
- Coral USB Accelerator / Intel NCS2
- Pi/Arducam camera module

### Deterrence System (~640g)
- Audio module: Mini speaker + amplifier
- Strobe LEDs + driver
- Predator decoy with mount
- Control PCB and GPIO interface

### Communication Backup (~110g)
- LoRa SX1278 module or LTE dongle
- Antenna and UART interface

---

##  Autonomous Control Architecture

**Layer 1: Primary Autonomy**
- GPS + Barometer for navigation.
- Bird detection AI triggering deterrents.
- Obstacle avoidance via LiDAR/stereo camera.
- Autonomous evasive flight logic.

**Layer 2: Remote Assist / Failsafe**
- LoRa (900 MHz) or LTE backup link.
- Remote override: Return to Home / Hover / Abort.
- Real-time telemetry: bird detection alerts, deterrent status, battery levels.

---

##  Weatherproof Design

| Component   | Protection Strategy                        |
|------------|---------------------------------------------|
| Electronics | IP65 housing, silica gel, conformal coating |
| Speaker     | Horn type with mesh + silicone seal         |
| LED Strobe  | Epoxy-sealed dome                           |
| Decoy       | Lightweight, waterproof plastic             |

