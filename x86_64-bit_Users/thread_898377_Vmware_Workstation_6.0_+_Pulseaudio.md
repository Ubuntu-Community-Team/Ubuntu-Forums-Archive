---
title: "Vmware Workstation 6.0 + Pulseaudio"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by brizon on 2008-08-23
Despite reading half the internet, downloading the vmware-dsp patch and tearing half my hair out, I cannot get VMWare to talk to pulseaudio properly. I want to be to access it from a thin client, it is happy to chuck sound out on the actual host but not pulseaudio. I have tried modifying the /usr/bin/vmrun script to preload the wrapper libraries but the damn thing keeps giving me the same message: ERROR: ld.so: object 'libvmdsp.so' from LD_PRELOAD cannot be preloaded: ignored. I want to try recompiling the vmware-dsp libs but I have some missing dependency. I tried the alsa wrapper for oss applications but installing that sent me back to square one, as in the /dev/dsp is busy message from vmware. I appreciate the fact that I'm lucky to have sound at all but if anyone has any suggestions it would be great.

Thanks, 
Brizon

---

