---
title: "help! why wont ndis wrapper work?"
date: 2008-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by davedom on 2008-04-02
have installed rt2500usb.inf for a linksys wusb54g v4! Already had Ndis wrapper 1.9 installed.

Then tried to configure via:


davedom@Ubuntu-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:12:17:80:fa:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
davedom@Ubuntu-desktop:~$ sudo lshw -C network
[sudo] password for davedom:
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:17:80:fa:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
davedom@Ubuntu-desktop:~$ sudo ifconfig wlan0 down
davedom@Ubuntu-desktop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:80:fa:1c
Sending on   LPF/wlan0/00:12:17:80:fa:1c
Sending on   Socket/fallback
davedom@Ubuntu-desktop:~$ sudo ifconfig wlan0 up
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 essid 
Error for wireless request "Set ESSID" (8B1A) :
    too few arguments.
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan essid "domobilemjcd-1"
[sudo] password for davedom:
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan ; No such device.
davedom@Ubuntu-desktop:~$ wlan essid "linksys"
bash: wlan: command not found
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 essid "domobilemjcd-1"
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 key HEX_KEY
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "HEX_KEY".
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 key Hex_Key
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "Hex_Key".
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 key DOMONEY
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "DOMONEY".
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 DOMONEY HEX_KEY
iwconfig: unknown command "DOMONEY"
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 key HEX_KEY
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "HEX_KEY".
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 key open
davedom@Ubuntu-desktop:~$ sudo iwconfig wlan0 mode Managed
davedom@Ubuntu-desktop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:12:17:80:fa:1c
Sending on   LPF/wlan0/00:12:17:80:fa:1c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
davedom@Ubuntu-desktop:~$ 

and got the folloing

No working leases in persistent database - sleeping.
davedom@Ubuntu-desktop:~$ 

am running ubuntu 64 bit  7.10 gutsy gibbon! Can anyone help me?

---

### Post by firecat53 on 2008-04-02
Did you blacklist the open source drivers? I can't remember the names, but if you search around a bit, you'll find the names of the modules to remove and blacklist.

Good luck!
Scott

---

