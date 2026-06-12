---
title: "sleep mode no longer possible"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by strongboww on 2008-04-29
hi,
my girlfriends pc went into sleep-state without problems in 7.10, after upgrading it instantly recovers when you try to make it stand-by

anyone else experienced this problem?

---

### Post by CAsurfer on 2008-04-29
This sort of problem usually has something to do with video card drivers. Do you know what kind of video card the computer has (e.g. ATI versus nVidia), or what driver is being used (you can find it in "/etc/X11/xorg.conf" in Section "Device")?

---

### Post by defenestratos on 2008-04-30
Is there an error box when you come back on? I had a problem which said "Unable to unload the module RT5100" or something similar. In my case it was the module/driver for my wireless card which couldn't unload because it was crapping out.

---

### Post by plazo on 2008-04-30
Hi,

You should open a terminal an type "tail -f /var/log/messages" in order to see exactly what's happening when you try to enter in sleep mode

It might be a problem with a module than can't suppport suspend or hibernate

---

