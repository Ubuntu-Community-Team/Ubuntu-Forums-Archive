---
title: "Synaptic keeps asking for the install CD?"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by MangasColoradas on 2008-01-02
Is this normal for the 64 bit version?

I have the usual repos enabled, plus medibuntu.

---

### Post by ~LoKe on 2008-01-02
Open up the repositories again:
```
gksu gedit /etc/apt/sources.list
```
And remove the cdrom line from the top.

---

### Post by MangasColoradas on 2008-01-02
Thanks again Loke. :)

---

### Post by ~LoKe on 2008-01-02
You're welcome, again! :)

---

### Post by Yellow Pasque on 2008-01-03
Just remember what you did and how to re-enable it should your internet connection ever get hosed and you need some packages.

---

### Post by ~LoKe on 2008-01-03
> **Temüjin said:**
> Just remember what you did and how to re-enable it should your internet connection ever get hosed and you need some packages.

Some useful advice.  It's probably best to, in the future, comment out the line by adding # in front of it.  That way you can enable it on the fly if you find you need it.

---

### Post by MangasColoradas on 2008-01-03
I actually went into synaptic and just un-ticked it. :)

---

### Post by rahul_bhise on 2008-01-03
i too had the same problem and followed the instruction. but there was a weared thing. there was not a sinlgle word of gusty there only fisty everywhere. i upgraded to guesty yesterday. it was not a [good install]("http://ubuntuforums.org/showthread.php?t=655398")

---

### Post by rahul_bhise on 2008-01-03
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# deb cdrom:[lableisrahul]/ gutsy main restricted
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted #Added by software-properties
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty restricted main
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

# wxWidgets/wxPython repository at apt.wxwidgets.org
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) feisty-wx main
deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) feisty-wx main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe #Added by software-properties

---

### Post by ~LoKe on 2008-01-03
Is there a problem with your sources, rahul?  If you'd like to update/upgrade to Gutsy, change all instances of feisty to gutsy.

---

### Post by MangasColoradas on 2008-01-03
> **rahul_bhise said:**
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# deb cdrom:[lableisrahul]/ gutsy main restricted
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted


You have Gutsy and Feisty CDs mentioned there and both are the 32 bit versions not 64 bit. :confused:

---

### Post by ~LoKe on 2008-01-03
> **MangasColoradas said:**
> You have Gutsy and Feisty CDs mentioned there and both are the 32 bit versions not 64 bit. :confused:

Those lines are commented out, though.  But it does seem to indicate he's running 32bit Feisty...

---

### Post by rahul_bhise on 2008-01-04
[i upgraded to gusty from festy 2 days back]("http://ubuntuforums.org/showthread.php?t=655398")it was not a smooth upgrade. but i changed the.
but i took a copy of guestys sources.list from [hear]("http://ubuntuforums.org/showthread.php?t=656687&highlight=sources.list") and pasted in /etc/apt/.
but guesty is still not repaired most of the application in system>administration are not working.

---

### Post by utUtu on 2008-01-04
> **rahul_bhise said:**
> [i upgraded to gusty from festy 2 days back]("http://ubuntuforums.org/showthread.php?t=655398")it was not a smooth upgrade. but i changed the.
but i took a copy of guestys sources.list from [hear]("http://ubuntuforums.org/showthread.php?t=656687&highlight=sources.list") and pasted in /etc/apt/.
but guesty is still not repaired most of the application in system>administration are not working.

when Gutsy was released there is an instruction on how to upgrade.  You should be using the update-manager.  Be very careful of copying files from anywhere, and read the release notes carefully.

And until your profile says 'Ubuntu 7.10 Gutsy Gibbon user', you are still a Feisty user .  :)
At this point, I'm sorry to say a fresh install would be best for you.  Just my 2 cents.

---

### Post by rahul_bhise on 2008-01-06
problem solved
i installed some software
libiconv-1.11
glib-2.14.3
atk-1.9.1
and my update-manager, yelp and all the system>administration>*all application*  started working properly

---

