---
title: "AMD64 running 32 bit Ubuntu - CPU autoscaling issue"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by ThaRabbit on 2005-10-15
Hello all, thanks for the work you guys n'  ladies do here.. much respect indeed :)

I own a 64 bit (AMD Turion based) laptop system on which I recently installed ubuntu 64 bit version. Everything, including automated cpu scaling, worked fine. I ran into some issues with madwifi and my network adapter and found that 64 is known to cause issues there. Also, my ATI chip (x700 mobile), or to be more precise, the latest apt-get update in combination with the latest ATI linux drivers, caused the buffer to fail and the 3d support to fluke.. a tread about this is in this very forum.

So far as for the introduction to my situation, now for my question. I've since migrated to ubuntu 32 bit and found my network card to be working 100% now. The only problem I found was that the system no longer seems to be able to autoscale my CPU's operating speed. I **am** able to use cpufreq command line to set it back to a lower speed by hand (or at least to make the cpu speed monitor say that it is at a lower speed, you never know do you...) but the powernowd doesn't seem to be autoscaling on this 32 bit ubuntu installation. With that the cpu load monitor gives a standard 50% min use of the cpu at all time. I had the same problem on the preview release of ubuntu 64 bit, but that solved itself with the new kernell which was instaled with apt-get update. The same 64 bit kernel version number that did work fine with autoscaling my cpu is not working with autoscaling on this 32 bit installation.

I have all the latest updates installed... the problem should be the same for all ubuntu 32 bit users with 64 cpu's I suppose... anybody willing to direct me in the right direction here ? Do I need to recompile this kernel and use powernow-k8 module ? Can I use those modules on a 32 installation ?

Thanks in advance,
ThaRabbit

---

