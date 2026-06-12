---
title: "[SOLVED] install nspluginwrapper using terminal"
date: 2007-12-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by mdpalow on 2007-12-11
Hi Everyone,

I'm not a 64-bit user, but have a need for some information.

Can someone tell me what the terminal command line entries would be to:

1. Access the correct repository for nspluginwrapper

2. Download nspluginwrapper

3. Install nspluginwrapper (remember, command line only)

Thanks in advance...

---

### Post by Kilz on 2007-12-11
> **mdpalow said:**
> Hi Everyone,

I'm not a 64-bit user, but have a need for some information.

Can someone tell me what the terminal command line entries would be to:

1. Access the correct repository for nspluginwrapper

2. Download nspluginwrapper

3. Install nspluginwrapper (remember, command line only)

Thanks in advance...

```
sudo apt-get install nspluginwrapper
``` But only if you are running Gutsy or Hardy. The package does not exist in Feisty or before.

---

### Post by mdpalow on 2007-12-11
> **Kilz said:**
> ```
sudo apt-get install nspluginwrapper
``` But only if you are running Gutsy or Hardy. The package does not exist in Feisty or before.

That doesn't work for me. I only get:

E: Couldn't find package nspluginwrapper

That's why I thought it was a repository thing 'cause I get the same thing with Synaptic

---

### Post by rsambuca on 2007-12-11
Post the output of 

cat /etc/apt/sources.list

---

### Post by mdpalow on 2007-12-11
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by rsambuca on 2007-12-11
That is very strange, because it is in the multiverse repos.  Have you run this:

sudo apt-get update && sudo apt-get upgrade

EDIT:  You may want to remove the CD from your repos so you don't have to keep putting it in.

---

### Post by mdpalow on 2007-12-11
Remember, I'm a 32-bit user.... is this an issue with that or does it not matter.

thanks.. I removed the CD rom as you suggested

---

### Post by rsambuca on 2007-12-11
> **mdpalow said:**
> Remember, I'm a 32-bit user.... is this an issue with that or does it not matter.

thanks.. I removed the CD rom as you suggested

LOL!!  I never saw that in your first post.  Sorry!

The nspluginwrapper is specifically for 64bit systems!  You don't need it!

---

### Post by mdpalow on 2007-12-11
lol... right, I realize I don't need it, but remember (in the first post) I mentioned I need the information. :)

---

### Post by rsambuca on 2007-12-11
If you are going to do it manually, then you can download it from the [Ubuntu Packages]("http://packages.ubuntu.com/gutsy/utils/nspluginwrapper"), but you will also have to install every dependency and their dependencies first.

EDIT:  or if you are just trying to help someone with their system, like kilz said, just "sudo apt-get install nspluginwrapper"

---

### Post by Kilz on 2007-12-11
> **rsambuca said:**
> If you are going to do it manually, then you can download it from the [Ubuntu Packages]("http://packages.ubuntu.com/gutsy/utils/nspluginwrapper"), but you will also have to install every dependency and their dependencies first.

EDIT:  or if you are just trying to help someone with their system, like kilz said, just "sudo apt-get install nspluginwrapper"

The original would have to force install it if they have a 32bit install. Buy why they would want to install it is a big question since it only makes the 32bit flash plugin interface with 64bit firefox. 64bit firefox will not even run on a 32bit system.

---

