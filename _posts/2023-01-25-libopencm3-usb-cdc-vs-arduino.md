---
title: "libopencm3 USB CDC Virtual Com Port vs Arduino"
author: Squintz
categories: [Troubleshooting]
tags: [STM32F103, Arduino, libopencm3]
math: true
mermaid: true
---

## libopencm3 Struggles

I could not get our custom STM32F103C8t6 based device to enumerate in windows or linux at full speed using the latest libopencm3 (88f4d11) branch and latest libopencm3-example branch from github. I tried dozens of combinations of previous branches of libopencm3, the arm gnu compiler, and the examples. Unfortunately, the original source code is not mine to share so I can't include it here.

## Arduino to the Rescue

To prove the the hardware is fine and the issue I'm experiencing is related to using libopencm3 or something related to the toolchain, I've turned to Arduino. 

I'm running Arduino 1.8.15 because I was too lazy to upgrade

Add the following to File -> Preferences

`https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json`

From Boards Manager Install: STM32 MCU based board by STMicroelectroncis. I was running version 2.10

#### Settings:

* Board: Generic STM32F1 series
* Board part number: Generic F103C8Tx
* U(S)ART support (if available): "CDC(genrric 'Serial' supersede U(S)ART) > Enabled
* USB speed (if available): "Low/Full Speed"
* Optimize: "Smallest (-Os default)"
* Debug symbols: "Enable (-g)"
* C Runtime Library: Newlib Nano (default)"
* Upload method: "STM32CubeProgrammer (SWD)"

```
#include

void setup() {
    Serial.begin(115200); // Initialize the serial communication
}

void loop() {
    // Nothing to do here
    delay(100);
    Serial.println("Hello, World!");
    }
```


I know right! I was shocked too that the Arduino code to print hello world over USB was this simple. Now I know the hardware is fine.

