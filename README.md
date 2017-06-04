Orange Pi A64 Ubuntu Xenial Xerus 16.04 LXDE OS Image (firmware)
================================================================

LXDE (Lightweight X11 Desktop Environment) is a desktop environment which is lightweight 
and fast and uses less RAM and less CPU while being a feature rich desktop environment.

** THIS IS a WiP **

Disclaimer: Use at own risk

## OPi Win A64 Booting linux

[![OPI A64 Booting linux](https://github.com/avafinger/opi-win-a64-firmware/raw/master/img/opi-a64.jpg)](https://youtu.be/kH-1PC7chIU)


This is a LXDE OS image for the Orange Pi Win A64
-------------------------------------------------

## Tested on OPi Win A64 board

- Camera (GC2035) - status: working
- Wifi (ap6212 A) - status: working
- HDMI 1080P - status: working (a64-2GB.dtb)
- GbE (Gigabit Ethernet) - status: working
- Kernel 3.10.105 - status: working
- Leds (Green) - status: working - "heartbeat"
- Firefox 64bit - stable
- HW decoding H264 (1080P)  - https://github.com/avafinger/cedrusH264_vdpau_A64

Improved GC2035
---------------
Improved gc2035 driver is included in the OS Image

* hres=0 => 640x480|1280x720|1600x1200 and 15 fps (good light condition), 640x480 good quality
* hres=1 => 800x600|1600x1200 and 10 fps (good light condition), 800x600 good quality
* hres=2 => 320x240|640x480|800x600 and 20 fps (good light condition), 640x480 medium quality
* hres=3 => 320x240|352x288|640x480 and 15 fps (good light condition), low quality, cropped to this window sizes

Issues:
- None at the moment

History Log:
------------
- initial commit
- added video
- image built with gcc 6.3
- ssh 
- initial work on GC2035 driver
- Improved GC2035 support
