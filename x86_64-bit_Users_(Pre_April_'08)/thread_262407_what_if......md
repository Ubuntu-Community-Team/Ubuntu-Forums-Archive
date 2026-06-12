---
title: "what if....."
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by kick6 on 2006-09-21
This just crossed my mind: Does anyone think it might be better if ubuntu64 came with 32bit firefox and totem/gstreamer straight out of the box?  Seems to me no one would notice, and that everyone goes ahead and installs these apps anyway to use the w32codecs and flash.

Also, maybe synaptics should have logic that will return suitable i386 packages when amd64 packages aren't available (wine, etc)?


Just crazy thoughts.....

---

### Post by Kilz on 2006-09-21
> **kick6 said:**
> This just crossed my mind: Does anyone think it might be better if ubuntu64 came with 32bit firefox and totem/gstreamer straight out of the box?  Seems to me no one would notice, and that everyone goes ahead and installs these apps anyway to use the w32codecs and flash.

Also, maybe synaptics should have logic that will return suitable i386 packages when amd64 packages aren't available (wine, etc)?


Just crazy thoughts.....

Not just crazy, I have been in a discussion on the developers maillist trying to get exactly that to happen. Packageing a 32bit application for the 64bit version isnt hard, in fact my f32bit firefox howto usess a deb file I made to install 32bit firefox.

---

### Post by kick6 on 2006-09-21
> **Kilz said:**
> Not just crazy, I have been in a discussion on the developers maillist trying to get exactly that to happen. Packageing a 32bit application for the 64bit version isnt hard, in fact my f32bit firefox howto usess a deb file I made to install 32bit firefox.

There's a howto for this!?

After I learned about the --force-architecture hook in dpkg I just went and snagged the official firefox deb, and installed it.  No problems to speak of.

---

### Post by Kilz on 2006-09-21
> **kick6 said:**
> There's a howto for this!?

After I learned about the --force-architecture hook in dpkg I just went and snagged the official firefox deb, and installed it.  No problems to speak of.

Look in my signature.  :D

---

### Post by kick6 on 2006-09-21
> **Kilz said:**
> Look in my signature.  :D


Ah.  Apparently I cheated.  While trying to get wine to work I did a build-dep, and it installed all the emulation stuff for me.

---

