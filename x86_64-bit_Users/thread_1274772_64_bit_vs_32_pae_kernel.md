---
title: "64 bit vs 32 pae kernel"
date: 2009-09-24
forum: x86 64-bit Users
---

### Post by dj-toonz on 2009-09-24
Hi all, I've been running fedora 11 on a new system what I built but using Ubuntu on every other system I've got (got 4 machines including a Dell mini 10v netbook) & want to install Ubuntu 9.04 onto it, Like I've got on the other 3 (1 of them is just a test machine In the sig)

When I was running fedora 11, I just downloaded the 32 bit version and installed it & it picked up all 12 gigs of the ram I've got installed why is that? I thought you needed a 64 bit kernel to access more then 3.2 or 4 gigs of ram 

here's the system specs

Intel Core i7 975 Extreme Edition 3.33GHz Socket 1366 8MB Cache (quad core)
XFX MB-X858I-CH19 Intel X58 DDR3 motherboard
12 GHZ of DDR3-1333MHz Ram
3x XFX 1792MB GTX 295 1792MB PCI-E 2.0 (x16) 2000MHz GDDR3 GPU 576MHz 480 Cores HDMI/ 2x DL DVI-I HDCP Graphics Cards Nvidia
4x 2TB Segate SATA II hard drives in raid 0
Codegen Briza Silver Gaming Case with Zalman 1000w ZM1000-HP Dual Heatpipe Cooled Modular PSU +80% Efficiency PSU
SATA II blue-ray reader
SATA II dvd-RW
15 in 1 card reader
30" widescreen Dell TFT

the kernel what is installed in the fedora system is 2.6.31-10-pae

will karmic 9.10 be using the pae kernel as default in the 32 bit version ? or how can you install the pae kernel in jaunty ? 

as I want to change from Fedora to Ubuntu (as I understand Ubuntu more) & only wanted to test the bleeding edge software & see what fedora was like

---

### Post by tuxxy on 2009-09-24
Just install 64-bit Ubuntu and all your RAM will be there for use, very nice system btw I'm so jealous hehe  :D

---

### Post by dj-toonz on 2009-09-24
thx for that, I'll replace Fedora 2mmorow with the 64bit Jaunty

I've got a mac aswell, 8 core (dual quad) 3.2gig, 32 gig of ram, 9TB hard drive in raid 0 4 x 512 meg ATI graphics cards, raid controller, 30" monitor 2 x mac drives (front slot dvd-rw's) & running 64bit Ubuntu on that along side osx snow leopard (still got OSX installed for me Iphone 3GS)

---

### Post by tuxxy on 2009-09-24
> **dj-toonz said:**
> I've got a mac aswell, 8 core (dual quad) 3.2gig, 32 gig of ram, 9TB hard drive in raid 0 4 x 512 meg ATI graphics cards, raid controller, 30" monitor 2 x mac drives (front slot dvd-rw's) & running 64bit Ubuntu on that along side osx snow leopard (still got OSX installed for me Iphone 3GS)

holy cow 32GB RAM! mate thats an awful lot :lolflag:

Do you know aria?

---

### Post by dj-toonz on 2009-09-24
I know :p, when your running tracktor DJ, cubase & alberton live on the system & got keyboards, samplers & mixers & other sh&t connected to it (what I do) I work as a DJ / remixer (for clubland) so need the system to run sweet (I tried XP pro 64 & Vista 64 (but no go) all the virus scans & having to wait for everything to load before the system booted. why I changed over to Ubuntu (it's more easier to use then MS any day) where abouts in Manchester then bud ?. I use LMMS, Rosegarden, Mixxx, Ultramixer *for day to day dj'ing (why I've still got OSX installed on the mac) if i could replace them & do the same in Linux I would (but don't fully understand how jacks works yet)

---

### Post by tuxxy on 2009-09-24
Damn thats a lot of things to run just out of curiosity how much do you usually get through of the 32GB when running near to full peripherals? I wouldnt mind a double quad hehe what motherboard runs that?

---

### Post by dj-toonz on 2009-09-25
I don't know what motherboard is in the system as it standard Apple mac board I do know the system cost me 13 & a half Grand for the full mac system, system performance, push it like for example, running 2 decks though, technic 1210 mark 5g's (gold lmtd ed) samples. for alberton & cubase & tracker & dj'ing with tracker & there is  no laticy (0%) & play samples though the keyboard at the same-time. I can scrach on the time discs  & throw a image & mix in though the projector coming out though one of the graphics cards (into a Projector) with HDMI port (all the ATI cards have got HDMI ports) & it dosen't even miss a beat, I've had the system from christmas & wouldn't get shut of it now I've had for 9/10 months the kernel i've got in that for Ubuntu is a realtime kernel & everything works like it does under OSX (If I could get something smaller like a dual quad core macbook i would In a shot) but intill then :( it's stuck in the basment

---

### Post by Arup on 2009-09-25
WOW! awesome specs on those machines and I thought having a dual quad core Xeon with 16GB was hot stuff. Use x64 Jaunty, PAE mode although works well in Linux doesn't truly utilize the full potential of your x64 CPU.

---

