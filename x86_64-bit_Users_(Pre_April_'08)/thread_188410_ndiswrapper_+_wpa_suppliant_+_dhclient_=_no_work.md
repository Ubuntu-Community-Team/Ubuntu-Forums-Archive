---
title: "ndiswrapper + wpa_suppliant + dhclient = no work"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by slamdunk on 2006-06-04
Hi,

I've installed KUbuntu 6.06 and I have configured wireless like this (INPROCOMM 2220 card):

# ndiswrapper -i neti2220.inf
# ndiswrapper -m

with "modprobe ndiswrapper" and "iwconfig" I can see iwlan0 device correctly.

In /etc/modules -> "ndiswrapper" (or "ndiswrapper hangcheck_interval=-1") without quotes.

In /etc/wpa_suppliant.conf:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="myessid"
        psk=<mykey>
        key_mgmt=WPA-PSK
        proto=WPA
}

in /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
wireless_essid myessid
pre-up /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

but after reboot my iwlan0 is disappared. Manually, after "modprobe ndiswrapper", if I launch "wpa_suppliant" and "dhclient" it disappares too.

Have you any idea?

Thanks,
Giulio

---

