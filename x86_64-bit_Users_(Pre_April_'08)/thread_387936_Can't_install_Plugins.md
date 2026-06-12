---
title: "Can't install Plugins"
date: 2007-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by blockdude14 on 2007-03-18
I can't install the plugins necessary for youtube like macromedia flash. :confused:

---

### Post by scxtt on 2007-03-18
what have you tried?  what browser are you using?

---

### Post by blockdude14 on 2007-03-18
I'm using mozilla firefox and I tried installing it from the pop-up that comes up for missing plugins which doesn't work.

---

### Post by scxtt on 2007-03-18
yeah, i've had that happen to me too ... but i have seen it work before, not w/ ubuntu tho :( ...

try doing "sudo aptitude install flashplugin-nonfree" ... if that doesn't work, we'll need to make sure you have the multiverse repository enabled ...

and let me know if you want v9 specifically ...

---

### Post by blockdude14 on 2007-03-18
I tried doing this and it still doesn't work. ?

---

### Post by blockdude14 on 2007-03-18
how do I enable the multiverse repository?

---

### Post by scxtt on 2007-03-18
**sudo nano /etc/apt/sources.list** --- see if you see the word multiverse anywhere in that file and if that line has a # at the beginning ...

if the word isn't there @ all, add the following line:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

then save (ctrl+o) and quit (ctrl+x)

then run **sudo aptitude update** and try **sudo aptitude install flashplugin-nonfree** again ...

---

### Post by blockdude14 on 2007-03-18
still not working?

---

### Post by scxtt on 2007-03-18
can you copy and paste the contents of /etc/apt/sources.list into this thread?

---

### Post by blockdude14 on 2007-03-18
## Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main universe #Added $

## Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe m$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer$

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

## Ubuntu Bug Fix Updates

## Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main univers$
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## Canonical 'Commercial' Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Skype - VoIP Client
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted #Added by sof$

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted unive$
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted u$

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe mul$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe$
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe mu$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main univers$

---

### Post by scxtt on 2007-03-18
looks like you've got some errant "$" in your file ... i'd clear it out, then paste this in there:
```
[font=courier]# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe[/font]
```save it, then do **sudo aptitude update** to "sync" ...

---

