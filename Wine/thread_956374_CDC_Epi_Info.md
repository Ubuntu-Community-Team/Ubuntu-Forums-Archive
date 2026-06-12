---
title: "CDC Epi Info"
date: 2008-10-23
forum: Wine
---

### Post by Abaddon on 2008-10-23
Has anyone had any luck getting Epi Info to run on Ubuntu?

[http://www.cdc.gov/epiinfo/]("http://www.cdc.gov/epiinfo/")

I got an error while it was installing, and it seems to be rather flaky running.

Any ideas?   Or any linux alternatives?

---

### Post by irw on 2008-11-25
I have been running it under wine without problems - I just installed by ```
wine EpiInfoSetup3_5.exe
```
I ignored all the comments in the terminal window, it installed without problems.

My next problem is that a colleague has given me a load of data for Epi6 - the DOS version. I am downloading now, and will see if dosemu or something similar works.

---

### Post by t42e24t on 2008-11-27
Hallo irw,
I have been trying to get Epi Info to work (WINE) with Kubuntu Hardy for some time now, but have only succeeded to install the program (with some error messages), but have not been able to open an existing database or create any new forms etc.
I would be interested to hear some more detail as to how you managed and if you are able to create and open a database.
What version of WINE and OS are you running? Do you use it on a regular basis?
Have you modified your WINE install in any way or added some dll's etc..?

Many thanks

---

### Post by t42e24t on 2008-12-30
I have not managed yet to get a functional EpiInfo via WINE, but stumbled upon the following development for those that might have an interest : EpiInfo Community Edition...
There is also an UBUNTU release but it is still early days and not functional enough, yet.

[http://www.codeplex.com/EpiInfo](http://www.codeplex.com/EpiInfo)

---

### Post by t42e24t on 2009-07-31
It has finally happened!
Epi-Info 3.5.1 installed without error message and I could run my database .mnu without error.

System : Ubuntu 9.04 (32 bit)
I did the following:
Uninstall the standard wine that comes with ubuntu

Install newest version of wine (Wine 1.1.26) as described the following link [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

(At this point I installed Office 2007 - I am not sure if it also added some dll´s or components to make EpiInfo work...)

Download winetricks: 
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

Install jet40 through winetricks: 

sh winetricks jet40

Double click on EpiInfo installer and it installed without error.


Hope it is helpful

---

### Post by manishmahabir on 2009-09-11
Hurrah...it is now open-source!...and ubuntu compatible version has been released.
somebody please package it for Ubuntu
Here is the bug-report
[https://bugs.edge.launchpad.net/ubuntu/+bug/427996](https://bugs.edge.launchpad.net/ubuntu/+bug/427996)

---

### Post by ppetruzalek on 2010-05-18
Thanks for the info t42e24t, it worked on the first try!

---

### Post by kickurs on 2010-07-16
it did install without problem but i cant use statcalc, is it because it is a DOS?

---

