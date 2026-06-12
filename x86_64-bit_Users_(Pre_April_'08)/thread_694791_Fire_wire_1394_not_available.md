---
title: "Fire wire 1394 not available"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by rushman on 2008-02-12
Hi 
I am new to Ubuntu, I have dual booted it with Suse 10.3. The computor is an Amd 64 dual core on an Asus Pro motherboard, running in 64 bit mode.

I copy my laser disks with Kino, Suse see's the 1394 but Ubunto does not Kino say's I do not have user rights.

How and where do I change this.

Thank you

rushman (jim)

---

### Post by sepia-shots on 2008-02-12
With the device attached (and on), open a terminal window and cd to /dev. Then chmod 666 the raw1394 file (sudo chmod 666 raw1394). If you look at the preferences in Kino it says that the raw1394 device must be read and write accessible by the user.
The irritating thing for me is that 
A) The raw1394 file only exists with the device plugged in and active
B) Therefore you have to do this each time you plug-in the device to capture content. 

Cheers

Pete

---

### Post by rushman on 2008-02-12
Sepia-shots,
Thank you for your reply

I found the cure under a Dlink query, so I am up and running

Than you 

rushman (jim)

---

### Post by linuxfan3 on 2008-04-01
i had the same problem
try to install the "dvgrab" package restart your system and it should work.

---

