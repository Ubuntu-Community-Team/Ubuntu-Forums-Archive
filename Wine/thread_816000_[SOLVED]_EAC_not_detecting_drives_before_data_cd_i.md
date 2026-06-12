---
title: "[SOLVED] EAC not detecting drives before data cd is mounted"
date: 2008-06-02
forum: Wine
---

### Post by AThomsen on 2008-06-02
I have a problem with EAC.

If I open EAC with no cd or a audio cd in the drive the drive is not found by EAC.

To see the drive I have to mount a data cd, then open EAC (it now detects the drive) and then insert an audio cd. This has not happened before hardy.

Anyone knows how to fix this as it is quite annoying?:confused:

Using latest Wine.

---

### Post by AThomsen on 2008-06-15
BUMP!

This is still very annoying :-(

Is anyone else having the same problem?

---

### Post by AThomsen on 2008-06-15
It seems adding this to fstab helps!

/dev/cdrw2        /media/dvdrw   udf,iso9660 user,noauto,exec 0       0

---

