---
title: "Sound fault on upgrade"
date: 2008-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by dfowensby on 2008-04-17
After online upgrade with cut/paste 'hardy' into all /etc/apt/sources.list'gutsy' entries, via update manager -d, I rebooted to a nice new spiffy Ubuntu Studio with no sound. The nag box whined about there not being a sound device installed, or gstreamer plugins not loaded in (both wrong).

The problem appears to be the upgrade fails include the existing module arrangement; I hope this is the correct solution, as this worked for me: 
Synaptic
search: modules
check boxes on all entries with the word module and/or sound and any with the orange Ubuntu logo next to it.
Reboot, enjoy.

Hope this helps someone!

Box config: P4,VIAmobo,AC97,nvidiaG6800/128,1Gram, Heron x86_64

---

