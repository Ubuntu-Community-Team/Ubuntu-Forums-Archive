---
title: "nVidia nforce Networking Driver - ASUS - M2n-MX Board"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by metalspree on 2006-10-21
I just happened to install Daper Drake (kernel = 2.6.15.26). My Network Card doesnt seems to be detected at all. Its a nForce networking card based on 430/6100 chipset (Motherboard==ASUS M2N-MX AM2 board)  (Location 0 (NVNETBUS Id: 00070000-000). Could someone tell me how to fix the issue with the driver..or a step by step guidence on procuring & fixing up the driver. 

Regards,
Metalspree.

---

### Post by metalspree on 2006-10-24
well..no replies so far. Atleast lemme know how to activate forcedeth during start up.

---

### Post by obound on 2006-10-25
metalspree,

I have been grappling with this situation for the past week. First it was the onboard gigabit ethernet not getting detected. Then I downloaded the Nvidia driver and compiled it and installed it. Still no progress. So I started experimenting with noapic, noacpi, pci=routeirq etc. kernel boot parameters. I also tried to disable the paralell and serial ports in the bios and tried setting the PNP OS setting to No. It still does not work.

To top it all even my mouse is not detected now. The cursor is there but the mouse does not work. I'm hoping the new release scheduled for tomorrow will help out.

Regards
Kumar

---

### Post by yolanc on 2006-10-31
Same bug here, still no solution ?

---

### Post by canuda10 on 2006-10-31
I installed dapper and, with the kernel on the installation/live disc, network did not work (and sound had lots of problems), but simply upgrading to the latest dapper kernel solved all of it.
As an upgrade is impossible to do without networking, I had to download the upgraded kernel image .deb package and then simply transfer it to my dapper system and install it (for example simply double clicking on it launches gdebi).
From then on (after a restart) everything was working right.

---

### Post by obound on 2006-10-31
canuda10,

Which kernel version have you upgraded to? Did you do anything other than upgrading the kernel version?

Is this some light at the end of the tunnel!

-
Kumar

---

### Post by canuda10 on 2006-10-31
> **obound said:**
> canuda10,

Which kernel version have you upgraded to? Did you do anything other than upgrading the kernel version?

Is this some light at the end of the tunnel!

-
Kumar

I downloaded the latest one (I think it was linux-image-2.6.15-27-amd64-generic which can be downloaded from [http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-27-amd64-generic](http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-27-amd64-generic) )
Only this was needed, after installing this kernel network worked and everything could be upgraded accordingly.

---

### Post by metalspree on 2006-12-12
Wasn't happy with this board & its support. Had to give it up. Got back to my ASUS-A8N-E (DDR400) & things are back to life once again. 

Between - The kernel upgrade did no good...it still wasnt able to recognise my networking controller. (However FC6 did)

---

### Post by stevech on 2006-12-15
I am very happy with my ASUS M2N-MX, using an AMD 4200 AM2 dual core. PC6400 low latency memory. It is a very fast (for the money) PC.

As of this date, I looked at Linuxes out there for this new mobo with a new gig-e LAN interface  and so on... I loaded Fedora core 6 and it worked out of the box in terms of LAN and video. SUSE 10.2 loaded but no LAN and the video driver wound up silly-slow.
The other distros don't seem to be up to the same newness as Fedora 6. Xandros (one that I like especially) isn't.  Ubuntu would, I suppose, lag by 6 months or so.

I think these kernels are x.18.x


So, as is often the case with new hardware, you gotta wait.

ASUS has some linux drivers  for this mobo on their website.

---

### Post by Ian Campbell on 2006-12-21
I had the same problem.  I tried Debian Sarge and Opensuse 10.1 but they didn't get the networking to go either.  I finally gave up and stuck in an RTL8139 which was detected and worked straight off with Ubuntu Edgy.  Those cards always work well with Linux.  I did think about the 2.6.19 kernel which may have the driver but that would no doubt have introduced its own problems.

---

### Post by HeinBehrens on 2007-01-02
Installed Feisty all works except sound has some problems. Sounbd works except when I change volume in Alsamixer all sound stops.

Networking and Video no problem

---

### Post by betchern0t on 2007-01-05
Hi,
    support for the 430 chipset was added by nVidia to the 2.6.18 kernel so you need a kernel later than that one for it to recognise the ethernet card.

Cheers Paul

---

### Post by tiswas on 2007-11-16
oh woe is me,,,, well guys here it is,,, the nvidia onboard network card is CRAP it has problems in linux and windows too so to be honest better stick another network card in yer box,,, and forget even trying to get the onboard card to work :(:( if the manufacturers can't get it right why should we waste our time trying????

---

