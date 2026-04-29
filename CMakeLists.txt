cmake_minimum_required(VERSION 3.13)

project(pico_w_keypad_led_controller C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# This project uses Arduino-style APIs (setup/loop, pinMode, digitalWrite)
# and the Keypad library in Wokwi.
# For native Pico SDK builds, a compatibility layer/framework would be needed.

add_custom_target(notes ALL
  COMMENT "Use this repository primarily as documentation + Wokwi simulation source")
