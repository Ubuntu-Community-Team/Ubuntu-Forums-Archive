---
title: "On board NVidia not configuring"
date: 2009-03-10
forum: x86 64-bit Users
---

### Post by Twig E. Pottox on 2009-03-10
I'm trying to set up an on board NVidia MCP73V on a ECS MoBo with a core 2 duo E7300 running 8.10 64 bit.  I get an error on start up:

 " EE Nvidia (0)   Failed to load Nvidia kernal..
Aborting
Screen found but none have usable config.

I have reloaded the 173 and 177 drivers.  separately, not at once,  and still no luck

Is this a 64 bit issue. I had no such problem with the 32 bit version.

thanks in advance for any help

---

### Post by athaki on 2009-03-10
It could be an 8.10 issue.  I'm using 8.04 and my nvidia 8600GS cards working fine.

---

### Post by norwoods on 2009-03-10
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

---

