---
title: "aoss not working with 32bit programs on x64 platform"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Goliath23 on 2007-04-27
Hi,

I'm on x64 and try to use wine (32bit and OSS) and teamspeak (32bit and OSS) together at the same time using "aoss" (from the package alsa-oss).

if I try that I get

```
david@sun:~$ aoss teamspeak
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

david@sun:~$ aoss wine
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
```

libaoss.so is compiled for x64

```
david@sun:~$ readelf -h /usr/lib/libaoss.so|grep Machine
  Machine:                           Advanced Micro Devices X86-64
```

I have ia32-libs and lib32asound2 installed.

Do I need a 32 bit version of alsa-oss, or is there something wrong with my dynamic linker configuration (ld.so)?

Any Ideas on this one?

Happy Summer,

David

---

### Post by Kilz on 2007-04-27
> **Goliath23 said:**
> 

**Do I need a 32 bit version of alsa-oss,** or is there something wrong with my dynamic linker configuration (ld.so)?

Any Ideas on this one?

Happy Summer,

David

If you do, [I made a package a that may help you. ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") Im not sure if it will help you, but its worth a shot.

---

### Post by Goliath23 on 2007-04-27
> **Kilz said:**
> If you do, [I made a package a that may help you. ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") Im not sure if it will help you, but its worth a shot.


Cool, thanks a lot, it seems you need the 32 bit alsa-oss package you made to make aoss work with 32 bit programs! The sound was sometimes a bit stuttering but thats a solution I can pretty much live with until Teamspeak 3 with alsa support is released! :)

Thanks again!

---

### Post by Kilz on 2007-04-27
> **Goliath23 said:**
> Cool, thanks a lot, it seems you need the 32 bit alsa-oss package you made to make aoss work with 32 bit programs! The sound was sometimes a bit stuttering but thats a solution I can pretty much live with until Teamspeak 3 with alsa support is released! :)

Thanks again!

Your welcome, I made it to make flash work with sound on the Firefox32 script I wrote. Glad it came in handy in another place.

---

### Post by dspari1 on 2007-05-08
> **Kilz said:**
> Your welcome, I made it to make flash work with sound on the Firefox32 script I wrote. Glad it came in handy in another place.

THANK YOU!!!!!!!!!!!!!!!!!!!

I honestly can't thank you enough for making this package, and it should be submitted into the repos.

---

### Post by dmcdante on 2007-05-19
your package is not working for me here (debian unstable) it keeps on giving me the same message, even though i changed aoss to go to right that file your package installs.
how did the ones who made it work do it?

---

### Post by Alpinist on 2007-07-13
This package is working for me, sort of.  I can now open Teamspeak in aoss and hear sound simultaneously with other applications.

But, now the microphone is not working in TS, it is just showing up muted.  

I can run TS without aoss and it works fine but then no sound from other programs.  Almost there if I can figure out the microphone with this package.  

Thanks for the package.  I did a lot of searching to try and figure out how to get aoss working for 32 bit apps on a 64 bit system.  This needs to be officially published.

---

### Post by L3oN on 2007-07-21
Hi,
I've downloaded package. installed it... but does not work!


This is my /etc/firefox/firefoxrc:```
# which /dev/dsp wrapper to use
FIREFOX_DSP="none"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See https://launchpad.net/bugs/29760.
```

I modified it to:
FIREFOX_DSP='aoss'

nothing changes....


Can you help me ?

---

### Post by Kilz on 2007-07-21
Exactly what application isnt working? What part of it? Do you have sound in other non related applications?

---

### Post by ves on 2007-08-11
> **Kilz said:**
> If you do, [I made a package a that may help you. ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") Im not sure if it will help you, but its worth a shot.

Thank you Kilz, that package was just what I needed to get teamspeak working with WoW.

---

### Post by Parallel on 2007-09-16
> **Kilz said:**
> If you do, [I made a package a that may help you. ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") Im not sure if it will help you, but its worth a shot.

You don't happen to have the source lying around somewhere?

---

### Post by Kilz on 2007-09-16
> **Parallel said:**
> You don't happen to have the source lying around somewhere?

Ididnt even use the source to make that package, its just a edited version of the i386 package from the Ubuntu repositories. I extracted the i386 deb and then used dpkg -b  to remake the deb.

---

### Post by Parallel on 2007-09-16
> **Kilz said:**
> Ididnt even use the source to make that package, its just a edited version of the i386 package from the Ubuntu repositories. I extracted the i386 deb and then used dpkg -b  to remake the deb.
Ah, thanks, got it working now :)

---

### Post by Tuho on 2007-11-27
> **Kilz said:**
> ...[I made a package a that may help you. ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") Im not sure if it will help you, but its worth a shot.
Did help indeed. I'm on amd64 gutsy and this was just what I needed to get teamspeak working with alsa.
Thank you.

---

### Post by John Jason Jordan on 2007-11-27
> **Kilz said:**
> If you do, [I made a package a that may help you. ]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb") Im not sure if it will help you, but its worth a shot.
Kilz,

I tried it but teamspeak is not what I was trying to fix. I have bluetooth audiophile headphones (Sony DR-BT50) that I love. Bluetooth on my Gutsy x86_64 laptop is working great, except for one app - RealPlayer. Every multimedia app I have plays to the headphones just fine as long as they are turned on before I launch the app, except RealPlayer. RealPlayer seems to be able to play only to the internal speakers or the headphone jack. Unfortunately, RealPlayer is the only app that can play certain radio streams. Plus, all the other audio apps have one thing or another that is annoying or doesn't work. I need my RealPlayer so as not to have to listen to local radio stations. I'm in the US, where over the air radio generally sucks, and during the Xmas season the suckage reaches unbearable levels.

I found out the other day that RealPlayer uses OSS, not ALSA. I have the alsa-oss compatibility app installed plus a bunch of other OSS stuff, but so far, nothing has resolved the issue. RealPlayer is 32-bit, so I was hoping your package would fix the problem. Sadly, it did not. :(

So thanks for giving me something to try, even if it didn't solve my problem. Any other suggestions welcome!

---

### Post by doorknob60 on 2008-05-31
Yay, thanks a lot for that package :) No I can play Runescape in 32 Bit Firefox and listen to Amarok at the same time :D

---

### Post by bapoumba on 2008-05-31
This thread is in the archived section of the forums. I'm closing here, feel free to start a new one in the support area. PM me with a link, so that I can include it in here for redirects. Thanks.

---

