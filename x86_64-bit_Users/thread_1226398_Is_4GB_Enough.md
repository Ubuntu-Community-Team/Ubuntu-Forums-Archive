---
title: "Is 4GB Enough?"
date: 2009-07-29
forum: x86 64-bit Users
---

### Post by david35580 on 2009-07-29
Hi all,
I'm planning a new build using a Phenom 9650 and ASUS Mobo.
I have purchased 4GB of RAM for it and suddenly had the idea (after reading this forum) that it would be nice to start my Linux computer life by diving straight into X64 Ubuntu.

Is 4GB of RAM realistically enough for good performance though?
I don't do anything like video editing, but will need to run a virtual machine with XP for my son's games. They wouldn't thank me if they couldn't play COD 4, 5 or 6 - out soon I'm told.
Wine might do at a pinch, I suppose.
Thanks,
David

---

### Post by nmaster on 2009-07-29
4GB is probably more than enough.  I have 3GB and everything is great.

---

### Post by Kulshrax on 2009-07-29
4Gb of RAM is more than enough to run Ubuntu, and well beyond what you would need for good performance. Ubuntu will run just fine on most new hardware.

Rather than using a virtual machine to run XP, I recommend setting up a dual boot with Ubuntu and XP. That way, you would be able to run Ubuntu while still having XP for running you son's games. A virtual machine is not an ideal environment for gaming, and would lead to decreased performance. A dual boot setup makes more sense for gaming.

---

### Post by david35580 on 2009-07-29
Thanks for the replies everyone.
I wanted to avoid a dual boot if possible as it seems less committed and it would be tempting to simply use XP and just tinker on Ubuntu. I need to be forced onto that Terminal by necessity, not leisure.

Also the hard disk becomes very complicated - my dual-boot laptop has six (or is it eight?) partitions and only 2 of them are for Windows. I've no idea what some are for, even.
However, I'll keep the idea in reserve - thanks.
David

---

### Post by PatrickVogeli on 2009-07-29
I don't think you will be able to play any COD game in a virtual machine. Direct X and 3 acceleration in Virtual Machines is still in very early stages, so you'd better forget about it.

---

### Post by Raffles10 on 2009-07-29
I run Ubuntu with 2gb RAM, according to htop I'm never using more the 500mb. I can play Neverwinter Nights with no issues or loss of performance. :D

---

### Post by david35580 on 2009-07-30
Any thoughts on COD in Wine on a X64 machine?
David

---

### Post by ericab on 2009-07-30
8gb headless server ftw!

---

### Post by david35580 on 2009-07-30
Can someone decifer that last reply please?

'8GB headless server ftw!' means nothing to me - sorry.

Bit too cryptic for a newbie.
Thanks,
David

---

### Post by itsamebuddich on 2009-07-30
I don't know what EricaB is saying, as he is probably a noobie himself, but use Wine for smaller, everyday applications, web browsing, word processing, email, if you prefer to use programs made for Windows (98, ME, XP, Vista, etc.), but for gaming, you really want to dual-boot into Windows.

P.S.  For the type of computing you do, 4GB is more than enough.

---

### Post by Nburnes on 2009-07-30
Idk how much good this will do you but up until today I was running Ubuntu 64 bit on 2GB of RAM and it performed flawlessly.

---

### Post by ericab on 2009-07-31
> **itsamebuddich said:**
> I don't know what EricaB is saying, as he is probably a noobie himself, but use Wine for smaller, everyday applications, web browsing, word processing, email, if you prefer to use programs made for Windows (98, ME, XP, Vista, etc.), but for gaming, you really want to dual-boot into Windows.

P.S.  For the type of computing you do, 4GB is more than enough.

actually not a newbie, but good try.
point is, the best upgrade you can give to your computer is more ram; so give it as much ram as possible right off the bat.
can you decipher that ?

---

### Post by xebian on 2009-07-31
Yes more the better.  4g of ram is about $50?  Newer Mobo support 16G.  

I think what he can't decipher is 'FTW' which means 'for the win':P

---

### Post by brayden13 on 2009-07-31
4GB is enough to have Ubuntu itself running and a Windows XP virtual machine. Games in a virtual machine don't do well, also if you are getting ubuntu 64-bit make sure your processsor is 64-bit. I got ubuntu 64-bit with 6GB of DDR3 and it works flawlessly. 2GB less than that would do just about as good. also if you want good performance on a game like COD make sure you have a good graphics card and half decent processor, as RAM isn't the universal upgrade to make everything faster. It does reach it's limit where it is as fast as possible and couldn't get any faster unless an upgrade for CPU or GPU.

---

### Post by david35580 on 2009-07-31
Thanks everyone.
Really grateful for all the replies.
I think I'll go for X64 and make the boys a separate, whizzy Windows machine for their games - I might get more of a look-in on my own computer then.
David
'For the win', eh? 
I must get out more.

---

### Post by coogur on 2009-07-31
YES!!  In Windows, applications get a maximum of 2GB of virtual memory.  It is possible to increase this value to 3GB in detriment, the kernel will get 1GB of virtual memory instead of 2G, so a the 4G of virtual memory per process is shared between the user (application host) and kernel (system host).
 
In Linux however, process management is done differently, it makes better use of physical RAM and will use swap or virtual space when needed.
 
I have 4GB of physical RAM, and I'm running Ubuntu-64 with a few applications.  Even when I have OpenOffice and my internet applications loaded, my system never relies on swap as my memory usage doesn't get higher than 40-45%.
 
I could run some windows games in a virtualbox machine however, I do agree with the others that you will be limited by the virtual machine in managing memory and more importantly, video.
 
You are better to install Windows in a dual-boot arrangment and load your games that way.
 
Wine is an alternative, keep in mind that it comes with some pre-installed in some applications like Google Picasa on Linux.

---

### Post by MG37221 on 2009-07-31
As a general rule, I like to have an available 1GB RAM per core.  I'm running a dual core Opteron and though I've 4GB installed, I find 2GB to be the sweet spot.  Note that I'm completely Windows free using 64bit Jaunty exclusively.  My next build will probably be a quad with 4GB.

---

