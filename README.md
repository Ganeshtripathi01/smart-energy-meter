# Smart Energy Meter with Load Control (STM32 + FreeRTOS + MQTT)

**One-line:** Real-time smart energy meter using STM32 + FreeRTOS that samples current/voltage, computes power/energy, reports via MQTT, and enforces automatic load cut-off.

## Contents
- `firmware/` — STM32/FreeRTOS example code & build notes
- `docs/` — block diagrams, calibration notes, Node-RED flow
- `hardware/` — schematic (placeholder PNG)
- `examples/` — sample telemetry JSON, config
- `README.md` — this file

## Features
- ADC sampling at 2 kHz for current & voltage (calibrated)
- RMS and active power calculation, energy accumulation
- MQTT over TLS (or plain) to publish telemetry
- Automatic load cut-off based on configurable thresholds
- FreeRTOS task architecture: sampling, processing, comms, protection
- Node-RED dashboard for live visualization

## How to use (developer)
- Firmware: open `firmware/` in STM32CubeIDE or build with `make` (toolchain dependent).
- Node-RED: import `docs/node-red-flow.json` into Node-RED.

## Example telemetry
`examples/telemetry_sample.json`

## Build & Flash (example)
This project contains implementation notes, NOT a full board support package.
- Use STM32CubeIDE or `arm-none-eabi` toolchain to compile `firmware/main.c`.
- Flash using ST-Link.

