---
title: "Pine"
date: 2006-09-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rush_898 on 2006-09-24
Trying to get Pine to work without success.  I did a --force-architecture install from a .deb file and then from the terminal it gives me this:

chase@chase-desktop:~$ pine
pine: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory
chase@chase-desktop:~$

So I tried to apt-get the lib file or search synaptic without success.  Ground to a halt here and not sure what else to try.

---

### Post by kleeman on 2006-09-24
sudo apt-get install libssl0.9.7

perhaps?

---

### Post by Kilz on 2006-09-24
> **Rush_898 said:**
> Trying to get Pine to work without success.  I did a --force-architecture install from a .deb file and then from the terminal it gives me this:

chase@chase-desktop:~$ pine
pine: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory
chase@chase-desktop:~$

So I tried to apt-get the lib file or search synaptic without success.  Ground to a halt here and not sure what else to try.

Trying to force a 32bit application is a learning experence. [Here is a page I wrote explaining how its done.]("http://www.tghc.org/staticpages/index.php/32bitapplications")

---

