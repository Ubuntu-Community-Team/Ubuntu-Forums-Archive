---
title: "Going Crazy...!"
date: 2007-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ebichuhamster on 2007-03-03
For the past few weeks I've been trying to install the 32 bit version, but due to some unidentifiable and constant error, i gave up

2 days ago i succesfully installed the alternate cd 64 bit version.  But on reboot the boot process just wont get pass either:

the grey ubunty image (20% of the times)
the green bar that comes right after it (80%)

I have no idea how to identify the error, but i beleive it's hardware related, because on the 32 bit version i tired to enable/disable the Network Adapter on the BIOS options. It loaded twice (once enabled, once disabled) then never again.

I've tried recovery mode and as messages start scrolling down the screen the computer seems to just give up, and it's not on some specific task (once it stopped on "configuring keymap [or something like that] other times the last message is just different)

I was suggested to run the live cd, (which i did try to install before but it hanged on boot) and it did it again.  

So since im such a newbie at all this, if theres anyone out there who can give me some kind of direction on how to diagnose/solve these problems, i'd be really grate full

Reeeeeally want to hear that nice ubuntu loading .wav file which i have heard on the very rare occasion that the computer actuallly allows me to enter the window manager...its like im entering the comunity

Specs:

AMD Turion 64 x2
Fujitsu 120Gb HD (my partitions are recognized as sda(1,2,3..) dont know if that has to do with anything
1Gb RAM

(hp Pavilion dv6000 laptop) im starting to guess that hp just configured it so that only windows can run on it effectively

---

### Post by teaker1s on 2007-03-03
do you have intel/nvidia 6150go/ or ati graphics

---

### Post by ebichuhamster on 2007-03-03
0_0 nvidia GeForce Go 6150............are you psychic??

---

### Post by kleeman on 2007-03-03
If I was you I would try getting it to boot with the alternate livecd. When the initial screen comes up there are a bunch of options listed (under the f4 key I think) that you can try passing to the kernel to get the thing to boot (things like "acpi=off" and so on). Run through these and see if anything works. If you get it to boot you can then hard install and pass the options that allow a boot via the grub kernel entry (you add options to the line starting with "kernel" in /boot/grub/menu.lst)

---

### Post by ebichuhamster on 2007-03-03
> **kleeman said:**
> If I was you I would try getting it to boot with the alternate livecd. When the initial screen comes up there are a bunch of options listed (under the f4 key I think) that you can try passing to the kernel to get the thing to boot (things like "acpi=off" and so on). Run through these and see if anything works. If you get it to boot you can then hard install and pass the options that allow a boot via the grub kernel entry (you add options to the line starting with "kernel" in /boot/grub/menu.lst)

Ok, this is the part where I'm really a newbie.  I'm gonna search around for tutorials on LINUX commands and try to familiarize myself with the system, but if there's any specific set of commands  (the exact commands b/c i really lack knowledge in computer lingo, therefore wont be able to fill in variables)

In any case,, thanks a lot for your help until now ^_^

---

### Post by kleeman on 2007-03-03
The livecd is fairly user friendly. Just get to the first screen and search around with the f1 f2 f3 f4 etc keys for help.

---

### Post by teaker1s on 2007-03-03
No super powers are not one of my assets, writing a wiki page with others, regarding dv6000=guilty

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by ebichuhamster on 2007-03-03
Whew

now i can breath again.  the new installation went smooth as silk (this being not configuring the network DHCP options)

well, not really, now I'm going crazy over ubuntu, not BECAUSE of ubuntu

^_^

thanks a lot teaker1s and kleeman for the interest and responses!

now i have other bugs to work out, but they are minor in comparison

i will continue to use this thread to post on these questions if i cant find the answers on the forum or elsewhere

LONG LIVE UBUNTU!

---

### Post by kleeman on 2007-03-03
Yeah there you go! As the wiki says press f6 and enter the three options.....

---

