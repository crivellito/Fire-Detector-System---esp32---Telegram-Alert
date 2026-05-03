# 🔥 Fire Detector System — ESP32 + Telegram Alert

![Platform](https://img.shields.io/badge/Platform-ESP32-blue?logo=espressif)
![Language](https://img.shields.io/badge/Language-C%2B%2B-orange?logo=c%2B%2B)
![Framework](https://img.shields.io/badge/Framework-ESP--IDF-red)
![Notification](https://img.shields.io/badge/Alerts-Telegram%20Bot-26A5E4?logo=telegram)
![License](https://img.shields.io/badge/License-Academic-lightgrey)

> IoT-based fire detection system built on ESP32. Monitors environmental conditions in real time and sends **instant alerts via Telegram Bot** when fire or smoke is detected.

---

## 📋 Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Telegram Bot Setup](#telegram-bot-setup)
- [Configuration](#configuration)
- [How It Works](#how-it-works)
- [Authors](#authors)

---

## 📖 About the Project

This project was developed as part of the **Electronic Engineering curriculum at UTN — Facultad Regional Córdoba (FRC)**. The goal is to implement a low-cost, reliable fire detection system using an ESP32 microcontroller that connects to a Wi-Fi network and notifies users remotely through a Telegram Bot when fire or smoke is detected.

The system is designed to be deployed in enclosed spaces such as offices, labs, or residential areas, providing an accessible and real-time alert mechanism accessible from any smartphone.

---

## ✨ Features

- 🔥 **Real-time fire and smoke detection** using dedicated sensors
- 📲 **Instant Telegram notifications** sent to a configured chat when danger is detected
- 📡 **Wi-Fi connectivity** via ESP32's built-in wireless module
- ⚡ **Low power footprint** — ideal for continuous 24/7 monitoring
- 🛠️ **Modular firmware** written in C++ with ESP-IDF
- 📐 **Full schematic** included for hardware replication

---

## 🔧 Hardware Requirements

| Component | Description |
|---|---|
| **ESP32** | Main microcontroller (Wi-Fi + processing) |
| **Flame Sensor** | Infrared-based fire detection (e.g., KY-026) |
| **Smoke / Gas Sensor** | Analog smoke detection (e.g., MQ-2) |
| **Power Supply** | 5V USB or regulated supply |
| **Jumper Wires & Breadboard** | For prototyping |

> Refer to the [`esquematico/`](./esquematico/) folder for the full circuit schematic.

---

## 📁 Project Structure

```
Fire-Detector-System/
│
├── esp32/                  # ESP32 firmware source code (C++)
│   └── main/
│       └── main.cpp        # Main application logic
│
├── esquematico/            # Circuit schematic files
│
├── images/                 # Project photos and diagrams
│
├── proyecto/               # Project documentation / reports
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- [ESP-IDF](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/) installed and configured
- A Telegram account with a Bot created via [@BotFather](https://t.me/BotFather)
- ESP32 development board connected via USB

### Clone the Repository

```bash
git clone https://github.com/crivellito/Fire-Detector-System---esp32---Telegram-Alert.git
cd Fire-Detector-System---esp32---Telegram-Alert
```

### Build & Flash

```bash
cd esp32
idf.py set-target esp32
idf.py build
idf.py -p /dev/ttyUSB0 flash monitor
```

> Replace `/dev/ttyUSB0` with the correct serial port on your system (`COMx` on Windows).

---

## 🤖 Telegram Bot Setup

1. Open Telegram and search for **@BotFather**
2. Send `/newbot` and follow the instructions to create a bot
3. Copy the **Bot Token** provided
4. To get your **Chat ID**, message **@myidbot** and send `/getid`
5. Add both values to the configuration (see below)

---

## ⚙️ Configuration

Inside `esp32/main/main.cpp`, update the following placeholders with your own credentials:

```cpp
#define WIFI_SSID       "your_wifi_ssid"
#define WIFI_PASSWORD   "your_wifi_password"
#define BOT_TOKEN       "your_telegram_bot_token"
#define CHAT_ID         "your_telegram_chat_id"
```

> ⚠️ **Never commit real credentials to a public repository.** Consider using `menuconfig` or environment variables to manage secrets safely.

---

## ⚙️ How It Works

```
[Flame / Smoke Sensor]
        │
        ▼
   [ESP32 reads sensor values]
        │
   ┌────┴──────────────────┐
   │  Threshold exceeded?  │
   └────┬──────────────────┘
        │ YES
        ▼
  [Connect to Wi-Fi]
        │
        ▼
  [Send Telegram Alert 🔥]
        │
        ▼
  [User receives notification on phone]
```

The ESP32 continuously polls the connected sensors. When a reading exceeds the defined danger threshold, it establishes a connection to the Telegram Bot API and dispatches an alert message to the configured chat ID.

---

## 👥 Authors

Developed by students of **Ingeniería Electrónica — UTN Facultad Regional Córdoba**:

| Name | GitHub |
|---|---|
| Augusto Crivelli | [@crivellito](https://github.com/crivellito) |
| Bruno Germani | — |
| Mateo Zanel | — |

---

*Universidad Tecnológica Nacional — Facultad Regional Córdoba*
