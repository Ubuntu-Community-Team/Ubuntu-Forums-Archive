---
title: "[SOLVED] no jack in wine (64bit?)"
date: 2007-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by stmiller on 2007-09-19
I am using the provided Feisty 64bit wine packages from winehq. There is no option for jack as an audio driver under the audio tab when I run winecfg. Can anyone else confirm this same problem? (You have to have libjack0.100.0-0 and jackd installed to get jack as an option.)

I'm trying to figure out if it is a problem of 32bit wine talking to 64bit jack, or perhaps the provided packages did not enable jack support when they were compiled. ?

---

### Post by stmiller on 2007-09-19
Ah, got a reply from the package maintainer:

> Actually it's because Ubuntu 64 bit doesn't have a 32 bit jack library
(ie, libjack is missing from the ia32-libs package).

I can't fix that without fixing the ia32-libs package itself, which
won't happen for Feisty.  Try alsa in the meantime.  Hopefully I can get
this (and the other missing 32 bit libs, like libssl) built into the
Gutsy ia32-libs package.

---

### Post by CheShA on 2007-11-29
ANy idea if this has been resolved? I still can't get Jack / wine working under Gutsy 64.

---

### Post by Cappy on 2007-11-29
Try installing getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and using the command
```
sudo getlibs -32 libjack.so.0
```

---

### Post by CheShA on 2007-11-29
Cheers for that cappy, still no dice though.  Have you actuallay got this working or were you just posting a possible solution from knowledge?

---

### Post by Cappy on 2007-11-30
> **CheShA said:**
> Cheers for that cappy, still no dice though.  Have you actuallay got this working or were you just posting a possible solution from knowledge?

I was just posting a possible solution based on the fact that it says you need that 32-bit library.

One last idea is that I didn't read it completely and there are some dependencies (mainly libc6 and lib32asound2!) I missed.
```
sudo apt-get install ia32-libs libc6-i386 lib32asound2 libjack0 libssl0.9.8
```

And it says "libssl" is missing also
```
sudo getlibs -32 libssl.so.0.9.8
```

With a lot of luck this might work. It says "other missing libs" so there might be more required.

If it doesn't, you might want to email the maintainer yourself and tell him you have [insert libraries you installed] but it won't work (getlibs drops the libraries, preserving the directories, into /usr/lib32 and run sudo ldconfig - since he might want to know) . You may have to use the i386 version of wine or some other kind of dark magic - but I wouldn't go to the trouble until I asked the maintainer first.

---

### Post by CheShA on 2007-11-30
Cool man, thanks for your time.  I'll have a look into that little lot after the weekend.

Thanks again!

---

