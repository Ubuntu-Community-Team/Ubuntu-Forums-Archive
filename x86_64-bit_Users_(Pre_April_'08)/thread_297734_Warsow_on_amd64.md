---
title: "Warsow on amd64"
date: 2006-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2006-11-11
Okay, so I installed Warsow as per normal and when run it I get this error message:
```

Console initialized.
------- sound initialization -------
Loading sound module: openal
LoadLibrary (./libs/snd_openal_i386.so):(libvorbisfile.so.3: cannot open shared object file: No such file or directory)
Loading openal failed
Loading sound module: qf
LoadLibrary (./libs/snd_qf_i386.so):(libvorbisfile.so.3: cannot open shared object file: No such file or directory)
Loading qf failed
Couldn't load a sound module
------------------------------------

----- R_Init -----
ref_gl version: GL 0.01
Segmentation fault
```

---

### Post by xstaticxgpx on 2006-11-12
download warsow .21 from their website which includes the 64bit linux libs. in .2 you had to build warsow linux 64bit from the sdk.

---

