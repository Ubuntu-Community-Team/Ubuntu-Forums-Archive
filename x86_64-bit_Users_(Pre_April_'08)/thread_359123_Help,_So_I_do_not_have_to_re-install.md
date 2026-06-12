---
title: "Help, So I do not have to re-install"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2007-02-11
All right this is a mess. I installed the new kernel yestday and after that re-installed my Nvidia drivers using the Envy script. Every thing went fine and the computer work for several hours with no problems.

 Ok here is where the problems start. I removed a 512Mb ram stick and replaced it with a 1gb stick. I was not getting any video when I powered up. So I cleared the CMOS. Noe the problems started.

 First time I booted I got the Xserver misconfgured blue screen, I then booted into the recovery mode and tried to re-install the Nvidia driver using the Envy Script. Rebooted and got to the log in screen and the mouse pointer was a square that was barely visible. when I logged in it sred to open bout there were several sqaures that were black with colored specs. the sound would stutter, loading was super slow. Eventually I got this message:

[PHP]Power Manager 
This program can not start until you start the dbus system service.
 It is strongly recommended you reboot your computer after starting message bus[/PHP]

 Ok I did a little search about the message and found the following command to run:

[PHP]sudo /etc/init.d/dbus restart[/PHP]

 I tried it and it did nothing.

 I also tried to manual configure the  xorg.conf to no avail.

 I am at a loss I can more info on this problem. I really do not want to do a re-install to solve this. Any hlep would be greatly appreciated!

---

### Post by kidders on 2007-02-11
Hi there,

Have you tried restoring your old kernel and/or your original RAM? One or both of them is probably bad, I'd say.

---

### Post by chrism66 on 2007-02-11
Ok, I tried the two ram sticks still getting the same probelem with bot kernels that are on the list for grub. However, I very sure that i was using 2.6.15.26 before the update yesterday. on grub it is only showing 2.6.15.27, and 2.6.15.28. How do I edit grub so that I could try the.26 kernel?

edit: Ok I edit the grub menu.lst to show all kernels. Problem is in then all with each stick of ram. So I am lead to belive that it is not the ram or new kernel. Maybe it is the Nvidia drivers but like I siad they were workinf just fine until the memory upgrade. I am going to try installing the nvidia-gls and see if that works.

Also another message that came up once last night was:

[PHP]This program cannot start until you start dbus sessionService

        This is usually started automatically in X or Gnome startup when you start up a new session[/PHP]

I even tried to install Kubunutu-desktop. Did not work would go through the boot sequence and would hang up when when the log on scrren was to come up.

Like I said earlier I am at a complete loss, I don't want to have to re-install (only post I found about dbus message seem to have only been resolved by a clean install). Arrgh!!! You know I have at least one good thing to say about winblows, it has the old repair option.

---

### Post by kidders on 2007-02-11
Hmm... Some dbus-related change might've crept in somewhere. I wonder if reinstalling it would help (long shot). If the problem was there though, **/etc/init.d/dbus restart** would surely have complained at you. :confused: 

It might also be worth making sure nothing in your box got shaken loose when you were working on it.

Is anything other than your X broken? It certainly looks like my initial suggestion was dumb.

---

### Post by chrism66 on 2007-02-12
Problem Solved.

When I hit cleared the cmos. It set the AGP ram size bios to 128MB, I set it to 64MB and every thing is working again. I think I remember reading some where that there a bug about this setting.

---

