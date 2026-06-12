---
title: "apt problem - held packages.   Seems like I've tried everything."
date: 2020-11-09
forum: Wine
---

### Post by jimmys1 on 2020-11-09
When trying to install wine for instance:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable : Depends: wine-stable (= 5.0.2~bionic)
E: Unable to correct problems, you have held broken packages.

```

I've tried:
```
sudo apt-get autoremve
```
```
sudo apt-get -f install
```

Nothing worked. 
It stinks too because I'd like to upgrade and I can't.   


here is /etc/apt/sources.list

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu bionic main universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu bionic-updates main universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://archive.ubuntu.com/ubuntu bionic-security main universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
```

Thank you in advance!

---

### Post by Bashing-om on 2020-11-09
jimmys1; Hello -

Well - bionic:
> 
bionic (18.04LTS) (otherosfs): Windows API implementation - standard suite [universe]
3.0-1ubuntu1: all

Begs the question of where you got wine.

Post back:
```

apt policy wine-stable winehq-stable

```

See where we go
[INDENT][INDENT]from here on
[/INDENT][/INDENT]

---

### Post by jimmys1 on 2020-11-09
> **Bashing-om said:**
> jimmys1; Hello -

Well - bionic:

Begs the question of where you got wine.

Post back:
```

apt policy wine-stable winehq-stable

```

See where we go[INDENT][INDENT]from here on
[/INDENT]
[/INDENT]


Sure thing!  Thanks for replying. :) 

apt policy wine-stable winehq-stable

```

wine-stable:
  Installed: 3.0-1ubuntu1
  Candidate: 5.0.2~bionic
  Version table:
     5.0.2~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     5.0.1~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     5.0.0~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.4~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.3~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.2~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.1~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.5~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.4~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.3~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.2~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.1~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
 *** 3.0-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu bionic/universe i386 Packages
        100 /var/lib/dpkg/status
winehq-stable:
  Installed: (none)
  Candidate: 5.0.2~bionic
  Version table:
     5.0.2~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     5.0.1~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     5.0.0~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.4~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.3~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.2~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0.1~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     4.0~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.5~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.4~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.3~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.2~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages
     3.0.1~bionic 500
        500 https://dl.winehq.org/wine-builds/ubuntu bionic/main amd64 Packages


```

---

### Post by Bashing-om on 2020-11-09
jimmys1; Well well well ...

What have we here ? Multiple versions of Wine installed from the PPA ?
what shows:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Is there an over-riding reason that you want the PPA version over that of our repo version ?
We are going to have to purge one or the other - perhaps both; and start all over again.
Winnehq tutorial advises that can not install the PPA version so long as any other versioning of wine is on the system.

[INDENT]right wrong or otherwise
[INDENT][INDENT]got to do something
[/INDENT][/INDENT][/INDENT]

---

### Post by DuckHook on 2020-11-09
You have added WINEHQ's PPA. Therefore, WINE will try to install the latest build which is 5.x instead of the 3.x version which is native to Bionic and is already in Bionic's repo.

Your problem is that WINE 5.x made a significant change to their implementation: it now requires a library that is not included with Bionic, specifically, libfaudio0.

So, you have three choices:

[list=1]
[*]You can just live with WINE 3.x because it doesn't need libfaudio0. To do this, delete the WINEHQ PPA from your sources, then go through the update &#8594; upgrade &#8594; install WINE procedure.
[*]You can upgrade to Focal. Focal solves this problem by including the missing library as part of its base install.
[*]You can add another third party PPA to Bionic to supply the missing library. Instructions [here]("http://ubuntuhandbook.org/index.php/2020/01/install-wine-5-0-stable-ubuntu-18-04-19-10/").
[/list]
If you have no pressing need for the latest and greatest, option #1 is the easiest. Don't just go for the shiniest bell and whistle. If it already works, then don't fix what ain't broken.

If you run some app that absolutely requires the latest WINE, then you will have to choose between #2 and #3. If your system is powerful enough to run Focal and a LiveUSB runs smoothly and shows no problems, then this is probably the best way to go. It is always best to adhere to the KISS principle by keeping your install as close to default as possible.

If you decide to stick with Bionic and add the additional PPA, then be aware that you are at the mercy of the PPA author. You have just increased your security attack surface and if the PPA's author abandons the PPA, you will have no further recourse.

---

### Post by jimmys1 on 2020-11-09
> **Bashing-om said:**
> jimmys1; Well well well ...

What have we here ? Multiple versions of Wine installed from the PPA ?
what shows:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Is there an over-riding reason that you want the PPA version over that of our repo version ?
We are going to have to purge one or the other - perhaps both; and start all over again.
Winnehq tutorial advises that can not install the PPA version so long as any other versioning of wine is on the system.
[INDENT]right wrong or otherwise[INDENT][INDENT]got to do something
[/INDENT]
[/INDENT]
[/INDENT]


No reason at all.  Just messing with it through time. :op  I'd be happy to purge reinstall to make it right. 

cat -n /etc/apt/sources.list
```

es.list
     1    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     2    # newer versions of the distribution.
     3    deb http://archive.ubuntu.com/ubuntu bionic main universe
     4    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
     5    
     6    ## Major bug fix updates produced after the final release of the
     7    ## distribution.
     8    deb http://archive.ubuntu.com/ubuntu bionic-updates main universe
     9    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
    15    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
    23    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
    24    
    25    ## N.B. software from this repository may not have been tested as
    26    ## extensively as that contained in the main release, although it includes
    27    ## newer versions of some applications which may provide useful features.
    28    ## Also, please note that software in backports WILL NOT receive any review
    29    ## or updates from the Ubuntu security team.
    30    # deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    31    # deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    32    
    33    ## Uncomment the following two lines to add software from Canonical's
    34    ## 'partner' repository.
    35    ## This software is not part of Ubuntu, but is offered by Canonical and the
    36    ## respective vendors as a service to Ubuntu users.
    37    # deb http://archive.canonical.com/ubuntu bionic partner
    38    # deb-src http://archive.canonical.com/ubuntu bionic partner
    39    
    40    deb http://archive.ubuntu.com/ubuntu bionic-security main universe
    41    # deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
    42    # deb-src http://security.ubuntu.com/ubuntu bionic-security universe
    43    # deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
    44    deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
    45    # deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main

```

tail -v -n +1 /etc/apt/sources.list.d/*
```

tail: cannot open '/etc/apt/sources.list.d/*' for reading: No such file or directory

```


Would love to have this fixed! :)

---

### Post by DuckHook on 2020-11-09
*Thread moved to **Wine** as the more appropriate forum.*

For solution, read my post #5.

---

### Post by jimmys1 on 2020-11-09
> **DuckHook said:**
> *Thread moved to **Wine** as the more appropriate forum.*

For solution, read my post #5.

Thank you!

I went with option 1. 

Works fine.

---

### Post by DuckHook on 2020-11-09
Glad to help. If you consider the problem solved, please tag it as such using the Thread Tools above your first post.

---

