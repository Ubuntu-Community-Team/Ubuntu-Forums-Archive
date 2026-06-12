---
title: "Hardware not supported, please help make it work in 8.10"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by BigIslandVegan on 2008-09-03
My friend recently acquired a new ASUS M51TA-X2 and it simply doesn't work with any non-Windows operating system we have tried so far...

Ubuntu 8.04 (both 32 and 64 bit, and the alternate disk), Novell Suse Linux Enterprise Desktop 10, OpenSuse 11, Fedora 10 Alpha x86_64, Fedora 9 x86_64, Mandriva Linux One 2008 Spring, PC-BSD 7 x86-BETA1, probably among others.

ASUS M51 Series M51TA-X2 NoteBook AMD Turion X2 Ultra ZM-82(2.20GHz) 15.4" Wide XGA+ 4GB Memory 250GB HDD 5400rpm DVD Super Multi ATI Mobility Radeon HD 3650

from newegg.com

ASUS tech support says the chipset is:

AMD M780G (ATI RS780MN without Macrovision +SB700)

One of the customers / reviewers on newegg.com says:

"...Also this macine has two GPUs the one metioned above the other an integrated Radeon X3200 that can be enabled in place of the X3650 for better battery life."

which I find to be curious and interesting.

Additionally, this system has something ASUS calls "Express Gate" or "Splashtop" by the developer of this small, fast loading linux installation that allows quick access to flash enabled web browsing, skype, etc.

[http://www.splashtop.com](http://www.splashtop.com)

So, the system must be functional with linux in some way, somehow...but how?

I would appreciate your help in making 8.04 or the upcoming 8.10 an option for us.

Aloha

---

### Post by soxs on 2008-09-04
Splashtop sucks, it is pimped with restricted drivers and stuff you will _NEVER_ get freely availiable.
If they would open up spashtop, you would have minor chance for 9.04 to get it supported.
Your may contact asus and or linux devs

---

### Post by Sef on 2008-09-04
> Hardware not supported, please help make it work in 8.10

Download the [Intrepid Ibex Live CD]("http://cdimage.ubuntu.com/daily/current/"), which is still alpha, and see if it works.  If it does, then likely it will work when it becomes stable at the end of October.

---

### Post by slavokrivak on 2008-09-16
i have the same notebook , and  8.10 alpha does not work , the problem is acpi , it can boot corectly only without acpi but using notebbok without acpi is not good idea

is there any chance that 9.04 will work , are there plans for new acpi modules in kernel 2.6.28 ?

---

### Post by BigIslandVegan on 2008-09-17
We have tried the latest Ibex Alpha and it didn't work, just a blank display a few moments into booting.:confused:

We have spent at least 3 weeks on this computer and many hours trying to get *any* non-Windows operating system to work. No success thus far.

---

### Post by Sef on 2008-09-18
> We have tried the latest Ibex Alpha and it didn't work, just a blank display a few moments into booting.:confused:

We have spent at least 3 weeks on this computer and many hours trying to get *any* non-Windows operating system to work. No success thus far.

Sometimes, the only solution is to get new hardware that is GNU/Linux compatible.

---

### Post by BigIslandVegan on 2008-09-19
My objective was to get something energy efficient and affordable.

The Turion Ultra seems to have a good balance of these points.

It's an all AMD system...I figured that would be good with Ubuntu.

There is some way to make this work...just haven't connected with the right solution yet.

---

