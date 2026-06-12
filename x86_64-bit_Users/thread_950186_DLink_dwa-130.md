---
title: "DLink dwa-130"
date: 2008-10-16
forum: x86 64-bit Users
---

### Post by TPrime on 2008-10-16
I can't get my usb wireless adapter to work. I have the latest driver installed with ndiswrapper. lshw -C network displays nothing. lsusb says bus 001 device 004: ID 07d1:3b11 D-Link System. Ndiswrapper -l lists the driver as installed and device present, but I still have nothing in iwconfig. Any suggestions?

---

### Post by Yellow Pasque on 2008-10-16
- Did you use a 64-bit driver (you probably did; I don't think ndiswrapper will install a 32-bit driver for you on a 64-bit system)
- Is the ndiswrapper kernel module loaded at boot (i.e. ndiswrapper should be listed in /etc/modules )
- Do you have a wireless interface declared in /etc/network/interfaces (i.e. did you run sudo ndiswrapper -m )?

---

### Post by TPrime on 2008-10-18
Affirmative on all of those, except the 64 bit driver. I don't know if there is one. There's no 64 bit drivers listed on their website. Any ideas?

---

### Post by pistlpete on 2008-10-25
I have the same problem.  The driver is installed and the hardware is listed as present.  But I don't see wlan0 on the network settings. 

Does anybody know if there are AMD64 drivers for the dwa-130 available?

---

### Post by robo100 on 2008-11-07
Yes, Same problem here. I ended up using a Linksys wireless G adapter and ubuntu works great, however I would really like to use the dwg-130 but just have not found a way to make it work. I am trying to use the ndiswrapper and the driver is loaded and the dwa-130 is seen but it just doesnt show up in the network configuration. My guess is that it just doesnt work in the 64 bit version of ubuntu without a 64 bit driver. It seems that everybody I have talked to has gotten it to work in the 32 bit version but not in the 64 bit version.

---

### Post by cariboo on 2008-11-07
There are 64bit Vista drivers if you have the right version of adapter. Have a look here:

[http://www.dlink.com/products/support.asp?pid=566](http://www.dlink.com/products/support.asp?pid=566)

Revisions B and C have Vista 64bit drivers available.

Jim

---

### Post by Yellow Pasque on 2008-11-07
Does ndiswrapper support Vista drivers now? The last time I checked, it didn't. Vista has a completely different driver interface than XP (hence the poor hardware support when it first came out).

---

### Post by tanha on 2009-04-28
Are you using it in 802.11g or 802.11n mode?

---

