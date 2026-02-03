# Ultrasonic Distance Sensor — Arduino Uno R4 WiFi

## Project overview
This project reads distance from an ultrasonic sensor (e.g. HC-SR04) using an Arduino Uno R4 WiFi and prints the measurement over the serial port. Source is in `src/main.cpp` and project configuration in `platformio.ini`.

## Hardware
- Arduino Uno R4 WiFi
- Ultrasonic sensor (HC-SR04 or compatible)
- Jumper wires
- Breadboard (optional)

## Wiring (example)
- Sensor VCC -> `5V` on Uno R4 WiFi  
- Sensor GND -> `GND`  
- Sensor TRIG -> digital pin `9`  
- Sensor ECHO -> digital pin `10`

Adjust pins if you modified `src/main.cpp`.

## Configuration
- The project uses PlatformIO with an environment for `uno_r4_wifi` (platform `renesas-ra`, framework `arduino`). See `platformio.ini` for the exact environment and serial/upload port.
- Default serial baud: `9600`.

## Build & upload (PlatformIO CLI)
- Build: `pio run`  
- Upload to board (use environment name from `platformio.ini`): `pio run -e uno_r4_wifi -t upload`  
- Open serial monitor (example using COM5 and 9600 baud): use your IDE serial monitor or `pio device monitor --port COM5 --baud 9600`

If using CLion with PlatformIO plugin, use the IDE build/upload/monitor actions.

## Usage
1. Wire the sensor as described.
2. Build and upload the firmware.
3. Open the serial monitor at `9600` baud to view distance readings (units: cm).

## Troubleshooting
- No output: check `platformio.ini` `upload_port` / `monitor_port` and correct COM port.
- Incorrect distance: ensure correct wiring, sensor stable power, and that TRIG/ECHO pins match `src/main.cpp`.
- If `pulseIn` behaves unexpectedly on alternate cores/boards, try pin-change-safe pins or measure timing with interrupts.

## License
MIT
