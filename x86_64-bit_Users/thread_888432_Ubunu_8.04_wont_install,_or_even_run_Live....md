---
title: "Ubunu 8.04 wont install, or even run Live..."
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by 2m4Y on 2008-08-13
...hi there, I hav a little problem, recently I changed CPU & Monitor, I've got now AMD Athlon 64 6400+ X2 & Asus MK241H! Well, till now, everything worked OK, but I must reinstal my LindowsXP, so I decided to instal also LindowsVista & again reinstall Ubuntu 8.04 (even tried Ultimate 1.8 x64)!
XP passed OK, but problems are in Ubuntu (& Vista), it boots, but doesn't do anything if I choose! I even tried with GParted, it booted OK, went into GUI, but searching for HDD drives, & keeps searching! I've even updated BIOS so it's working OK, don't know what could it be!

Can USB cam & mike be the problem, withc are on Asus MK241H monitor?!?

I have:
AMD Athlon 64 6400+ X2 (~3220MHz)
Asus M2N-E SLi, BIOS v1102 (was v0802)
2x 1GB PQI DDRII 800MHz (~804MHz)
Asus 8800GTS 320MB (G80, ~500/1200/1600MHz)
SB Live 5.1 Digital
Codegen 600W PSU
Asus MK241H 24" LCD
Logitech MX510
PS/2 Standard Keyboard

Cheers...

---

### Post by Crafty Kisses on 2008-08-13
That's weird, post the following output:
```
sudo fdisk -l
```

---

### Post by youngpatrick on 2008-08-14
> **2m4Y said:**
> ...hi there, I hav a little problem, recently I changed CPU & Monitor, I've got now AMD Athlon 64 6400+ X2 & Asus MK241H! Well, till now, everything worked OK, but I must reinstal my LindowsXP, so I decided to instal also LindowsVista & again reinstall Ubuntu 8.04 (even tried Ultimate 1.8 x64)!
XP passed OK, but problems are in Ubuntu (& Vista), it boots, but doesn't do anything if I choose! I even tried with GParted, it booted OK, went into GUI, but searching for HDD drives, & keeps searching! I've even updated BIOS so it's working OK, don't know what could it be!

Can USB cam & mike be the problem, withc are on Asus MK241H monitor?!?

I have:
AMD Athlon 64 6400+ X2 (~3220MHz)
Asus M2N-E SLi, BIOS v1102 (was v0802)
2x 1GB PQI DDRII 800MHz (~804MHz)
Asus 8800GTS 320MB (G80, ~500/1200/1600MHz)
SB Live 5.1 Digital
Codegen 600W PSU
Asus MK241H 24" LCD
Logitech MX510
PS/2 Standard Keyboard

Cheers...

Last month, I have the similar experience. That was no problem to install Windows XP but failed to install sound card driver and could not boot-up the Kubuntu Live CD. 

First of all, you can try to unplug the SB LIVE 5.1 digital sound card from your system and then try to boot-up Ubuntu Live CD. Keep in mind that many PC hardware problem caused by peripheral such video card, RAM or sound card. Thus, the basic hardware trouble-shooting is to unplug the unnecessary peripheral such as the above interface. That is MB + RAM + HDD + MONITOR + MOUSE + KEYBOARD + POWER SUPPLY (of course) to start-up under such basic PC hardware configuration. If you can hear the 'beep'signal not 'beep...b e e p...b e e p...b e e p' etc.  That means the BIOS test all the hardware components successfully. 

Good Luck !!!

Good Luck !!!

---

### Post by xphil9 on 2008-08-14
2m4Y the problem is with your Codegen 600W PSU and PS/2 Standard Keyboard. Also if that 5.1 digital was 2.1 analog you wouldn't have this issue.
Good luck in future system building.

---

