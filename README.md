# Pico W Keypad-to-LED Controller

This repository documents and organizes a Raspberry Pi Pico / Pico W project that reads a 4x4 matrix keypad and controls 12 LEDs.

## Project Features
- 4x4 keypad scanning using `Keypad` library (`R1..R4`, `C1..C4`).
- 12 independent LED outputs.
- Key mappings:
  - `1..8`: turn ON LED bank 1 (single channel each)
  - `9`: turn ON LEDs 1..8
  - `0`: turn OFF LEDs 1..8
  - `A..D`: turn ON LED bank 2 (single channel each)
  - `*`: turn ON LEDs A..D
  - `#`: turn OFF LEDs A..D

## Repository Structure
- `src/main.cpp` - original firmware logic (preserved behavior)
- `include/` - reserved for headers/extensions
- `docs/wiring.md` - hardware wiring and GPIO mapping
- `docs/architecture.md` - software structure and behavior
- `wokwi/diagram.json` - hardware diagram source
- `CMakeLists.txt` - minimal top-level build/documentation scaffold

## Components (from diagram)
- 1x Raspberry Pi Pico (compatible with Pico W pinout)
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red)
- 12x 220Ω LED resistors
- 4x 1kΩ pull-up resistors for keypad rows
- Jumper wires and USB power

## GPIO Allocation Summary
- Keypad columns: GP16, GP17, GP18, GP19
- Keypad rows: GP26, GP22, GP21, GP20
- LED outputs: GP11, GP10, GP9, GP8, GP7, GP6, GP5, GP4, GP3, GP2, GP28, GP27

## Run in Wokwi
1. Create a new Pico project in Wokwi.
2. Copy `src/main.cpp` into the sketch/editor.
3. Copy `wokwi/diagram.json` into `diagram.json`.
4. Ensure `Keypad` library is enabled in Wokwi libraries.
5. Start simulation and press keypad buttons.

## Run on Real Hardware (Pico W)
> Note: The supplied code uses Arduino-style APIs (`setup`, `loop`, `pinMode`, `digitalWrite`, `delay`) and `Keypad.h`.

1. Use an Arduino-compatible RP2040 toolchain (e.g., Arduino IDE with RP2040 core).
2. Select **Raspberry Pi Pico W** board.
3. Wire according to `docs/wiring.md`.
4. Build and upload.
5. Validate key-to-LED behavior.

## Pico SDK note
A pure Pico SDK build needs adaptation because the current program depends on Arduino runtime + `Keypad` library API. This repository keeps the original logic unchanged and focuses on maintainability/documentation.

## Wi-Fi / Credentials
This project does not use Wi-Fi in its current logic. No credentials are required or stored.
