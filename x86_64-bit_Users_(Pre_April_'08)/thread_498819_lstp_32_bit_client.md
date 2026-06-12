---
title: "lstp 32 bit client"
date: 2007-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by benford on 2007-07-11
Hey all.

I've got a dual core Opteron server running Edubuntu 7.04 and I am pleased for the most part. LTSP 5 worked great with minimal configuration when using a 64 bit thin client. Sound and removable devices were just a matter of setting permissions right for my user. TFTP, DHCP et al, are all working just fine. I give a big thanks to the *buntu team for make the distro have a good out of the box experience.

Unfortunately MueKow seems to play a bit less friendly with 32 bit clients, as far as I can tell so far. Before attempting to boot an i386 client, I knew that I would need to install a chroot forthem so I ran:

sudo ltsp-build-client --arch=i386

Which built successfully without any error messages. The problem came when I tried to boot an i386 client. My first attempt was on a Dell Optiplex 280 (mini-desktop version). When opting for a network boot, my screen goes blank for a while, then hangs with a blinking cursor in the upper right of the screen. Alt+F1 takes me to the first virtual terminal where it seems that some progress has been made, but the process just stops. I'll get an exact readout what progress it made, but it is clear that the client received an IP address and that the kernel was transferred by tftp successfully. I'm wondering what went wrong at this point. I'll find some more 32 bit systems to test upon later but I don't see why it would fail like this. Any help would be nice.

---

### Post by benford on 2007-07-12
Ok, so it appears that the command

sudo ltsp-update-kernels

needs to be run after building an ltsp 32 bit chroot on an x86_64 system.  I've gotten a 32 bit client to boot after running this. Is this issue important enough to issue a bug report?

The only problem now is increasing the resolution on the client. Monitor can handle 1280x1024 but the gnome resolution selector (System->Preferences->Screen Resolution) only allows me to choose up to 1024x768.  The card is  a G-Force 4 so it should have no problem with the higher resolution, but that is probably a topic for a different thread.

---

