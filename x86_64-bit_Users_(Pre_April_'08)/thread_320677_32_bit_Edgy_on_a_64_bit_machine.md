---
title: "32 bit Edgy on a 64 bit machine?"
date: 2006-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by TheVrolok on 2006-12-17
On my old laptop (compaq presario v5000) I was using 32bit edgy without a problem (once I got everything set up) but then I got a new laptop (acer aspire 5102 (Turion x2 64)) and I tried to put the 64 bit version on but it was just a nightmare.  A lot of hassle going to 64 bit it seems?  Basically, I was wondering about putting 32 bit edgy on this Acer and just using it like that, would there be any real drawbacks?  I'm currently using Windows and it's not like I'm running anything in 64 bit now anyway, nor am I really taking advantage of the dual cores.

---

### Post by Travisty on 2006-12-17
You can go either way with this. the 64 bit version would better utilize your CPU. The only problem is that most programs are still in 32 bit versions. So you'll find yourself still running in 32 bit mode despite having a 64 bit processor. 

There is also not a lot of driver support for hardware in the 64 bit version. I have been running 32 bit dapperand now edgy on my AMD X2 for this very reason. I would love to move over to the 64 bit version but the current lack of hardware and software support is not worth it yet. Who knows, maybe we'll be able to run complete 64 bit systems in 5 years.

---

### Post by Kilz on 2006-12-17
> **Travisty said:**
> You can go either way with this. the 64 bit version would better utilize your CPU. The only problem is that most programs are still in 32 bit versions. So you'll find yourself still running in 32 bit mode despite having a 64 bit processor. 

There is also not a lot of driver support for hardware in the 64 bit version. I have been running 32 bit dapperand now edgy on my AMD X2 for this very reason. I would love to move over to the 64 bit version but the current lack of hardware and software support is not worth it yet. Who knows, maybe we'll be able to run complete 64 bit systems in 5 years.

Thats a load of FUD. There is less than a 2% difference in available packages between the 64bit version and the 32bit one according to launchpad. Secondly the driver support is good. Granted there will be some people running hardware that have problems. But that is true of all versions of linux. There are some people with 64bit hardware that cant run 32bit because of hardware. 32bit is not the cure all some people make it out to be.

---

### Post by jvc26 on 2006-12-18
I wouldnt have said 'most' programs were still in 32bit for the ones I use on a regular basis they all seem to run fine with 64bit, and those which didnt such as wine I could just compile and sort out myself with stuff from the forums. Granted, I'm sure there are a few out there which wont work but I'd say they arent as common as you make out. Hardware problems seem to happen to everyone regardless of version and that depends entirely upon pc to pc.
Il

---

### Post by Travisty on 2006-12-20
I agree that 64 bit support has gotten better. I just don't think that it's ready for mass adoption on desktops. Now don't get me wrong. I'm all for it and fully support 64 bit ( hence why I have an AMD X2).  I was simply trying to say that TheVrolok has the option to run either the 32 bit version or the 64 bit and why I am running 32 bit right now.

---

### Post by Arabian on 2007-02-04
So what should we use for cflags for Turion64 X2 when we run it in 32 bits?

Regards,
-Arabian

---

### Post by green00guy on 2007-03-08
ok

---

### Post by sirbats on 2007-03-20
> **Travisty said:**
> I agree that 64 bit support has gotten better. I just don't think that it's ready for mass adoption on desktops. Now don't get me wrong. I'm all for it and fully support 64 bit ( hence why I have an AMD X2).  I was simply trying to say that TheVrolok has the option to run either the 32 bit version or the 64 bit and why I am running 32 bit right now.

I have Intel 64 bit desktop box, and Installed edgy-amd64, installation went well. But in my feeling the box run slow; firefox frequently crashes. I'm a manager in a shipping industry, used computer just for emailing, editing office documents, surfing internet, and common data base. I have bad experience with edgy_amd64 on intel 64 when doingcopy paste from hard-disk to portable disk. I can only get the folder and sub folder, 85% of file disappeared. Is the bug in nautilus? Then I wipe edgy-64 and install edgy-32; the box run faster and everything went flawlessly. My Linksys wusb54g work very well without tweaking in which can not work at all at edgy-64 even after compiling the driver (rt2570).

cheers up

---

### Post by chrisinator_Shuttle_XPC on 2007-03-23
Install AMD64, I did and I'm happy, you can "linux32" things, and I created a "chroot" environment. The other choice you have is to install both running 64 as your main, and run 32 as a partition, or vice versa.

---

### Post by wolffkrieger on 2007-09-28
I just got a new EM64T machine. I decided to install 64bit Feisty since I had the architecture to run in. Works great... with a few exeptions. Flash doesn't work on my firefox, however I found a way to install a 32bit version of firefox and when I need the flash I run the 64bit firefox. I'm willing to be flexible as long as I have my 64bit Ubuntu. :-D

ps. read the posts and search a bit on the web... solutions are all over the place...

---

### Post by jeremy1138 on 2007-10-22
I use 64 bit Ubuntu 6.04 on my hp dv5020us with the 64 bit amd turion processor without much in the way of problems.  The one problem I do have is that flash stuff just doesn't work right in Firefox.  I've been out of touch with Ubuntu for a while but flash has always been a problem for me.  The onther problem is my video card.  My laptop has an ATI Radeon Xpress 200M.  I guess this is like one of the worst cards a Linux user could have.  I just can't get 3d acceleration to work nor can I get any of Ubuntu's cool desktop effects to work.  I messed with it for weeks.  I've just updated to 7.10 so I'm hoping something will come up to fix it soon.  It appears right off the bat that it isn't going to work any better but I'm optomistic.  Anyway...  Yeah everything else seems to work fine on 64 bit Ubuntu.

---

