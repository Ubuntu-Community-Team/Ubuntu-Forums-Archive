---
title: "Problem with open gl."
date: 2008-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by tobak30 on 2008-02-03
After following these steps provided in this thread. [http://ubuntuforums.org/showthread.php?t=677748](http://ubuntuforums.org/showthread.php?t=677748) I cant seem to get the open gl things running. And I need that for my blender work.

---

### Post by Kilz on 2008-02-03
I believe you need the accelerated driver from the maker of your video card. What video card do you have?

---

### Post by tobak30 on 2008-02-03
I got a Nvidia gforce 7200 gs. trying to install the closed drivers now.

---

### Post by tobak30 on 2008-02-04
I tried the propriatery driver again. but it seems like the driver is the culprit in my system locking up. So I tried the x.org drivers.

But what is this meaning. Especially the Fatal error thingy. Battery I don't have any battery except the  clocl battery on my motherboard:

A backup of xorg.conf has been stored as:
/var/backups/xorg.conf.2008-02-04-07:30:54.
If the new configuration will not work you will be able to
revert the changes simply using this command:
cp /var/backups/xorg/xorg.conf.2008-02-04-07:30:54 /etc/X11/xorg.conf

FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko): No such device

Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

Have also had trouble getting the driver to show the resolution above 800*600. And try  that on a 24 inch screen and see if you are happy with that. cause I am not. I am now trying the second driver. The one that says its not new. but its not the legacy driver.

---

### Post by altersense on 2008-02-05
I strongly recommend installing the nvidia drivers via Envy 
(Alberto Milone's most excellent utility).

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by solitaire on 2008-02-12
Had a problem with Blender and opendGL "Envy" worked a treat !
  thanks altersence

---

