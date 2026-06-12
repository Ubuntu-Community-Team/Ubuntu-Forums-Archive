---
title: "live cd and graphiccard problems"
date: 2006-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by vbd on 2006-02-01
Hello,

to ensure that the sata-controller is supported by ubuntu I tried out the Ubuntu 5.10 AMD live cd. Loading the Gnome-Desktop ends up in showing ascii chars - no mouse cursor or anything else.
The boot-option debian-installer/framebuffer=false didn't help much. 
Graphiccard: gigabyte nvidia 6600 with 256 MB

Possibly 
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
would help if ubuntu was installed - but what todo with the live cd?

best regards 
Volker

---

### Post by FluffyElmo on 2006-02-01
I think you can enable the VESA driver using the LiveCD. You won't have any graphic acceleration, so it'll be slow but it should work. From another thread:

*"You can boot the livecd with "live-expert", and when the time comes, change the X driver from "nv" to "vesa". That should get a working GUI."*

Regarding your questions, I'm actually using a 6600GT with no problems. I also had no issues with SATA, didn't need special drivers like installing XP. My chipset is a VIA K8T800Pro so results may vary...searching the forum for your chipset/controller may turn up useful info.

Good Luck!

---

