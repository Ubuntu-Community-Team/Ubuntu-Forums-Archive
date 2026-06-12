---
title: "Nvidia 8600gt driver issue"
date: 2008-12-06
forum: x86 64-bit Users
---

### Post by simmo2032 on 2008-12-06
Hi everyone,
I a newby so please forgive any ignorance as I try to learn Linux.

I just installed ubuntu yesterday and I cannot get the display to change from 800x600 or install the recommended driver 177.  I tried downloading the new 64bit package from nvidia but I have no clue how to install it.

Tried sudo sh Nvidia( pakage name)  tried sh Nvidia

always said cant open package???
If anyone is kind enough so help would be greatly appreciated.

I am using 8.10 with latest updates running now.

AMD64
2gig ram
Nvidia 8600gt

Simmo

---

### Post by rootsonwings on 2008-12-07
Experienced member can tell you how to install the downloaded package,

I have GeForce 9600, I went to the "Change Desktop Background" and "Visual Effects" and chose "Extras". It asked me confirm the download of the nvidia driver.

That was it.

In the mean time, Default driver should allow you to increase the resolution ..

---

### Post by Sef on 2008-12-07
> I just installed ubuntu yesterday and I cannot get the display to change from 800x600 or install the recommended driver 177. I tried downloading the new 64bit package from nvidia but I have no clue how to install it.

Have you tried System > Administration > Hardware Drivers?

---

### Post by garrettjrussell on 2009-01-07
I need to give this thread a bump because I'm completely lost as well.

8600gt, 8.10 gnome and have no idea how to get my drivers working correctly. I have tried both of your suggestions and nothing happens. I have searched far and wide on google for answers, but it seems like every forum has a different solution, thus making me even more confused.

I have absolutely no idea what's going on haha. I JUST switched to ubuntu today to take on a new challenge. This is seriously kicking my tail.

do I need to uninstall current drivers? How do I even do that? Through the packet manager I would assume, but trying to find anything in there is near impossible.

any help would be appreciated. I am a noob and totally lost.

---

### Post by garrettjrussell on 2009-01-07
actually, after going to "hardware drivers" and activating the 177 drivers, it installs them, then I reboot my computer when it tells me to. Upon loading I get this:

(EE)NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE)NVIDIA(0): ***Aborting***
(EE)Screen(s) found, but non have a usable configuration

---

### Post by garrettjrussell on 2009-01-07
bump

---

### Post by IQRules on 2009-01-07
Can you enter single user mode, rename xorg.conf file?
I used envyNG to fix my fx 1400 video card.

Do apt-get install envy packages and run application -> OTher -> envy gui, reboot.

---

### Post by garrettjrussell on 2009-01-07
I finally figured it out, a friend came and helped me, thanks.

---

### Post by rmarkle on 2009-04-18
Well given that almost everyone with an 8600GT has problems, could you enlighten us on how you resolved it?

:popcorn:

---

### Post by jespdj on 2009-04-18
> **rmarkle said:**
> Well given that almost everyone with an 8600GT has problems, could you enlighten us on how you resolved it?
Really? My desktop has a 8600 GTS, my laptop a 8600M GT and they both work without any problems with the normal nVidia drivers that you can install with System > Administration > Hardware Drivers. Works on Hardy, Intrepid and Jaunty without any problems. I don't think the nVidia 8600 is a difficult video card to get working.

---

### Post by pickboy87 on 2009-04-19
> **rmarkle said:**
> Well given that almost everyone with an 8600GT has problems, could you enlighten us on how you resolved it?

:popcorn:

That's odd, the only problems I've ever had with it was back in the 7.04 days. It absolutely hated my SLi setup with it. Try the envy tip, but in all honesty, I just installed the restricted driver when I turned on the various desktop effects in the Preferences menu. You could also try the newest version of Ubuntu and see if that fixes your troubles too.

---

### Post by Marlonsm on 2009-04-19
I also had some problems to install the driver for my 8600gt.

I've gone to System > Administration > Hardware drivers and clicked to install, but the download never got past 0%.
I've left that window open and came here to the forums to see if I could find something, I've found nothing that worked, and the download at still showing 0%.

I had to do something else, so I turned the computer off and went away. When I came back and turned the computer on, the driver was installed and working.

