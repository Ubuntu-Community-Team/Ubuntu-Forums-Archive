---
title: "Monitor switching between digital and analog"
date: 2007-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by APGunner on 2007-04-12
I am trying to boot the livecd of a 64 bit version of ubuntu, it gets to the screen where i can select my options for booting it such as safe graphics mode and such, but when i hit safe graphics mode or the regular one they both give me the same thing. My monitor turns black and switchs back and forth between analog and digital. I have a 20 inch Samsung 206bw widescreen monitor. The 32 bit version of ubuntu boots just fine for me though which is weird because the 64 bit version doesn't. I want to get the 64 bit version install so I can get more out of my amd processor. If you need any more of my computer specs just tell me. btw im trying to use the 7.04 64 bit version. but i also tried using 6.06 64 bit version and it did the same thing

---

### Post by Spr0k3t on 2007-04-12
On the liveCD, have you tried the alternate install disc (ie textmode).  As for the 64bit not loading correctly, can you give a run down of your system configuration with emphasis on the processor and graphics card and connectors used from the graphics card to the monitor?  If the graphics card is integrated, what chipset is used on the motherboard?

---

### Post by APGunner on 2007-04-12
Radeon X800GTO 256 mb PCI-E
AMD Athlon 64 +3500 2.2ghz venice core

No i haven't tried the alternate cd and im using DVI connectors. I also tried switching to VGA connects but the same thing happened.

It only happens with the 64 bit version the 32 bit version runs fine. My computer should boot the 64 bit version though since my processor supports 64 bit.

I am going to bed now though since it is 1 in the morning. I'll check back here in the morning though.

---

### Post by Spr0k3t on 2007-04-12
You may want to try the alternate install CD and see if that gives you a better result since it uses a very generic 640x480 driver.  If you have problems after install, you can always make simple changes with the alternate CD as it has a simplified bash terminal.

---

### Post by APGunner on 2007-04-12
ok i'll try that tomorrow and give a status report. thanks for helping :)

---

### Post by APGunner on 2007-04-12
well I managed to get ubuntu 64 bit 7.04 install but when i try to boot it up it does the same thing it did when i tried to boot the live cd. It goes between digital and analog until the monitor just shuts off because its not receiving a signal.

---

### Post by kuja on 2007-04-12
> **APGunner said:**
> well I managed to get ubuntu 64 bit 7.04 install but when i try to boot it up it does the same thing it did when i tried to boot the live cd. It goes between digital and analog until the monitor just shuts off because its not receiving a signal.
Doesn't sound like a fun problem. Anyhow, next step will probably run something like this: 1. boot up in recovery mode which should give you a root linux console (no graphical interface). After that, the plan is probably to install the proprietary ati drivers (and edit the /etc/X11/xorg.conf to suit) and see if it'll function. Granted, I've not played with an ati card for a while, so someone else can fill in the missing holes.

---

### Post by APGunner on 2007-04-12
I can get to a the command line. I know how to access the xorg.conf file, but I don't have an internet connection set up in it because I have a wireless card but I suppose I can't get a wired connection if someone will help me step by step in installing the properitary drivers, but I can't even get the the ubuntu loading screen so I don't think installing the properitary drivers will work. I'll give it a try though.

---

### Post by APGunner on 2007-04-12
ok unless anyone else can help me get 64 bit ubuntu running on my machine or anyone else has anymore ideas im just going to go back to 32 bit because 64 bit is a pain in the ***.

---

### Post by DrOni on 2008-01-26
For some reason Ubuntu 64 doesn't like showing it's boot up screen on a digital connection. If you just wait it out, gnome will eventually show up. Mine then went straight into the screensaver at that point, so watch if you leave it to boot up and come back and it's still doing it after say, 5 minutes. Move the mouse.

I'm still a newbie myself, so I can't explain why it does this. But both my 22" Viewsonic VX2235wm monitors do it on my GeForce 8600GT. I haven't tried it on a different setup

---

