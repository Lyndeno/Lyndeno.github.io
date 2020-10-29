---
title: Setting up External Monitor Brightness Controls on Arch Linux
date: 2020-XX-XX 13:25:00 -0600
categories: [Announcements]
tags: [announcement]     # TAG names should always be lowercase
pin: no
---

This will be the first technical post on my website. I will use this post to describe the process in setting up external brightness control in Sway on Arch Linux.

## Background

Kernel 5.9 added improved I2C support to Navi 10 cards, which include the Radeon RX 5600XT. Using I2C in combination with [ddcutil](https://www.archlinux.org/packages/community/x86_64/ddcutil/) can allow us to control an external monitors brightness using commands.

## Using ddcutil

### Detecting Monitors

First we need to make sure that the ```i2c-dev``` module is loaded into the system; In my case, it was loaded automatically. We now want to identify the monitors:

``` console
# ddcutil detect
Display 1
   I2C bus:             /dev/i2c-5
   EDID synopsis:
      Mfg id:           GSM
      Model:            LG QHD
      Serial number:
      Manufacture year: 2020
      EDID version:     1.4
   VCP version:         2.1

Display 2
   I2C bus:             /dev/i2c-6
   EDID synopsis:
      Mfg id:           DEL
      Model:            DELL P2014H
      Serial number:    J6HFT3B9AK7L
      Manufacture year: 2013
      EDID version:     1.4
   VCP version:         2.1
```

The monitor I am interested in is the LG QHD, with a bus number of 5. ```ddcutil``` can change various properties of connected monitors, we are only interested i brightness right now.

### Adjusting Brightness

We can change the 
