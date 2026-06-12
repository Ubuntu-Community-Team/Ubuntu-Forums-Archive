---
title: "major system error message, help!"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by elquer on 2007-06-06
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 44 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
-------------------------------------------------------
the above is the error message i got, and now i can't add any programs and can't update anything on my computer. i'm using a compaq press. v2000 amd turion 64 with ati graphics and running ubuntu 7.04. i tried installing automatix but i guess it was instruction for a different version or something and i got an error message, after i rebooted that's the error message i got ( the one abot), and cant' install any new programs or view my add remove program window. can somoe one help?

---

### Post by dabl on 2007-06-06
Your /etc/apt/sources.list file got screwed up by the attempted Automatix installation.  If you will open that file with gedit and paste it into a reply on this forum, probably we can spot the error and help you fix it. :)

---

### Post by srt4play on 2007-06-06
Sounds to me like automatix screwed up your /etc/apt/sources.list file.  This is the second thread with this problem I've read today.  

Press Alt-F2, type 'gksudo gedit /etc/apt/sources.list'  and post the contents here.

---

### Post by capecove on 2007-06-06
This thread may help...

[http://ubuntuforums.org/showthread.php?t=464576](http://ubuntuforums.org/showthread.php?t=464576)

> **srt4play said:**
> Sounds to me like automatix screwed up your /etc/apt/sources.list file.  This is the second thread with this problem I've read today.  

Press Alt-F2, type 'gksudo gedit /etc/apt/sources.list'  and post the contents here.

---

### Post by elquer on 2007-06-06
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”


that's what i got, help please, i'm new to linux and really dont' wanna go back to vista. thanks guys.

---

### Post by elquer on 2007-06-06
problem solved, i used the thread you posted. thanks a lot man

---

### Post by arnieboy on 2007-06-07
> **srt4play said:**
> Sounds to me like automatix screwed up your /etc/apt/sources.list file.  This is the second thread with this problem I've read today.  

Press Alt-F2, type 'gksudo gedit /etc/apt/sources.list'  and post the contents here.
when the user ends up with double quotes in his sources.list.. it's typically because he is new to copying and pasting commands on a terminal.. automatix does not screw up sources.list.. users do it themselves and we help them resolve issues.. Automatix has not taken hard line approaches like removing unsupported repositories which new users take a fancy to and add at will without realizing their implications.. but it might be a safe and smart thing to do in the future.. it will take care of a ton of issues which users create on their own.

---

