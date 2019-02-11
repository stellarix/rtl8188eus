## rtl8188eus v5.3.9

# Realtek rtl8188eus &amp; rtl8188eu &amp; rtl8188etv WiFi driver

[![Monitor mode](https://img.shields.io/badge/monitor%20mode-working-brightgreen.svg)](#)
[![Frame Injection](https://img.shields.io/badge/frame%20injection-working-brightgreen.svg)](#)
[![GitHub issues](https://img.shields.io/github/issues/aircrack-ng/rtl8812au.svg)](https://github.com/kimocoder/rtl8188eus/issues)
[![GitHub forks](https://img.shields.io/github/forks/aircrack-ng/rtl8812au.svg)](https://github.com/kimocoder/rtl8188eus/network)
[![GitHub stars](https://img.shields.io/github/stars/aircrack-ng/rtl8812au.svg)](https://github.com/kimocoder/rtl8188eus/stargazers)
[![GitHub license](https://img.shields.io/github/license/aircrack-ng/rtl8812au.svg)](https://github.com/kimocoder/rtl8188eus/blob/master/LICENSE)

<b>This driver supports:</b>
* Android 8
* MESH Mode Operation
* .. and kernels up to v5.0+ (rc3 tested)

This is a pure Realtek release, not from vendor but from all the Realtek multichip "bases"
we've seen, this must be the newest, most stable and effective one.
The performance and code quality has been improved and thats about time.

# HowTo build/install
1. You will need to blacklist another driver in order to use this one instead of the kernel provided.
Create a file named "rtl8188eus.conf", add a 1 liner to it: "blacklist r8188eu"
<br>
2. Then move the file to "/etc/modprobe.d/"
<br>
3. "make && make install"<br>
4. "rmmod r8188eu && insmod rtl8188eus"

# MONITOR MODE ATTENTION

There is a bug or interferrence with the driver and/or Network-Manager,
so if you wan't to use the monitor mode, DON'T kill the network-manager or use airmon-ng (infact)

<b>FIX:</b>
Add these lines below to "NetworkManager.conf" and ADD YOUR ADAPTER MAC below [keyfile]
This will make the Network-Manager ignore the device, and therefor don't cause problems.
```
[device]
wifi.scan-rand-mac-address=no

[ifupdown]
managed=false

[connection]
wifi.powersave=0

[main]
plugins=keyfile

[keyfile]
unmanaged-devices=mac:c4:e9:84:dc:99:e9
```

# TODO
* Finish the walkthrough of the base for understanding.
* There is a bug in monitor mode related to Network-Manager.
  This needs priority because it causes interferrence.
* Add HT (RX) Greenfield capabilities
* pcap_activate error on "reaver" - investigate
* Go through the VHT.
* Add more VID/PIDS for all 3 chipsets supported.
<br>
more tba..
