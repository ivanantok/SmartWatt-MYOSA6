# SmartWatt
### MYOSA 6.0 — Smart Home Energy Awareness System

SmartWatt is a MYOSA-based intelligent home energy system that automatically switches off fans and lights when the last person leaves a room, and warns families before their KSEB electricity bill crosses the expensive slab threshold — projecting the bill live in rupees.

---

## The Problem

Kerala is facing a 900 MW power deficit. Most household electricity waste comes from two sources:
- Fans and lights left running in empty rooms
- Families unaware they are about to cross the KSEB 250-unit slab threshold — the point where the entire bill recalculates at the highest rate, often doubling overnight

SmartWatt solves both.

---

## Features

- **Automatic room management** — dual APDS9960 proximity sensors detect entry and exit direction, counting occupants. When the last person leaves, the relay automatically cuts power to the fan and light
- **KSEB slab-aware bill intelligence** — tracks electricity consumption in real time and projects the monthly bill in rupees using KSEB Tariff 2025-27 slab rates
- **Live OLED display** — shows occupancy count, units consumed, projected bill, and slab status
- **Buzzer alert** — fires when projected consumption will cross 250 units within 5 days
- **Web dashboard** — live updates via Firebase, accessible on any phone on the same network

---

## Components

### MYOSA Mini Kit
| Component | Role |
|---|---|
| ESP32 Motherboard | Core processing, WiFi, Firebase communication |
| APDS9960 (×2) | Directional people counting at door frame |
| MPU6050 | Secondary footstep vibration confirmation |
| BMP180 | Temperature correlation with AC usage |
| OLED Display | Live readings display |
| Buzzer | Slab threshold alert |

### Additional Components
| Component | Role |
|---|---|
| CT Clamp SCT-013-100A | Non-invasive current measurement |
| Relay Module 5V | Auto switch-off for fan and light |
| Potentiometer 10kΩ | Simulates CT clamp for demo |
| 5V DC Fan | Represents room fan |
| LED | Represents room light |

---

## How It Works

### Layer 1 — Directional People Counting
Two APDS9960 sensors mounted at ankle height on opposite sides of the door frame. Sensor A triggering before Sensor B means entry — count increments. Sensor B before A means exit — count decrements. When count reaches zero the relay switches off the fan and light automatically.

### Layer 2 — KSEB Bill Intelligence
CT clamp measures current draw every 10 seconds. ESP32 calculates units consumed and projects end-of-month bill using KSEB slab rates hardcoded in firmware. Alert fires when projected consumption approaches 250 units.

---

## Repository Structure










---

## Setup Instructions

1. Clone this repository
2. Open `firmware/smartwatt/smartwatt.ino` in Arduino IDE
3. Install required libraries — Adafruit APDS9960, Adafruit BMP085, MPU6050, Firebase ESP32 Client, Adafruit SSD1306
4. Update WiFi credentials and Firebase URL in the code
5. Select board — ESP32 Dev Module
6. Upload to MYOSA board
7. Connect phone to same WiFi network
8. Open Firebase dashboard URL on phone

---

## Team

| Name | Role | Branch |
|---|---|---|
| Ivana Anto | Hardware, Firmware, Demo | B.Tech ECE 3rd Year, CUSAT |
| Nandagopal SB | Web Dashboard, Firebase | B.Tech IT 4th Year, CUSAT |

**Faculty Mentor:** Dr. Anju Pradeep, Dept. of Electronics and Communication Engineering, CUSAT

---

## Competition

**IEEE MYOSA 6.0** — Make Your Own Sensor Applications
Organized by IEEE Sensors Council
Blog Submission Phase — August 2026

---

## License

MIT License — see LICENSE file for details
