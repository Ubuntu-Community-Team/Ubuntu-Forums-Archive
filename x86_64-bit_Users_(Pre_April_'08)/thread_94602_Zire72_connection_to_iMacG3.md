---
title: "Zire72 connection to iMacG3"
date: 2005-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by xerman on 2005-11-24
Hi there folks,

I've tried to connect my Palm Zire72 to the iBuntu (iMac+Ubuntu) through the usb cable provided with the device and following the on screen guidelines (Gnome-Pilot) until I get the "press the sync button on your palm device" pop up. Once I press the sync button on the Zire I can be waiting for several minutes until Zire says "there's no way to connect to your PC".
  I tried with "/dev/pilot" and "/dev/usb"

After taking a look at Ubuntu 5.10 starter guide provided in the Ubuntu's help menu I added what stated there:

> How do I configure PalmOS devices?
       1. ```
sudo gedit /etc/udev/rules.d/10-custom.rules
```
       2. Insert the following line into the new file
```
BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
```
       3. Save the edited file (```
sample/10-custom.rules_configurepalmosdevices
```)
       4. System &#8594; Preferences &#8594; PalmOS Devices
       5. Follow the instructions on screen

and tried again with "/dev/pilot" and "/dev/usb" and have the same problem, Zire will keep waiting until it gets tired and says again the "cannot connect to PC".

Thanks a lot in advance
best regards
xermán

---

### Post by Rxke on 2005-11-25
Maybe this helps: [http://ubuntuforums.org/archive/index.php/t-78918.html](http://ubuntuforums.org/archive/index.php/t-78918.html)

It's pretty convoluted, though, just read it through carefully to get an idea and/or whether you're up to this kind of stuff....

---

### Post by teripittman on 2005-11-26
Mine has to be set to ttyUSB1 to work. I used the instructions on the pilot-link page. I can't remember exactly which command I used to find out which port I connected with. Will take a look at my notes this weekend and post it then.

---

