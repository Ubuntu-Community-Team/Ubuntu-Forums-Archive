---
title: "apt-get error: &quot;E: Line 1 too long (max 1024)&quot;"
date: 2006-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrestomanci on 2006-05-27
Hi

Apt get on my System has become screwed up somehow. If I run it even just "apt-get -h" I get the above error message. It does not say which file it has a problem with. I get the same error message from apt-cache, apt-cdrom, and apt-config but not apt-key

I was editing my /etc/apt/sources.list file before it happened, but I have since restored those files from a backup, and it has not cured the problem.

I have also tried reinstalling apt using "dpkg -i" and .deb package downloaded from a Ubuntu mirror?

I also tried moving aside the directories in "/var/cache/apt/" and "/var/lib/apt" but that did not cure the problem either.

I have run out of ideas, can anyone think what might be the problem. I have faily good backups, so if the offending file can be identified, then I can delete & restore it, but I am not ready to re-install my system just yet.

Help.

Here is my sources.list file, though I am fairly certain there is nothing wrong with it.
> # CD Rom (not in use)
# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

# Local repository.
deb file:///var/mirrors/ubuntu stable  main restricted

# Main ubuntu servers.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# Mplayer
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) breezy multiverse


---

### Post by chrestomanci on 2006-05-29
Update: I reposted this issue in a non AMD-64 Specific forum and got a solution:

[http://ubuntuforums.org/showthread.php?p=1062054](http://ubuntuforums.org/showthread.php?p=1062054)

---

