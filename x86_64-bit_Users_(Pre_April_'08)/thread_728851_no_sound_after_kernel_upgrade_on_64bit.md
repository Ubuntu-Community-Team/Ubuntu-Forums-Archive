---
title: "no sound after kernel upgrade on 64bit"
date: 2008-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by kaiwan on 2008-03-19
Hi! 

I have (had) ubuntu gutsy 64 and decided tu upgrade kernel to 2.6.24 and now I have no sound.
While compilin new kernel I left all options on default.
I went to compile new alsa drivers but got this error:

make[1]: Entering directory `/home/miroslav/bin/alsa-driver-1.0.15/acore'
mkdir -p /lib/modules/2.6.24.3/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.24.3/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/miroslav/bin/alsa-driver-1.0.15/acore'
make: *** [install-modules] Error 1

What can I do?

---

### Post by firecat53 on 2008-03-21
I can't say for sure, but it looks like you're missing some dependencies. Check the README or INSTALL file or the website and see if they have a list. Sometimes you just have to google some of the filenames until you figure out what package they belong to....and then figure out the name of that package in Ubuntu repos!

Good luck :)
Scott

---

### Post by kaiwan on 2008-03-22
> **firecat53 said:**
> I can't say for sure, but it looks like you're missing some dependencies. Check the README or INSTALL file or the website and see if they have a list. Sometimes you just have to google some of the filenames until you figure out what package they belong to....and then figure out the name of that package in Ubuntu repos!

Good luck :)
Scott

thanks for answering

fixed it....simply compiled newer version of ALSA which sopports 2.6.24 kernel

---

