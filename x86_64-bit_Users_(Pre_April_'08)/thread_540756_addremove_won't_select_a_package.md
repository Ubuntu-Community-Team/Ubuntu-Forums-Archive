---
title: "add/remove won't select a package"
date: 2007-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by firstc624 on 2007-09-01
ok i am trying to put a tick in the box to install RAR and it won't let me.  is this a known bug w synaptic.  yes i am running 64 bit  fiesty if that matters.

i had the same problem when i wanted to install wine 64bit.  i had to use the terminal to install it, i followed wine own directions from their site.  there is apparently a deb file for fiesty, but only let it insall and remove via terminal only.

anyone else have this?

---

### Post by aysiu on 2007-09-02
No, there's a 64-bit version of *rar*:
[http://packages.ubuntu.com/feisty/utils/rar](http://packages.ubuntu.com/feisty/utils/rar)

Can you close Add/Remove and open a [terminal](http://www.psychocats.net/ubuntu/terminal)? In the terminal, paste in these commands. Then paste the output back here: ```
sudo apt-get update
sudo apt-get install rar
cat /etc/apt/sources.list
```

---

### Post by firstc624 on 2007-09-02
I was able to install it already via termina sudo apt-get install rar  but i wasn't able to install it stricly synaptic.  and when it did install synaptic did show it was, but if i wanted to remove it thru synaptic (add/remove)  it wouldn't select it.

here is the output of the cat /etc/apt/sources.list

[HTML]firstc624@firstc624-laptop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
firstc624@firstc624-laptop:~$ 
[/HTML]

Just thought i would ask as if this is a bug or something it would be good to post it but wanted to check w/ the community first  :-)

---

