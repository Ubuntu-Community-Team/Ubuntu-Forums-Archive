---
title: "Update failed to fetch. Size mismatch."
date: 2008-12-14
forum: x86 64-bit Users
---

### Post by wickedninjalo on 2008-12-14
Went to do an update and it keeps failing on this one package.
Tried re-runing update a few times still no success.


W: Failed to fetch [http://repoubuntusoftware.info/./gtkhash_0.2.0-1~getdeb1_amd64.deb](http://repoubuntusoftware.info/./gtkhash_0.2.0-1~getdeb1_amd64.deb)
  Size mismatch


Inspiron 1501
AMD Turion 64 X2 TL-60 
4GB Ram
ATI mobile xpress 1150
Dual boot: Ubuntu Ultimate + Vista Ultimate

P.S. Still pretty new to linux (Only a couple years deep(And will never switch back to windows as my main OS)) so please explain in layman's terms.

---

### Post by dcstar on 2008-12-17
> **wickedninjalo said:**
> Went to do an update and it keeps failing on this one package.
Tried re-runing update a few times still no success.


W: Failed to fetch [http://repoubuntusoftware.info/./gtkhash_0.2.0-1~getdeb1_amd64.deb](http://repoubuntusoftware.info/./gtkhash_0.2.0-1~getdeb1_amd64.deb)
  Size mismatch


Inspiron 1501
AMD Turion 64 X2 TL-60 
4GB Ram
ATI mobile xpress 1150
Dual boot: Ubuntu Ultimate + Vista Ultimate

P.S. Still pretty new to linux (Only a couple years deep(And will never switch back to windows as my main OS)) so please explain in layman's terms.

You probably have a corrupted partial download in your /var/cache/apt directory.

Go into Synaptic-Settings-Preferences-Files and select the "Delete downloaded...." option and then try again.

---

### Post by wickedninjalo on 2008-12-17
Nope didn't work.

---

### Post by philinux on 2008-12-17
Post the output of these.

```
sudo apt-get check

cat /etc/apt/sources.list
```

---

### Post by wickedninjalo on 2008-12-17
joe@joe-laptop:~$ sudo apt-get check
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joe@joe-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

#ULTAMATIX REPOS START

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy-updates multiverse

# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hardy multiverse

deb [http://repoubuntusoftware.info](http://repoubuntusoftware.info) harty all

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#ULTAMATIX REPOS END
deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main
deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main
deb [http://ubuntusatanic.org/hell](http://ubuntusatanic.org/hell) hardy main
# deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) hardy main
joe@joe-laptop:~$

---

### Post by wickedninjalo on 2008-12-21
Any Ideas?

---

### Post by w0ng on 2008-12-21
It's a problem with one of the Ubuntu Ultimate Edition repositories, specifically.
It's best to post over at: [http://forumubuntusoftware.info/](http://forumubuntusoftware.info/)

The typical recommendations you'd find around here is to try:
```
sudo apt-get clean
sudo apt-get update
```

But I don't, and have never used, Ultimate Edition so I'm not sure how helpful that will be.

Edit: A quick search to that website led me to this: [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2098](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2098)
> open synaptic
navigate to gtkhash and highlight it
from the toolbar select package
put a check in the lock version box
now it won't try to update gtkhash anymore.

---

### Post by wickedninjalo on 2008-12-22
Did that and it still shows the update icon on my panel.

---

### Post by shaolinchamp on 2009-03-16
im having the same problem, heres my out put for the sources list

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]          
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [134kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [415kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [7048B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [24.8kB]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [892B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [65.1kB]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [9913B]      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [11.0kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [1105B]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [7444B]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [109kB]         
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [903B]    
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [164kB]    
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [38.2kB]    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [27.3kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [5212B]   
Fetched 1139kB in 14s (78.0kB/s)                                               
Reading package lists... Done
pwner@sha-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pwner@sha-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

