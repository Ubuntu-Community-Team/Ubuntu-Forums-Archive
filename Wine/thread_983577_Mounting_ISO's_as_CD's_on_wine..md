---
title: "Mounting ISO's as CD's on wine."
date: 2008-11-15
forum: Wine
---

### Post by maheshjr2000 on 2008-11-15
Is this possible?

---

### Post by hikaricore on 2008-11-15
You can mount ISO outside of WINE from cli or fstab.

> sudo mount -t iso9660 -o loop filename.iso /media/mountpoint

Then you can map them as drives in WINE.
If you plan on using them constantly you'd be wise to read up on fstab and how to set up mounts there.

---

