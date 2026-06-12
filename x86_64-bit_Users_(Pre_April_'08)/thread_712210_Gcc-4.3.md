---
title: "Gcc-4.3"
date: 2008-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by stoneage on 2008-03-01
Does anyone know the status of GCC-4.3 for Ubuntu? I have a Core2 and optimising isn't entirely successful with '-march=nocona'; I don't get much of an efficiency improvement.  I know It is available for Debian but I don't know the potential consequences of installing it on Ubuntu, so I didn't(It wanted to install about 9 other packages). Can I build it from source and what dependencies would I need? Presumably G++-4.3 and maybe libgomp1(I haven't seen these available as source).
I am currently using GCC-4.2 on Gutsy but it doesn't recognise the 'core2' or 'native' options. I could wait, but is there a viable alternative?

---

### Post by rkrell on 2008-03-31
> **stoneage said:**
> Does anyone know the status of GCC-4.3 for Ubuntu? I have a Core2 and optimising isn't entirely successful with '-march=nocona'; I don't get much of an efficiency improvement.  I know It is available for Debian but I don't know the potential consequences of installing it on Ubuntu, so I didn't(It wanted to install about 9 other packages). Can I build it from source and what dependencies would I need? Presumably G++-4.3 and maybe libgomp1(I haven't seen these available as source).
I am currently using GCC-4.2 on Gutsy but it doesn't recognise the 'core2' or 'native' options. I could wait, but is there a viable alternative?

Nothing new to this time in Hardy as well. You can pick up the package gcc-snapshot, which currently contains a snapshot of gcc according to the gcc 4.3.0 release from 5th of march 2008 (see the Changelog, might be updated every time).
You might encounter problems in compiling different package sources, because many of them need to be adapted especially in header files.

I'm interested in compiling kernel and libc to optimize on a Core 2 Duo system, too. Looking forward what's going on here.

R.

---

### Post by spitf1r3 on 2008-04-04
Maybe you could try to build gcc-4.3 from debian testing or unstable source repository?
I tried to do it, but I didn't succeed:/
Edit:
I found this:
```
https://launchpad.net/~ubuntu-toolchain/+archive
```

---

### Post by fjgaude on 2008-04-04
In Hardy, latest updates, I find gcc-4.4.2.3 is auto installed with build-essential.

---

### Post by stoneage on 2008-04-15
Thanks for the information.
I am trying the Ubuntu Toolchain Hackers version but so far it isn't working out. My system seems not to recognise gcc-4.3(doesn't show in a file-search), and when I try to build Blender with it I get an internal compiler error(It **does** seem to be using gcc-4.3 - it says to send a bug report on gcc-4.3).
So, no luck so far, but thanks for your help.

Error Message:-

extern/ffmpeg/libavcodec/elbg.c: In function ‘try_shift_candidate’:
extern/ffmpeg/libavcodec/elbg.c:245: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
scons: *** [/home/organic/build/linux2/extern/ffmpeg/libavcodec/elbg.o] Error 1
scons: building terminated because of errors.

---

### Post by jespdj on 2008-04-15
> **fjgaude said:**
> In Hardy, latest updates, I find gcc-4.4.2.3 is auto installed with build-essential.
Are you sure? I just checked on my Hardy test system and it's gcc version 4.2.3 (not 4.4.2.3), which is still older than 4.3.

---

