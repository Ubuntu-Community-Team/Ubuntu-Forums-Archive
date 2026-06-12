---
title: "horrible performance(worse than windows :( )"
date: 2008-08-28
forum: x86 64-bit Users
---

### Post by boblemur on 2008-08-28
iv reticently gotten a new computer because my old computer wasnt cut out for the work i do, so my new hardware is:

-dual quadcore xeons 3.16Ghz
-2x4 GB ddr3 ram
-2x1 TB internal hard disks

so i was defiantly expecting my computer to be very responsive.

i was thinking of running a Debian install so its a little more server like but i decided against it and stuck with ubuntu. however my programs are rather slow to load.

the computer came imaged with xp pro on it (filled with their oem trials software garbage) and it still logs in with a ready desktop in under 3 seconds...

gnome however takes almost a minute before my top pannel loads(the last thing to load for me)

pidgin often locks up and firefox, gnome settings/menus etc. are still rarther slow, very comparable to the performance i get from my 1.6ghz (512 mb ram) laptop.... which i find disgraceful

so any help would be much appreciated... the last thing i want is to be stuck back in windows... 

compiz is off (graphics set to none)

so just as a summary:
-very powerful hardware
-runs very quickly in windows xp
-ubuntu takes approx 60 seconds to load from login to ready desktop
-pidgin locks up constantly
-menus(applications,system etc..) load slowly
-lag while gksudo appears

thank you for any help in advance

---

### Post by philinux on 2008-08-28
That 60 second delay from login to desktop sounds like it could be a graphics driver issue.

Which card is it and what does system>admin>hardware drivers report?

Try the failsafe graphics option just to see if there is a difference.

Also look in system>admin>system log at the log files for any clues.

---

### Post by Kilz on 2008-08-28
> **boblemur said:**
> iv reticently gotten a new computer because my old computer wasnt cut out for the work i do, so my new hardware is:

-dual quadcore xeons 3.16Ghz
-2x4 GB ddr3 ram
-2x1 TB internal hard disks

so i was defiantly expecting my computer to be very responsive.

i was thinking of running a Debian install so its a little more server like but i decided against it and stuck with ubuntu. however my programs are rather slow to load.

the computer came imaged with xp pro on it (filled with their oem trials software garbage) and it still logs in with a ready desktop in under 3 seconds...

gnome however takes almost a minute before my top pannel loads(the last thing to load for me)

pidgin often locks up and firefox, gnome settings/menus etc. are still rarther slow, very comparable to the performance i get from my 1.6ghz (512 mb ram) laptop.... which i find disgraceful

so any help would be much appreciated... the last thing i want is to be stuck back in windows... 

compiz is off (graphics set to none)

so just as a summary:
-very powerful hardware
-runs very quickly in windows xp
-ubuntu takes approx 60 seconds to load from login to ready desktop
-pidgin locks up constantly
-menus(applications,system etc..) load slowly
-lag while gksudo appears

thank you for any help in advance

How long until the first program starts to load in XP?

---

### Post by phidia on 2008-08-28
There ia a guide to speed up booting [here]("http://lightningcrash.blogspot.com/2007/08/making-ubuntu-boot-in-19-seconds.html") or maybe give [crunchbang]("http://news.softpedia.com/news/First-look-CrunchBang-A-faster-Ubuntu-77535.shtml") a try?

---

### Post by TenPlus1 on 2008-08-28
You can also get the latest version of Pidgin and other apps from [www.getdeb.net](www.getdeb.net) to see if that stops it from crashing...

Turn off Tracking, Disable services/sessions you dont need and that will improve bootup time...

---

### Post by Coolcool on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by philinux on 2008-08-28
> **Kilz said:**
> How long until the first program starts to load in XP?

60 seconds delay in ubuntu is way off.

Mine takes about 13 seconds to display desktop fully. Wallpaper et all.

---

