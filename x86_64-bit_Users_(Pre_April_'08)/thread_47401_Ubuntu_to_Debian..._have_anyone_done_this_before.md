---
title: "Ubuntu to Debian... have anyone done this before???"
date: 2005-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by nortoncillo on 2005-07-08
i have my AMD64 Web server with Ubuntu, nice and quiet....

but now

i must change to Debian...

as far as i know Ubuntu distro is a kind of "founded" Son, of Debian... 

and is a fact that both use the apt-get package manager.. so..

to change distro should be like...
..change de sources list
..then # apt-get debian-distro???

or i'm totally lost??

---

### Post by Jet2k5 on 2005-07-08
You are totally lost.  I don't think that you can change distros by just downloading packages.  That is an absurd statement.

You can simply change Mandriva to redhat by doing urpmi red-hat.  It's no possible.  Since each distro has different set ups and they each have their own programs that are for that distro alone.

Anyhow I don't think that it can be done, atleast to my Linux knowledge

---

### Post by nortoncillo on 2005-07-08
Jet2k5... i think that you are lost... 

you'll see... if you are using warthy (the previus release of ubuntu) you can upgrade the distro to hoary, with just an "apt-get update distro"...

and as i told before...ubuntu comes from debian.... so... i think that it should be posible... 


ps: use google and you'll find a "how to" to get Debian from Suse...

---

### Post by NickB on 2005-07-08
As someone who recently "upgraded" from sarge to ubuntu, most of the packages that were in conflict were actually "downgrades" to lesser package versions in ubuntu.  I would say that it's most likely possible to go from ubuntu to sarge, though probably easier to go to unstable (sid).  I would test that theory on a throwaway system first, though :)  e.g. install ubuntu from CD then change sources.list to point to debian archives and apt-get update + apt-get dist-upgrade.

Good luck,
Nick

---

### Post by crashtest on 2005-07-08
[QUOTE=Jet2k5]You are totally lost.  I don't think that you can change distros by just downloading packages.  That is an absurd statement.

You can simply change Mandriva to redhat by doing urpmi red-hat.  It's no possible.  Since each distro has different set ups and they each have their own programs that are for that distro alone.

Anyhow I don't think that it can be done, atleast to my Linux knowledge[/QUOTE]

Ubuntu is far closer to Debian than you think.  In most respects it is Debian Sid with a slightly different repository.  By changing the sources list, followed by a sudo apt-get dist-upgrade you should be able to turn it into regular Debian Sarge, or Debian Sid.  I'd try it on a throw-away system first as someone else said in here, just to see what wacky dependancy issues need to be overcome.

Before Debian came out with their new installer (which Ubuntu's installer closely resembles) it had the reputation of being difficult to install.  Many people used to install Libranet for the easy installation, and the super-nice Admintool, then change their sources list to Debian Sid, and become regular Debian.

I'm willing to bet you could do the same thing with Simply-Mephis as well, if they haven't strayed too far from the Debian path.  As time goes on however, this will become more and more difficult, as Ubuntu, Simply-Mephis, Libranet, and all the other spawn of Debian begin to go their own separate ways.  How long before Ubuntu has a bigger install base than Debian?  It absolutely must be growing faster than Debian by leaps and bounds at this point.

---

### Post by Jet2k5 on 2005-07-09
I apologize for my misunderstandment.  I totally thought that this could be done, but I guess it can now.

---

### Post by dmn_clown on 2005-07-09
[QUOTE=Jet2k5]I apologize for my misunderstandment.  I totally thought that this could be done, but I guess it can now.[/QUOTE]

Theoretically it is possible to update from one distro to another, but it is insanely difficult to accomplish when each distribution is using patches for certain packages that are specific to that distribution (check the kernel and gcc patches that are specific to Red Hat and Fedora).

Ubuntu currently is somewhat compatible with Debian packages, and it should be possible, as long as you go with the "Unstable" branch.  Problems that I would expect:  X would have to be reconfigured (Debian is still using XFree86) lib versions would be different, there may also be a problem with  the kernel update (2.6.9 and 2.6.10 were skipped in Debian "Unstable" in favor of 2.6.11, the installer for AMD64 currently uses 2.6.8 ).

Though, if you need an AMD64 version of Debian that has official support and security updates, Ubuntu is (currently) the way to go.  Debian's AMD64 port will not become officially supported until "Etch" is released, with security releases for Sarge (currently) being handled away from security.debian.org.

---

### Post by dewey on 2005-07-11
It's entirely possible, but I wholeheartedly do not recommend it, especially for a server.

Backup your files, and your configurations, and do a clean debian install.  Trying to convert distros is just asking for downtime, and unnecessary frustration.  If you were just on a workstation, I'd say go for it, and learn while you do it.  But server downtime is no fun.

---

### Post by fistfullofroses on 2005-07-13
I just think that you are nuckin futs, and I will tell you why.

1.) Debian does not update their distribution all that much and therefore hardware support will not be as good (there were great innovators though!)

2.) The two distributions are so much alike, yet Ubuntu has newer and faster everythings

3.) Ubuntu is prettier.

---

### Post by nortoncillo on 2006-01-12
[QUOTE=fistfullofroses]

3.) Ubuntu is prettier.[/QUOTE]

is that an argument?... for a server?


anyway, time ago i was waiting the conclusions of this thread to go for the "imposible mission", but, a month after i started this thread the motherboard of that server died (in fact died the Hd controller so goodbye data), then i had to make a fresh install, tryed debian etch... results?.. a big PIA, there are no AMD64 support at all, so... i used my recently arrived ubuntu disks.

take my advice... if you plan to have an AMD64 machine, running some debianLike Linux, go and ask your ubuntu disk's..;)

---

### Post by nocturn on 2006-01-12
What I'd really like to know if it would be possible to do something like Hoary -> Dapper.

Two updates a year on a server are a bit too much and the five years of support for Dapper is too long...

---

