---
title: "VLC , DVD movie don't work"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by JuanC on 2005-10-23
I try to play a DVD movie from VLC , but i get this :
> 
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Attempting to use device /dev/hdc mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/juan/.dvdnav/.map'


---

### Post by bored2k on 2005-10-23
You need to install libdvdcss2.
[http://download.videolan.org/pub/videolan/debian/pool/libdvdcss/1.2.8/](http://download.videolan.org/pub/videolan/debian/pool/libdvdcss/1.2.8/)

---

### Post by JuanC on 2005-10-24
[QUOTE=bored2k]You need to install libdvdcss2.
[http://download.videolan.org/pub/videolan/debian/pool/libdvdcss/1.2.8/](http://download.videolan.org/pub/videolan/debian/pool/libdvdcss/1.2.8/)
[/QUOTE]
Thanks for your reply , but i don't see an AMD64 package for libdvdcss2.

---

### Post by Perfect Storm on 2005-10-24
here if you need it  AMD64 package [http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)
If it's okay it's v1.2.5

---

### Post by RAOF on 2005-10-24
I believe that the install-css script will do all the hard work for you.
Just run:
```
/usr/share/doc/libdvdread3/examples/install-css.sh
```
from a console.

EDIT: Oh, you'll need some packages for that - it compiles it from source.  You'll need at least build-essential, and possibly other things.

---

### Post by JuanC on 2005-10-24
I try it but VLC still don't work
> 
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000135
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000f45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000f82
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001fb8bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001fb8e2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002142ef
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00216f31
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0021e5c8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0021e600
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0


---

### Post by JuanC on 2005-10-27
Anyone knows what's the problem with VLC and DVD movie?

---

### Post by BoyOfDestiny on 2005-10-30
[QUOTE=JuanC]Anyone knows what's the problem with VLC and DVD movie?[/QUOTE]

Yes, nothing. Ubuntu does not include support for libdvdcss (it is GPL'd). It conflicts with things like the DMCA, so they could be held legally responsible.

In short, you cannot play a DVD you own if it has CSS without installing this library. That's the sad truth

---

### Post by Mevsthevoices on 2007-12-05
I got the same feed back but I managed to get VLC to work perfectly
I got mine to work, if the script doesn't exist and you are using gutsy/feisty use
$ sudo /usr/share/doc/libdvdread3/install-css.sh
Then open DVD using
$wxvlc dvd:///dev/cdrom
for some reason or another the command
$wxvlc /media/cdrom0
Comes up with the same errors displayed before

---

### Post by Perfect Storm on 2007-12-05
Please check the date of the thread before posting....


Thread closed.

---

