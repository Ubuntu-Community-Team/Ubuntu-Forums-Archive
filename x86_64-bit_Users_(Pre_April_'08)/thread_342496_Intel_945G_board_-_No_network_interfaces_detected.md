---
title: "Intel 945G board - No network interfaces detected"
date: 2007-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by gkovacs on 2007-01-20
I have installed Ubuntu 6.10 Server amd64 edition on a computer with Intel 945G chipset, which sports a built-in gigabit ethernet connection.

The installer says: "No network interfaces were found. The installation system was unable to find a network device."

What to do now? Is there a similar deficit of 64-bit hardware drivers on Linux as on Windows?

Where and HOW can I download and install a driver for the most common network card in the world?

---

### Post by btdown on 2007-01-20
I have an Asus P5LD2-VM motherboard which I believe has the same chipset. 
I installed Ubuntu 32 and 64 bit on this new machine like 3 times each and sometimes it detected it, and sometimes it didnt. However, when it did not detect, I was able to go into the System -> Administration -> Networking tab and configure it manually. (Im typing on it now)

Another option is to check your dmesg output to see if it's being recognized.

Good luck!
BT

---

### Post by gkovacs on 2007-01-20
Unfortunately, I can't go to the Networking tab you suggested, as this is a console only server installation of Ubuntu, and I have no idea how to start the GUI.

OTOH the **dmesg** command shows it as a Realtek Ethernet controller, but the installer does not find it, even if tried several times.

Is there a way to install the driver that comes on the Ubuntu CD?

I even found a driver for it at the Realtek site at:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
Can you have a look at it, how can it be installed?

---

