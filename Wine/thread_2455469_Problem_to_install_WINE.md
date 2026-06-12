---
title: "Problem to install WINE"
date: 2020-12-20
forum: Wine
---

### Post by someindianguy99 on 2020-12-20
Hello , I am a new user. I am facing problems as I cannot figure out why I am not being able to install WINE.

Here's what the terminal spat out:

[REDACTED]@[REDACTED]:~$ wget -nc [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key)
File ‘winehq.key’ already there; not retrieving.

[REDACTED]@-[REDACTED]:~$ sudo apt-key add winehq.key
[sudo] password for [REDACTED]: 
OK
[REDACTED]@[REDACTED]:~$ sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) eoan main'
E: Malformed entry 60 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.

---

### Post by howefield on 2020-12-20
Are you using Eoan Ermine, Ubuntu 19.10 ?

Few will care what issues you have with an unsupported release of Ubuntu.

The error is giving you a clue, so what does your sources.list file say ?

```
cat /etc/apt/sources.list
```

---

### Post by someindianguy99 on 2020-12-20
I realise my mistake. I was trying to install wine on ubuntu 20.04 and I tried out something else. What should be the correct command?

```
[REDACTED]@[REDACTED]:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates main restricted
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main
deb [https://dl.winehq.org/wine-builds/eoan](https://dl.winehq.org/wine-builds/eoan) main
# deb-src [https://dl.winehq.org/wine-builds/eoan](https://dl.winehq.org/wine-builds/eoan) main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) eoan main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) eoan main
```

---

### Post by ajgreeny on 2020-12-20
It is a long time since I had anything to do with Wine as I do not need any Windows applications.
However, the final four lines in your sources.list are still showing **eoan** versions which are no longer available, **eoan** having lost support about 3 months ago.

Comment out those four lines in the file by running ```
sudoedit /etc/apt/sources.list
``` and add # at the start of each of those lines; this will mean they are ignored by the system. Alternatively just delete the lines completely.

---

### Post by someindianguy99 on 2020-12-20
What should I do next?

---

### Post by deadflowr on 2020-12-20
> What should I do next?
[s]Reinstall a clean installation of Ubuntu 20.04.
[/s]
FTR, the entry with the error is the second to last uncommented entry:
```
deb https://dl.winehq.org/wine-builds/eoan main
```
this is wrong.
Normally you would either comment it out or delete the line.
[s]But since there is no point in running an out of service release, I'd recommend ignoring it and do the clean install.

(It's recommended to do a clean install as Ubuntu 19.10's archives have been moved 
and are broken.
And any fix can be shady or unreliable.
And it's full of security holes already
And there are probably other reasons.)[/s]

Nevermind, I missed that the actual archives are for 20.04.


Edit:
Looking it over I'd say delete the last four lines altogether
as you already have the focal entry you need and the eoan entries are most likely broken or bad or will be gone.

---

### Post by someindianguy99 on 2020-12-20
I found out it was a problem with livepatch. I simply removed eoan main as a source and it runs perfectly. I did try out what was said to do : delete the last four lines. It now works perfectly.

---

### Post by deadflowr on 2020-12-21
> I found out it was a problem with livepatch.
Not sure what that means.
Livepatch has nothing to do with either wine or apt.
If livepatch had an issue it would be unrelated to the problem at hand.

---

