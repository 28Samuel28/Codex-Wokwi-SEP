# Wiring and GPIO Mapping

## Overview
The design connects a 4x4 matrix keypad and 12 LEDs to Raspberry Pi Pico/Pico W GPIO pins.

## Components and Electrical Notes
- Each LED is connected in series with a 220Ω resistor and then to a GPIO.
- LED cathodes are tied to GND.
- Keypad rows are connected to GPIOs and externally pulled up to 3V3 with four 1kΩ resistors (one per row).
- Keypad columns are connected directly to GPIOs.

## GPIO Mapping Table

| Function | GPIO | Physical net in code |
|---|---:|---|
| LED1 (label "1") | GP11 | `ledPins[0]` |
| LED2 (label "2") | GP10 | `ledPins[1]` |
| LED3 (label "3") | GP9  | `ledPins[2]` |
| LED4 (label "4") | GP8  | `ledPins[3]` |
| LED5 (label "5") | GP7  | `ledPins[4]` |
| LED6 (label "6") | GP6  | `ledPins[5]` |
| LED7 (label "7") | GP5  | `ledPins[6]` |
| LED8 (label "8") | GP4  | `ledPins[7]` |
| LED9 (label "A") | GP3  | `ledPins[8]` |
| LED10 (label "B")| GP2  | `ledPins[9]` |
| LED11 (label "C")| GP28 | `ledPins[10]` |
| LED12 (label "D")| GP27 | `ledPins[11]` |
| Keypad R1 | GP26 | `rowPins[0]` |
| Keypad R2 | GP22 | `rowPins[1]` |
| Keypad R3 | GP21 | `rowPins[2]` |
| Keypad R4 | GP20 | `rowPins[3]` |
| Keypad C1 | GP19 | `colPins[0]` |
| Keypad C2 | GP18 | `colPins[1]` |
| Keypad C3 | GP17 | `colPins[2]` |
| Keypad C4 | GP16 | `colPins[3]` |

## Assumptions and Clarifications
- The provided code targets a Pico-class board and is pin-compatible with Pico W for used GPIOs.
- Diagram text references shared VCC/GND; all LED cathodes share GND and keypad row pull-ups share 3V3.
- UART GP0/GP1 are connected to Wokwi serial monitor for debug compatibility.
