---
title: "Struggling with Ubuntu 8.04 - DVD movie playback?"
date: 2008-10-12
forum: x86 64-bit Users
---

### Post by khelben1979 on 2008-10-12
Hi.

I'm sitting here and struggling with Ubuntu 8.04 and I need help getting the ability to be able to view DVD:s over here.

I recently installed and configured libdvdcss and now I can watch DVD:s but the screen is flickering all the time.

What should I do?

(I get the same result with different movie players)

---

### Post by nikgare on 2008-10-12
Which graphic card do you have, and what graphic driver are you using?

---

### Post by khelben1979 on 2008-10-13
ATi Radeon 3200(256MB) integrated on a 64 bit ASUS F5Zseries laptop.

Driver version 8.53.4.

---

### Post by guyfromva on 2008-10-13
I'm having a similar problem- the DVD loads and I hear audio but just a blank screen. If I fast forward or go back I get a brief flicker of picture. 

I have updated the appropriate codecs, and the current ATI drivers. Is there something I'm missing?

---

### Post by nikgare on 2008-10-13
Does it flicker in all the movie players? 
(eg mplayer, ogle, realplayer(?), xine, vlc...)

---

### Post by khelben1979 on 2008-10-14
By installing nonfree codecs and all the packages which belonged to this I have managed to solve the problem.

---

### Post by Th3Professor on 2008-11-16
> **khelben1979 said:**
> By installing nonfree codecs and all the packages which belonged to this I have managed to solve the problem.

Could you share the steps you took to solve the problem? I followed the steps in the sticky on DVD playback and they aren't helping. Thanks.

---

### Post by khelben1979 on 2008-11-16
I just downloaded libdvdcss from [here]("http://download.videolan.org/pub/libdvdcss/").

Configured up and installed from source.

At the Mplayer homepage there is a codecs package to get also.

---

### Post by bash on 2008-11-16
If you screen flickering during video playback and an ATI graphics card using the fglrx driver be sure to set "Video output" to "X11" in your video player options. That should solve your problems.

---

