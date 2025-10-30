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

## 🧩 Hardware Components

| Component | Description |
|------------|-------------|
| ESP32 | Controls traffic lights |
| 6 LEDs (2 sets of R/Y/G) | Represent two-lane signals |
| Jumper Wires | Circuit connections |
| Breadboard | Hardware setup |
| Android Phone (IP Webcam) | Camera source |
| Laptop | Runs Python detection logic |

---

## 💻 Software Requirements

| Software | Purpose |
|-----------|----------|
| Python 3.x | AI logic |
| OpenCV | Vehicle detection |
| NumPy | Frame processing |
| PySerial | Communication with ESP32 |
| Arduino IDE | Flashing ESP32 code |

### Install Dependencies
```bash
pip install opencv-python numpy pyserial
```

---

## 🧠 Working Principle

1. Two camera feeds are captured via IP Webcam URLs.  
2. `Car Detection and Logic.py` detects and counts vehicles using **MobileNetSSD**.  
3. Based on density, Python decides which lane gets green.  
4. Commands (`L1_5`, `L2_8`, `NO`) are sent to ESP32 over serial.  
5. The **ESP32 Code.ino** script interprets these commands and lights up corresponding LEDs.  

---

## 🧾 Code Structure

```
SmartTraffic/
│
├── Car Detection and Logic.py      # AI + logic + serial communication
├── ESP32 Code.ino                  # ESP32 traffic light control
├── requirements.txt                # Python dependencies
└── README.md                       # Documentation
```

---

## 🔌 Serial Communication Protocol

| Command | Meaning |
|----------|----------|
| `L1_5` | Lane 1 → Green for 5 seconds |
| `L2_8` | Lane 2 → Green for 8 seconds |
| `NO`   | No vehicles → Blinking yellow |

ESP32 listens on **9600 baud rate** and switches signals accordingly.

---

## 🧩 ESP32 Pin Configuration Example

| Light | GPIO Pin |
|--------|-----------|
| Lane 1 Red | 25 |
| Lane 1 Yellow | 26 |
| Lane 1 Green | 27 |
| Lane 2 Red | 14 |
| Lane 2 Yellow | 12 |
| Lane 2 Green | 13 |

*(You can change pin numbers in the `.ino` file as needed.)*

---

## 🧪 Example Output

```
Switch → Lane 2 GREEN for 8s
Sent L2_8 to ESP
No vehicles detected → Blinking YELLOW
Sent NO to ESP
```

---

## 🧠 Model Details

- **Model Used:** MobileNetSSD (Caffe model)
- **Classes:** Car, Bus, Bicycle, Motorbike, Truck
- **Confidence Threshold:** 0.5  
- **Input Size:** 300×300

You can download `MobileNetSSD_deploy.prototxt` and `MobileNetSSD_deploy.caffemodel` from the OpenCV model zoo.

---

## 🚀 Future Improvements

- Add **ambulance detection** for emergency lane priority  
- Add **Flask web dashboard** for live monitoring  
- Integrate **cloud-based data logging**  
- Use **YOLOv8** for more accurate detection  
- Expand to **4-lane control** and synchronization across junctions  

---

## 🧑‍💻 Contributors

| Name | Role |
|------|------|
| **Prem Patel** | AI & Software Integration |
| **[Teammate 1]** | Hardware & ESP32 Logic |
| **[Teammate 2]** | Testing & Visualization |

---

## 📽️ Demo (Optional)

Add your demo video link below once uploaded:  
👉 [Watch Demo on YouTube](#)

---

## 🏁 Conclusion

This project showcases the real-world integration of **AI and IoT** for solving urban traffic challenges.  
By combining live vehicle detection with dynamic traffic control, it significantly reduces waiting time and enhances traffic efficiency.

---

## 📜 License

This project is licensed under the **MIT License** — feel free to modify and expand.
