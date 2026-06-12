---
title: "[SOLVED] I need something in amd64 but..."
date: 2007-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Amazona aestiva on 2007-10-02
So there is a software in x86 RPM. There isn't any way to convert it to amd64, is it?
I used alien, but I would like to move on a amd64 Gutsy.

About the software:
It is like a driver in windows so it has no alternatives. (as I know)

---

### Post by Unterseeboot_234 on 2007-10-02
Look in on this Forum discussion. 

[Virtual Box]("http://ubuntuforums.org/showthread.php?t=565553")

I've tried VMserver (another product), but I didn't like the performance hit on my AMD64. VirtualBox is in the apt downloads. I would consider VitrualBox if I need a USB connect for video. (I use Firewire, and Linux Kino)

---

### Post by John.Michael.Kane on 2007-10-02
> **Amazona aestiva said:**
> So there is a software in x86 RPM. There isn't any way to convert it to amd64, is it?
I used alien, but I would like to move on a amd64 Gutsy.

About the software:
It is like a driver in windows so it has no alternatives. (as I know)

You might garner better answers, If you provided the name of said program/driver etc.

---

### Post by Amazona aestiva on 2007-10-02
> **SD-Plissken said:**
> You might garner better answers, If you provided the name of said program/driver etc.

Sorry... [Here]("http://ubuntuforums.org/showthread.php?p=3391837#post3391837") you are.

---

### Post by Amazona aestiva on 2007-10-02
> **Unterseeboot_234 said:**
> Look in on this Forum discussion. 

[Virtual Box]("http://ubuntuforums.org/showthread.php?t=565553")

I've tried VMserver (another product), but I didn't like the performance hit on my AMD64. VirtualBox is in the apt downloads. I would consider VitrualBox if I need a USB connect for video. (I use Firewire, and Linux Kino)

I use Virtualbox, but I don't want to. I use Kino too.

---

### Post by John.Michael.Kane on 2007-10-02
Heres how one person set up that printer.
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

Also for reference heres a report/question filed on this printer.[https://answers.launchpad.net/ubuntu/+question/3742](https://answers.launchpad.net/ubuntu/+question/3742)

As for converting it you would have to find out what the dependencies are if any, and install those. 

IMHO looking at all the info available on this printer it's a headache to say the least , I would say the above method is your best shot. Till native Linux drivers are made or you find a printer with those features with out of the box Linux support.

In the end your printer may be the hold back to you moving to 64bit completely.

---

### Post by arvevans on 2007-10-02
I too run an AMD X2-64 3200 CPU and motherboard.  After a month of fighting with 64-bit software I gave up and reloaded Fiesty 32-bit version.  Both CPUs still run, but now at 32 bits instead of 64, with no noticeable slowdown.

I tried re-compiling from source for several of the 32 bit app's that were not available for 64-bit but after hours of searching for required libraries it became obvious that the easiest route was to just to  run at 32 bits for now.  Maybe later I will switch back to 64 but not now.

I very recently did an on-line upgrade from Fiesty to Gutsy and had only minor problems with the change, none of which related to using a 32 bit OS on my 64-bit machine.

Arv
_._

---

### Post by Amazona aestiva on 2007-10-02
> **SD-Plissken said:**
> Heres how one person set up that printer.
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

Also for reference heres a report/question filed on this printer.[https://answers.launchpad.net/ubuntu/+question/3742](https://answers.launchpad.net/ubuntu/+question/3742)

As for converting it you would have to find out what the dependencies are if any, and install those. 

IMHO looking at all the info available on this printer it's a headache to say the least , I would say the above method is your best shot. Till native Linux drivers are made or you find a printer with those features with out of the box Linux support.

In the end your printer may be the hold back to you moving to 64bit completely.

Unfortunately this isn't new for me.:( I've used this with succeed. But the RPMs are for i386 or whatever... The question is still: How can I make it run under amd64?:confused::confused::confused:

---

### Post by Amazona aestiva on 2007-10-19
I'll stay with x86 now.

Thanks anyway.

---

