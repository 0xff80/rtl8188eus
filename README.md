## rtl8188eus v5.7.6.1

# Realtek rtl8188eus &amp; rtl8188eu &amp; rtl8188etv WiFi driver

[![Monitor mode](https://img.shields.io/badge/monitor%20mode-supported-brightgreen.svg)](#)
[![Frame Injection](https://img.shields.io/badge/frame%20injection-supported-brightgreen.svg)](#)
[![MESH Mode](https://img.shields.io/badge/mesh%20mode-supported-brightgreen.svg)](#)
[![GitHub issues](https://img.shields.io/github/issues/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/issues)
[![GitHub forks](https://img.shields.io/github/forks/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/network)
[![GitHub stars](https://img.shields.io/github/stars/aircrack-ng/rtl8188eus.svg)](https://github.com/aircrack-ng/rtl8188eus/stargazers)
[![GitHub license](https://img.shields.io/github/license/aircrack-ng/rtl8812au.svg)](https://github.com/aircrack-ng/rtl8188eus/blob/master/LICENSE)<br>
[![Android](https://img.shields.io/badge/android%20(8)-supported-brightgreen.svg)](#)
[![aircrack-ng](https://img.shields.io/badge/aircrack--ng-supported-blue.svg)](#)


# Supports
* Android 9
* WPA3-SAE
* P2P Mode
* WiFi Direct
* MESH Support
* Monitor mode
* Frame injection
* Supported up to kernel v5.4+
... And a bunch of various wifi chipsets

# Howto build/install
1. You will need to blacklist another driver in order to use this one instead of the one provided with kernel.
   Simply follow instructions below:<br>
2. "echo "blacklist r8188eu" > /etc/modprobe.d/realtek-wifi.conf"<br>
3. Then run "make && make install"<br>
4. And reboot in order to blacklist the module and load this module instead.

# MONITOR MODE howto
Use these steps to enter monitor mode.
```
$ sudo airmon-ng check-kill
$ sudo ip link set <interface> down
$ sudo iw dev <interface> set type monitor
```
Frame injection test may be performed with
```
$ aireplay -9 <interface>
```

# NetworkManager configuration
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
unmanaged-devices=mac:A7:A7:A7:A7:A7
```

# TODO
* Turn down log level / DEBUG
  (we want it now for some months just to see)

* Implement txpower control

* Remove Windows (NDIS) code
