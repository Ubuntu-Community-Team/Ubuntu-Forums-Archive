---
title: "AMD 64 want p2p privacy-moblock"
date: 2007-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ubukanuba on 2007-04-05
So i have been having serious issues with trying to install certain apps on ubuntu 6.10 edgy eft for my AMD 64.  Mainly I am concerned with getting some type of security program like peerguardian or moblock to run on my system.  I tried to get moblock to run last night and it ate harddrive number 1 somehow, someway??  Anyhow.......

I am in search of a guide to install either peer guardian or moblock on my amd 64.  Thanks to anybody out there that might be able to point me in the right direction.

UbukanooBa

---

### Post by beefcurry on 2007-04-06
There is a moblock faq

[http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock)

Its not AMD 64 specific but what it says are still relevant, next time try searching first.

---

### Post by jamesford on 2007-04-07
i made amd64 debs of moblock a while ago, you can find them towards the bottom here [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

install procedure is as follows:
sudo dpkg -i libnfnetlink0_0.0.14-1.1_amd64.deb
sudo dpkg -i libnfnetlink-dev_0.0.14-1.1_amd64.deb
sudo dpkg -i libnetfilter-queue_0.0.11-1.1_amd64.deb
sudo dpkg -i libnetfilter-queue-dev_0.0.11-1.1_amd64.deb
sudo dpkg -i moblock-nfq_0.8-10_amd64.deb

the rest u need to know should be covered in the moblock thread on this forum somewhere

---

### Post by paul_banks on 2007-05-25
I followed **jamesford's** steps and moblock works, as far as I can tell, but I've got a broken package now. Synaptic manager tells me that libnetfilter-queue-dev is broken, but when I try to reinstall it, it tells me I have to install libnetfilter-queue1 as well. Fine by me, but I get the following error:

E: /var/cache/apt/archives/libnetfilter-queue1_0.0.12-1_amd64.deb: trying to overwrite `/usr/lib/libnetfilter_queue_libipq.so.1.0.0', which is also in package libnetfilter-queue

I'm **very** new to Ubuntu, so I'm afraid to proceed on my own here... tried the official moblock thread, but couldn't find anything about broken packages...

---

### Post by iBART on 2007-05-31
i got the same error of paul_banks :(

---

### Post by jamesford on 2007-05-31
in feisty u dont need all the packages supplied on that page, you only need the following, in this order:
 libnfnetlink0_0.0.14-1.1_amd64.deb
 libnetfilter-queue_0.0.11-1.1_amd64.deb
 moblock-nfq_0.8-10_amd64.deb

the rest are probably autimaticly installed as dependencies

before installing that u should probably uninstall all the moblock related packages previously installed including the broken ones iirc

---

### Post by iBART on 2007-06-02
thanks, now it works!

---

