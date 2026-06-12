---
title: "Libdvdcss2/DVD playback"
date: 2006-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by shaundbrown on 2006-03-28
Help!!

I'm running an AMD athlon 3700+ with a Gig of ram, all very nice, and ubuntu runs at lightning speed.  Great.

I'm trying to sort out DVD playback.  I've setup dvdread3 and managed to create a folder full of bits of libdvdcss-1.2.5

I now need to make that work, I can't remember having such problems on the 32 bit version....:confused:

---

### Post by ehsan on 2006-03-28
According to [this wiki page]("http://wiki.ubuntu.com/RestrictedFormats"), you need to run the following commands to enable DVD playback using gstreamer on Breezy:

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

I have used these instructions, and the DVD playback works great.  I have also installed Xine and it can play DVDs as well.

Another approach is to setup a 32-bit chroot and install DVD playback support there, but I don't recommend it, since you can play DVDs in 64-bit mode just fine.

Ehsan

---

