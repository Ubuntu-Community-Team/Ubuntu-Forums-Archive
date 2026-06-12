---
title: "New Kernel Problem"
date: 2007-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomus on 2007-03-21
I am new to ubuntu and have to say I have been very impressed thus far.

However, I'm having a few problems.  At first I decided to install the i386 32bit version of edgy eft on my acer aspire 5021 with a dual boot with xp.  After having lots of problems trying to install the wireless I decided to try the 64-bit version.  This version however seems to take a lot longer to boot up giving error messages about the firmware install for my broadcom wireless card. (I think this may just be due to the fact that I haven't managed to install it yet though).  It then proceeds to give messages such as starting up swap drive etc which wasn't present on the 32-bit version, I realise this may well be normal I was just curious.

After logging into ubuntu for the first time I downloaded the kernel updates giving me the 2.6.17.11 kernel version. Once I restarted I tried to boot this kernel but it failed completely getting stuck on the splash loading screen (incidently this is in a clumsy black and white grayscale display).

Has anyone got any idea why the updated kernel isn't booting properly? (It failed also on the 32bit version but then worked once I re installed ubuntu and updated again)

Also can anyone tell me why it is taking getting on for 3-5mins to boot after GRUB?

Thanks for any help.

---

### Post by prince_niceguy on 2007-03-22
Seems you are having some issue. try removing quiet and splash from the boot option you can do that by hitting e on the grub boot screen, again hitting e and then deleting the splash and quiet. Hit enter and hit b.

post the result where the boot process hangs... based on that some body will be able to give some input.

---

