---
title: "mplayer32 woes"
date: 2006-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by mreams13 on 2006-10-30
I upgraded to edgy about an hour or two ago and something is bombing my mplayer32 install.

The failure it gives is:
$ mplayer32 gv.com.R6VDemo1HD_1280x720.wmv 
mplayer32: error while loading shared libraries: libaudio.so.2: cannot open shared object file: No such file or directory

I've got libaudio2 installed (but there doesn't seem to be a 32-bit version, ie: it's default install is to /usr/lib/libaudio.so.2.4).

Any ideas? Have I lost my mind?

Should it be looking for a /usr/lib32/libaudio.so.2.4 or is it the fact that there is no sym-link from libaudio.so.2 to libaudio.so.2.4?

---

### Post by fabertawe on 2006-10-30
How bizarre... I'd not noticed any problem playing wmv after upgrading to Edgy but after now trying to play from the command line with mplayer32 I get an 'error while loading shared libraries: libgnutls.so.13'. However, if I navigate to the same file (file://...) from my 32bit browser I can play it perfectly! :-k 

Paul

---

