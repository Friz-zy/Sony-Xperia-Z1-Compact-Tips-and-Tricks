# Sony Xperia Z1 Compact Tips & Tricks

## Guides

* [Xperia™ Z1 Compact Specs](http://developer.sonymobile.com/products/phones/specification/xperiaz1compact/)
* [Xperia on Ubuntu (Udev rules, Flashtool, ADB&Fastboot)](http://forum.xda-developers.com/showthread.php?t=1612273)
* [Easy Root Tool for various Xperia devices](http://forum.xda-developers.com/showthread.php?t=2784900)
* [Making Dump Files Out of Android Device Partitions](http://forum.xda-developers.com/showthread.php?t=2450045)
* [Backup DRM partitions](http://forum.xda-developers.com/showthread.php?t=2292598)
* [Free Xperia Project](https://sites.google.com/site/projectfreexperia/)
* [Xperia Z1 Compact driver for Microsoft Windows™](http://developer.sonymobile.com/downloads/drivers/xperia-z1-compact-driver/)
* [Flashtool](http://www.flashtool.net/index.php)

## Setup environment

* Android ADB

```
$ sudo apt-get install android-tools-adb
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
