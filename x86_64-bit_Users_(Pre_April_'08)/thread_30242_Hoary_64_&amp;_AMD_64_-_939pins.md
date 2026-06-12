---
title: "Hoary 64 &amp; AMD 64 - 939pins"
date: 2005-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by DutchLau on 2005-04-27
Hi, 

I have a really quick question to ask the community. Does Ubuntu 64-bits support the new AMD 64 - 939 pin processor? PLEASE let me know, I want to install Hoary 64 on it *really* soon, but only if Hoary supports it  :-P 

Thanks,

DutchLau

---

### Post by mthaddon on 2005-04-27
Don't mean to be an ass, but have you tried the LiveCD? That'll give you a very good idea of what hardware support there is in Hoary.

Thanks, Tom

---

### Post by FluffyElmo on 2005-04-28
Yes, it supports it. I'm running it on a Socket 939 system now.

---

### Post by psoulocybe on 2005-04-28
It sure do!

I'ze a runnin it rite now!

---

### Post by gomadtroll on 2005-04-29
The # of pins is not relevant.  I do run on an AMD64, 939 pins, though.


greg

---

### Post by DutchLau on 2005-04-29
Thanks for all the replies!  :)  

On Monday I'll be getting the parts for my AMD 64 system. It's going to be an AMD 64 939pins 3500+ on an ASUS A8V Motherboard with 1024 PC400 DDR Samsung Ram, 256MB GeForce FX 5200 and it will have a 160GB Serial ATA HDD. (Cost the equivalent of about $700) Hopefully all of this will be recognized by Ubuntu!   :neutral: 

I'm sure it will be though.

Cheers to all,

DutchLau

---

### Post by psoulocybe on 2005-04-29
Good luck, you should have no problems!

Enjoy your 64bit goodness.

You planning on running A64 or i386 ubuntu?

---

### Post by DutchLau on 2005-04-29
@ psoulocybe

I'm actually planning to run both Hoary i386 and Hoary 64 with a dual boot. I've snooped around the forums alot and it seems like there are many lackings with Hoary 64 still (mainly with audio and video codecs which I quite frankly can't do without). That's why I'm installing both. With one I'll experiment as much as possible to get stuff working and the other will be a fallback PC. I'll have 3 partitions, one for i386 one for x64 and one for my /home & files. 

I have just one question. Could someone please tell me if I can run i386 games (such as Americas Army) on my AMD 64 in Hoary 64? I believe that isn't possible without a complicated chroot or 32 emulation command. 

Thanks already,

DutchLau

---

### Post by mduduzi on 2005-05-01
Can't comment on the games... Just on your hardware.

I had difficulty with grub on my SATA - both Silicon and nVidia SATA chips. I do not remember where the thread is where Michael gives a workaround. 

In short, you man not be able to boot with grub. Fix grub using a Live CD - Michael suggested the Gentoo minimal live CD and it worked for me. Only remember to replace 'hda' on his instructions with 'sda'.

If you can't find the thread, post and I'll type it out because I printed it.

Admittedly, this has nothing to do with 939 or 740 pins.

---

### Post by DutchLau on 2005-05-01
Hi, mdudzi and thanks for the information,

Could you please give me the instructions for doing that please? (I haven't setup the computer yet, but I won't have a working computer when I finally put it together because, I don't have another one at the moment (I'm on a friend's PC right now). I can't seem to find the thread in the Ubuntu database either. This is indeed quite annoying though because SATA is so much faster than a regular drive. 

Thanks already,

DutchLau

---

### Post by mduduzi on 2005-05-01
Found it!

[http://www.ubuntuforums.org/showthread.php?t=13112](http://www.ubuntuforums.org/showthread.php?t=13112)

The Gentoo minimum live CD is approx. 78MB. So with broadband it should be snappy to get.

---

### Post by DutchLau on 2005-05-01
Thanks mdudzi! 

Now the question is, where can I find the 2004 minimal Live CD? I assume I can use the 2005 minimal CD, but I can't find any Live Gentoo CD's anywhere. Do these minimal CD's also work as Live CD's, or do I have to install Gentoo? Could you otherwise *please* send me the link of the place where I can get a minimal Live CD? Thanks alot already,

DutchLau

---

### Post by mduduzi on 2005-05-01
I was wrong about one thing. It's not a live CD. But for this intent, it doesn't alter anything.

 I used the latest 2005 version. You should be able to get it from your nearest Linux ISO mirror.  Perhaps you can google for the file name?

[ftp://ftp.is.co.za/linux/distributions/gentoo/releases/amd64/current/installcd/install-amd64-minimal-2005.0.iso](ftp://ftp.is.co.za/linux/distributions/gentoo/releases/amd64/current/installcd/install-amd64-minimal-2005.0.iso)

That's the link to my closest mirror.

---

### Post by verden01 on 2005-05-02
I have an Abit AV8 S939 M/B , AMD 64 3500+, 160Gb SATA HDD, 1024MB Kingston Ram etc and have had no problems installing Kubuntu at all and its the only distro that has recognised ALL of my hardware :).

---

### Post by dewey on 2005-05-03
All gentoo installation cds perform like Live CDS. (Excluding the package cds)

---

### Post by DutchLau on 2005-05-03
Alright, great! I don't have any problems with Grub, but now I don't have any sound in Ubuntu! What's going on

---

### Post by Jarz Corp on 2005-05-06
Hi DutchLau

U will have no problems with Army Ops on your machine, except maybee the fact that it doesn't really give the Cpu the challenge it deserves =), but then your cpu will just turn down the clock speed to something befitting the need.

I am on a 939 3500+ with 1gig Ram, 2 x 160 Sata Maxtor cheapass stuff, Ati x700 and a A8N-SLI board.

It ubuntu runs sweet on this system, except as earlier mentioned the java, flash,  xxxx stuff. Which is in no way ubuntus fault.

---

