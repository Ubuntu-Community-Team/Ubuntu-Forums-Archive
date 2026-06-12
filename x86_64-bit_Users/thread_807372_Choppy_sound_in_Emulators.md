---
title: "Choppy sound in Emulators"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by Ryanhedge on 2008-05-25
Hello, I've been using Ubuntu and it's variants for the past few months and recently decided to start running various game console emulators in it. Most of the emulators run fine graphically and clock speed wise, but most of them have choppy sound and music. I've tried VBA,Gens, and Mupen so far. Anyone got some info?

Sys specs:
Amd Atholon 64 3,700+
2 gigs of DDR 400 Ram
SB Audigy SE
ATI X300, 256 megs of ram
ASrock 939 dual vista board
DVD/CD-rw combo
30 gig ide HDD, 750 gig sata hdd (Ubuntu install)
OS: Ubuntu 8.04 64bit using KDE desktop.

---

### Post by soxs on 2008-05-26
In case ou use alsa, you should set the emulators audioautput to oss and run the emulators with the pulseaudiowrapper for oss: ```
padsp ossEmulator
```

---

