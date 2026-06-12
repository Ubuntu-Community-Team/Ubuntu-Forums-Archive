---
title: "Airport Extreme Detected; Can't Get Onto Network."
date: 2006-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-03-21
I have a 15" Al PowerBook G4 with the Airport Extreme card.  I followed the instructions in [this thread](http://www.ubuntuforums.org/showthread.php?t=142727), except in the myscript I set my interface to eth1.  I get this feedback in the Terminal after executing sudo ~/fwcutter/.myscript:

> ./myscript: line 11: Setting up dhcp: command not found
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:0d:93:7f:32:82
Sending on   LPF/eth1/00:0d:93:7f:32:82
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Typing iwconfig returns this:

> lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Bio-SLC104"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:30:65:06:0E:96
          Bit Rate:54 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off

eth0      no wireless extensions.

sit0      no wireless extensions.


What am I doing wrong?  :???:

---

### Post by cherrysmooth on 2006-08-02
Did you resolve this issue?  I am having the same exact problem.

---

### Post by AlphaMack on 2006-08-04
This is an old thread when I was still struggling to get the AE card working with my PowerBook.

Before getting NetworkManager to work, my solution for WEP encrypted networks was to prefix the key with "s:" (e.g. if the key was "mypassword123" then one would enter "s:mypassword123").  Once I tinkered around enough and discovered (forgot the thread) that wifi-radar and bcm43xx conflicted with each other, I had success in connecting to WEP networks via NetworkManager.

[http://www.ubuntuforums.org/showthread.php?t=211315](http://www.ubuntuforums.org/showthread.php?t=211315)

---

