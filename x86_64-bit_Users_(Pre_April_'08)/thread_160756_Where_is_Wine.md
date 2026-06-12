---
title: "Where is Wine?"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Loffe_ on 2006-04-15
Hello folks!

I'm trying to get Wine working, but I can't find it in Synaptic.

I've added multiverse and universe. I also added deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/ but i don't find Wine in the list.

What should I do?

/etc/apt/sources.list

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
 deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

//Loffe

---

### Post by VoiceOvGod on 2006-04-15
Though I don't know the process, you could use Alien to help you adapt Wine from another distro to Ubuntu.

---

### Post by John Jason Jordan on 2006-04-15
[QUOTE=Loffe_]Hello folks!

I'm trying to get Wine working, but I can't find it in Synaptic.[/QUOTE]
I think the problem is that it does not work and cannot be installed in 64-bit Ubuntu. You have to create a 32-bit chroot environment to install it. 

That having been said, I understand that Crossover Office will install on 64-bit Ubuntu. At least I received that information in an e-mail from them. Crossover Office is commercial, however, although the price is not bad.

---

### Post by Loffe_ on 2006-04-16
ok, I see.

Well, i'll try to create that 32-bit chroot and see what happens...

---

### Post by Loffe_ on 2006-04-18
This stuff with both 32-bit and 64-bit seems to be more than easy.

So now I installed only the 32 version and everything works perfectly :D

Is there some advantages of running the 64-bit that I cannot have in the 32?

---

### Post by handy on 2006-04-19
[QUOTE=Loffe_]This stuff with both 32-bit and 64-bit seems to be more than easy.

So now I installed only the 32 version and everything works perfectly :D

Is there some advantages of running the 64-bit that I cannot have in the 32?[/QUOTE]

Hi, I've tried both 64 & 32 bit.  I can see no advantage in 64bit for my uses of a computer.

Changing to 32bit showed no speed decreases that I could notice!

I find living in 32bit Ubuntu so much easier & more comfortable.

I know 32bit will go the way of 8 & 16bit, & that's great.  

Though at this point of the transition, 32bit is still ahead!

---

### Post by brentoboy on 2006-04-19
I have an Amd64, and I run the 32 bit ubuntu.

But, If I were using this PC as a server, I think I would go 64 bit, so as to get the best performance out of the services and things.

but on a desktop, it isnt worth it to me, becuase of little annoyances with unsupported stuff.

---

### Post by XDR on 2006-04-19
Were is it i cant find it or get it to run??:(

---

### Post by handy on 2006-04-20
[QUOTE=XDR]Were is it i cant find it or get it to run??:([/QUOTE]

What?

---

### Post by cosmoshell on 2006-04-20
hey i still dont have wine and im wondering how to install it with this 32-bit chroot environment thing. can someone give it to me step by step

---

### Post by handy on 2006-04-21
[QUOTE=cosmoshell]hey i still dont have wine and im wondering how to install it with this 32-bit chroot environment thing. can someone give it to me step by step[/QUOTE]

Use the search function, you will find that there is more than one great step by step thread to help you out.  You will have to find them in the search results, but they **ARE** there, it won't take you very long to have all the information that you need. :KS

---

