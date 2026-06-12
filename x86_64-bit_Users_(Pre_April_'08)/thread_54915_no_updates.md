---
title: "no updates ?"
date: 2005-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by cakey on 2005-08-06
Hi.  I've been running Ubuntu-64 for around a week or so and since my initial installation there have only been a few software updates and none in the last few days.  Is this normal?  I'm coming from Debian (sid) and got used to seeing lots of daily package updates when apt-get upgrading.  

I just want to make sure theres nothing wrong on my end. 


my sources.list:

[SIZE=1]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

## amd64 users repository
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) hoary main  

## amd64 packages testers repository
deb [http://tamir.nooms.de/ubuntu/](http://tamir.nooms.de/ubuntu/) tests main  
[/SIZE]

---

### Post by Ubunted on 2005-08-06
Well Ubuntu has nowhere near the number of installed packages as a default Debian, so no, you probably won't see as many updates.

Coming from Mandrake myself, where there's 300MB of updates a month after a release, I found it a bit odd as well.

You might want to add the official backports repos though; [http://www.ubuntuforums.org/showthread.php?t=52168](http://www.ubuntuforums.org/showthread.php?t=52168)

---

### Post by cakey on 2005-08-06
Cool.  Thanks.

---

### Post by wmcbrine on 2005-08-08
If you'd been with Hoary before the official release in April, or (I presume) if you went with Breezy now, you'd [have] see[n] tons of updates. But once the release date comes, the only updates are supposed to be security patches.

---

