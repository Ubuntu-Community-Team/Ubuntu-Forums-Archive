---
title: "Wireless problem in 10.3, anyone else?"
date: 2007-10-06
forum: openSUSE and SUSE Linux Enterprise
---

### Post by 3ark on 2007-10-06
I decided to try out Opensuse 10.3 on a laptop I have here. I am running a Compaq Presario V2000 laptop with a bcm4318 card. I blacklisted the bcm43xx drivers and I have successfully configured ndiswrapper on ubuntu dapper/feisty but am having trouble with opensuse 10.3. I am using the same drivers I did for Ubuntu Feisty. and when I do ' ndiswrapper -l ' I get the following output.
> 
bcmwl5 : driver installed
device (14E4:4318) present (alternate driver: bcm43xx)


So... it appears as though I have a driver but I still cannot connect wirelessly, perhaps I am configuring it all wrong. I would be very appreciative for some help solving this as it is the sole black mark on my OpenSuse experience thus far. Figured I would try a post here as these forums are usually amazing.

---

### Post by mjwhitfield on 2007-10-06
have you done modprobe ndiswrapper?

---

### Post by 3ark on 2007-10-07
Yes, I have done that command still no luck I'm afraid. I have noticed this:

> linux-sorr:~ #  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by 3ark on 2007-10-07
I managed to get it working, I just tried the whole procedure again from start. Not exactly sure what I was doing wrong but at least it works now. Thanks for your help. :popcorn:

---

