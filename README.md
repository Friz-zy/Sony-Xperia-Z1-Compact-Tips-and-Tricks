# Sony Xperia Z1 Compact Tips & Tricks

## Guides

* [Xperia™ Z1 Compact Specs](http://developer.sonymobile.com/products/phones/specification/xperiaz1compact/)
* [Xperia on Ubuntu (Udev rules, Flashtool, ADB&Fastboot)](http://forum.xda-developers.com/showthread.php?t=1612273)
* [Easy Root Tool for various Xperia devices](http://forum.xda-developers.com/showthread.php?t=2784900)
* [Making Dump Files Out of Android Device Partitions](http://forum.xda-developers.com/showthread.php?t=2450045)
* [Backup DRM partitions](http://forum.xda-developers.com/showthread.php?t=2292598)
* [Official Sony Downloads](http://developer.sonymobile.com/downloads/)
* [Free Xperia Project](https://sites.google.com/site/projectfreexperia/)
* [Xperia Z1 Compact driver for Microsoft Windows™](http://developer.sonymobile.com/downloads/drivers/xperia-z1-compact-driver/)
* [Flashtool](http://www.flashtool.net/index.php)

## Setup environment

* Android ADB

```
$ sudo apt-get install android-tools-adb gcc-arm-linux-androideabi
```

* Udev rules

```
## connect the phone via usb and turn it on
$ lsusb
Bus 001 Device 004: ID 0fce:1111 Sony Ericsson Mobile Communications AB
## connect the phone via usb and turn it in "Flash" mode (hold the Volume Down button and press Power On)
$ lsusb
Bus 001 Device 014: ID 0fce:2222 Sony Ericsson Mobile Communications AB Boot loader
## connect the phone via usb and turn it in "Fastboot" mode (hold the Volume Up button and press Power On)
$ lsusb
Bus 001 Device 023: ID 0fce:3333 Sony Ericsson Mobile Communications AB
## add rules into /etc/udev/rules.d/52-sony-xperia-z1c.rules
SUBSYSTEMS==”usb”, ATTRS{idVendor}==”0fce″, ATTRS{idProduct}==”1111″, MODE=”0660″, OWNER="{{ your user }}", GROUP="root"
SUBSYSTEMS==”usb”, ATTRS{idVendor}==”0fce″, ATTRS{idProduct}==”2222″, MODE=”0660″, OWNER="{{ your user }}", GROUP="root"
SUBSYSTEMS==”usb”, ATTRS{idVendor}==”0fce″, ATTRS{idProduct}==”3333″, MODE=”0660″, OWNER="{{ your user }}", GROUP="root"
## restart udev
$ sudo restart udev
```

## Info

- Default Build Version for D5503
  * Kernel 3.4.0-perf-gaee6e5a
  * Build 14.4.A.0.157

- Partitions
```
shell@D5503:/ $ ll /dev/block/platform/msm_sdcc.1/by-name/                     
lrwxrwxrwx root     root              1970-08-10 22:37 DDR -> /dev/block/mmcblk0p17
lrwxrwxrwx root     root              1970-08-10 22:37 FOTAKernel -> /dev/block/mmcblk0p16
lrwxrwxrwx root     root              1970-08-10 22:37 LTALabel -> /dev/block/mmcblk0p18
lrwxrwxrwx root     root              1970-08-10 22:37 TA -> /dev/block/mmcblk0p1
lrwxrwxrwx root     root              1970-08-10 22:37 aboot -> /dev/block/mmcblk0p5
lrwxrwxrwx root     root              1970-08-10 22:37 alt_aboot -> /dev/block/mmcblk0p11
lrwxrwxrwx root     root              1970-08-10 22:37 alt_dbi -> /dev/block/mmcblk0p10
lrwxrwxrwx root     root              1970-08-10 22:37 alt_rpm -> /dev/block/mmcblk0p12
lrwxrwxrwx root     root              1970-08-10 22:37 alt_s1sbl -> /dev/block/mmcblk0p9
lrwxrwxrwx root     root              1970-08-10 22:37 alt_sbl1 -> /dev/block/mmcblk0p8
lrwxrwxrwx root     root              1970-08-10 22:37 alt_tz -> /dev/block/mmcblk0p13
lrwxrwxrwx root     root              1970-08-10 22:37 apps_log -> /dev/block/mmcblk0p22
lrwxrwxrwx root     root              1970-08-10 22:37 boot -> /dev/block/mmcblk0p14
lrwxrwxrwx root     root              1970-08-10 22:37 cache -> /dev/block/mmcblk0p24
lrwxrwxrwx root     root              1970-08-10 22:37 dbi -> /dev/block/mmcblk0p4
lrwxrwxrwx root     root              1970-08-10 22:37 fsg -> /dev/block/mmcblk0p21
lrwxrwxrwx root     root              1970-08-10 22:37 modemst1 -> /dev/block/mmcblk0p19
lrwxrwxrwx root     root              1970-08-10 22:37 modemst2 -> /dev/block/mmcblk0p20
lrwxrwxrwx root     root              1970-08-10 22:37 ramdump -> /dev/block/mmcblk0p15
lrwxrwxrwx root     root              1970-08-10 22:37 rpm -> /dev/block/mmcblk0p6
lrwxrwxrwx root     root              1970-08-10 22:37 s1sbl -> /dev/block/mmcblk0p3
lrwxrwxrwx root     root              1970-08-10 22:37 sbl1 -> /dev/block/mmcblk0p2
lrwxrwxrwx root     root              1970-08-10 22:37 system -> /dev/block/mmcblk0p23
lrwxrwxrwx root     root              1970-08-10 22:37 tz -> /dev/block/mmcblk0p7
lrwxrwxrwx root     root              1970-08-10 22:37 userdata -> /dev/block/mmcblk0p25
```

## Root

Can not find work opensource exploit =`(
