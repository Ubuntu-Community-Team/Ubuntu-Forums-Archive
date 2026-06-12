---
title: "Problems installing Ubuntu64bit"
date: 2007-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chamelion on 2007-09-17
I just bought a new computer. Intel Core 2 Duo. 512 Mb Nvidia GF 8500GT PCI-E Graphics card.
I am running Feisty on my old computer. I just tried the Gutsy Tribe 5 CD 64 Bit (Live) and the Feisty 64 Bit.
The monitor (Asus 1680 x 1050 resolution) turns itself of when loading. The computer keeps on running. After a minute I turned monitor back on and Ubuntu was there. 
Even the right resolution. (This is with Gutsy) Monitor also turns of with Feisty 64 though.
After installation took out the live CD and rebooted. 
Same situation. Monitor went blank. 
Last message I could see was:
> Kernel %100.
Kernel direct mapping tables up to 1000000 @ 8000. 
Went very quick so numbers might not be exactly right.
After I turned the monitor back on I was straight at the Ubuntu log in screen. 
There was no chance to access my other operating systems anymore, regardless from which hard drive I was booting. (separate hard drive. Sabayon, XP)
The options screen was not accessible.
I have fixed that by now (Super Grub Disc).
But now Ubuntu on the other drive has become unbootable. 
I already have Sabayon 64 bit installed so I think there is no problem with the format and the computer.
I tested the 32 bit Feisty disc and it works (live). 
So I will have Ubuntu eventually, but I would very much like to use the 64 Bit.
Would anybody please have some advice?
Thank you
I hope this is not too much, but I have one more question. Ubuntu does not seem to recognize the Sabayon file system. (Ext4). 
Will it still let me boot into it?
Once everything is fixed of course.

---

### Post by danieljay on 2007-09-17
I can relate to your monitor issue. I have a MSI GeForce 8600 dual head graphics card and it is not recognized during the boot process. I used the alternate feisty(Also tried Gutsy) 64bit install and then installed the nvidia 8 drivers with envy and the monitors work fine. (Except durring boot)

---

### Post by Chamelion on 2007-09-18
I have not tried the alternate install CD yet. I might give that a go. Will the boot options screen come up that way?

---

### Post by Kilz on 2007-09-18
You might also want to try a released version of Ubuntu. Gutsy is under development and may have problems.

---

### Post by dabl on 2007-09-18
Kilz' advice is good, but I'll speculate the video issue is more "new hardware" than "new software" related.

I have Gutsy running pretty stably on Intel Core 2 Duo & Nvidia hardware, but it's not as new as yours. Here's the general approach, I would think:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

I think you want to get it running as a VESA display first.

Then, of the two ways to install the Nvidia driver (nvidia-glx-new package, or Envy script installer), there are problems with both of them in Gutsy.  I resolved it by first downloading and installing the Envy installer:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

then BEFORE attempting to run Envy you have to modify it slightly, as described in the July 29 post here:

[http://albertomilone.com/wordpress/?m=200707](http://albertomilone.com/wordpress/?m=200707)

It worked fine for me.

Final note -- yesterday's Gutsy updates nuked my Intel HDA sound system.  I'm told that there's more updates today that fixed the problem, but I'm away from my system and can't confirm that.  Fair warning for Beta guinea pigs.  :lolflag:

---

### Post by Chamelion on 2007-09-18
Thank you. This will give me something to work with. Might install Feisty now. As you might have noticed I am not exactly an expert. :)
Probably will take me a few weeks till I have everything running, then I can update.
One more thing. I tried the 32bit live Feisty yesterday. It told me that the link to my Sabayon OS on the other hard drive is broken and just showed me an empty drive. Do you think I am running into trouble with the EXT4 File system on Sabayon here?
Does Ubuntu recognize EXT4?
I am on the verge of installing everything again anyway. Sabayon is a cool system to play around with, but I do need Ubuntu and all it's possibilities as a serious OS.
( I am hooked, cannot be without it!)
Thanks again all for your help. 
This really is a great community.

---

### Post by dabl on 2007-09-18
My quick skim of Gparted's file formatting capabilities reveals that, of the 13 filesystem formats available, EXT4 is NOT one of them.

So, your Sabayon partition is not going to be recognized from Ubuntu, as far as I can see, but I'm far from an expert on that subject.  I personally prefer reiserfs on my desktop system, but it is too slow booting for a laptop.  Probably 95% of Ubuntu users use ext3 and are perfectly happy with it. (My statistically unsupported opinion.)

:lolflag:

---

### Post by danieljay on 2007-09-18
I had Gutsy working on my 8600 but I thought that the issues that I had were related to Gutsy so I went back to Feisty 64bit and things work great. Envy works straight out of the box with the install instructions on their website and with a one line tweak you can get Envy to work in Gutsy. 

Using the alternate install cd seemed to work the best for me. It should recognize your card as the NV driver instead of the nvidia driver that you will eventually want.

Good luck!

---

