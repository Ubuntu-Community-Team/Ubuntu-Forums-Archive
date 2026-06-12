---
title: "Patching Wine"
date: 2008-08-11
forum: Wine
---

### Post by Noxxan on 2008-08-11
I'm trying to patch wine to get painkiller working again but this is what i get:

joakim@joakim-desktop:~/Desktop/wine-1.1.2$ patch -p1 < patch.diff
patching file dlls/wined3d/device.c
Hunk #1 FAILED at 2254.
1 out of 1 hunk FAILED -- saving rejects to file dlls/wined3d/device.c.rej

Patch: [http://bugs.winehq.org/attachment.cgi?id=15335](http://bugs.winehq.org/attachment.cgi?id=15335)

Any ideas?

---

### Post by Noxxan on 2008-08-11
Bump

---

### Post by kdorf on 2008-08-12
Have you verified that this patch is compatible with this version of wine?

---

