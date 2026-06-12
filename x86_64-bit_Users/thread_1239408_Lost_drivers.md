---
title: "Lost drivers"
date: 2009-08-13
forum: x86 64-bit Users
---

### Post by chris1950 on 2009-08-13
I used apt-get install linux-header-2.6.28-14-server. After completed I lost my broadcom b43 wireless driver and system sound driver as well as my lan. Can I uninstall this and get everything back or is there a back up file I can use to restore?
Also are  the old kernels still there somewhere and if they are can I edit the menu.lst file to the old values and reboot?
I have it on another drive and compared the menu.lst and saw that the original headers were changed from generic to server,  I downloaded linux-headers-lbm-2.28-13-generic_2.6.28-13.14amd64.deb and linux-image-2.6.28-14.47_amd64.deb. in case I could just reinstall them, if I can which do I install first?

---

### Post by chris1950 on 2009-08-14
I solved it myself by editing Grub and deleting the server entries.:)

---

### Post by Yellow Pasque on 2009-08-14
If you still have the -server kernel, those entries will probably be automatically regenerated at some point. Make sure you uninstall the -server packages.

---

