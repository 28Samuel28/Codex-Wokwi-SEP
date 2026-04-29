# Firmware Architecture

## High-Level Flow
1. Initialize all 12 LED GPIO pins as output and set LOW in `setup()`.
2. Continuously scan keypad with `keypad.getKey()` in `loop()`.
3. If a valid key is pressed, execute a `switch` branch that updates one LED or a group.
4. Wait 10ms (`delay(10)`) and repeat.

## Module / Data Structure Breakdown

- `keys[4][4]`:
  Maps matrix positions to characters (`1..9`, `0`, `A..D`, `*`, `#`).

- `ledPins[12]`:
  Output pin list for each LED channel.

- `rowPins[4]`, `colPins[4]`:
  Keypad matrix interface pins.

- `Keypad keypad` object:
  Handles keypad scanning/debouncing behavior through the library API.

## Key Behavior Matrix

| Key | Action |
|---|---|
| `1..8` | Turn ON a single LED in bank 1 |
| `9` | Turn ON LEDs 1..8 |
| `0` | Turn OFF LEDs 1..8 |
| `A..D` | Turn ON a single LED in bank 2 |
| `*` | Turn ON LEDs A..D |
| `#` | Turn OFF LEDs A..D |

## Non-Functional Notes
- Logic was intentionally preserved (no behavior changes).
- No network/Wi-Fi features are active.
- Current source is ideal for Wokwi/Arduino-style runtime; Pico SDK-native migration would require API shims or refactor.
