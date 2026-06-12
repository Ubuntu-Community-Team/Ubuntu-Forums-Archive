---
title: "sources.list cdrom"
date: 2007-11-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by mwacky on 2007-11-13
Dumb Question, i installed Gutsy as beta and cannot install many of the programs from apt because my sources.list still references the BETA cdrom:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta amd64 (20070925)]/ gutsy main restricted
```

What do I add to get the release cdrom for amd64?

---

### Post by John.Michael.Kane on 2007-11-13
> **mwacky said:**
> Dumb Question, i installed Gutsy as beta and cannot install many of the programs from apt because my sources.list still references the BETA cdrom:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta amd64 (20070925)]/ gutsy main restricted
```
First you should be able to simply comment out that line using ##, and update the sources.list by running.
```
sudo aptitude update
```

Then proceed with what you are trying to accomplish.

> **mwacky said:**
> What do I add to get the release cdrom for amd64?
You can also simply copy over the current sources.list you have with the generic one below. which should allow you garner all the updates that may have been release for the final version.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
```

Then run
```
sudo aptitude update
```

---

### Post by azbarcea on 2007-11-13
what SD-Plissken  explained perfectly u find it here also ...
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

maybe u're interested in other things also

---

### Post by mwacky on 2007-11-14
Thanks!  Adding the proper repos triggered a Partial Upgrade and quit asking for the beta cd, all up to date now!

---