It seems that although the progress bar was stuck at 0% it was actually downloading and installing the driver.

---

### Post by BennyWhatever on 2009-04-19
Actually, I had that exact same issue... GeForce 8600GT, amd64, Intrepid.  For some reason, it just WOULDN'T install the 180 nvidia driver.  It worked perfectly with Hardy, but when I upgraded, I could never get it above the basic driver.  I tried everything humanly possible with the Xorg and everything... nothing.

I got fed up a few days ago and just did a fresh install (lost all my files on this partition, but nothing too useful, so it was okay), and used the Jaunty release candidate...
Problem COMPLETELY solved! :)

If you do it, make sure you do a fresh install, that way you can get the nice ext4.  It's super fast.

---

### Post by stchman on 2009-04-20
> **simmo2032 said:**
> Hi everyone,
I a newby so please forgive any ignorance as I try to learn Linux.

I just installed ubuntu yesterday and I cannot get the display to change from 800x600 or install the recommended driver 177.  I tried downloading the new 64bit package from nvidia but I have no clue how to install it.

Tried sudo sh Nvidia( pakage name)  tried sh Nvidia

always said cant open package???
If anyone is kind enough so help would be greatly appreciated.

I am using 8.10 with latest updates running now.

AMD64
2gig ram
Nvidia 8600gt

Simmo

Just activate the Nvidia driver in the Hardware Drivers.  Viola, Nvidia works!!!!!

---

### Post by stchman on 2009-04-20
> **jespdj said:**
> Really? My desktop has a 8600 GTS, my laptop a 8600M GT and they both work without any problems with the normal nVidia drivers that you can install with System > Administration > Hardware Drivers. Works on Hardy, Intrepid and Jaunty without any problems. I don't think the nVidia 8600 is a difficult video card to get working.

My 8800GT works like a top on Hardy 64 bit.

---

### Post by RedSingularity on 2009-04-20
> **stchman said:**
> Just activate the Nvidia driver in the Hardware Drivers.  Viola, Nvidia works!!!!!


Yeah thats all i had to do.....no problems.

---

### Post by stchman on 2009-04-20
> **Shadow121 said:**
> Yeah thats all i had to do.....no problems.

Why make things hard when in Ubuntu they are so easy.  Heck there is no need to use the terminal to get 3D rendering going.

---

### Post by RedSingularity on 2009-04-20
> **stchman said:**
> Why make things hard when in Ubuntu they are so easy.  Heck there is no need to use the terminal to get 3D rendering going.


I fully agree

---

### Post by BennyWhatever on 2009-04-20
> **stchman said:**
> Just activate the Nvidia driver in the Hardware Drivers.  Viola, Nvidia works!!!!!

Not so much.  I've done that 90 million times back when I used 8.10, and every time, when I restarted, it started in Safe Graphics Mode, so I had to revert back to the old settings.  It's a glitch that I've read to be very common with nvidia cards, and this one most importantly.
Like I said, I'm good now that I've updated to 9.04.  But with Intrepid, everything involving that graphics card and my graphics driver was completely snafu.  For the longest time I couldn't even go to the splash screen before my screen went black and got "no signal," so I finally figured out how to work on the xorg.

---

### Post by pickboy87 on 2009-04-21
> **BennyWhatever said:**
> Not so much.  I've done that 90 million times back when I used 8.10, and every time, when I restarted, it started in Safe Graphics Mode, so I had to revert back to the old settings.  It's a glitch that I've read to be very common with nvidia cards, and this one most importantly.
Like I said, I'm good now that I've updated to 9.04.  But with Intrepid, everything involving that graphics card and my graphics driver was completely snafu.  For the longest time I couldn't even go to the splash screen before my screen went black and got "no signal," so I finally figured out how to work on the xorg.

I used to have that problem (don't remember what version caused that...I believe all of them did that). I would install the restricted driver via the little pop-up, or by enabling Compiz-Fusion and when I would reboot, it would just be a black screen. I either had to reboot it once more, or try running it in safe mode and fixing the X config file via the repair option. I've noticed in Ubuntu or any other version of Linux for that matter, if something doesn't work, it will most likely work in the next release.

---

### Post by a2z on 2009-04-23
I"m still pretty green with Linux. I believe what got my 8600 working was the 180 driver in Ubuntu 8.10

---

