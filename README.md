===
adb is a useful tool for debugging android devices, you can download the
binary from google/android.com(mostly), but it only supports small amount
devices. To support some specific android device, you need to add the VID,
add udev rule, etc.
If you want to support your devices natively of adb, you should change the
usb_vendors.c code, then build the whole android source to get the adb tool.
It cause too much to gain the benity.

This project is to build the adb source standalone out of the Android build
script system. I merged the main adb source with some essential libraries
(libcutils and libzipfile), and add Makefile for it.

* This project has supported fastboot (from 0.1.0).

===
INSTRUCTIONS:

Build for FreeBSD 9.x

1. After get the source, you can change the usb_vendor_ids.c to add your VID.
    use debian/gen_udev_rules.sh to generate udev rule for those VID.

3. ./configure

2. gmake
    build the adb binary

At the moment I have no install process done but you can run adb manually

1. ./adb fork-server server & 
	Launch the adb server. Check if you have the sufficient permission to read/write to the usb port
2. ./adb shell [<command>]
	Open a shell to the connected android device and alternativelly run the <command>


Enjoy it!
