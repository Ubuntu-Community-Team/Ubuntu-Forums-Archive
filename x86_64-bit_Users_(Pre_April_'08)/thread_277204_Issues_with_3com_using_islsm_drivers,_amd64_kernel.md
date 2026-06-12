---
title: "Issues with 3com using islsm drivers, amd64 kernel"
date: 2006-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by kiwifish on 2006-10-14
Hi all,

I've been using Ubuntu for a couple of years now, I guess you could say I'm experienced at being a newbie :rolleyes:

I have a 3Com USB wireless dongle - model 3crwe254g72 . I'm pretty sure it uses the prism chipset (it is listed in [the prism website]("http://prism54.org/newdrivers.html")). Back in Breezy, I took the easy route of using ndiswrapper and the windows drivers, which continued to work fine in dapper. Recently, a friend with an identical usb dongle installed dapper and found it worked out of the box with the islsm prism drivers. With that, I thought I would try upgrading to the amd64 kernel (there are no 64 bit windows drivers for the dongle, so ndiswrapper is useless).

Okay, so I install dapper amd64. the 3com adapter is detected, I can set SSID and Channel using iwconfig, but whenever I try to set the key, it fails with an 'unknown error 254'.

(things I typed are in blue)
```
[COLOR="Blue"]lshw[/COLOR]
(SNIP)
*-usb
     description: Generic USB device
     product: 3CRWE254G72 802.11g Adapter
     vendor: 3Com Corp.
     physical id: 4
     bus info: usb@3:4
     version: 2.03
     capabilities: usb-2.00
     configuration: driver=islusb maxpower=500mA speed=480.0MB/s
(SNIP)
[COLOR="Blue"]sudo iwconfig eth2 essid Test
sudo iwconfig eth2 channel 11
sudo iwconfig eth2[/COLOR]
eth2      IEEE 802.11b  ESSID:"Test"
          Mode:Auto  Channel=11  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[COLOR="Blue"]sudo iwconfig eth2 key open[/COLOR]
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth2 ; Unknown error 524.
[COLOR="Blue"]sudo iwlist eth2 key[/COLOR]
eth2      3 key sizes : 40, 104, 256bits
          4 keys available :
Error reading wireless keys (SIOCGIWENCODE): Unknown error 524
```

I tried various ifconfig eth2 up, ifconfig eth2 down - no difference. I tried removing WEP encryption from the router - still doesn't connect. dhclient eth2 - just tries for a while and gives up. iflist eth2 list - immediately says no networks found.

I have attached the output of lsusb and dmesg - i don't know if they help.

I'm stuck. I know it works in dapper x86. I'd be eternally grateful for any help, or ideas for what I could try...

Thank you!

---

