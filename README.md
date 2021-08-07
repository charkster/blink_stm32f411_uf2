# blink_stm32f411_uf2
Arduino Blink made into a UF2 for STM32F411 Blackpill. First, tinyuf2 for Blackpill needs to be flashed as the bootloader. This UF2 file can then be copied to the MCU.

https://www.arduino.cc/en/Tutorial/BuiltInExamples/Blink

https://github.com/adafruit/tinyuf2

Instructions for making a STM32F411 UF2 file in

(1) Edit arduino/packages/STM32/hardware/stm32/1.9.0/system/STM32F4xx/system_stm32f4xx.c

Change to: #define VECT_TAB_OFFSET         0x00010000U

(2) Edit arduino/packages/STM32/hardware/stm32/1.9.0/variants/Generic_F411Cx/ldscript.ld

Change to: FLASH (rx)      : ORIGIN = 0x8010000

(3) uf2 creation command:

uf2conv.py -b 0x08010000 -f STM32F4 -o Blink.ino.uf2 Blink.ino.bin 
