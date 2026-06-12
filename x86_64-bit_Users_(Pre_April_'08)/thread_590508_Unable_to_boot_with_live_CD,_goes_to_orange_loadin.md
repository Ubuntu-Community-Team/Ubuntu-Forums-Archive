---
title: "Unable to boot with live CD, goes to orange loading bar then Black screen"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by comfortablynumb on 2007-10-24
I received a 64bit version of feisty a while back and could never get it to boot, I saw the Ubuntu splash screen, the orange bar like it was loading and then a black screen. I chucked it up to an incompatibility somewhere in my system. I just tried to download and run the newest live cd of Gusty Gibon with the same effect. I then tried the 32 bit version of Gusty that I run on my Laptop and once it the splash screen with the orange loading bar clears the screen just goes crazy with a bunch of colored bars.

My system specs:
DFI Lanparty Nforce 4 Mobo
AMD 64 3200 socket 939
1 Gb Corsair PC3200 DDR
Geforce PCI Express 6200 256MM ddr
View Sonic VA1912 LCD monitor 
Western Digital SATAII 16mb cache 320GB Hd
I  have 2 Sound Cards
- Audigy 
- EMU 0404

---

### Post by carlinuxlearner on 2007-10-24
It some kind of graphics driver problem, there is a way to get it to work on the live disk but it's not easy. Just download the alternate installation disk and use that.

C@RL

---

### Post by jaybombalous on 2007-10-27
Use the alternate cd image to install, its a text based installer. This should stop the resolution problems.

---

### Post by praxis22 on 2007-10-27
Not done this for a while but there should be the ability to give the kernel special options when booting

add this to the boot line, you can also do this from grub I think by hitting escape:

**quiet naopic nolapic**

That should get you around both graphic glitches, and problems with the built-in hardware detection.

You're likely to need this when you actually get it installed too, even if you do use the alternate installer.

---

### Post by comfortablynumb on 2007-10-27
Thanks for the replies, Ill try download the alternate cd and give it another go sometime this week probably.

---

### Post by emotionlovesyou on 2008-04-11
Where do you get the alternate CD image?

---

### Post by emotionlovesyou on 2008-04-11
Apparently people who've had similar problems came to the conclusion that it was because they had an NVIDIA GeForce. Do you guys have this kind of a graphics card?

Just curious.

I'd still like to download the alternate install. Does anyone know the exact url?

---

