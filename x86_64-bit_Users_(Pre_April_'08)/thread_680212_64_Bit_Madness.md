---
title: "64 Bit Madness"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by cj100570 on 2008-01-27
I currently have Feisty 32 bit installed on my main pc and 64 bit on a spare pc. Last night I decided to install 64 bit on my main pc and ran into a brick wall.... When I boot the live cd it black screens and I'm not able to proceed. I've tried booting with noapic and specifying a resolution after pressing F6 but neither has worked. Anyone have any idea what the issue and fix may be?

---

### Post by Ravanous on 2008-01-27
I ended up having to install via the non-graphical installer and then installing the video drivers for my ATI card.

Going the same route might help. Looking at your rig stats doesnt seem like you have an ATI card....but you never know.

---

### Post by cj100570 on 2008-01-27
I have an nvidia video card and it black screens after choosing boot options.

---

### Post by Cappy on 2008-01-28
You want to add "nosplash" on to the end of the boot options.
If the installation still hangs you will need to try "nosplash noapic nolapic"

Instead of "nosplash" you can also use "vga=771" if you want to keep the splash loading screen.

---

### Post by cj100570 on 2008-01-28
It didn't work. I'm not gonna worry about it anymore. I have a perfectly functioning 32 bit system. I know it's the video card but I'm too lazy to switch it out with the one in my other pc. Thanks for the suggestions.

---

### Post by Jouke74 on 2008-01-28
That is a well known problem of the 8800 and AMD64 UBuntu 7.10.

hmm, nosplash usually solves it.

Please keep the nosplash and use on the first screen, the boot menu on the cd, press F6 (extra options) you will be presented with some preloaded parameters. Append the pre-existing parameters by adding “noapic nolapic pci=noacpi acpi=off irqpoll noirqdebug” at the end of the line (without " "). This disable for the moment the acpi daemon.

(If you haven't done so).

Another option is the Alternate CD text install, which should "always" work.

Then after it is installed, you might get the problem again :)

---

