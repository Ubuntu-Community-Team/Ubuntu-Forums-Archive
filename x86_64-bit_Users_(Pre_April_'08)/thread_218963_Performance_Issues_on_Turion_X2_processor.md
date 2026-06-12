---
title: "Performance Issues on Turion X2 processor"
date: 2006-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by kpeng1 on 2006-07-19
Hi,

I just recently installed Ubuntu on my turion X2 laptop.  The specs on the laptop is that its got 1 gig of ram, a 128mb ati integrated video processor, 100 gig HD, and a 2.0 ghz tl-60 turion x2 processor.  The model of my laptop is nx6325 from HP.

What happens is that the install itself actually took a long time compared to a friend who has a dell core solo laptop ( I believe he has the 600m).  The install process itself took over an hour or so maybe more (I was not keeping exact count).  I also noticed that aspects of it where lagging.  It seems that other than the terminal, programs like gedit would take a while to load.  Also, I noticed that it would take a while to render some of the fonts; like when I shut down ubuntu the font scripts that appear during the shut off process would appear, but not smoothly, but rather choppy.  This is probably has is due to some driver issues associated with the video card, but I am not 100% positive.

Also, I have problems with Ubuntu restarting and shutting off.  I am not sure if it is related to Ubuntu or something else, but when I perform a restart Ubuntu shutdowns, but nothing happens.  My laptop screen is just black even though I can see it is still on.  In terms of shutdown, when I shut down ubuntu it is fine, but when I turn on my computer again I get a blank screen.  I would have to manual turn my laptop off again and then back off before it would respond and go into a boot menu.  I have windows as a dual boot as well, I do not think that maybe a problem, but I am not sure.

Any help would be appreciated.  Thanks

---

### Post by ipa on 2006-07-20
I am not sure that I can help you as I have no experience with X2 processors, but your problems will not be related to dual boot.

Do you know what kernel you are running? (type "uname -r" without " into a terminal window)

Do you know what video drivers you are using? This might have something to do with your restarting problems.("gedit /etc/X11/xorg.conf" look for devices section, driver will be ati or preferably fglrx)

Ivan

---

### Post by jokmi on 2006-08-08
Here's a link explaining why passing noapic as a kernel parameter might help:
[http://gentoo-wiki.com/HARDWARE_HP_Compaq_nx6125_with_Turion64]("http://gentoo-wiki.com/HARDWARE_HP_Compaq_nx6125_with_Turion64")

---

### Post by hizaguchi on 2006-08-09
The slow video is probably just the video driver.  Have you tried fglrx?

---

### Post by rffn on 2006-08-12
The noapic switch as suggested above will not really help. Though it removes all issues the OP describes, it also removes the dual core ability. Using the second core requires the use of the APIC, the boot core (cpu0) starts the second core (cpu1) using the APIC. No APIC, no second core.
The issues described are for sure partly a nx6325 issue, but mainly Ubuntu related. SuSe 10.0, 10.1, SLES10, FC5 and Knoppix 5 don't have this issue. A kernel.org 2.6.17 kernel showed other weird behavior though.
The mentioned Linux distributions cannot have something special for the X2 or even the nx6325, some of them are just too old for this. This issue could be fixed in Ubuntu.
I have a nx6325 myself, so this is first hand experience. I moved to FC5, because I need a working system.

RFFN

---

### Post by usernamed on 2006-08-12
I have a single core AMD64 processor and the no_apic processor solution worked for me.  My understanding was that this issue was fixed in later kernels, but I admin I'm slightly puzzled that this hasn't been given higher priority by the developers, given that Ubuntu specifically offers an AMD64 release.

I'd thought that later kernels didn't have this issue, have you tried doing a 'sudo apt-get dist-upgrade' and then rebooting after it's finished?

---

### Post by rffn on 2006-08-12
Yes, I tried to update the kernel, no effect. Also the new 6.06.1 Live CD still shows the same behavior. But this should not be different from sudo apt-get dist-upgrade anyway.
This is a sad thing, because I would like to use Ubuntu on the machine, but I need a working system as well. Ubuntu is at this time not.

RFFN

---

