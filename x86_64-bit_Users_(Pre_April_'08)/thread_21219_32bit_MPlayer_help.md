---
title: "32bit MPlayer help"
date: 2005-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tree on 2005-03-21
I've been searching for a guide about getting a 32bit MPlayer running on my amd64 system without chroot. Can anybody help me?

---

### Post by mips on 2005-03-21
Why dont you just install the 64bit version ???

add the following sources to your  /etc/apt/sources.list

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

and intsall mplayer64 from synaptic


cheers
mips

---

### Post by Tree on 2005-03-21
There is an issue with the 64-bit MPlayer preventing me from hearing audio in a certain video file I have. I talked to someone else and they said they got around it by using a 32-bit MPlayer(no chroot involved), but they were running Gentoo. I found a guide [here](http://forums.gentoo.org/viewtopic.php?t=250235.)  but it was for Gentoo... I suppose I could try it for Ubuntu. Does anybody know where I can get an rpm2targz package?

edit: I found rpm2targz and used that guide and now the audio works in the video file I was having trouble with. Does anybody know of a better way than this, though? Thank you

---

### Post by wmcbrine on 2005-03-21
[QUOTE=mips]Why dont you just install the 64bit version ???
[/quote]
Presumably because it doesn't work with (closed-source) 32-bit libraries, like the Win32 codecs or the RealPlayer libs.

---

### Post by Tree on 2005-03-22
Actually, that wasn't my reasoning. There seems to be a problem with MPlayer using FAAD on 64-bit. I'm unable to hear audio from a video file that has AAC audio during playback. I've tried recompiling with different options to no avail. Then someone told me they had the same issue, and recommended I try 32-bit MPlayer, and that seems to have solved it.

---

### Post by blinksilver on 2005-03-22
i noticed that two, interesting, i did not know it had to do with FAAD though

---

### Post by X3N on 2005-04-08
I've noticed a few problems with the 64bit version. Mplayer haven't released a proper 64 bit version with all the codecs yet from what i can tell, mostly because they are wrapped up in legal problems with patents and such :(

---

### Post by c_dog on 2005-04-09
Or the fact the most of the win32 codecs are binary rips from Windows with no source available. Maybe now that Windows XP 64 has gone gold we'll see some win64 codecs for those things we'll never see the code for.

---

### Post by X3N on 2005-04-12
I don't know quite how, but i seem to be able to play win32 formatted files such as .wmv in mplayer without any problem.

Mplayer version:

MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes

I also extracted from [http://www.mplayerhq.hu/homepage/design7/codecs.html](http://www.mplayerhq.hu/homepage/design7/codecs.html) the codecs into /usr/local/lib/codecs/

I've got the configure.log for it, its not pretty, if anyone wants a poke at it, just let me know. I didn't do anything special though so maybe its just this version that works.....

---

### Post by FluffyElmo on 2005-04-13
Do you have WM9 files working? I noticed that many of my wmv and avi files suddenly worked in MPlayer and Totem after an update a little while ago (~couple of weeks?). Any files encoded with the Windows Media 9 codec (and some other codecs) don't work, but the majority do.

I have to say I was *very* happy to see progress in this area :)

---

