---
title: "Problems upgrading from Intrepid  to Jaunty"
date: 2009-04-17
forum: x86 64-bit Users
---

### Post by mtnwalker2b on 2009-04-17
Running  64 bit  Intrepid on  AMD Phenom II x4.   I did the  Alt  F2  and typed in  upgrade manager -d   and followed all the instructions.  All seemed to be going well until time came to reboot.
It  Won't   All manner of errors reported,  I'm told the X server is not configured properly.  Then on screen  Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System:  Linux zoew-phenomII 2.6.28-11-generic #42-Ubun Build Date: 09 April 2009
xorg-server 2:1.6.0-Oubuntu14   yada yada
EE Failed to load /usr/lib/xorg/modules/extensions//libglx.so
EE Failed to load module "glx" (loader failed, 7)
EE module ABI major version (1) doesn't match the server's version (2)
EE Failed to load module "dri" (module requirement mismatch, 0)
{atiddxSetup} X version mismatch - detected X.org 7.1.0.0, required X.or
EE Failed to load module "fglrx" ( module requirement mismatch, 0)
EE No drivers available.

Fatal server error:
no screens found

Now  Im completely new at this  but  it  seems to be telling me that somehow  I got the server version installed  instead of the desktop-  is this correct?   and what do I do now?

---

### Post by mtnwalker2b on 2009-04-18
Tried to fix the above problem by  downloading and burning the 64-bit jaunty CD.    This loaded  and installed  and it boots up,  however  most of the functionality  was missing.   Could not access anything on the top panel.

It then became apparent that my boot drive was failing  and fast.   So I unplugged it.  Prepared another drive  and installed  Intrepid  on the new drive.   Once I get over the sting  will try to upgrade to jaunty  once more and  see what happens.

---

### Post by mtnwalker2b on 2009-04-18
OK,  with a bit of trepidation. I have reinstalled  9.04  from the Live CD
and it went quite well this time.   Even with ext3  it loads  many times faster  than intrepid  did on this machine.
I am running  64- bit  on an  AMD PhenomII x4 on a Gigabyte MA78GM-US2H with 4 G of PC1066  and even with these challenges  it seems to be running quite well.  It actually  likes  Jaunty  much better than Intrepid  which is why I attempted the upgrade in the first place.  I will be in line for the Final Release  when it becomes  available.  Tis amazing how many problems a failing HD can cause  before it finally   bites the dust.

Many thanks to all of you who work so hard to bring is  these upgrades.

---

