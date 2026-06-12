---
title: "Wine / Peggle Error"
date: 2008-01-13
forum: Wine
---

### Post by nburns on 2008-01-13
Is anyone having problems running Peggle under wine?  I was able to install Peggle ok, but everytime I try to run it, I get an error box that pops up and says:

"Please set your desktop color depth to 16 bit"

In the console, I see the following error:
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x32)! (XRandR)


Any ideas?

---

### Post by nburns on 2008-01-13
Also, some other threads recommended turning off compwiz.  I tried that, but still hit the same errors.

---

### Post by yoblin on 2008-01-13
same error, will post if I figure anything out

---

### Post by yoblin on 2008-01-13
updating to the newest version of wine fixed it for me!

follow the instructions here, then run an apt-get update as they say, then go into synaptic and search for wine. There will be a newer version to install.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

