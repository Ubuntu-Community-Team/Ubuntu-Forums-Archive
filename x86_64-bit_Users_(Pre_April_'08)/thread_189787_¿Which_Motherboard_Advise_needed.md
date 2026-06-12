---
title: "¿Which Motherboard? Advise needed"
date: 2006-06-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Findeton on 2006-06-05
I recently acquired a new motherboard and CPU: Sempron 3200+ and a K8 ASROCK UPGRADE K8NF3. Unfortunately, the motherboard gave me so much trouble with linux that I've returned it to the shop. Now i need advise, don't want to have more trouble with kernels not loading or a linux without DMA support! I just want a 32bit (I want compatibility) ubuntu for my sempron running, if possible, with one of those motherboards:

[LIST]
[*]K8 ASUS K8S-MX SK754 AGP DDR M-ATX
[*]FOXCONN 760GXK8MB-RS SK754 DDR AGP M-ATX
[*]GIGABYTE 8VM800M SK754 DDR AGP M-ATX
[*]GIGABYTE K8VT800
[/LIST]

Has anyone tested any of those motherboards? That's what I've got on my local store. Anyway, which motherboards would you recommend/suggest me apart from those ones?

---

### Post by maury on 2006-06-06
My system is now a couple of years old, Depending on how cutting edge you intend to go, this may ar may not help. I use replaceable drive bays and so I have run many distros sucessfully on this box.I'm using Dapper AMD_64 at the moment. Simply Mepis is my primary system.
My System :  Built 3/04
Original MB ASUS K8V- Expired 11-13-05
Gigabyte GA-K8NS MB - Installed 11-05
AMD_64 3200+ CPU
e-GeForce FX 5200 Nvidia AGP Video
1024 2700 DDR-SDRam
Removable IDE 133 or 100 Hard Drives
Note! Very Stable- Never seen Windows
Primary OS - Simply Mepis
Linux User #280929

---

### Post by Findeton on 2006-06-06
[QUOTE=maury]My system is now a couple of years old, Depending on how cutting edge you intend to go, this may ar may not help. I use replaceable drive bays and so I have run many distros sucessfully on this box.I'm using Dapper AMD_64 at the moment. Simply Mepis is my primary system.
My System :  Built 3/04
Original MB ASUS K8V- Expired 11-13-05
Gigabyte GA-K8NS MB - Installed 11-05
AMD_64 3200+ CPU
e-GeForce FX 5200 Nvidia AGP Video
1024 2700 DDR-SDRam
Removable IDE 133 or 100 Hard Drives
Note! Very Stable- Never seen Windows
Primary OS - Simply Mepis
Linux User #280929[/QUOTE]

Thanks for the info. I didn't include the GIGABYTE K8NS SK754 DDR AGP in first place because it had the Nvidia Nforce3 250 Chipset. Which is the very same chipset that the motherboard I had to return had. So thank you! I'll try that configuration on the store and see if it works!

BTW, I've got:

AMD_64 SEMPRON 3200+ CPU
512MB DDR-SDRAM PC333
256MB DDR-SDRAM PC333
ATI Radeon 9250 AGP
120GB SEAGATE HD IDE 100/133 
¿Windows? ¿What is windows? :grin:

---

### Post by GAMINGKID on 2006-06-27
Hey Im new to thise fourm . I use to have a peace of S*** 208 not ddrram .'
Well I have a  Gigabyte k8triton series motherboard it supports amd athlon.It is only $80.00.Also I got in my motherboard 768 mb ddrram its my baby.I think you need a diffrent type of video card.I use to have a 128 mb ati .But someone help me i half to use 64 mb nvidia video card plz help.Well dude trust me its worth your money just bye a nvidia 64 mb video card and it will run like a beuty.ok i also have not ddrram memory for sale if  any body would like.I can give some1 208 mbs  just for $20.00!k well try it worth your money.=D>

---

### Post by jvictor on 2006-06-27
My Config

AMD 64 bit 3000+ (754 pin)
Gigabyte K8VM800M mobo with integrated ethernet
512 x 2 Kingston RAM
Nvidia  FX 5200 256 MB
Sony DVD+RW

Ivent faced any issues till now except with the GFX card.. things work really well even on 64 bit Dapper 

I'd to add these lines to xorg.conf to stop the machine freezing at random.. 

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "NvAGP" "0"
        Option "RenderAccel" "Off"
        Option "IgnoreDisplayDevices" "DFP,TV"
        Option "NoRenderExtension" "Off"
        Option "AllowGLXWithComposite" "Off"
EndSection


IMHO its more of a X problem than a H/W prob coz ati & nvidia users have the deadly freeze :)

---

### Post by Teroedni on 2006-06-27
[QUOTE=Findeton]I recently acquired a new motherboard and CPU: Sempron 3200+ and a K8 ASROCK UPGRADE K8NF3. Unfortunately, the motherboard gave me so much trouble with linux that I've returned it to the shop. Now i need advise, don't want to have more trouble with kernels not loading or a linux without DMA support! I just want a 32bit (I want compatibility) ubuntu for my sempron running, if possible, with one of those motherboards:

[LIST]
[*]K8 ASUS K8S-MX SK754 AGP DDR M-ATX
[*]FOXCONN 760GXK8MB-RS SK754 DDR AGP M-ATX
[*]GIGABYTE 8VM800M SK754 DDR AGP M-ATX
[*]GIGABYTE K8VT800
[/LIST]

Has anyone tested any of those motherboards? That's what I've got on my local store. Anyway, which motherboards would you recommend/suggest me apart from those ones?[/QUOTE]

What kind of problems were you getting?


I have 2 socket 754 boards   [64 bits ofcourse;)]
An Asus k8n which works great:) <---crappy sound thought:(, therefore i used an audigy se and that works good:) Sata works fine:)


I also recently bought a Msi K8m Neo-V from clearance sale and  damn i was suprised. I was expecting it to be hard and crappy, but it worked like a charm.
The install was problem free, and the integrated sound was amazing, as good as an audigy se:D. The only negative is the integrated garphics(Unichrome) so if you want 3d i reccomend you an add on card. I also have not tested it with S-ata ,so i dont known if S-ata works on this board.

---

### Post by Mtnear on 2006-06-29
Hi.  I'm also looking to build a Linux system utilizing a socket 754 board.  My question would be what is the recommended mobo chipset that best works with Linux / Dapper?  My current Socket A board has no sound and I'd like to avoid any hiccups like this in a new system.  Thanks.

---

### Post by jvictor on 2006-07-01
Gigabyte K8VM800M works well **provided** u have a extra AGP card.. The unichrome chipsets can be a cause of nuisance. Sound and Ehternet work well for me.. Since AGP is on its way out , u can consider buying a MOBO that supports PCIe

My Config
AMD64-3000+ (754)
Gigabyte K8VM800M
Nvidia FX-5200 256-MB
1G Kingston RAM
Sony DRU810-A DVD-RW


There seems to be a bug in Xorg 7.0 that makes the card to freeze at random , there are two ways out 
1) Disable AGP 
2) Use XGL instead of Xorg to  run your display

---

