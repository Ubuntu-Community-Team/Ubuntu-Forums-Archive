---
title: "Problem playing some avi files with mplayer on hardy"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by mtrainer on 2008-11-12
Hi,

I am getting the error:

xacodec: failed to dlopen /usr/lib/codecs/vid_iv41.xa while /usr/lib/codecs/vid_iv41.xa: cannot open shared object file: No such file or directory

opening some avi files.  Others work OK.  I  have the following installed:

mplayer 2:1.0~rc2-0ubuntu13+medibuntu1
libavcodec1d 3:0.cvs20070307-5ubuntu7.2
non-free-codecs 1.1
w64codecs 20071007-0medibuntu1

Anyone have a fix for this?

Thanks

Murray

---

### Post by mtrainer on 2008-11-13
> **mtrainer said:**
> Hi,

I am getting the error:

xacodec: failed to dlopen /usr/lib/codecs/vid_iv41.xa while /usr/lib/codecs/vid_iv41.xa: cannot open shared object file: No such file or directory

opening some avi files.  Others work OK.  I  have the following installed:

mplayer 2:1.0~rc2-0ubuntu13+medibuntu1
libavcodec1d 3:0.cvs20070307-5ubuntu7.2
non-free-codecs 1.1
w64codecs 20071007-0medibuntu1

Anyone have a fix for this?

Thanks

Murray

Surely someone else is having this issue?

---

### Post by xen-uno on 2008-11-13
Do you have a link to a host that has these problem avi's? I haven't run into any yet that have been problematic (but haven't played many either).

I do not have non-free*, libavcodec1d (but I do have libavcodec-unstripped-51), or w64* installed

---

### Post by andrew.46 on 2008-11-14
Hi mtrainer:

On my system this file exists as follows:

```
andrew@skamandros:~$ sudo find /usr -iname vid_iv41.xa
/usr/local/lib/codecs/vid_iv41.xa
```

Mind you I have installed the codecs manually from the [MPlayer site]("http://www.mplayerhq.hu/MPlayer/releases/codecs/").

  Andrew

---

