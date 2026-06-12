---
title: "Problems with dvd playback"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by r0y4l on 2008-05-15
hi guys,

for some days I installed the brand new kubuntu 8.04-64bit to my Dell xps. After that I recognized that playing dvd's isn't possible anymore... With the 32bit system, everything worked fine.

Under 64bit I get the following error message with i.e. xine, I get the same errors when I try to play the dvd with mplayer or any other dvd player (but under 32bit systems, the dvd's works).

```

libdvdread: Elapsed time 0 
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x003a33c1 libdvdread: Elapsed time 0 
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003a33c6 libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x003a33c6)!! 
libdvdread: Elapsed time 1 
libdvdread: Found 11 VTS's 
libdvdread: Elapsed time 4  

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1526 *** 
*** for info_length % sizeof(uint32_t) == 0 ***

```

I don't know if it is really a 64bit issue, but i think so. Can anyone help how to fix this problem?

---

### Post by saru411 on 2008-05-15
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Medibuntu might help you with the dvd issue. Follow the Wiki's instructions for amd64/64 bit. Hope this helps

---

