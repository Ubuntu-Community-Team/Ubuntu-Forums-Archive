---
title: "Problems with the X, resolution and keyword"
date: 2008-09-23
forum: x86 64-bit Users
---

### Post by lezich on 2008-09-23
hi, i am having problems with my ubuntu.

my hardware is and ASUS M2N-MX SE PLUS with nvidia integrated

when i first installed ubuntu, i could configure my nvidia Gforce 6100 nfx 430, but when i update the kernel, the ndvidia configuration did not work anymore.

and i could not fix it, and the resolution was 800x600, so i put in the comand line

sudo dpkg-reconfigure -phigh xserver-xorg

and it fixs, but since 15 days ago, i installed ubuntustudio and did not like it, so i removed, but now, i could not use dkpg-reconfigure anymore, i mean, the commando does work, but when i reboot the x, the same message that it is running with low resolution.

Looking for fixing the problem, i use this command

sudo dpkg-reconfigure xserver-xorg

and after that, my keybord, did not work correctly, like it use to. now combination of key like AltGr+2 = @, "ñ" and other key, does not work now.

And now, whe i reboot the X, i got this message

--------------------
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---------------------
The result of xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "es_ES", "pc105", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "es_ES", "pc105", ""

The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = []
 model = pc105
 options = [eurosign	eurosign:e,eurosign	eurosign:2,eurosign	eurosign:4,eurosign	eurosign:5]
 overrideSettings = true


i really do not what else to do, i been thinking reinstaling the ubuntu, but i have so many new programs, that it will be a huge work for me

thanks for your help

---

### Post by sjbaugh on 2008-09-23
I got this problem with a kernel update and it had the same effect on my nvidia card (8400 GS) on Hardy 64 bit. I solved it by using EnvyNG (it's in the repositories). EnvyNG auto-senses nvidia and ati cards and builds an appropriate video driver and links it to the kernel.

It may work for you too.

---

### Post by lezich on 2008-09-23
thanks for you quote, i will download and install througt the Synaptic to try it if it works for me.

Now i remember that i enter in [www.nvidia.com](www.nvidia.com) and donwloaded one driver for my card, and it did not work, i hope this driver will cause me no problem with EnvyNG

regarts

Luis

> **sjbaugh said:**
> I got this problem with a kernel update and it had the same effect on my nvidia card (8400 GS) on Hardy 64 bit. I solved it by using EnvyNG (it's in the repositories). EnvyNG auto-senses nvidia and ati cards and builds an appropriate video driver and links it to the kernel.

It may work for you too.

---

### Post by sjbaugh on 2008-09-23
lezich,

It uninstalled the previous driver I was using automatically (also installed with EnvyNG). It seems to sort out all the X settings as well.

Best of luck, Steve

---

### Post by lezich on 2008-09-24
i did install what you told me, but it still doesn't work, i dont know what else to do

i did reinstall with the synaptic parts of gnome everything that i have already installed and now a am reinstalling XKG and and gconftool, i will let you guys now if these will fix my ubuntu

regarts

---

### Post by sjbaugh on 2008-09-24
Luis,

Sorry it didn't work. Anything else would be beyond my experience. I hope someone else has a better idea.

Steve

---

### Post by lezich on 2008-09-24
Steve, thank you very much, it did not work reinstaling everything with XKG
i am still seeking for the solution, i hope that somebody who really got a clear idea and knwolege can help me

---

### Post by lezich on 2008-09-24
Steve!!! thanks man!!!....i download and installed the EnvyNG, but i did not run it!!.......so i notice that, run the EnvyNG and now it works!!!!!

thanks again man!!

best of lucks for you

Luis:):guitar:

---

### Post by sjbaugh on 2008-09-24
Luis,

Thanks for letting me know you got it working!

Glad to be of some help,

Steve

---

### Post by itisbasi on 2008-10-21
I had a similar problem getting a resolution greater than 800 x 600 on my m2n mx se plus board which has onboard geforce 6150 se . I installed nvidia settings manager from synaptic and i was able to easily change to a much higher resolution and even save the changes to my xorg.cong file without any trouble...

---

