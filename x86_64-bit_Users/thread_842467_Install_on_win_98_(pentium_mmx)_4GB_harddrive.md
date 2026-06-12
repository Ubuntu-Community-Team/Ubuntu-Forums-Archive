---
title: "Install on win 98 (pentium mmx) 4GB harddrive?"
date: 2008-06-27
forum: x86 64-bit Users
---

### Post by NikolasP on 2008-06-27
Hi, im trying to install ubuntu on  win 98 (pentium mmx) 4GB harddrive.

I have now tried xbuntu, ubuntu and wubi and all say I do not have enough space to install.  Which can I install on it to make it work?

It's a very old laptop it currently runs win 98, but i want to install linux on it.

---

### Post by tamoneya on 2008-06-27
try the alternative install cd for xubuntu:
[http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/xubuntu-8.04-alternate-i386.iso](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/xubuntu-8.04-alternate-i386.iso)

The alternative install does not include the LiveCD and is less resource intensive.  If that doesnt work it will be rather hard to get ubuntu working with the limited harddrive space.  If that is the case I would recommend you look at Damn Small Linux, Puppy Linux and gOS.

EDIT:  There is also fluxbuntu a non-official variant of ubuntu.
[http://fluxbuntu.0x12.com:8080/releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso](http://fluxbuntu.0x12.com:8080/releases.fluxbuntu.org/7.10/rc/fluxbuntu-7.10-installer-i386.iso)

---

### Post by snowpine on 2008-06-27
> **NikolasP said:**
> Hi, im trying to install ubuntu on  win 98 (pentium mmx) 4GB harddrive.

I have now tried xbuntu, ubuntu and wubi and all say I do not have enough space to install.  Which can I install on it to make it work?

It's a very old laptop it currently runs win 98, but i want to install linux on it.

I have successfully installed both Xubuntu (using the alternate install disk that tamoneya mentioned) and Fluxbuntu on hard drive partitions of 4 gb or less. I've not tried it personally, but I think Ubuntu should work, too, provided you use the alternate install. If you check out the eee pc user forum (eeeuser.com) there are people running ubuntu on their 4 gig eee's. 

Another option is the bare-bones installation described here: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

ps How much RAM do you have? Often, that is a bigger limiting factor than hard drive space. You should have at least 128 for Xubuntu and 256 for Ubuntu, in my opinion. Any less and Fluxbuntu is your best 'buntu option; you might want to consider something like Puppy or DSL at that point (or buying more RAM).

Good luck!

---

### Post by NikolasP on 2008-06-27
My ram is only 32 meg!

I am currently burning the fluxbuntu iso and will try it.  see if it works.

---

### Post by snowpine on 2008-06-27
> **NikolasP said:**
> My ram is only 32 meg!

I am currently burning the fluxbuntu iso and will try it.  see if it works.

Please report back because I'm curious to know if it will work. My Fluxbuntu install seems to use up 40-50 mb when idle. You are definitely pushing it with only 32! :)

Damn Small Linux (DSL) would be my recommendation.

---

### Post by howlingmadhowie on 2008-06-27
i think your best bet would be to go with a gnu/linux distribution for older hardware. have a look at dsl or puppy. i don't think that even fluxbuntu will bring you much joy
[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")
[http://www.puppylinux.org/]("http://www.puppylinux.org/")

---

### Post by stchman on 2008-06-28
I am with poster #6 Puppy or DSL would be a better choice,

I have an old PIII 450 and Xubuntu ran kind of slow.  Puppy runs great on the same machine.

---

### Post by darrelljon on 2008-08-25
DeLi Linux works with computers even older than those designed for Damn Small Linux and DeLi is still being updated.

---

### Post by lisati on 2009-03-15
Hmmmm, found this thread while researching Puppy Linux (currently getting my old Win98 machine ready to try it. 133MHz 64Mb Ram, 1Gb hard drive, waiting for gparted to format the HD to ext3. Soooooo slow!). 

I wonder how the OP got on.....

---

### Post by jaqie on 2009-03-16
Honestly with such low RAM the only linux OS that is supported and desktop friendly that will run with any appreciable usability is DSL. I have battled with a similar system, and even DSL uses over 32MB when running, but that's the best bet for really low spec computers like the ones listed here.

---

### Post by Hobgoblin on 2009-03-16
> **NikolasP said:**
> Hi, im trying to install ubuntu on  win 98 (pentium mmx) 4GB harddrive.

I have now tried xbuntu, ubuntu and wubi and all say I do not have enough space to install.  Which can I install on it to make it work?

It's a very old laptop it currently runs win 98, but i want to install linux on it.

Are you trying to install alongside Win98?

I have Ubuntu (8.10) running on a laptop with a 4GB HDD but it only has Ubuntu on there and it has 320MB of RAM.

---

### Post by jespdj on 2009-03-16
Why is this in the x86 64-bit Users forum? It does not have anything to do with 64-bit Ubuntu at all.

---

### Post by jmorsman on 2009-03-16
I have an old gateway solo 9150, 333mhz, 14g hd  I tried to load linux on it. The only version of linux that I found that would install on such an old computer and work was fedora 7. Out of all of the different versions that was the only version that would work. The live cd's took the computer to long to process and locked it up frequently. and other distros locked up before they installed. 

Have a great day and have fun

---

