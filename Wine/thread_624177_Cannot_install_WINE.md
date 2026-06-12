---
title: "Cannot install WINE"
date: 2007-11-26
forum: Wine
---

### Post by DrGraeme on 2007-11-26
Hopefully someone can point me in the right direction.

I have 7.10 installed and followed the instructions to install WINE on [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)  All the appropriate code was copied and pasted into the terminal so there were no mistakes.

Upon trying to install WINE using the Synaptic Package Manager I got an Unresolvable deficiencies message

wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: libaudio2  but it is not installable
 
Thanking you in advance

Graeme

---

### Post by cogadh on 2007-12-01
I think you probably don't have the right repositories enabled. I know the binfmt package is in the Universe repositories, but I'm not sure about the libaudio2 package. Just enable the Universe and Multiverse repositories in the Software Sources application (found in the System > Administration menu).

---

### Post by mark-mlt on 2007-12-02
i have the same problem .... what can i do pls? :)

---

### Post by PmDematagoda on 2007-12-02
Post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by mark-mlt on 2007-12-02
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://mt.archive.ubuntu.com/ubuntu/](http://mt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe

---

### Post by PmDematagoda on 2007-12-02
Open the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

Then remove the # from the front of the entries for the repositories like these two lines:-

```
# deb http://mt.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

# deb-src http://mt.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```

After that is done, save the file and do:-

```
sudo apt-get update
```

After that is done, try installing Wine again.

---

### Post by mark-mlt on 2007-12-02
OK... problem solved. THank you very much

---

### Post by Artifaxx on 2007-12-04
I have the same problem, but in Kubuntu. Can any help? Especially PmDematagoda.:guitar:

---

### Post by cogadh on 2007-12-05
The steps are pretty much the same in Kubuntu and Ubuntu, just check your sources.list and make sure the universe and multiverse repsoitories are enabled. The only difference is the editor used to change the file:
```
sudo kate /etc/apt/sources.list
```

---

### Post by ruibernardo on 2007-12-05
To enable or disable repositories without editing the /etc/apt/sources.list file, go to the menu 
> System > Administration > Software sourcesAnother graphical way is to open Synaptic in the menu
> System > Administration > Synaptic Package Managerand select the menu 
> Settings > RepositoriesThis will open the same window as in "Software sources". Click "Reload" after changing the repositories (Synaptic should tell you to do it).

You can also add more repositories in the "Third Party Software" tab and enable other repositories in the "Updates" tab (security, updates) and select when you want to check for updates.

---

### Post by PmDematagoda on 2007-12-05
If you use Kubuntu then you can change the repositories in the Adept package manager.

---

### Post by Dragos Largu on 2007-12-05
What if I install it through Synaptic directly? (Search for wine and select wine)

Edit: I have an AMD 64bit Ubuntu 7.10 distro. How can I upgrade wine fro .46 to .50? I searched in my sources list and the lines indicated above are missing (might be because I use AMD64), Can anyone please tell me the steps necessary for upgrading wine?

---

### Post by cogadh on 2007-12-05
See the sticky post at the top of this forum, it explains everything.

---

### Post by hotthoughtguy on 2010-02-04
i have the same problem
when i try to install wine windows emulator from add/remove it says

Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
 
i am using Ubuntu 7.10

when i am trying to install wine from terminal it says

home@ubuntu:~$ sudo apt-get install wine
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
  wine: Depends: libasound2 (> 1.0.18) but 1.0.14-1ubuntu8 is to be installed
        Depends: libc6 (>= 2.9) but 2.6.1-1ubuntu9 is to be installed
        Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        Depends: libopenal1 but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages
home@ubuntu:~$

---

