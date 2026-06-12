---
title: "Tri-boot? (and a couple of misc questions)"
date: 2008-08-21
forum: x86 64-bit Users
---

### Post by zx6r1033 on 2008-08-21
I've had the hardware setup for 64bit for some time now. I am still relatively new to Linux, as well. (I've been using it for 3 weeks now.) I currently have a Dual boot XP/32bit Ubuntu configuration. There are still a couple of programs that either will not run in Ubuntu, or that I cannot find a Linux counterpart for. (FSX, DVD Software, Itunes, etc.)

Anyway, to make a long story short... I want to check out 64bit and see how it works out for me. Given my current hardware configuration, 32bit Ubuntu won't even recognize some things. (Like my 8gb memory.) The thing is, I finally have 32bit Ubuntu set up the way I want to, and I would hate to jump to 64bit only to find it doesn't work out. Windows can't go, though. Is it possible to successfully set up a Tri-boot system until I can figure out if things will work out or not? If so, what kind of difficulties can I expect at a later date if I decide to move to 64bit and ditch the 32bit system?

Is there anything else I should know about or consider at this point? (Other than what I can/have read in the FAQs and stickies?)

---

### Post by Kilz on 2008-08-21
> **zx6r1033 said:**
> I've had the hardware setup for 64bit for some time now. I am still relatively new to Linux, as well. (I've been using it for 3 weeks now.) I currently have a Dual boot XP/32bit Ubuntu configuration. There are still a couple of programs that either will not run in Ubuntu, or that I cannot find a Linux counterpart for. (FSX, DVD Software, Itunes, etc.)

Anyway, to make a long story short... I want to check out 64bit and see how it works out for me. Given my current hardware configuration, 32bit Ubuntu won't even recognize some things. (Like my 8gb memory.) The thing is, I finally have 32bit Ubuntu set up the way I want to, and I would hate to jump to 64bit only to find it doesn't work out. Windows can't go, though. Is it possible to successfully set up a Tri-boot system until I can figure out if things will work out or not? If so, what kind of difficulties can I expect at a later date if I decide to move to 64bit and ditch the 32bit system?

Is there anything else I should know about or consider at this point? (Other than what I can/have read in the FAQs and stickies?)

You can do a triple boot if you have the hard drive space. It shouldnt be that hard to remove either the 32bit or 64 bit installs later depending on what happens. Check out k9copy for dvd copy software, brasero if you just want to burn them. Both are in synaptic.

---

### Post by jnw222 on 2008-08-21
yes 

1. create enough free space
2. install ubuntu 64 bit
3 repair 32 bit ubuntu's bootloader (in case you decide to uninstall ubuntu)
4. enjoy

*alternative method 1:
use wubi

*alternative method 2:
use ubuntu server and add a gui. I think server 32 supports 8gig ram


ps. 8Gb is a lot did your computer come with vista?

---

### Post by zx6r1033 on 2008-08-21
> **jnw222 said:**
> . 8Gb is a lot did your computer come with vista?

I build all of my computers. I've never owned a thoroughbred (other than laptops). I currently have 8 desktop computers in my house... each one serves a different purpose. This one started life as a dedicated computer for flight simulators. 2.5gig AMD X2 processor overclocked to 3.0gb, 8gig memory, 250gb sata primary drive (operating system only), 2 x 1tb sata hds for storage, 2 x (SLi) evga nvidia 8800gt 128bit 1gb gpus. etc etc. I still use it as a flight sim computer, but that has been happening less and less lately. FSX is windows-only and I have grown to hate windows in the past 3 weeks on Ubuntu. Xplane runs like crap on either platform, but considerably worse in linux. I've been eyeballing a new motherboard, though. I've found a couple of them that support 16gb. Current memory is only 2b per stick, though. I'll have to wait until 4gb sticks come out. 


Anyway... hd space won't be an issue. I use a 250gb sata hd for program files only, and all of my major storage is on other hard drives. Currently, I have 160gb of free space to use for another OS. 




How do you go about repairing the bootloader?

---

### Post by elmoosecapitan on 2008-08-21
Absolutely, you can n-tuple-boot. That is to say, you can run as many OSes as your heart desires. The only issue comes in whether or not you have the space on your hard drive.

Seriously, 8 GB of RAM? = ) That makes me smile.

---

### Post by Yellow Pasque on 2008-08-21
If you have your /home folder on a separate partition, that would make life a lot easier for you.

---

### Post by zx6r1033 on 2008-08-21
> **elmoosecapitan said:**
> 

Seriously, 8 GB of RAM? = ) That makes me smile.

lol  When you can get Kingston HyperX 2gb sticks for $49 each, why not have your memory maxed out?

---

