🚀 Smart Energy Meter with Load Control (STM32 + FreeRTOS + MQTT)

Real-time embedded smart energy metering system built using STM32, FreeRTOS, and MQTT.
It measures voltage, current, power, and energy, publishes live telemetry via MQTT, and automatically disconnects loads when thresholds are exceeded.

---

✨ Features

-⚡ 2 kHz ADC sampling for voltage & current<br>
-📊 RMS, active power, and energy computation<br>
-🔌 Automatic load cut-off using relay/GPIO<br>
-☁️ MQTT telemetry publishing<br>
-📉 Node-RED dashboard for real-time visualization<br>
-📦 Modular FreeRTOS tasks:

-Sampling Task<br>
-Processing Task<br>
-MQTT Communication Task<br>
-Protection Task<br>

---

## 📁 Repository Structure

```
smart-energy-meter/
├── firmware/               # Embedded STM32 + FreeRTOS firmware skeleton
│   └── main.c
│
├── docs/                   # Documentation, calibration notes, Node-RED flow
│   └── README.md
│
├── hardware/               # Schematic placeholder (PNG recommended)
│   └── SCHEMATIC.txt
│
├── examples/               # Sample telemetry JSON
│   └── telemetry_sample.json
│
├── run.sh                  # Simple demo script (non-firmware)
└── README.md               # Project documentation
```



---

🔧 Architecture Overview

🟦 FreeRTOS Tasks

| Task Name         | Function                                      |
| ----------------- | --------------------------------------------- |
| `vTaskSampler`    | Samples voltage & current using ADC           |
| `vTaskProcessor`  | Computes RMS, active power, energy            |
| `vTaskComms`      | Publishes telemetry via MQTT                  |
| `vTaskProtection` | Disconnects load on overload/threshold breach |

---

📐 Measurement Flow

ADC Samples → Calibration → RMS/Power Calculation → MQTT Payload → Dashboard

---

🔌 Load Protection Logic

if (current_rms > max_limit || energy_wh > daily_limit)
     cut_off_load();

---

🖥 Example Telemetry Output<br>
examples/telemetry_sample.json:<br>

{<br>
  "device": "smart-meter-001",<br>
  "timestamp": "2025-12-06T12:00:00Z",<br>
  "voltage_rms": 230.1,<br>
  "current_rms": 3.25,<br>
  "active_power": 748.0,<br>
  "energy_wh": 12.4,<br>
  "overload": false<br>
}

---

🛠 Building the Firmware

Option 1 — STM32CubeIDE

1. Create a new STM32 project
2. Copy files from firmware/main.c
3. Configure:
-ADC (dual-channel sampling)
-Timer interrupt
-GPIO for Relay
-FreeRTOS tasks
4. Build & flash using ST-Link

Option 2 — ARM GCC Toolchain

This repository contains a firmware skeleton, not a full BSP.

arm-none-eabi-gcc main.c -o smart-meter.elf ...

---

📊 Node-RED Dashboard

Import the flow file from:
docs/node-red-flow.json

Dashboard includes:<br>
-Live Voltage RMS<br>
-Current RMS<br>
-Power usage<br>
-Daily energy chart<br>
-Overload indicator<br>

---

📄 Future Enhancements

-Add preemptive power disconnection over MQTT<br>
-Add modbus energy meter compatibility<br>
-Export telemetry to InfluxDB or Grafana<br>
-Add Wi-Fi connectivity (ESP8266/ESP32 bridge)<br>
-Add mobile dashboard<br>

---

📝 License

MIT License (optional—add LICENSE file if needed)
