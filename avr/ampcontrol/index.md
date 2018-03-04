---
layout: avrproject
title: Ampcontrol
description: Amplifier control module with spectrum analyzer and FM radio
project: ampcontrol
---

# Project overview

This system is an amplifier control module supporting various audio processors with I²C interface. It can be managed either with RC-5, RC-6, NEC or Samsung infrared remote control or with front panel 5 buttons and rotary encoder. All appropriate information during control is displayed on monochrome graphic LCD. When nothing is controlled, current time, FM radio screen or results of signal spectrum analisis are displayed.

<iframe width="640" height="360" src="https://www.youtube.com/embed/i6dqi8C9fBk" style="border: 0;" allowfullscreen></iframe>

Upstream development is focused on [ATmega32](https://github.com/WiseLord/ampcontrol/tree/m32) MCU and 128x64 graphic displays (KS0108 and ST7920 controllers). This version provides many features, possibly missing in other possible hardware options. Alphanumeric displays with size 16x2, which based on HD44780 (KS0066) controllers are also now supported, but they don't look so cute as graphic displays.

Also [ATmega8](https://github.com/WiseLord/ampcontrol/tree/m8) version is under active development. But it doesn't include some features from main branch and supports only alphanumeric displays

# Main features:

|Feature                                                                 |ATmega32|ATmega8|
|------------------------------------------------------------------------|--------|-------|
|Amplifier control (mute/standby external signals)                       |yes     |yes    |
|Digital audio control (feature set depends on used audio processor)     |yes     |yes    |
|32-band spectrum analyzer (0..5kHz)                                     |yes     |yes    |
|RC5 remote control support                                              |yes     |yes    |
|English, Russian, Belarusian, Ukrainian and possible other localizations|yes     |yes    |
|FM radio support                                                        |yes     |yes    |
|Up to 50 FM stations can be saved in EEPROM                             |yes     |yes    |
|RC6, NEC, Samsung remotes support                                       |yes     |-      |
|Learning mode for remote control                                        |yes     |-      |
|Nice graphics (icons, fonts) on graphic LCDs                            |yes     |-      |
|Alarm support (per day of week)                                         |yes     |-      |
|Standby timer (adjustable from 2 minutes to 5 hours)                    |yes     |-      |
|No-signal standby timer                                                 |yes     |-      |
|Sound level meter, various modes of spectrum analyzer look'n'feel       |yes     |-      |
|10 favourite FM stations support (mapped to 0..9 buttons of remote)     |yes     |-      |
|10 favourite FM stations support (mapped to 0..9 buttons of remote)     |yes     |-      |

# Supported audio processors:

|Audioprocessor|Feature set                                                                    |ATmega32|ATmega8|
|--------------|-------------------------------------------------------------------------------|--------|-------|
|TDA7439       |4 stereo inputs, bass, middle, treble                                          |yes     |yes    |
|TDA7312       |4 stereo inputs, bass, treble                                                  |yes     |yes    |
|TDA7313/PT2313|3 stereo inputs, bass, treble, fade, loudness                                  |yes     |yes    |
|TDA7314       |Stereo input, bass, treble, fade, loudness                                     |yes     |yes    |
|TDA7315       |Stereo input, bass, treble                                                     |yes     |yes    |
|TDA7318       |4 stereo inputs, bass, treble, fade                                            |yes     |yes    |
|PT2314        |4 stereo inputs, bass, treble, loudness                                        |yes     |yes    |
|TDA7448       |6-ch input, fade, center, subwoofer                                            |yes     |yes    |
|PT2323/PT2322 |4 stereo inputs, 5.1 input, bass, treble, fade, center, subwoofer, surround, 3d|yes     |yes    |
|TEA6300       |3 stereo inputs, bass, treble, fade                                            |yes     |yes    |
|TEA6330       |Stereo input, bass, treble, fade                                               |yes     |yes    |
|PGA2310       |High-end stereo volume control                                                 |yes     |yes    |
|RDA580X       |Use built-in tuner volume control as audioprocessor                            |yes     |yes    |

# Supported displays:

|Display      |Description                                                                |ATmega32|ATmega8|
|-------------|---------------------------------------------------------------------------|--------|-------|
|KS0108 type A|Monochrome 128x64 graphic display with direct CS1/CS2 polarity             |yes     |-      |
|KS0108 type B|Monochrome 128x64 graphic display with inverted CS1/CS2 polarity           |yes     |-      |
|ST7920       |Monochrome 128x64 graphic display                                          |yes     |-      |
|SSD1306      |Monochrome 128x64 graphic OLED I²C (SCK - PA4, SDA - PA2)                  |yes     |-      |
|KS0066 16x2  |Monochrome alphanumeric display                                            |yes     |yes    |
|LS020        |Color 176x132 graphic display found in some Siemence mobile phones like S65|yes     |-      |

# Schematics

* ATmega32:
    * [KS0108 type A](https://raw.githubusercontent.com/WiseLord/ampcontrol/m32/files/sch/ks0108a.png)
    * [KS0108 type B](https://raw.githubusercontent.com/WiseLord/ampcontrol/m32/files/sch/ks0108b.png)
    * [ST7920](https://raw.githubusercontent.com/WiseLord/ampcontrol/m32/files/sch/st7920.png)
    * [KS0066 16x2](https://raw.githubusercontent.com/WiseLord/ampcontrol/m32/files/sch/ks0066.png)
    * [LS020](https://raw.githubusercontent.com/WiseLord/ampcontrol/m32/files/sch/ls020.png)
* ATmega8:
    * [KS0066 16x2](https://raw.githubusercontent.com/WiseLord/ampcontrol/m8/files/sch-m8.png)

# Supported FM tuners

|Tuner     |Description                                   |ATmega32|ATmega8|
|----------|----------------------------------------------|--------|-------|
|TEA5767   |I²C FM tuner                                  |yes     |yes    |
|RDA5807   |I²C FM tuner with RDS support                 |yes     |yes    |
|TUX032    |I²C FM tuner found in some Sony car radio     |yes     |yes    |
|LM7001    |SPI-control frequency synthesizer             |yes     |yes    |
|RDA5802   |I²C FM tuner                                  |yes     |yes    |
|RDA5807_DF|Option for RDA5807 with direct frequency input|yes     |yes    |
|LC72131   |SPI-control frequency synthesizer             |yes     |yes    |

# Ampcontrol EEPROM editor

While project uses various parameters from EEPROM memory (for example, audioprocessor and tuner selection), special desktop application to edit eeprom_xx.bin was designed. It allows to load, modify and save eeprom binary file in easy way. Currently ampcontrol editor can manage only eeprom files for main (m32) branch of code, but also can be useful in combination with hex editor in other branches, for example, for localizations.

![Ampcontrol EEPROM editor](editor.png)

Ampcontrol editor is written on Qt5 and it's sources are availiable on <a href="https://github.com/WiseLord/ampcontrol/tree/m32/editor">Github</a>. Exetuable for windows (statically compiled) can be downloaded from <a href="https://www.dropbox.com/sh/nkiajkuuobk6uvi/AABCGfvy3UZC1HBU0lJsWyqKa?dl=0">Dropbox</a>

# Other hardware options:

* [Atmega16](https://github.com/WiseLord/ampcontrol/tree/m16) branch

    This branch is based on old audio and tuner architecture (initially project was started on ATmega16 and later main MCU was changed to ATmega32), so it lacks many features of upstream previously described. Only TDA7439/TDA7313/TDA7318 audio processors are supported (because branch uses old audio architecture). Also in latest releases ST7920 support was dropped in this branch due to very slow performance and big RAM requirements.

* [Atmega8-lcd](https://github.com/WiseLord/ampcontrol/tree/m8-lcd) branch

    This branch is hardcoded to be used with 16x2 character display, TDA7313 audio processors and it doesn't support FM radio. But it's interface localization can be switched between Russian and English without EEPROM reflashing, and also it supports RC5 learning mode. Both m8 and m8-lcd branches has the same pinout.

# Useful links

* [First article about the project](http://radiokot.ru/circuit/audio/other/39) (in Russian)
* [Second article about the project](href="http://radiokot.ru/circuit/audio/other/45) (in Russian)
* [Forum thread](http://radiokot.ru/forum/viewtopic.php?t=98758) (in Russian)
