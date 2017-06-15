Orange Pi A64 Ubuntu Xenial Xerus 16.04 LXDE OS Image (firmware)
================================================================

LXDE (Lightweight X11 Desktop Environment) is a desktop environment which is lightweight 
and fast and uses less RAM and less CPU while being a feature rich desktop environment.
This is a bare minimum Desktop OS Image where you can learn and build/install new features. 

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
Improved gc2035 driver is included in the OS Image, for more infor read: https://github.com/avafinger/gc2035

* hres=0 => 640x480|1280x720|1600x1200 and 15 fps (good light condition), 640x480 good quality
* hres=1 => 800x600|1600x1200 and 10 fps (good light condition), 800x600 good quality
* hres=2 => 320x240|640x480|800x600 and 20 fps (good light condition), 640x480 medium quality
* hres=3 => 320x240|352x288|640x480 and 15 fps (good light condition), low quality, cropped to this window sizes

Instructions to Install
-----------------------
You will need a linux box to create the OS Image.

- Get a good (brand new and trusted SD CARD) 8GB SD card or any other size >= 4 GB,
  failing to get a good SD card you get a lot of troubles booting the board
- Get a good PSU to power the board with the barrel conector, ensure your 
  PSU is rated 2.5A and 5v
- Get a good USB card reader/writer, this is really important!
- Don't use HDMI to DVI converter if you can

Requirements
------------
- Install md5sum and git on your host PC
- Your HOST PC must be running linux
- check-list the items above about SD CARD, PSU and USB card reader/writer
- Image is default to 1080P, HDMI so you need a 1080P monitor

### Manual installation

1.  Download the files entirely with git 

    a.  **In shell type (host PC):**


            git clone https://github.com/avafinger/opi-win-a64-firmware
            cd opi-win-a64-firmware



    or


            Click on the green button [Clone or download] and choose *Download Zip*
            Unzip it with your preferred tool
            cd opi-win-a64-firmware-master




    b. Rebuild boot and rootfs and check MD5 for integrity (must match)

             cat rootfs_opi-a64_rc1.tar.gz.* > rootfs_opi-a64_rc1.tar.gz
             md5sum rootfs_opi-a64_rc1.tar.gz 
             ded1dc1f262923e41140002a6ae618d9  rootfs_opi-a64_rc1.tar.gz

             md5sum boot_opi-a64_rc1.tar.gz 
             3a67fd14cbd1943868d2fd222fd02495  boot_opi-a64_rc1.tar.gz


    c.  **Insert a new SD card (get a good one, 8 GB or > )**


    d.  **Find your SD card**


            dmesg|tail
            [33082.449482]  sdc: sdc1
            [33084.897979] EXT4-fs (sdc1): mounted filesystem with writeback data mode. Opts: (null)



        in this example our sd card is /dev/sdc if we use an SD CARD reader (USB), it could be /dev/sdb if you have only one HDD on your host PC
        so the format is something like /dev/sdX where X is [b,c,d..,g]


    e.  **Start flashing... (Warning, make sure you get the correct device or you may WIPE your HDD)**


            sudo chmod +x *.sh
            sudo ./format_sd.sh /dev/sdc
            sudo ./flash_sd.sh /dev/sdc


    f.  Now you have SD card with OS Image in it, you can now boot up your OPi Win A64 with this SD card

  
            user: ubuntu
            pass: ubuntu


2.  On the first boot type in the command line:

    a. For update

           sudo apt-get update
           sudo apt-get dist-upgrade
           sync

    b. Shutdown and do a cold boot.

           sudo shutdwon -h now (wait....)
           unplug the power cord from the board


    c. Boot again
    
           Enjoy!



Issues:
- None at the moment


Credits:
--------
@lex, longsleep, Armbian, BananaPi, FriendlyArm and all those nice people who really cares to answer questions. :)


If you want to play with mailine kernel, go to Armbian and check the work of @martinayotte.

**Enjoy it!**

History Log:
------------
- initial commit
- added video
- image built with gcc 6.3
- ssh 
- initial work on GC2035 driver
- Improved GC2035 support
- OS Image released and built with gcc 7.1
