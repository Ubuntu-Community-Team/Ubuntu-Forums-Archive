---
title: "32-bit firefox problem (flash-plugin)"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by baRRacuda on 2005-10-15
Hello, i've just created a 32-bit chroot for firefox with flash support, but i've problems. when i run the 32-bit firefox i get this error :

```
LoadPlugin: failed to initialize shared library /home/barracuda/.mozilla/plugins/libflashplayer.so [libXmu.so.6: cannot open shared object file: No such file or directory]
``` 
and in runs, but the flash plug-in doesn't work. (i installed it via synaptic (32-bit))
 (it used the work in hoary :???: )

(i used the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=24575&highlight=32-bit+chroot"), except used breezy-32 repos, not hoary)


BIG BIG BIG EDIT : i just realized i forgot to install flashplayer-mozilla package (i had just installed flashplugin-nonfree package), now everything works like a charm.

Note : i wish i could delete this post not to confuse people.

---

### Post by gsaathoff on 2005-10-15
have you tried installing gplflash for 64 bit firefox?  that should probably work.  see the other post in this forum "flash in AMD" or something like that.

-graham

---

