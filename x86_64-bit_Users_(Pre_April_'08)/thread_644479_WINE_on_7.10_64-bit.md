---
title: "WINE on 7.10 64-bit"
date: 2007-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by clearsky on 2007-12-18
Hi Folks, 

This topic has been discussed and various suggestions have been made. I followed many of them but still unable to install wine. I tried to follow wine website and that didn't work either. 
Here is the issue:
$ sudo apt-get update
whole bunch of files got and then this 

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Segmentation fault (core dumped)
-desktop:~$ sudo aptitude install binfmt-support ia32-libs lib32asound2 libc6-i386 wine
Segmentation fault (core dumped)
-desktop:~$ sudo apt-get install wine
Segmentation fault (core dumped)
:~$ 

Any suggestions would be appreciated.

---

### Post by Kilz on 2007-12-18
Remove the wine repository. Wine is in the ubuntu repositories for Gutsy. Then install with ```
sudo apt-get install wine
```

---

### Post by clearsky on 2007-12-19
> **Kilz said:**
> Remove the wine repository. Wine is in the ubuntu repositories for Gutsy. Then install with ```
sudo apt-get install wine
```

Thanks. I did that and now I get the following error: 

$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but 1.5ubuntu9 is to be installed
        Depends: lib32asound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
        Depends: libc6-i386 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages

---

### Post by Kilz on 2007-12-19
> **clearsky said:**
> Thanks. I did that and now I get the following error: 

$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but 1.5ubuntu9 is to be installed
        Depends: lib32asound2 (> 1.0.14) but 1.0.13-1ubuntu5 is to be installed
        Depends: libc6-i386 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages

Are you 100% sure that you are running Gutsy Gibbon also known as Ubuntu 7.10?
Because the versions of the required libraries that are to be installed, that you quote, are from Feisty Fawn 7.04. If you are running Gutsy, did you do a clean install, or did you upgrade from a previous version install?

---

### Post by PmDematagoda on 2007-12-19
Post the results of:-
```

uname -a

```
and
```

cat /etc/apt/sources.list
```

---

### Post by clearsky on 2007-12-19
> **PmDematagoda said:**
> Post the results of:-
```

uname -a

```

Linux (my name)-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

and
```

cat /etc/apt/sources.list
```
 cat /etc/apt/sources.list
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


Sorry, for some reason looks like feisty is being used here although I installed it from UBUNTU 7.10 cd. Now, I just checked the system monitor and it does say that it is feisty as you mentioned. Is there a way to upgrade? Any benefit of doing so? 

UBUNTU Release 7.04 (feisty).

---

### Post by PmDematagoda on 2007-12-19
You do not have Ubuntu 7.10, you have Ubuntu 7.04 since you have Kernel 2.6.20 which is the one found in Ubuntu Feisty.

Follow the directions [here]("http://www.winehq.org/site/download-deb") for Ubuntu 7.04 not Ubuntu 7.10.

---

### Post by PmDematagoda on 2007-12-19
> **clearsky said:**
> 
Sorry, for some reason looks like feisty is being used here although I installed it from UBUNTU 7.10 cd. Now, I just checked the system monitor and it does say that it is feisty as you mentioned. Is there a way to upgrade? Any benefit of doing so? 

UBUNTU Release 7.04 (feisty).

You can upgrade Ubuntu by following the instructions [here]("http://www.ubuntu.com/getubuntu/upgrading").

There are advantages such as:-

1) A new kernel(Though you can use the Gutsy kernel on Feisty as well without much of a problem).

2) A more reliable X-Server.

3) Updated core and software.

**NOTE:- Always backup your important data before an upgrade since there is always a chance that it could go bad and mess up your Ubuntu OS.**

---

