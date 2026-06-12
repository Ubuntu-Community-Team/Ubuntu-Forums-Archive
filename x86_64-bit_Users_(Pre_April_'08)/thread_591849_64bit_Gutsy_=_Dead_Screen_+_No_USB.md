---
title: "64bit Gutsy = Dead Screen + No USB"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bennett2005 on 2007-10-25
It's an equation I'm stuck on.

I"m a relatively new Linux user, with only a couple weeks of poking around in 7.10 behind my belt.  I'm loving Ubuntu, itching to give Kubuntu a try for a few weeks, but I would like to get the 64bit version working properly the next time around.

I tried the 64bit version first when 7.10 Gutsy was released.  I've downloaded a few different ISO's to make sure I didn't just have a corrupted file.  The normal 32bit versions of Ubuntu and Kubuntu fire up with no problems, clean install, they even do my dishes.

The problem:

Upon loading the 64bit version, I would lose all USB support.  It would be there on boot, then when the Live CD took over USB would go away.  

After waiting for the countdown timer to wind down and the live CD to load, I would see a brief status bar "Loading Linux Kernel," a few other lines of text (nothing that was error related), then the screen would go blank and my monitor would hit the stand-by setting like I hit the alarm clock after a long night of doing things I shouldn't be doing at my age.

I've posted about the blank screen before, and I've seen numerous other posts talking about the same thing.  I haven't been able to try any keyboard fixes to correct the problem because, well, I...can't use my keyboard.  I've even tried using a PS2 adapter to  hook up via old school connection, and nada. 

Anyone have any ideas, leads, fingers to point with, etc?  I'll even accept a few fingers pointing in my general direction with laughter if it'll help me in the long run. :)

System stats:

Mo-freakin-bo:  Lanparty NF4 SLI
Processor:       AMD Athalon 64 X2 Dual Core
Ram:               2 Gigs of Hot Action
Dog:                English Black Lab, 60 Pounds of Insanity

Any help would be appreciated :)

---

### Post by Therion on 2007-10-26
See if this will get you up and running.  

Boot with your LiveCD and at the boot menu, use F6.
Find and edit the following line...
```
kernel          /boot/vmlinuz-2.6.22-14-genericroot=UUID=43a49820- ... dcb2c ro splash quiet
```
by removing the word "splash".  Just delete it right out of existence and continue with the LiveCD.  I shortened the line because it's insanely long.  You'll know it when you see it.  What's important is that **ro splash quiet** part.

If you decide to install, you'll most likely need to boot into Recovery Mode and edit that line again, or make some other minor adjustments to your GRUB.  That's what happened to me anyway.  The Black Screen o' Death IS fixable, it's just annoying.  Once I got the correct driver installed everything was good.  Well, I still don't have a splash-screen, but I can live with that.

I too have problems with my USB keyboard not being recognized until after Ubuntu has fully loaded.  This makes entering the GRUB menu difficult, since the keyboard is unresponsive.  I solved the problem by installing an old PS2 keyboard I had lying around* as well as* my primary USB keyboard (ha!  dual hard drives AND dual keyboards - beat that!!).  I keep the PS2 KB tucked away and out of sight unless I need to enter GRUB for some reason.  Otherwise, the USB keyboard is fine once Gutsy boots up.  I believe this is a bug that has already been reported.

---

### Post by Bennett2005 on 2007-10-26
> **Therion said:**
> See if this will get you up and running.  

Boot with your LiveCD and at the boot menu, use F6.
Find and edit the following line...
```
kernel          /boot/vmlinuz-2.6.22-14-genericroot=UUID=43a49820- ... dcb2c ro splash quiet
```
by removing the word "splash".  Just delete it right out of existence and continue with the LiveCD.  I shortened the line because it's insanely long.  You'll know it when you see it.  What's important is that **ro splash quiet** part.

If you decide to install, you'll most likely need to boot into Recovery Mode and edit that line again, or make some other minor adjustments to your GRUB.  That's what happened to me anyway.  The Black Screen o' Death IS fixable, it's just annoying.  Once I got the correct driver installed everything was good.  Well, I still don't have a splash-screen, but I can live with that.

I too have problems with my USB keyboard not being recognized until after Ubuntu has fully loaded.  This makes entering the GRUB menu difficult, since the keyboard is unresponsive.  I solved the problem by installing an old PS2 keyboard I had lying around* as well as* my primary USB keyboard (ha!  dual hard drives AND dual keyboards - beat that!!).  I keep the PS2 KB tucked away and out of sight unless I need to enter GRUB for some reason.  Otherwise, the USB keyboard is fine once Gutsy boots up.  I believe this is a bug that has already been reported.

Hmm...maybe I'll be 'borrowing' my keyboard from work this weekend.   :guitar:

Thanks! I'll give it a shot.

---

