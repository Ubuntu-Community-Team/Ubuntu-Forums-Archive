---
title: "Is Mac OS noisier than Linux?"
date: 2006-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by GreenCountry on 2006-02-08
Hey all,

Has anyone noticed that Mac OS on a Mac laptop runs the fans much more than Linux (or Ubuntu at least)?  I got kind of worried when I ran the Breezy liveCD on my Powerbook G4 1.33GHz, and after 15-20 minutes, the fan still didn't spin up.  When I rebooted back into OSX, the fan immediately came on, and not at it's lowest setting, but pretty high - like there was a danger of overheating...?

And I now have Breezy on a G3 iBook 500MHz - and the fans never run more than minimal speed.

?

---

### Post by butmunch on 2006-02-08
It'll be because of ACPI, an advanced power management standard implemented on most modern computers and laptops. It tells the fan when to spin, and the use of the LiveCD (are you sure it wasn't the cd drive making the noise? they're noisy) may have  prevented ACPI working properly.

---

### Post by GreenCountry on 2006-02-08
But what about the iBook I mentioned?  It's not running off liveCD (sorry I wasn't clear) - it's running a HDD installation of Breezy.

Still, no fans though.

And should I be worried?

---

### Post by macbuff on 2006-02-08
It depends on the individual Mac and what its doing.

I have two Mac laptops:

a 12" 867MHz G4 PowerBook (Panther 10.3.9)
and
a 15" 1.67GHz G4 PowerBook (Tiger 10.4.4)

My mate has a 12" 867MHz G4 PowerBook, and he has always commented that the fan on his system seems to be running most of the time.  But he runs the system flat out with a full screen brightness and the system is always clogged up with loads of running applications..  Its probably swapping like mad as well.

On my 12" it runs very cool, especially on batteries because I tend to run the system on lower CPU speed and with a screen brightness cut down.  The fan hardly ever kicks in..

On the 15" the auto screen brightness settings ensure that the screen is running full on whilst in a brightly lit office and since its plugged in the CPU also runs at full speed.  The fan does come on but its not on all the time.  When at home on batteries, the auto-brightness cuts the screen brightness right down and the CPU speed drops and the fan hardly ever comes on.

John

---

### Post by sonofcolin on 2006-02-08
Power management on the iBook G3 500 doesn't function correctly. This could be the reason you are not hearing the fans kick in (when they should). Sleep doesn't work either for this ibook and Breezy.

---

### Post by GreenCountry on 2006-02-08
Yeah, I was thinking that... I mean, that the fact that sleep doesn't function properly might be related to the fan not working.  Though, according to other threads, the sleep not working may not be a function of the power management in Breezy, but of the CD drive daemon.

The $300 question though is, is the iBook at risk of overheating?  Should I pass on the kernel compiling kind of stuff until Dapper comes out?  Even after pretty intensive operations, the fan on the iBook hasn't come on, and the case feels pretty hot especially on the underside.

---

### Post by sonofcolin on 2006-02-08
Yes, it gets hot. I decided to wait and see if this gets fixed in future updates.

---

### Post by ounas on 2006-02-08
I am sure it runs quiter on a miniMac, any comments?

-Ounas

---

### Post by ssam on 2006-02-08
on my 1ghz ti powerbook ubuntu does automatic speed stepping down to 667mhz. on mac os x you have to tell it which speed to run at. this could explain with linux runs cooler if you are not doing much.

on some machines though linux is not so good at powersaving or fan control so they run louder.

also linux is not so good at spinning down the hard drive. there seem to always be a process that want to write to disk.

---

