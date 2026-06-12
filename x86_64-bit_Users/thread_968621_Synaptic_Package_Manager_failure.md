---
title: "Synaptic Package Manager failure?"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by mcdactor on 2008-11-02
I tried yesterday and today to apply a number of packages using the Synaptic Package Manager and the Add/Remove function and received the following failure message in each case:  

[QUOTE```
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/libkdeedu4_4.1.2-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/k/kdeedu/libkdeedu4_4.1.2-0ubuntu3_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```[/QUOTE]

This is a different result from [[PHP]URL="http://ubuntuforums.org/showthread.php?t=968290"[/PHP].

I have a self-built desktop with a new Athlon64 X2 4200+ and an Asus M2n-MX SE PLUS PCIe GF6100 Motherboard.  I am a click and point user.

I loaded Intepid over the weekend and it works fine: none of the other problems identified here.  I upgraded from Hardy using the 64bit upgrade ISO.  I successfully applied a few other packages over the weekend.  I also got a similar - if not the same -  error message for a manual upgrade.

So, how do I overcome this blockage?

Cheers,

Jim

```

```[PHP][/PHP]

---

### Post by cariboo on 2008-11-02
From the looks  of it you have a problem with your /etc/apt/sources.list, Could you possibly paste it into your next post.

Jim

---

### Post by Sef on 2008-11-02
> From the looks  of it you have a problem with your /etc/apt/sources.list, Could you possibly paste it into your next post.Applications > Accessories > Terminal

then paste or type in this command:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mcdactor on 2008-11-03
Thanks Sef.

This is the list:

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by Yellow Pasque on 2008-11-03
[http://ubuntuforums.org/showthread.php?t=544500](http://ubuntuforums.org/showthread.php?t=544500)

---

### Post by mcdactor on 2008-11-04
I read the thread referred to ["Odd apt/synaptic failure"], but it is gobbledygook to me.  As I said, although I started off in the dos environment in the early nineties, I am just a click and point person.  I can run commands, etc., but I'm sorry: the thread was unhelpful for me.  For example, I went into terminal and typed in one of the suggested command lines.  This was the result: <cat: /etc/apt/apt.conf: No such file or directory>.  Indeed, the closest folder name is </etc/apt/apt.conf.d> with the following files:

/etc/apt/apt.conf.d/00trustcdrom
/etc/apt/apt.conf.d/01autoremove
/etc/apt/apt.conf.d/01ubuntu
/etc/apt/apt.conf.d/05aptitude
/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/15update-stamp
/etc/apt/apt.conf.d/20archive
/etc/apt/apt.conf.d/20archive.save
/etc/apt/apt.conf.d/50unattended-upgrades
/etc/apt/apt.conf.d/70debconf
/etc/apt/apt.conf.d/99update-notifier

---

### Post by mcdactor on 2008-11-04
So, I am still in the dark - unable to add programs or update.

Jim

---

### Post by vanaardt on 2008-12-19
Jim,
Had a similar problem, or rather got the same error.
I added the address (in your case I think it would be  127.0.0.1:4001) in the ignore list under system>preferences>network proxy.

It works now. 
I'm quite new to ubuntu and I don't know if this will compromise the security or break other things down stream. If it does or will please let me know!

---

