---
title: "Laptop crashes, kernel panic? fglrx ?"
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by wastedfluid on 2008-05-18
Hi guys.

Running Ubuntu 8.04 on an Acer 5100.. upgraded to 4gb of ram, decided to go with 64-bit.  So it's AMD 64Bit Turion 1.6ghz, 4gb of DDR2 5300 memory, and my video card is:  ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975].  Running Compiz, and Emerald.

My laptop is constantly crashing.  I have no idea, or where to look.  It's not a high load, or high temperatures.  I have logged/monitored it.  The typical crash looks like this:

[link] [http://www.sendspace.com/file/93w4pu](http://www.sendspace.com/file/93w4pu) [/link] 

Is that a kernel panic?  That's typically what happens.  Sometimes, it'll just lock up(turn black.. no screen, etc) and there will be nothing on the screen, and nothing will restart.. have to do hard restart(ie ctrl+alt+backspace don't work)

Some stuff I think might help..

> 
fluid@wasted:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size= 512MB: write-back, count=1
reg02: base=0xa0000000 (2560MB), size= 128MB: write-back, count=1
reg03: base=0xa8000000 (2688MB), size= 128MB: uncachable, count=1
fluid@wasted:~$ 


If i can't find a solution - I'll have to go back to 32-bit, and just run a whopping 4gb on 32-bit and see no extra pull from all the memory.

---

### Post by garyedwardjohnston on 2008-05-18
Don't give up on 64bit.  I think its a video card/driver issue.

Try Envy.

---

### Post by wastedfluid on 2008-05-18
> **garyedwardjohnston said:**
> Don't give up on 64bit.  I think its a video card/driver issue.

Try Envy.

I'll start digging into that.

Someone said it sounds like a memory issue.

I have 2x2gb sticks.. I tested each stick in slot 1, no errors through 2 complete test runs on each stick.

I'm running off 2gb for now.. to see if it crashes at all.  If it doesn't crash in the next day or so - it has to be a problem with the memory.


Envy appears to just be an automated install.  Do you really think Synaptics messed up installing fglrx?

---

### Post by wastedfluid on 2008-05-19
Update:

Someone suggested this was faulty memory.

I tested each stick(2x2gb) 4 passes each - single.. BOTH slots(16 total tests.. 8 per each stick)

Additionally, I ran 7 passes(24 hours!!!) for BOTH sticks in there.  0 errors all in all.  Memory is NOT faulty.

I'm testing it now- to see if the issue only happens with 4gb.. as I've thought all along, this appears to be a memory mapping issue IMO... with 4gb in there. 

Any ideas?  PLEASE?

EDIT:

I got home from work, computer was fine - launched firefox, played music in Amarok(uses pulseaudio) - and it crashed.  Music continued to play, screen was white.  did a hard shut off... TOok out one stick of 2gb, ran STRICTLY on 2gb instead of 4gb - within 2 minutes of turning on, playing music, and browsing.. it crashed again - this time, the screen went TOTALLY white..

Hope someone can help.

---

### Post by ASULutzy on 2008-05-19
The problem is with your mtrr tables.

I almost hate to even bring it up because of how much of a pain in the butt it is to mess with them.

(Note I'm not 100% sure of this, but a quick test to verify would be to change your xorg.conf to use "vesa" driver instead of "fglrx" and booting up with all 4 GB. If that works, then yea, probably mtrr)

I made a how to on the forums for it in the x86_64 forums, let me see if I can dig it up

---

### Post by ASULutzy on 2008-05-19
[http://ubuntuforums.org/showthread.php?t=743472](http://ubuntuforums.org/showthread.php?t=743472)

You can check that, but it's a tricky game from here on in.

---

### Post by wastedfluid on 2008-05-19
> **ASULutzy said:**
> [http://ubuntuforums.org/showthread.php?t=743472](http://ubuntuforums.org/showthread.php?t=743472)

You can check that, but it's a tricky game from here on in.

Thanks for the reply

Here is my MTRR with 4gb of ram;

> 
fluid@wasted:~$ cat /proc/mtrr
reg00: base=0x00000000 ( 0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size= 512MB: write-back, count=1
reg02: base=0xa0000000 (2560MB), size= 128MB: write-back, count=1
reg03: base=0xa8000000 (2688MB), size= 128MB: uncachable, count=1
fluid@wasted:~$ 


Here is my MTRR with 2gb of ram:

> 
fluid@wasted:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x78000000 (1920MB), size= 128MB: uncachable, count=1
fluid@wasted:~$ 



With 2gb of ram, it doesn't match your guide.. your guide shows uncacheable BEFORE the end of your memory..

Could you possibly assist me with this?  I'm afraid to work on it, because it doesn't match your problem.

P.S; it even crashed w/ 2gb of ram.  Is that still a memory mapping error?

Has this been submitted to launchpad?

Once again, thanks for your response!

---

### Post by ASULutzy on 2008-05-19
Oh, no, I think I misread your first post, my mistake. If you are unable to get fglrx working with even 2 GB of ram then this most likely has nothing to do with mtrr tables.

I'll reread your post and try and help out as much as I can

---

### Post by wastedfluid on 2008-05-19
> **ASULutzy said:**
> Oh, no, I think I misread your first post, my mistake. If you are unable to get fglrx working with even 2 GB of ram then this most likely has nothing to do with mtrr tables.

I'll reread your post and try and help out as much as I can

Thanks bro.

Yeah, fglrx works fine... it just crashes/freezes locks up.  I think it's a kernel panic - but I'm not sure.  I posted a video to what it normally does.. i got it on camera.  It happens *that* frequently.  Additionally, sometimes.. it just goes white(the entire screen)

Let me know if you have ANY ideas.  I'm almost about to give up on 64bit and go back to 32-bit.

---

### Post by markbuntu on 2008-05-19
What does fglrxinfo tell you?

I had a terrible time with 386i and my ATI 3650 so I switched to amd64 and the ONLY problem I have now is with that crappy beta firefox.

The problem with compiz is that it defaults to indirect rendering with the ATI driver because of a faulty call to GLX_pixmaps... This in turn puts all the compiz rendering on the cpu which can cause it to basically overheat and freak out. The problem can be compunded if fglrx is not properly installed and has defaulted to mesa for even more indirect rendering.

Try these simple tests from terminal
fglrx info; should say ATI, not mesa
fgl_glxgears should be >1000
glxgears should be about 4-5000
run the compiz benchmark
it will probably be about 40-60 which will cause time out problems.
if it is around 100, it is probably OK and you might really have some sort of low level memory allocation problem, faulty bios or something.


HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L

SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024

Ubuntu 8.04 "Hardy Heron" - Release amd64
Kernel Linux 2.6.24-16-generic
ATI Proprietary Linux Driver Version Identifier:8.47.3
Big Desktop, compiz, emerald

---

### Post by wastedfluid on 2008-05-19
> **markbuntu said:**
> What does fglrxinfo tell you?

I had a terrible time with 386i and my ATI 3650 so I switched to amd64 and the ONLY problem I have now is with that crappy beta firefox.

The problem with compiz is that it defaults to indirect rendering with the ATI driver because of a faulty call to GLX_pixmaps... This in turn puts all the compiz rendering on the cpu which can cause it to basically overheat and freak out. The problem can be compunded if fglrx is not properly installed and has defaulted to mesa for even more indirect rendering.

Try these simple tests from terminal
fglrx info; should say ATI, not mesa
fgl_glxgears should be >1000
glxgears should be about 4-5000
run the compiz benchmark
it will probably be about 40-60 which will cause time out problems.
if it is around 100, it is probably OK and you might really have some sort of low level memory allocation problem, faulty bios or something.


HP 1330n Media Center (modified)
ASUS A8AE-LE motherboard (OEM)
AMD Athlon64 3800+ 2.9GHZ 939 socket
3GB 3200 DDR RAM
ATI Radeon Express 200M (disabled in bios)
ATI HD3650 1GB DDR2  PCI Express
AC97 on board sound
Realtek 810L

SOYO 24 inch LCD wide screen monitor 1920x 1200
Samsung 930B 19 inch LCD 1280x1024

Ubuntu 8.04 "Hardy Heron" - Release amd64
Kernel Linux 2.6.24-16-generic
ATI Proprietary Linux Driver Version Identifier:8.47.3
Big Desktop, compiz, emerald

Compiz Benchmark gave me a solid 100+ fps.

> 
fluid@wasted:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
952 frames in 5.0 seconds = 190.400 FPS
983 frames in 5.0 seconds = 196.600 FPS
949 frames in 5.0 seconds = 189.800 FPS

fluid@wasted:~$ 


> 
fluid@wasted:~$ glxgears
4710 frames in 5.0 seconds = 941.953 FPS
4809 frames in 5.0 seconds = 961.746 FPS

fluid@wasted:~$ 



I'm too stupid to figure out fglrx info; what's the command for it?

I did buy new ram about a week ago, but I have ran so many memtest86's on it - only to remain baffled with 0 errors.

Please let me know!

Thanks so much!

---

### Post by wastedfluid on 2008-05-20
Ok, did a 32-bit install, too.

Compiz gives me 90 fps.

> 
fluid@wasted:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1010 frames in 5.0 seconds = 202.000 FPS
1159 frames in 5.0 seconds = 231.800 FPS
1130 frames in 5.0 seconds = 226.000 FPS

fluid@wasted:~$ glxgears
5011 frames in 5.0 seconds = 1002.092 FPS
5611 frames in 5.0 seconds = 1122.011 FPS
5586 frames in 5.0 seconds = 1116.659 FPS

fluid@wasted:~$ 



No crash yet in over 12 hours on 32 bit..

---

