---
title: "Ubuntu won't boot"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Skaarg on 2005-11-03
I have been having a problem with ubuntu live cd AMD64 version where it will not boot on my AMD 64 comp.  I type live and hit enter to start it up, it goes through all the setup stuff, and then gets the ubuntu loading screen where it gets OK for everything. Then it just goes to a black screen with a white line in the corner. my cd rom drive light flashes for a while and then stops and my whole comp locks up, I can't even open the cd rom drive.

Here are my system specs if they are what is causing the problem.

GA-K8NXP-SLI 
AMD 64 socket 939 3500+
1 GB of DDR400 RAM
Dual chipset GeForce 6600 GT
I know my audio is onboard, but I think it's AC97
Hard drives
1 IDE Western Digital 60 gb
1 SATA Seagate 80gb

---

### Post by jvictor on 2005-11-03
Are u using a DVD writer ? For me the install used to hand at 13 % , had to enable DMA. Ive a SONY DRU810-A . try enabling dma at boot up. that may help

---

### Post by Skaarg on 2005-11-03
Nope I'm not using a dvd writer, I just used a CD-writer/dvd player combo to make the cd. but it is a Sony drive so I'll try enabling DMA.

EDIT* I checked and DMA was already eneabled so that can't be the problem.

---

### Post by RAOF on 2005-11-04
It's possible that booting with the magic incantation
```

live apci=off noacpi

```
will help.  On the other hand, what it's not doing is starting X (the graphical environment) successfully.  You should be able to press Ctrl-Alt-F1 to get to a terminal, where you can check /var/log/Xorg.0.log to see what the problem is.  My guess would be that your dual 6600s are freaking out the nv driver.

---

### Post by Skaarg on 2005-11-04
Well I tried the stuff you said, and I do I hit ctrl-alt-f1 at where it asks me how I wish to boot, because if so that didn't do anything. O well maybe ubuntu isn't ment for this machine. Atleast it runs on my other one, but I don't use it as much as I do this one.

---

### Post by RAOF on 2005-11-04
Sorry for not being clear.  I meant: Try pressing Ctrl-Alt-F1 after it has finished booting, and you've just got the black screen with the white line.

---

### Post by Skaarg on 2005-11-06
[QUOTE=RAOF]Sorry for not being clear.  I meant: Try pressing Ctrl-Alt-F1 after it has finished booting, and you've just got the black screen with the white line.[/QUOTE]
Well I did that and it went to a black screen where that just showed text and it got an O.K. for everything it showed loading, and then it went to the black screen with the white line and completely locks up, I can't even take the cd out of the drive, or press ctrl alt del to reboot.

---

### Post by jvictor on 2005-11-06
Well, when can u tell us what is ur cd combo configd as ? Primary slave or secondary master ? 

if ur cd combo is primary master type 
live hda=nodma

if ur cd combo is primary slave type 
live hdb=nodma

if ur cd combo is secondary master type 
live hdc=nodma


if ur cd combo is secondary master type 
live hdd=nodma


try booting , and get back to us... lets c what happens

---