### Post by TenPlus1 on 2008-08-28
Check out this guide also: [http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

---

### Post by tuxxy on 2008-08-28
You may be using the old pidgin, have you installed the correct plugins for firefox as this could cause it to slow down.

---

### Post by Thelasko on 2008-08-28
With a rig like that, I'd guess an Nvidia Quadro.  It has a big marketshare/ vendor support in applications that require that kind of power (CAD/CAM, 3D modeling, CFD).  That kind of power for checking e-mail would be ludicrous.

A system like that should be smokin no matter what version of Pidgin you use.  It's gotta be the video card driver.

---

### Post by phidia on 2008-08-28
What kind of frame rates does "glxgears" output?

---

### Post by Jouke74 on 2008-08-29
Could you please post any errors found in the output of the following command in terminal: "dmesg". Also your full hardware specs would be nice, including video chip etc. Are you using Raid?

Logging into Windows under 3 seconds I find amazing? I never got it down less than 30 seconds on any computer (because most stuff needs to be loaded from harddisk).

I assume the pidgin lockup has to do with something else, although it is also a problem of course. Which might also point at your LAN hardware being the problem under Ubuntu although it is hard to imagine.

---

### Post by kosmiciatakuja on 2008-08-29
This is just a guess but it might be a problem with networking - some time in the past (in Feisty I think) I had some issues with painfully slow system. Turned out it was waiting for some network address to reply but this address did not exist. Thus before any program started it hat to wait until the network timeout which was like 30 secs or so. 

Please check your /etc/hosts, or maybe network configuration in /etc/networking or maybe try sudo rmmod ipv6 (if you don't use ipv6 of course). 

there is also the possibility of booting with noapic or nolapic or acpi=off on the kernel line, but I have little idea of what those options do, it's just that they seem to help some people. You might give them a try, it shouldn't hurt even if it doesn't help. Of course, if they don't help, remove them from the kernel line, they turn off some things which may be needed.

---

### Post by Thelasko on 2008-08-29
> **kosmiciatakuja said:**
> there is also the possibility of booting with noapic or nolapic or acpi=off on the kernel line, but I have little idea of what those options do, it's just that they seem to help some people. You might give them a try, it shouldn't hurt even if it doesn't help. Of course, if they don't help, remove them from the kernel line, they turn off some things which may be needed.

You can add those options at boot time and it will only run them once.  It's very useful for troubleshooting.  [Here are some instructions on how to do so]("http://ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed") (note: it's old and for a fast system clock but it should be the same).  From the linked post:
> Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and Press "e".
Then you will see 3 lines:

```
root (hd0,0)
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
initrd	/boot/initrd.img-2.6.12-10-k7
```

Select the line which begins with the word "kernel" and press "e" to edit it.

Add one [ONLY ONE i.e. only 1) or only 2) ] of the following things at the end of the line:

1) noapic nolapic
so that it will look like this:

```
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic
```

OR
2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=off
OR
7) noapic acpi=noirq nolapic

Then get off the text field and press "b" to boot the kernel.

---

### Post by skunkTrader on 2008-08-29
> **boblemur said:**
> iv reticently gotten a new computer because my old computer wasnt cut out for the work i do, so my new hardware is:

-dual quadcore xeons 3.16Ghz
-2x4 GB ddr3 ram
-2x1 TB internal hard disks

so i was defiantly expecting my computer to be very responsive.


I have a similar system:
-dual quadcode xeons 2.0 GHz
-8 GB DDR3 ram
-500 GB internal hd
-nvidia FX570 driving 2*24 inch panels (1920x1200x32bpp each)

Time from login screen -> desktop is less than 3 secs

I'm running KDE 3.5.9

glxgears fps is approx 4700 when the machine is "busy"

---

### Post by boblemur on 2008-08-30
first of all thanks for all the reply and sorry i havnt been able to reply... iv had problems login into the forums...(posted about it in genral help, ironicly)

but i managed to get on now...

glxgears gives 5500 fps minimum over like 10 intervals

i do not use raid....

im running gnome, and my setup is pretty default atm (bing a new computer and all)


nothing bad in dmesg looks all normal

---

