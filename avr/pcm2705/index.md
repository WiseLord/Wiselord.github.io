---
layout: avrproject
title: PCM2705
description: External USB DAC with remote control feature
project: pcm2705
---

# Project overview

PCM2705 is an USB DAC which can be used as external audio card for your PC. This project adds functionality to control media player on the computer by sending standard HID commands through USB like multimedia keyboards do that. Device can be controlled via buttons or RC5/NEC remote control.

<iframe width="640" height="360" src="https://www.youtube.com/embed/stMPUYBaQmc" style="border: 0;" allowfullscreen></iframe>

# Main features:

* RC5 and NEC remote control support
* Remote control learning support
* Signal LED to monitor control commands

# Schematic

![schematic](https://raw.githubusercontent.com/WiseLord/pcm2705/master/files/schematic.png)

# Remote control

By default button sends appropriate HID command to PC when pressed and LED flashes once. To learn your NEC/RC5 remote your first  need to enter learn mode by pressing MUTE, VOLUP and VOLDN buttons simultaneously. LED will flash 3 times. Then, press button on your remote control followed by button on device to link them. LED will flash 2 times. So, learn all other buttons by the same method and exit learn mode by pressing MUTE, VOLUP and VOLDN buttons simultaneously again. Now you can use remote control.

# Useful links:

* [Article about the project](http://radiokot.ru/konkursCatDay2015/07) (in Russian)
* [Forum thread](http://radiokot.ru/forum/viewtopic.php?t=124202) (in Russian)
