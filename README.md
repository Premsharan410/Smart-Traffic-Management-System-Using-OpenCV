# 🚦 Smart Traffic Management System (AI + IoT)

An AI-powered **Smart Traffic Management System** that dynamically controls traffic lights based on **real-time vehicle detection** using **OpenCV + MobileNetSSD** and communicates decisions to an **ESP32 microcontroller** for physical light control.

---

## 🧠 Overview

This project uses **computer vision** to analyze live camera feeds and detect vehicles across multiple lanes.  
Depending on vehicle density, it dynamically adjusts the traffic signal duration to optimize flow.  
Additionally, the system detects no-traffic conditions and triggers a blinking yellow state.

---

## 🔧 Features

✅ Real-time vehicle detection using **OpenCV** and **MobileNetSSD**  
✅ Dynamic signal switching based on lane congestion  
✅ “No Vehicle” detection triggers blinking yellow lights  
✅ IoT integration with **ESP32** via serial communication  
✅ Two-lane intelligent control logic  
✅ Real-time camera feed visualization  

---

## ⚙️ System Architecture

```
📷 Cameras (Lane 1 & Lane 2)
        ↓
🧠 Python (OpenCV + MobileNetSSD)
        ↓
📡 Serial Communication (COM Port)
        ↓
🔌 ESP32 → Controls Traffic Lights (LEDs)
```

---

## 💻 Software Requirements

| Software | Purpose |
|-----------|----------|
| Python 3.x | AI logic |
| OpenCV | Vehicle detection |
| NumPy | Frame processing |
| MobileNetSSD | Object Detection Model |
| PySerial | Communication with ESP32 |
| Arduino IDE | Flashing ESP32 code |

### Install Dependencies
```bash
pip install opencv-python numpy pyserial
```

## 🧠 Working Principle

1. Two camera feeds are captured via IP Webcam URLs.  
2. `Car Detection and Logic.py` detects video using **OpenCV** and counts vehicles using **MobileNetSSD**.  
3. Based on density, Python decides which lane gets green.  
4. Commands (`L1_5`, `L2_8`, `NO`) are sent to ESP32 over serial using PySerial
5. The **ESP32 Code.ino** script interprets these commands and lights up corresponding LEDs.  

---

