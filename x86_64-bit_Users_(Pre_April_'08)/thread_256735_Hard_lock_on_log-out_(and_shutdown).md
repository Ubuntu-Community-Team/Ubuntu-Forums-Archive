---
title: "Hard lock on log-out (and shutdown)"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by CaveMole on 2006-09-13
Whenever I try to log out, (or shutdown) from an Xsession,
my system locks, HARD.

This is my 3rd install attempt, and I got this behavior EVERY TIME,
eventually.  At least 2 of the installs worked.... for a while.
It might be something else I'm installing.  Google Earth?

Details at:
   [http://nmosug.org/admin-wiki/index.php/Ubuntu](http://nmosug.org/admin-wiki/index.php/Ubuntu)
   [http://nmosug.org/admin-wiki/index.php/3rd_Dapper_Drake_Install_Log](http://nmosug.org/admin-wiki/index.php/3rd_Dapper_Drake_Install_Log)

My best guess is that it is somewhere in Xorg (fglrx) or gdm.

Please advise...

---

### Post by CaveMole on 2006-09-13
I just (tried to) reboot.  It froze, as usual.
Went to recovery mode and removed gdm.

reboot.

I was able to startx, and then logout sucessfully.
Perhaps gdm was the problem.
Unfortunately I did startx again, this time it locked on logout.

So... GDM is looking less like the culprit.
More likely fglrx driver?

It seems to be 32-bit.  Is this an issue?

---

### Post by CaveMole on 2006-09-13
I was able to kill -9 the X server, and not lock.
GDM went back to the loging screen.

I think that in the past kill -TERM on the X server produced
a system lock.

Does that help?

---

### Post by kuja on 2006-09-13
My bets on fglrx. I had issues similar to that when using fglrx on my old computer (which is now my brothers). Locked up when I tried to switch vts, log out, reboot, shutdown, stuff like that. That computer however is using kdm, not gdm.

---

### Post by CaveMole on 2006-09-13
Another data point...

I tried to flip back to a console while in X, using
```
ctrl-alt-f1
```
That froze the machine too.

It is looking more and more like the fglrx driver.

Is fglrx the propriatary ATI driver?
Is there an equivalent Xorg driver?

---

### Post by italian_boy on 2006-09-13
I have the same problem (it happens with about 1/2 probability when I logout), I suspect it is related to the fglrx driver and xorg, not gdm.
Anyway, shutting down from a terminal is a good workaround while we wait (and hope) it is fixed.
I want to keep my high fps values, so for now fglrx and "sudo halt" :(

---

### Post by Kilz on 2006-09-13
After reading the links My guess is that he has radon express graphics and is running the dreadful,awful, worst ever, 8.25.18 drivers in the repositories that can cause crashes on exit with the onboard graphics. I know this from experence. The solution is to install the newest 8.28.8 drivers from ATI [with this howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

---

### Post by italian_boy on 2006-09-13
> **Kilz said:**
> After reading the links My guess is that he has radon express graphics and is running the dreadful,awful, worst ever, 8.25.18 drivers in the repositories that can cause crashes on exit with the onboard graphics. I know this from experence. The solution is to install the newest 8.28.8 drivers from ATI [with this howto.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

I tried installing 8.28.8 drivers and, as you say, it solved that shutdown problem /it only showed a strange multicolor background for a fraction of second before running normal usplash)

However, with 8.25 ubuntu version I get around 1500 fps with glxgears (fgl_[something] for me doesn't work) and I can run Google Earth etc...
with 8.28 I get 200 fps, Google Earth gives me an error... so I think hardware acceleration doesn't really work with that driver for my card (xpress 1100, which actually isn't supported), even if glxinfo says "direct rendering: Yes"

---

### Post by Kilz on 2006-09-13
> **italian_boy said:**
> I tried installing 8.28.8 drivers and, as you say, it solved that shutdown problem /it only showed a strange multicolor background for a fraction of second before running normal usplash)

However, with 8.25 ubuntu version I get around 1500 fps with glxgears (fgl_[something] for me doesn't work) and I can run Google Earth etc...
with 8.28 I get 200 fps, Google Earth gives me an error... so I think hardware acceleration doesn't really work with that driver for my card (xpress 1100, which actually isn't supported), even if glxinfo says "direct rendering: Yes"

Some people do have problems with acceleration with the 8.28.8 drivers. You can still get the [8.26.18]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run") drivers . 8.27.10 has issues, seems the even ones are the best. Then follow the same howto and you should get acceleration back.

---

### Post by kuja on 2006-09-13
Troublesome indeed. I know glxgears is not at all a benchmark, but even with my processor under the heaviest load imaginable (video encoding), I'm getting about 15,000fps from glxgears...

---

### Post by Kilz on 2006-09-13
> **kuja said:**
> Troublesome indeed. I know glxgears is not at all a benchmark, but even with my processor under the heaviest load imaginable (video encoding), I'm getting about 15,000fps from glxgears...

Id love to get that, but I have a radon express 200. It gets 1500 and im happy. Everything works, including windows games with cedega.

---

### Post by italian_boy on 2006-09-14
> **Kilz said:**
> Some people do have problems with acceleration with the 8.28.8 drivers. You can still get the [8.26.18]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.26.18-x86_64.run") drivers . 8.27.10 has issues, seems the even ones are the best. Then follow the same howto and you should get acceleration back.

Thanks Kilz, that version solved the problem: I get 3d acceleration and also stable shutdown from X session.
Perhaps we should post that in the sticky ATI topic... at least for me it worked.

---

### Post by CaveMole on 2006-09-14
I went to the 8.28.8 driver, and it did solve the stability problem.
My system did not lock up when I logged out.
I have not fully tested reboot or switch users yet.

Unfortunately, my frame rate on glxgears went from about 950 to 80.
I turned on the kernel frame buffer, tried again, and it got to 122.
Still pretty bad.

The part that really bugs me though is that Google Earth is now BROKEN.
It seems to hang in a CPU-burning (mostly system) continual loop with
the splash screen.

Any suggestions?

Perhaps I'll try a version between 8.25.18 and 8.28.8

---

### Post by CaveMole on 2006-09-14
8.28 would not run Google Earth, and crappy performance on glxgears.

8.26.18 is running 3D Accel fine.

Sounds like as of today, 8.26 is your best bet for an fglrx driver.

---

