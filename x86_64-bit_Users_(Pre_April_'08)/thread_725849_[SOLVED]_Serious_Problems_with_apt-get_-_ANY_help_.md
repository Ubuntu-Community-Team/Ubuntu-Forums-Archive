---
title: "[SOLVED] Serious Problems with apt-get - ANY help appreciated!"
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by s13_mills on 2008-03-16
Hi everyone,

I have been using Ubuntu for a while, and have recently built myself a new computer for a mythtv backend/frontend/fileserver for our flat - I had it working not long ago, but there were several random issues I had struggled with (mostly related to apt). Recently, I went to upgrade mythtv from 0.20.2 to 0.21, and it broke - thinking not too much of this, and not having anything of significance on this computer (all media is on another HDD), I simply reinstalled Ubuntu, this is where the trouble started!

Ubuntu appears to install fine - installer from live CD completes and computer boots fine first time. My LCD TV is the screen for this computer, so the first thing I do is install nvidia-glx-new. This is always fine. Problems occur subsequent to this when I try to update the computer using any of:

sudo apt-get upgrade
updating using the update manager
updating using synaptic

I have tried each and every one of these, each on a fresh install, and every time it throws up a number of errors, mostly:

```
E: /var/cache/apt/archives/[name of some package here] corrupted filesystem tarfile - corrupted package archive
```

I purchased a new harddrive, as I thought perhaps a bad drive was the issue (even though fsck returned OK) but same issues still occur.
I have NEVER had these errors on my other computer, and it has undergone several reformats/upgrades etc. Memtest86+ found NO issues with ram (pass = 17).

The strangest thing about this issue is that I cannot reliably replicate exactly which packages will fail - running
```

sudo apt-get clean
sudo apt-get install [the package that wouldn't install]
```

sometimes works and sometimes does not!

This is really, really getting me down, because I see no good reason for this to happen - ANY help is appreciated!

My hardware:
OS Drive: WDC 80GB
Media Drive: 750GB Seagate
Motherboard: Asus P5K
Gfx card: Asus EN8600GT
CPU: E6750
Ram: 667Mhz 4GB
and two Hauppauge Nova-S plus DVB-S cards

If you need more info to help, please don't hesitate to ask! If anyone has had a similar problem and found a solution, I would be very interested!

Thank you in advance!

Andrew

---

### Post by Cappy on 2008-03-16
Try deleting the file(s) manually when they error.
```
sudo rm /var/cache/apt/archives/[name of some package here]
```

---

### Post by s13_mills on 2008-03-16
I have done this, and you are absolutely right, but only for the individual packages - I am more interested in eradicating the problem, as I am certain it should not occur as much as it does! The issue can also create dependency issues which apt is not always able to resolve! Ubuntu shouldn't be like this, and previously it has always treated me well!

UPDATE: Memtest86+ found no issues with the ram (Pass = 17)!

---

### Post by Jouke74 on 2008-03-17
What happens if you switch ethernet ports (if I remember well your motherboard has two)?

---

### Post by s13_mills on 2008-03-17
Nope, just the one ethernet port! I tried switching my server from my local New Zealand one to the main one, and instead of the "corrupted package tarfile" I got a dpkg ended with error exit code (100) - maybe dpkg is the problem? I was looking around and came up with this: [http://www.debian-administration.org/articles/251]("http://www.debian-administration.org/articles/251")
but that seems like quite a workaround - why would there be so many errors? Anything else I can check in terms of hardware?
Any way I can download the necessary .debs on my other comp (there's 194 of them so I'd rather not pick them all out manually...?
Thanks for your help guys but this is still getting me down!

---

### Post by s13_mills on 2008-03-17
Reinstalling again with separate partition for /home and /. Prior to this I had used the "Guided - use entire disk" option. Will update with how this goes.

Any suggestions for solutions are still welcome! Please, people, it's getting harder and harder to recommend linux to my friends, help me out!

---

### Post by shane2peru on 2008-03-17
What I'm thinking is that some how your sources.list is not correct.  Somehow you have sources in there that shouldn't be in there.  I assume you edited them and added something because the mythtv version in my sources list is only 0.20.2, not the .21 that you mention. 
You must be careful with your source list as there can be danger in just accepting anything here is a copy of mine (I have edited out a few non essential entries):
```

 # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pe.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://pe.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

If you need help editing this just let us know.  

Shane

---

### Post by s13_mills on 2008-03-18
Shane,

I had thought this might be the case as well, but the sources.list I'm using now is off a totally fresh install of gutsy - not tampered with in any way shape or form!

Thanks,

Andrew

---

### Post by s13_mills on 2008-03-21
Alright, so turns out 8th (ish) time is the charm. This time when I installed Ubuntu I managed to get it up to date without it breaking! Admittedly I did have to do a

```
dpkg --configure -a
```

When the upgrade crashed (because of a corrupted package...) but Synaptic was able to fix dependencies subsequently. I have talked to a lot of my friends who also use linux, and they suspect it has something to do with the New Zealand repository - I'm not so sure though, I would have thought any issues would be better reported!

In any event, all is fine now (still have to install my mythtv, but don't see it being an issue!), but this is still unexplained (Even though I'm going to mark it closed), and it is things like this that keep people away from Linux, which is a crying shame because Ubuntu is a great operating system that is very stable and easy to use and administer once it is up and running - even my mother had great success with it once I installed it for her!

---

### Post by shane2peru on 2008-03-22
> **s13_mills said:**
> Alright, so turns out 8th (ish) time is the charm. This time when I installed Ubuntu I managed to get it up to date without it breaking! Admittedly I did have to do a

```
dpkg --configure -a
```

When the upgrade crashed (because of a corrupted package...) but Synaptic was able to fix dependencies subsequently. I have talked to a lot of my friends who also use linux, and they suspect it has something to do with the New Zealand repository - I'm not so sure though, I would have thought any issues would be better reported!

In any event, all is fine now (still have to install my mythtv, but don't see it being an issue!), but this is still unexplained (Even though I'm going to mark it closed), and it is things like this that keep people away from Linux, which is a crying shame because Ubuntu is a great operating system that is very stable and easy to use and administer once it is up and running - even my mother had great success with it once I installed it for her!

Andrew,

That is sad!  I probably should have thought of that too, since the first thing I do is get rid of the country code for my sources list!  I live in Peru, and have in the past found them to be slower, and if my memory serves me correctly, I even had a problem with it once.  I'm really surprised to see this type of thing happen else where too!  Perhaps there is somewhere we should suggest a stronger checkup on the other (official) repo servers.

Shane

Ps.  Glad you got it!

---

