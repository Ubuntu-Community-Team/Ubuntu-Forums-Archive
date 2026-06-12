---
title: "Oracle 10g on 64bit AMD Ubuntu Tips"
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ab5602 on 2006-05-09
Hi,

Here are a few tips for getting the Oracle 10g installer to load up on AMD-64 Ubuntu (tips mostly stolen and compiled from various other threads):

1) Set the environment variable "XLOCALELIBDIR=/usr/lib32/X11/locale" before running the installer. This tells the java installer to reference the 32-bit locale directory, otherwise, the java installer failes to load locale settings.

2) You will need a copy of a 32-bit version of libXp.so.6 (from the xorg libs package).  It is easiest to just copy this from a 32-bit system and put it into your /usr/lib32 dir.

3) Run the installer with the option 'runInstaller -ignoreSysPrereqs'.  This tells the installer to ignore the fact that Ubuntu is unsupported as an Oracle-capable distro.

---

