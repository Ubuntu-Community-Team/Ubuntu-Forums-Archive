---
title: "WMV9 Codec"
date: 2007-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by beanzapper on 2007-10-16
Harro,

I'm trying to get .wmv file to play, but to no avail, I can't get it to work.  I've read that it isn't possible to play WMV9's on 64bit Ubuntu, is this true? If not, can anyone help me get this set up?

I've installed w64codecs and ffmpg, didn't seem to do it for me though.

-Thanks

---

### Post by Case_f on 2007-10-16
Mplayer can play WMV9 files natively even on x64 for some time now (well, at least most of them).

---

### Post by stmiller on 2007-10-16
VLC can also play any WMV9 content, including live streams.

---

### Post by Jouke74 on 2007-10-16
It seems to be going  ok with just the VLC player installed without any additional codecs like w64codecs. After I installed w64codecs, they did more harm than good on my system.

---

### Post by Kilz on 2007-10-16
I would like to know exactly what wmv files. are we sure that they are wmv9 and not wmv10 ? Also what version of Ubuntu are you running?

---

### Post by beanzapper on 2007-10-16
I'm running 7.04, and under Properties>Video>Codec it states that it uses WMV9.

I have made some progress by installing VLC and removing w64codecs - I now get video, but no sound.

-Thanks for teh replies :KS

EDIT: Same goes for mplayer, no sound.

---

### Post by FredB on 2007-10-17
WMV is a *crappy* format by concept. My computer nearly read them all. I just installed all gstreamer plugins using ubuntu-restricted-extras + vlc + mplayer 1.0rc1 which can read wmv9 out of the box without any codecs.

But you can find bad wmv9 file on the web, or worse, DRMed ones :(

---

### Post by Kilz on 2007-10-17
> **beanzapper said:**
> I'm running 7.04, and under Properties>Video>Codec it states that it uses WMV9.

I have made some progress by installing VLC and removing w64codecs - I now get video, but no sound.

-Thanks for teh replies :KS

EDIT: Same goes for mplayer, no sound.

Do you have sound in other formats/applications?

---

### Post by beanzapper on 2007-10-17
> **FredB said:**
> WMV is a *crappy* format by concept. My computer nearly read them all. I just installed all gstreamer plugins using ubuntu-restricted-extras + vlc + mplayer 1.0rc1 which can read wmv9 out of the box without any codecs.

But you can find bad wmv9 file on the web, or worse, DRMed ones :(

I already have those installed :(

And yes, I hear sound when I watch vids on youtube etc.

I'm testing this codec on [ftp://ftp.funcom.com/media/Age_of_Conan/videos/cgTrailer/blur_trailer720P.wmv](ftp://ftp.funcom.com/media/Age_of_Conan/videos/cgTrailer/blur_trailer720P.wmv) if you want to try it on your box.

---

### Post by Kilz on 2007-10-17
> **beanzapper said:**
> I already have those installed :(

And yes, I hear sound when I watch vids on youtube etc.

I'm testing this codec on [ftp://ftp.funcom.com/media/Age_of_Conan/videos/cgTrailer/blur_trailer720P.wmv](ftp://ftp.funcom.com/media/Age_of_Conan/videos/cgTrailer/blur_trailer720P.wmv) if you want to try it on your box.

My system playes wmv with sound.[ Here is an example of a wmv9 file that works.]("http://louisacounty.va.schoolwebpages.com/education/components/docmgr/default.php?sectiondetailid=7972&fileitem=5438&catfilter=ALL") But the wmv9 file you link to does not have any sound on my system.

---

### Post by FredB on 2007-10-17
I got a codec error in mplayer. And no sound with vlc. Crappy file or what ?

---

### Post by beanzapper on 2007-10-17
Idk, I got the file I linked to play on winblows.

I can play the file Kilz linked fine w/ sound though. Problem solved I suppose.

-Thanks everyone.

---

### Post by Kilz on 2007-10-17
> **beanzapper said:**
> Idk, I got the file I linked to play on winblows.

I can play the file Kilz linked fine w/ sound though. Problem solved I suppose.

-Thanks everyone.

Sadly Microsoft changes things and make it harder for linux to use formats. Its all part of vendor lock in. Some wmv9 files have drm that isnt playable in linux..... yet.

---

