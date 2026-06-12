---
title: "Nvidia / Compiz / Xgl / Hardy issue (first driver load prob, then white screen)"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by vertago1 on 2008-04-29
I know compiz, xgl, and hardy work fine together for the 32 arch because I am running them on my laptop.

On my desktop to get the nvidia settings menu I originally installed NVIDIA's manual-install driver off of their site which worked fine. When I performed a distribution upgrade to Hardy the kernel update broke the nvidia drivers so I fought with them for a while and had to do the following to get the nvidia drivers to work:
-uninstall all nvidia packages
-make sure nvidia wasn't installed through envyDS
-run: sudo ./<nvidia installer file> --uninstall

From there I could install the new NVIDIA driver, I was unable to get the xserver to load using any of nvidia packages through the repos.

At this point KDE 4.0, and the nvidia drivers were working properly. I installed compiz and couldn't get it to run from kde 4 and realized I forgot to install xserver-xgl.

When I restarted the xserver after installing xserver-xgl I faced the black white screen problem. So I killed the xserver using ctrl-alt-backspace and after some forum searching and various fix attempts I was left with little choice but to uninstall xserver-xorg, and compiz until I can find a resolution.

I tried reinstalling the mesa libraries and running 
LD_PRELOAD==/usr/lib/fglrx/libGL.so.1.2.xlibmesa
xstart
but I faced the white screen again when kde finished loading

(note xstart was running kde3 not kde4 it would be helpful to know how to run kde4 from the console too)

I really prefer the nvidia driver over nv because the nvidia driver lets me control my two monitors with the nvidia-setup.

Pretty much I am hoping someone knows the solution to one of the following:
-delt with the problem of installing nvidia drivers for a EVGA Geforce 7900 GS either through apt or envyds
-delt with the white-screen issue with nvidia's driver on hardy

Thanks

---

### Post by vertago1 on 2008-05-05
I setup the nvidia drivers on another 64bit kubuntu system and ran into the same problems, I suspect the packages used by the repos and EnvyDS are for the older kernel, I may try installing them and using grub to run the older kernel later to see if this is true. Nvidia's installer gave a warning about the version of gcc used for the kernel installed when I ran the older kernel, but when I started the new kernel it didn't give the error because the gcc installed by hardy matches the newer kernel.

---

### Post by bijeeshvs on 2008-05-05
if u use hardy there is a new version of "Envy" for the driver installation try your luck on that..................

---

### Post by vertago1 on 2008-05-09
Alright so this is how I resolved the issue:
1. make sure you uninstall any nvidia proprietary drivers from nvidia
the problem I was having with nvidia-glx-new as that it didn't have a dependency set to linux-restricted-modules so the fix was simply running the command:

sudo apt-get install nvidia-glx-new linux-restricted-modules

There may have been a change in the packages between when I first started this thread and this post. My new problem is that when I install xserver-xgl no longer get the white screen but the 2nd monitor is very glitchy I may post screen shots later.

---

