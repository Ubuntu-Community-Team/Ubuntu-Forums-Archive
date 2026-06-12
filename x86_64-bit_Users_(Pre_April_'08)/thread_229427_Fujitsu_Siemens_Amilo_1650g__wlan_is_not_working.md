---
title: "Fujitsu Siemens Amilo 1650g  wlan is not working"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by jkrbv on 2006-08-04
I've installed on my laptop (Fujitsu Siemens Amilo 1650g) the new 6.06 Ubuntu x64(cause it’s a AMD64), my damn wlan is not working!!! I tried to find something in the forum, but all the solutions were wired and couldn’t find something that would help me. I’m a new Ubuntu user but, an old friend of RedHat and SuSe. Could anyone tell me how to solve the problem?
Btw. I followed this thread [http://www.ubuntuforums.org/showthread.php?t=207428](http://www.ubuntuforums.org/showthread.php?t=207428)
and the solution was interesting, the only thing that, for a mysterious reason:confused: , didn’t work was the “make” command. It sad “Bad command name” or something like that.
Help!
Thanx!

---

### Post by The Keeper on 2006-08-06
Most Fujitsu Siemens entry-level Amilo notebooks have a software-based switch to enable/disabled WLAN. Even Windows users needs to use a program supplied by FSC to make WLAN work. Since FSC does not support linux on consumer computers, projects like fsaa1655g are linux users only hope. May not work with A1650G though.

Anyway, to fix the "make" problem, you need to install a package called build-essential. Use synaptic or apt-get install for that.

---

### Post by belekas on 2007-04-25
can anyone advise me how to setup broadcom wifi driver on ubuntu 7.04 amd64 edition. my wifi chipset is broadcom 4318 airforce one 54g. i tried all the tutorials with ndiswrapper and still nothing, i think my card gets detected after long long trail and error but the light on amilo 1650g still doesnt come up that means wifi is not working. can anyone advise me pls

thank you in advance

peace

---

### Post by freak101 on 2007-05-02
I had the same problem, now solved. Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=247108](http://ubuntuforums.org/showthread.php?t=247108)

---

### Post by Clarkx on 2007-08-08
Hello, have a AMD 64 with Ubuntu 7.04 64bit Version. My WLAN Light is on, have the latest Version of Ndiswrapper, but the driver will not load. Can anyone help me to resolve this?

Here my recorded steps:
--------------------------------------------------------------------------------
root@edubuntu:/home/clarkx# lsusb
Bus 002 Device 002: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 1509:9242  
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000  

root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# ndiswrapper -i sis163u.inf
installing sis163u ...
root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# ndiswrapper -l
sis163u : driver installed
        device (0BF8:100F) present
root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 
root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# depmod -a
root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# modprobe ndiswrapper

root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# tail /var/log/messages
Aug  8 22:00:16 edubuntu gconfd (root-6253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  8 22:00:16 edubuntu gconfd (root-6253): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  8 22:00:16 edubuntu gconfd (root-6253): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  8 22:00:16 edubuntu gconfd (root-6253): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  8 22:00:16 edubuntu gconfd (root-6253): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  8 22:15:37 edubuntu -- MARK --
Aug  8 22:20:48 edubuntu kernel: [ 1548.211266] ndiswrapper version 1.47 loaded (smp=yes)
Aug  8 22:20:48 edubuntu kernel: [ 1548.472299] usb 2-3: reset high speed USB device using ehci_hcd and address 2
Aug  8 22:20:49 edubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver sis163u 
Aug  8 22:20:49 edubuntu kernel: [ 1548.688857] usbcore: registered new interface driver ndiswrapper

root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:0B:0B:5B:27  
          inet addr:192.168.178.32  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bff:fe0b:5b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2624 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2835134 (2.7 MiB)  TX bytes:476121 (464.9 KiB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5304 (5.1 KiB)  TX bytes:5304 (5.1 KiB)

root@edubuntu:/home/clarkx/wlan/R111_USB_Vista/Vista64/USB# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

____________________________________________________________________________________________________________________________________________
Would appreciate any help! Thanx Mark

---

