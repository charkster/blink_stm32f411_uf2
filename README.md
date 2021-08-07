# blink_stm32f411_uf2
Arduino Blink made into a UF2 for STM32F411 Blackpill. First, tinyuf2 for Blackpill needs to be flashed as the bootloader. This UF2 file can then be copied to the MCU.

https://www.arduino.cc/en/Tutorial/BuiltInExamples/Blink

https://github.com/adafruit/tinyuf2

Instructions for making a STM32F411 UF2 file in the Arduino environment

(1) Edit arduino/packages/STM32/hardware/stm32/1.9.0/system/STM32F4xx/system_stm32f4xx.c

Change to: #define VECT_TAB_OFFSET         0x00010000U

(2) Edit arduino/packages/STM32/hardware/stm32/1.9.0/variants/Generic_F411Cx/ldscript.ld

Change to: FLASH (rx)      : ORIGIN = 0x8010000

(3) uf2 creation command:

uf2conv.py -b 0x08010000 -f STM32F4 -o blink.ino.uf2 Blink.ino.bin 

The UF2 bootloader will have the Blackpill appear as a flash drive, and blink.ino.uf2 can be copied to that drive. If another UF2 file is to be copied to the Blackpill, a double-press of the NRST pin will activate the bootloader and it will appear as a flash drive again.
