---
title: "Sound problems with GeForce6100"
date: 2005-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by xraycharlie on 2005-12-19
Hello,

Hoping someone out there is UbuntuLand can help me.

I picked myself up a Asus GeForce6100 + nForce410 the other day.
Plugged in 2gigs ram and an x2 processor and plopped on Ubuntu with k8-smp.

Installed the latest drivers from Nvidia so now the graphics are working OK (although the bottom bit of the screen seems to jump every now and then.

The probalem has been the sound drivers. I can;t for the life of me get them to work.

I've been through the forums and tried all the suggestions to no avail.

typing 'esd' gives me:
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave

any suggestion would be great.  

Regards

---

### Post by wjp.reg on 2005-12-20
I'm in the same boat (GA-K8N51GMF-9 with onboard 8-channel HD Audio.  My solution was to install an old SB-Live! PCI card until someone gets it right :).

I had to install the NVIDIA ...8174 driver as well as it's the only one compatable with the 6100.

cheers.

---

