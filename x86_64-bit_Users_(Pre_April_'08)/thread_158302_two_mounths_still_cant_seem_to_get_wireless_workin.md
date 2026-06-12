---
title: "two mounths still cant seem to get wireless working"
date: 2006-04-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by cosmoshell on 2006-04-10
im trying to connect to ther internet through an BCM4318 [AirForce One 54g] 802.11g wireless lan but im not sure what to do get it set up or connect.

---

### Post by Third Thoughts on 2006-04-14
I think this will help you out. [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)
It looks like your wireless chip has a BroadCom chipset and this how-to talks about them.

---

### Post by Jefim on 2006-04-15
1. install ndiswraper.
2. install the driver you have for your wireless card (using ndiswrapper).
3. lsmod | grep bcm43xx
4. if the output indeicates that there is a module called bcm43xx loaded, then just "rmmod bcm43xx" it.
5. modprobe ndiswrapper.
6. now you should be able to see wireless networks with "iwlist [your_card] scan". (for me its "iwlist eth0 scan").

Note: if you have an Acer laptop you will need to install the acer_acpi module!

---

### Post by cosmoshell on 2006-04-19
wireless still dosent work

---

