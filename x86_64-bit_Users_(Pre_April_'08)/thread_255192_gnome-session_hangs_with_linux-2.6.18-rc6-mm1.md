---
title: "gnome-session hangs with linux-2.6.18-rc6-mm1"
date: 2006-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by dermoth on 2006-09-11
I'm one of the lucky owner of a VIA-based motherboart that will have fully-supported IDE and SATA only in 2.6.19. Dapper Drake kernel works ok for SATA but I have to recompile a newer or patched kernel to get the PATA to work properly.

So I decided to go with linux-2.6.18-rc6-mm1. I build it, installed it, created an initrd by hands by extracting the original initrd, replacing modules and repacking it. I also upgrated udev (And e2fsck to resolve deps) using the edgy source packages as distribution-provided udev is too old for curent kernels.

The system boots, disks, cdroms, everything works well with both PATA and SATA. GDM login screen loads fine, but when I login from GDM I get a brown screen and nothing seems to load.

From a tty I can see that it loaded all init scripts from /etc/X11/Xsession.d/ (although xrdb appears as a zombie, not sure it it's expected but I guess so since with the distribution kernel it's not there once the session is loaded) and then loaded /etc/alternatives/x-session-manager (which end-up loading /usr/bin/gnome-session) and looks like this process is stalled.

Any idea what's going on? Since it failed on the first try, I tried to keep my config as close as possible to the distribution config but that didn't help. Is there any know issues between gnome and recent kernels?

Thanks

---

