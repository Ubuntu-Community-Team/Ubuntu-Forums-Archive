---
title: "vlc 0.8.4 breezy amd64 - SEG FAULT w/ DVD"
date: 2006-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by digitalsy on 2006-01-30
Well, for the life of my I CANNOT get vlc to play DVDS.  Yes, I've installed libdvdcss2 (1.2.5) and DVDs work PERFECTLY using totem-xine and gxine and all the other good stuff...but not using vlc. Here's what I get...


```

VLC media player 0.8.4-test1 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: THE_MATRIX_16X9LB_N_AMERICA
libdvdnav: DVD Serial Number: 27028BAA
libdvdnav: DVD Title (Alternative): THE_MATRIX_16X9LB_N_AMERICA
libdvdnav: Unable to find map file '/home/digi/.dvdnav/THE_MATRIX_16X9LB_N_AMERICA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00036f47
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00083f42
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00095b04
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00357b55
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
Segmentation fault

```

I even removed libdvdcss2 to see if that was the problem, but it crashes with a seg fault before even being able to tell me it's an encrypted stream.

this is an amd64 system.

Does anyone else have this problem? Have you gotten it to work? If so I'd really appreciate some help here, as I'd like to use vlc for all my media instead of switching between multiple apps.

Thanks!

---

### Post by digitalsy on 2006-01-30
Anyone? Someone using an amd64 system has got to be having the same issues...

---

### Post by 5ketcher on 2006-01-31
I do have the same problem :(

---

### Post by lemsto on 2006-02-08
i too can't play dvds trough "DVD (menus)" option but it works if i read it with "DVD"...

---

### Post by Elktro on 2007-10-24
Same problem! I want to use VLC because it has deinterlacing feature. :mad::mad: Argh so frustrating. Why anyone with expertise to solve this problem has not answered!? It seems pretty frequent problem.

---

