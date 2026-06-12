---
title: "ubuntu 64-bit crashes on logoff/restart/shutdown"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by dcfly on 2007-06-13
After installing the "restricted" ATI display driver (I have Radeon x800), ubuntu insists on crashing on logoff, restart, or shutdown. The symptoms experienced are a dead display and blinking keyboard lights. While I enjoyed these effects last night while experimenting with peyote, today they are just irritating.

I have searched these exciting forums and found a chap with [similar experiences]("http://ubuntuforums.org/showthread.php?p=1950800") but, sadly, the suggestions there did not work for me.

Thanks for any help.

---

### Post by Kilz on 2007-06-13
> **dcfly said:**
> After installing the "restricted" ATI display driver (I have Radeon x800), ubuntu insists on crashing on logoff, restart, or shutdown. The symptoms experienced are a dead display and blinking keyboard lights. While I enjoyed these effects last night while experimenting with peyote, today they are just irritating.

I have searched these exciting forums and found a chap with [similar experiences]("http://ubuntuforums.org/showthread.php?p=1950800") but, sadly, the suggestions there did not work for me.

Thanks for any help.

You might just have to remove them and reinstall the ubuntu drivers. You could also try a older version of the ATI drivers.

---

### Post by dcfly on 2007-06-17
That seriously bums out my trip.

I'd enjoy hearing from someone who:

1. Has ATI Radeon X8xx series or similar.
2. Has ubuntu x64.
3. Has any drivers installed that allow direct rendering (3d) and can enable desktop effects, with no kernel crashes.

How you did that?

I really like ubuntu but I can't get it working on my system. I must say that everyone on this forum and the IRC channel have been extremely helpful.

Cheers!

---

### Post by Cappy on 2007-06-17
Here is a thread that is somewhat related:
[http://ubuntuforums.org/showthread.php?t=473521](http://ubuntuforums.org/showthread.php?t=473521)

Edit: Actually, that problem isn't related to this one.
Consider this a
/bump

---

### Post by dcfly on 2007-06-18
Actually, it seems to be a similar problem, in that he/she is experiencing kernel crash on log-off, restart, and shut-down. Also, I too had to edit the "splash" parameter out of the boot config to get ubuntu to start.

My system:

AMD Athlon 64 3200 (Venice)
ATI Radeon X800
nVidia nForce 4 chipset
1 GB Corsair XMS series DDR400 RAM

---

### Post by fumduck on 2007-10-07
I used this  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.39.4_Driver_Manually")
and followed method 1...  then after could not boot I edited /boot/grub/menu.lst     put nosplash  instead of vga=whateverihad  and it booted right up..
I have an x800 gto  and am running both 64 and 32 ubuntu.. works on 32 bit.. just got it to work on 64 bit today??  Goodluck

---

