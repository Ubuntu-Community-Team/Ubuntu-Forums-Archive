---
title: "Gaim-otr for Gaim2.0.0beta5"
date: 2007-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by tns on 2007-02-24
I'm running Edgy, and I'm trying to get gaim-otr working. I downloaded and built litotr-3.0.0 from source. Then, I downloaded the otr source along with the patch gaim2b2-otr.diff. I opened the patch and changed gtkstock.h to gaimstock.h and then ran it. *patch -p0 < gaim2b2-otr.diff* Then I scattered the OTR library files all over the place trying to get Gaim to see the plugin.

The OTR plugin still doesn't show up in Gaim, and when I run *gaim -d* from terminal, I found this line 
> 
plugins: probing /usr/lib/gaim/libotr.so
plugins: /usr/lib/gaim/libotr.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?


Now I'm stumped... Has anybody got Gaim-OTR working in Gaim2.0.0beta5?

---

