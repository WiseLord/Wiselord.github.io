---
layout: avrproject
title: BikeComp
description: Simple bike computer with 320x240 color LCD
project: bikecomp
---

# Project overview

This project is a simple bike computer. It measures such parameters as speed (current and average), cadence, track time, etc. The information is displayed on color LCD based on ILI9431 driver

<iframe width="640" height="360" src="https://www.youtube.com/embed/masuh6hbeew" style="border: 0;" allowfullscreen></iframe>

# Main features:

* Automatic sleep mode
* Automatic wakeup on signal from sensors
* Speed, cadence, time measurement
* Color themes: white on black mode, black on white mode, color mode

# Schematic

![Schematic](https://raw.githubusercontent.com/WiseLord/bikecomp/master/files/bikecomp_sch.png)

# How it works

There are two magnets attached to the wheel and pedal. When wheel/pedal rotates, it goes near a sensor, which is the reed switch. The signals from these two (wheel and pedal) sensors goes to MCU which calculates all parameters.


# Useful links:

* [Article about the project](http://radiokot.ru/circuit/digital/measure/153) (in Russian)

* [Forum thread](http://radiokot.ru/forum/viewtopic.php?t=146831) (in Russian)
