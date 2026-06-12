---
title: "3D games crash on AMD 64 system"
date: 2006-10-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by kpeil on 2006-10-06
I've just upgraded from an Athlon XP (32 bit) to an Athlon 64 X2 3800+
Mainboard is Asus M2N-E (0304 bios)
Video is GeForce 7300 LE (Inno)
Ram 1GB Corsair Value (so single channel)

Problem:
3D games I've tried crash. I've tried Quake3, UT2004, Bzflag, Neverball, Neverputt.
They all start up and look as if they're going to work. After a few seconds (it varies) the keyboard and mouse cease to work and mostly the box reboots.
Not good. Sometimes I have to reach for the reset button.
Any ideas anybody?
Neil

---

### Post by xstaticxgpx on 2006-10-06
are you video card drivers functioning? sounds like a opengl issue, and did the games work before you upgraded cpu's? do you have the correct kernel from the package manager installed?

---

### Post by kpeil on 2006-10-06
Im sorry to see I missed an important point!
I've tried with 3 installations 

1. Dapper amd64
2. Dapper i386
3. My old installation of Dapper (i386) but running the K7 SMP kernel

All 3 seem to react the same to 3D games.

Neil

---

### Post by xstaticxgpx on 2006-10-06
perhaps its a hardware issue, most likey ram or video... if you have any backup ram or a back up videocard try them to see if they react the same. Also can you post the reply of uname -r?

---

### Post by kpeil on 2006-10-06
uname -r gives 2.6.15-27-k7 at the moment - as I noted in my 2nd post I have 3 installations which seem to give the same result.


In answer to your first reply these games were all working on the old system.
The nvidia drivers were installed with synaptic and according to lsmod are loaded.

Neil

---

### Post by xstaticxgpx on 2006-10-06
k7 = 32bit, thats probably your issue. I would go into synaptic package manager, uninstall the k7 kernel (leaving the generic 64bit kernel) and then install the k8 kernel. 

or just do these commands:

> sudo apt-get install linux-amd64-generic

then

> sudo apt-get install linux-amd64-k8

this will install the amd64-k8 restricted modules and image package. I would also get the amd64-k8 headers as well, but thats just me.

> sudo apt-get install linux-headers-amd64-generic

and then

> sudo apt-get install linux-headers-amd64-k8

a reboot is required after doing the commands, hope this helps!

---

### Post by kpeil on 2006-10-06
As I said I have 3 installations one of which is using the 64 bit kernel you suggest installing - there is no improvement with this kernel.

---

### Post by kleeman on 2006-10-06
Sounds like a nvidia driver issue to me. Try asking on the nvidia board:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)
 and possibly lodging a bugreport (they have instructions about what they want)

---

### Post by kpeil on 2006-10-07
As good and bad luck would have it I have the answer.
After my last post I rebooted and the box came up with "no signal" on the monitor. Couldn't get it to work at all. Borrowed another card and tried that on DVI - same result. Not good. Tried an analog monitor and it booted and although the video was not set really well I could use things. Tried some 3D games. They worked perfectly! 
So. Tried my own monitor (Viewsonic VX2025wm) on analog and that worked, too.
So my monitor seemed to work on analog but not DVI anymore. Bad. Gave it another try on DVI, and it worked. Great.
Seems like I have a dodgy card which screwed up my monitor for a while. Running it on analog seemed to reset it. Now I have to go to the shop and change the card. Had it less than 7 days so should be no problem.
Thanks to all who took the time to consider my problem.
Neil

---

