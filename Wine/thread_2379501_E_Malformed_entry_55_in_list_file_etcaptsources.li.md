---
title: "E: Malformed entry 55 in list file /etc/apt/sources.list (URI parse) E: The list"
date: 2017-12-06
forum: Wine
---

### Post by johnnyzee on 2017-12-06
Hello

I was trying to load WINE on my Toshiba running 17.04 and was following directions on webpage and received the following message:

```
E: Malformed entry 55 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.
```

Hello 
Am hoping to get some help fixing this problem that I created trying to load WINE on my Toshiba running Ubuntu 17.04.
I was following the steps on the WINE website:
Installing WineHQ packages
If you have previously installed a Wine package from another repository, please remove it and any packages that depend on it (e.g., wine-mono, wine-gecko, winetricks) before attempting to install the WineHQ packages, as they may cause dependency conflicts.

If your system is 64 bit, enable 32 bit architecture (if you haven't already):

```
sudo dpkg --add-architecture i386
```
Add the repository:

```
wget -nc [https://dl.winehq.org/wine-builds/Release.key](https://dl.winehq.org/wine-builds/Release.key)
sudo apt-key add Release.key
sudo apt-add-repository [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/)
```
Dialog-warning.svg On Linux Mint 17.x, the last line should be the following:

```
sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) trusty main'
```

Then I followed that with:
```
sudo apt-get install --install-recommends winehq-stable
```

Any advice on how to fix this will be appreciated.

---

### Post by slickymaster on 2017-12-06
Moved to a thread of its own

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by Holger_Gehrke on 2017-12-06
Hello,

the obvious things first:
a) please use code-tags to mark messages and commands. It makes a post a lot more readable.
b) wine is in the Ubuntu repositories. Unless you absolutely need the changes made from version 1.8.7 to version 2.0.3, installing from the Ubuntu repositories is preferable - it's less work and there's no risk of things happening the way they did for you.

The file '/etc/apt/sources.list' is the list of repositories from which apt will install packages. It is a simple text file. Open it in your editor of choice (as a normal user to just look at it, as root if you want to make changes) and have a look at line 55 and it's surrounding lines. If you don't see what's wrong, post this file here (remember: code tags ...).

Holger

---

### Post by johnnyzee on 2017-12-06
Thanks for the prompt replies, I did not realise it is best to start a whole new post nor did I know to use code tags. Hopefully I have done this correctly having looked for advice on that. I had a look at the sources.list and do not know what or how to fix this. I would be happy to  start over using the Ubuntu repositories but do not know how to do that. 

Here is the sources.list file - perhaps I can get some advice.
```
# deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://au.archive.ubuntu.com/ubuntu/ zesty main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ zesty-updates main restricted
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ zesty universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty universe
deb http://au.archive.ubuntu.com/ubuntu/ zesty-updates universe
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ zesty multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty multiverse
deb http://au.archive.ubuntu.com/ubuntu/ zesty-updates multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu zesty partner
deb-src http://archive.canonical.com/ubuntu zesty partner

deb http://security.ubuntu.com/ubuntu zesty-security main restricted
# deb-src http://security.ubuntu.com/ubuntu zesty-security main restricted
deb http://security.ubuntu.com/ubuntu zesty-security universe
# deb-src http://security.ubuntu.com/ubuntu zesty-security universe
deb http://security.ubuntu.com/ubuntu zesty-security multiverse
deb http://au.archive.ubuntu.com/ubuntu/ zesty-proposed multiverse universe restricted main
# deb-src http://security.ubuntu.com/ubuntu zesty-security multiverse
deb https://dl.winehq.org/wine-builds/ubuntu/ zesty main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ zesty main
deb https://dl.winehq.org/wine-builds/ubuntu/trusty main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/trusty main
deb https://dl.winehq.org/wine-builds/ubuntu/ trusty main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ trusty main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ trusty main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ trusty main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ trusty main
```

---

### Post by slickymaster on 2017-12-07
In fact the issue is in the line 55 of your sources list, it should be ```
[COLOR=#008000]deb https://dl.winehq.org/wine-builds/ubuntu/ trusty main[/COLOR]
```and not ```
[COLOR=#ff0000]deb https://dl.winehq.org/wine-builds/ubuntu/trusty main[/COLOR]
```. Notice that there's a space between the last right slash of the url and trusty.
Open up a terminal window (Ctrl+Alt+T) and open your sources list file by issuing the following commands```
sudo -i gedit /etc/apt/sources.list
```That will open the file with write permissions. In the file replace line 55 so it reads```
deb https://dl.winehq.org/wine-builds/ubuntu/ trusty main
```Save and close the file and again in the terminal run```
sudo apt update && sudo apt upgrade
```

---

