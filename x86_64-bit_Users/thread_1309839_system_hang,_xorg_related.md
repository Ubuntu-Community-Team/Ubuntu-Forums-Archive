---
title: "system hang, xorg related?"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by mechfly on 2009-11-01
Hi folks,

i am getting system hangs in which only the mouse movement is responsive, no keyboard or mouse clicks, and i am forced to hard boot. after a lot of searching, i think this may be related to one of the many xorg bugs that cause these errors. the only relevant kernel messages left (that correlate to the crash times) in syslog and dmesg is :

i2c adapter i2c: unable to read EDID block
i915 0000:00:2 HDMI Type AI: no EDID data  

what i know: i2c and i915 are graphics related hardware ( the laptop is a new HP G71, intel core2 and 4Gb RAM) so this is what really leads me to believe that its and xorg issue. i am reluctant to post a bug report yet, as the hardware is new and i don't completely understand what the problem is yet. 

note that this problem started with a 9.04 installation, and i thought originally it was a kernel bug and i was to wait for the release of karmic (a week later). i performed a fresh install with 9.10 and the system still locks up on non-regular intervals, with no trackable triggers that i can tell (has hung during any one of multiple tasks from Gimp to web browsing). removing graphic heavy themes and turning compiz off has made the hangs less frequent, but not removed them completely.

this may be related : my new computer purchase was instigated by the failure of my previous computer, in which i thought that the motherboard / CPU was going, as the desktop would lock up in much of the same fashion as my present system, throwing cpu errors to dmesg. this  computer has been reinstalled with server 9.04 with only ssh access and it has had no cpu problems or otherwise in the 10 days uptime.

any info is appreciated. btw i love karmic, its blazing fast on this computer!

---

### Post by whoop on 2009-11-01
> **mechfly said:**
> Hi folks,

i am getting system hangs in which only the mouse movement is responsive, no keyboard or mouse clicks, and i am forced to hard boot. after a lot of searching, i think this may be related to one of the many xorg bugs that cause these errors. the only relevant kernel messages left (that correlate to the crash times) in syslog and dmesg is :

i2c adapter i2c: unable to read EDID block
i915 0000:00:2 HDMI Type AI: no EDID data  

what i know: i2c and i915 are graphics related hardware ( the laptop is a new HP G71, intel core2 and 4Gb RAM) so this is what really leads me to believe that its and xorg issue. i am reluctant to post a bug report yet, as the hardware is new and i don't completely understand what the problem is yet. 

note that this problem started with a 9.04 installation, and i thought originally it was a kernel bug and i was to wait for the release of karmic (a week later). i performed a fresh install with 9.10 and the system still locks up on non-regular intervals, with no trackable triggers that i can tell (has hung during any one of multiple tasks from Gimp to web browsing). removing graphic heavy themes and turning compiz off has made the hangs less frequent, but not removed them completely.

this may be related : my new computer purchase was instigated by the failure of my previous computer, in which i thought that the motherboard / CPU was going, as the desktop would lock up in much of the same fashion as my present system, throwing cpu errors to dmesg. this  computer has been reinstalled with server 9.04 with only ssh access and it has had no cpu problems or otherwise in the 10 days uptime.

any info is appreciated. btw i love karmic, its blazing fast on this computer!

Have you tried restarting X, maybe that won't work cause keyboard doesn't work (but it also could be that the keyboard only seems to not work)

press Alt+PrtScr+k when your system fails and check if X can be restarted. Not that this really helps you allot but, if it restarts than it might be a xorg bug if it doesn't it might be a kernel bug.

On a side note: you don't need to completely understand what the problem is when posting a bug. Be as descriptive as possible, and keep an eye on the thread to see if troubleshooters need more information from you.

I have selected wrong packages in the past, and although it really helps to provide the right package, it is no shame if you make a mistake. In this case I would choose xorg or the kernel.

---

### Post by mechfly on 2009-11-01
thanks for the swift reply. i really do love this community. 

i can ssh into the locked up laptop, the subsystems seem fine. restarting the gdm doesnt do anything though. the keyboard is completely disabled, though i will try the keycombo you suggested just in case. apparently it locks up from the screensaver too, not that it surprises me at this point, lol.

thanks for the clarification on bug reporting. i will attend to that also now. 

...still open to more suggestions and questions...

---

### Post by whoop on 2009-11-01
> **mechfly said:**
> thanks for the swift reply. i really do love this community. 

i can ssh into the locked up laptop, the subsystems seem fine. restarting the gdm doesnt do anything though. the keyboard is completely disabled, though i will try the keycombo you suggested just in case. apparently it locks up from the screensaver too, not that it surprises me at this point, lol.

thanks for the clarification on bug reporting. i will attend to that also now. 

...still open to more suggestions and questions...

Really sounds like it's xorg.org

---

### Post by EnderTheThird on 2009-11-02
I'm not sure, but I think I'm experiencing similar results on both of my computers: my primary desktop and my MythTV server/frontend. It's very strange, and I'm not really sure what's causing it. At first I thought it might be an HDD failing on me, but it doesn't seem to do it when accessing one particular drive or another.  Did you make a bug report yet?

For reference, my specs for the desktop are:
MSI P6N SLi Platinum
Core 2 Duo E6600 @ 2.4GHz
6GB RAM
GeForce GTS 250
nvidia driver 190.42 w/ TwinView

---

### Post by adityadixit44 on 2009-11-12
I think I too have a similar problem, although I am using a far more primitive configuration. I have an old P-4 1.6 ghz with 1GB ram on a 915 motherboard. however, previous to karmic koala, everything was working extremely smoothly. Immediately after installing 9.10, i am getting absolutely random system hangs. so much so that i have not been able to shut down my computer properly for the last week or so. it hangs almost everytime if used for more than a few hours. no trigger could be identified. one minute its working nicely and the next it hangs. the mouse responds but no other thing does. I am sure this is software related because windows xp on the same machine works smoothly. I hope this bug or whatever it is is soon resolved because i am getting sick of backing up my data almost everyday.

---

### Post by whoop on 2009-11-12
> **EnderTheThird said:**
> I'm not sure, but I think I'm experiencing similar results on both of my computers: my primary desktop and my MythTV server/frontend. It's very strange, and I'm not really sure what's causing it. At first I thought it might be an HDD failing on me, but it doesn't seem to do it when accessing one particular drive or another.  Did you make a bug report yet?

For reference, my specs for the desktop are:
MSI P6N SLi Platinum
Core 2 Duo E6600 @ 2.4GHz
6GB RAM
GeForce GTS 250
nvidia driver 190.42 w/ TwinView

Maybe it's this one:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/413933](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/413933)

Hhhmm, but then you are using nvidia, so this might be the OP's bug, but probably not your problem.

---

