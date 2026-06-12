---
title: "Netgear WLAN 111 under 64 bit"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Uriel2006 on 2007-06-15
Hello All, 

i have one netgear wlan 111 usb card as wifi card.

Other forums says it works with ndiswrapper, but the problem is they miss it works on 
ndiswrapper ***on 32 bit systems only***, due netgear releases just the windows32 driver.

Someone has a workaround/trick to make this hardware to work on 64 bit ubuntu systems?

thanks in advance,

Uriel

---

### Post by jharrop on 2007-06-16
I'm using the default rtl8187 driver with Feisty x64 and wpa_supplicant.  No need for the wrapper.  Its not bad, but does die sometimes (last time was about a week ago).    I do run a VNC session over it, which receives about 50KB/s, for a total of 80GB since the connection last died.  I suspect it may die under high load - obviously higher than that!

 lshw 

              *-usb
                   description: Generic USB device
                   product: NETGEAR WG111v2
                   vendor: NETGEAR WG111v2
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.00
                   serial: 00146CAF59D4
                   capabilities: usb-2.00
                   configuration: driver=rtl8187 maxpower=500mA speed=480.0MB/s

  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:af:59:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.5 multicast=yes wireless=IEEE 8
02.11g

---

### Post by Uriel2006 on 2007-06-18
> **jharrop said:**
> I'm using the default rtl8187 driver with Feisty x64 and wpa_supplicant.  No need for the wrapper.  Its not bad, but does die sometimes (last time was about a week ago).    I do run a VNC session over it, which receives about 50KB/s, for a total of 80GB since the connection last died.  I suspect it may die under high load - obviously higher than that!


02.11g

Hello Jharrop,

i guess there are differences between different hardwares: lshw on my machine describes the USB device such way:

 *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: WPN111
                   vendor: Atheros Communications Inc
                   physical id: 5
                   bus info: usb@3:5
                   version: 0.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s


So the real problem is the Atheros chip, i guess. This may explain why my colleagues were able to use the board in a breeze, and i am getting crazy... maybe they have a different chip on board...

Uriel

---

### Post by jharrop on 2007-06-18
Not wanting to hijack your thread, but in case you do decide to go the rtl8187 route...

When my connection dies (as it just did after a week or so):

jharrop@jharrop-490:~$ iwconfig
         
wlan0     IEEE 802.11g  ESSID:"XYZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:DA:81:96   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality=43/64  Signal level=18/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ie Encryption key is gone ...

jharrop@jharrop-490:~$ iwlist wlan0 scanning
wlan0     No scan results

jharrop@jharrop-490:~$ ifconfig
 [looks normal]

To get it going again:

root@jharrop-490:/home/jharrop# ifdown wlan0
root@jharrop-490:/home/jharrop# wpa_supplicant -dd -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

root@jharrop-490:/home/jharrop# iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:DA:81:96
                    ESSID:"XYZ"
                    Mode:Master
                    Frequency:2.462 GHz
                    Quality=54/64  Signal level=33/65  
                    Encryption key:on

root@jharrop-490:/home/jharrop# ifup wlan0

.. and life is good!

---

### Post by Uriel2006 on 2007-06-18
> **jharrop said:**
> Not wanting to hijack your thread, but in case you do decide to go the rtl8187 route...

When my connection dies (as it just did after a week or so):

jharrop@jharrop-490:~$ iwconfig
         
wlan0     IEEE 802.11g  ESSID:"XYZ"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:DA:81:96   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality=43/64  Signal level=18/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ie Encryption key is gone ...

jharrop@jharrop-490:~$ iwlist wlan0 scanning
wlan0     No scan results

jharrop@jharrop-490:~$ ifconfig
 [looks normal]



.. and life is good!


Hello, my problem now is getting the hardware running, and the native driver you mentioned is for a different chipset...

Uriel

---

