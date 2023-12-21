# HapticDriver

> Compact and over-engineered solenoid driver board for the purpose of generating localised haptic feedback.

## Features

* ESP32S3 module
* USB-C host port
* 12 MOSFET H-bridges with current regulation (up to 1A each)
* Powered by LiPo batteries (15V max)
* Extremely compact size - approx 6x3cm including antenna
* 4-layer PCB

---

## Description

This is a _work in progress_ driver board which has the capability to drive 12 solenoids bi-directionally
for the purpose of providing focused and precise haptic feedback. It's intended to be used in tendem with
a host application communicating over either WiFi or Bluetooth.

Due to the ESP module's limited number of GPIO, 3 8-bit shift registers over I2S were used to effectively
expand 3 I2S GPIO into 24 individually assignable outputs. This corresponds to the 24 H-bridge driver
inputs, which allow powering 12 electromagnets (forming solenoids) with regulated current of either
direction.

There is a 3V3 LDO regulator onboard for powering the logic bus - including the ESP32, shift registers
and motor driver logic power. It's powered through the battery power input, and provides up to 800mA and
has an absolute maximum voltage of 15V. Although the drivers tolerate a power input of up to 18V, the
LDO effectively limits the maximum battery input voltage to 15V. Care should be taken not to exceed this.
