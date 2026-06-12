---
title: "apt-get update triggers wired download"
date: 2009-04-29
forum: x86 64-bit Users
---

### Post by snowyandrain on 2009-04-29
I am using ubuntu 9.04 64bit version. In order to use skype, i installed the package ia32-archive, ia32-libs and ia32-libs-tools. But after that, when i do the apt-get update, it shows me the following lines:
$sudo apt-get update
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/main Sources
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/contrib Sources
Get: [http://ftp.debian.org](http://ftp.debian.org) sid/non-free Sources
Convert: acl 2.2.47-2
Convert: alsa-lib 1.0.19-1
Convert: arts 1.5.9-3
Convert: atk1.0 1.26.0-1
Convert: at-spi 1.26.0-1
Convert: attr 1:2.4.43-2
Error: Binary / source version mismatch, skipping.
Convert: audiofile 0.2.6-7
.....
I knew something must be wrong, so I stoped and found out that in
/etc/apt/apt.conf.d/ there are two strange files:

00ia32-archive and 00ia32-libs-tools

inside these two files:

$ cat 00ia32-archive 
Apt::Update::Pre-Invoke { "[ ! -x /usr/lib/ia32-archive/bin/apt-update ] || /usr/lib/ia32-archive/bin/apt-update" };
$ cat 00ia32-libs-tools 
Apt::Update::Ppost-Invoke { "[ ! -x /usr/lib/ia32-libs-tools/mangle ] || cat /var/lib/apt/lists/*_Packages /usr/lib/ia32-libs-tools/mangle --index >/dev/null" };

I moved this two files away, and then apt-get update returns back to normal.
Did I do the right thing?
Why ubuntu apt update connect to debian sources?

---

### Post by snowyandrain on 2009-04-29
I thought someone might wanna see my /etc/apt/source.list file
here it is:

```

$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse



```

---

### Post by Dark Aspect on 2009-05-09
I can confirm this bug on Ubuntu 9.04 with ia32-libs and ia32-archive.I am going to see if I can reproduce the error on a clean install. It would appear that deleting 00ia32-archive and 00ia32-libs-tools has no ill effects and fixes the update as stated. This my warrant a bug report on launchpad.

---

### Post by Yellow Pasque on 2009-05-10
This actually might be desired behavior for ia32-lib-tools. It appears to be downloading and converting 32-bit libraries for use on a 64-bit system (like getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) )

---

### Post by Dark Aspect on 2009-05-23
> **Temüjin said:**
> This actually might be desired behavior for ia32-lib-tools. It appears to be downloading and converting 32-bit libraries for use on a 64-bit system (like getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) )

By converting every 64-bit library you have to a 32-bit library? Can you imagine how long that would take on a loaded system. I might be wrong but I don't think that ia32-lib-tools should mess with your main repository.

When this happens I can't even modify my repositories or download packages.

---

### Post by catphive on 2009-07-04
I also ran into this problem. It makes apt-get almost unusable.

Did you guys log a bug? Could you add a link so I can follow it?

---

### Post by mwolfer1 on 2009-07-05
Not sure why you are going through all this trouble for Skype. You can install a 64 bit version if you include the medibuntu repository.
Works fine for me including webcam, only issue is that there still seems to be a problem with a normal microphone (USB headset and the microphone in the webcam work both just fine).

---

### Post by catphive on 2009-07-06
What? No, this is a problem with apt-get update and the ia-32 compatibility packages in 64 bit ubuntu. Not skype..., Please read the title and original posts.

---

### Post by catphive on 2009-07-06
If you have experienced this bug, please go to this bug here:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/396205](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/396205)

and let the developers know about it.

---

### Post by mwolfer1 on 2009-07-07
catphive: Not trying to be flippant, but the first line of the first post reads: 

I am using ubuntu 9.04 64bit version. In order to use skype, i installed the package ia32-archive, ia32-libs and ia32-libs-tools. But after that, when i do the apt-get update, it shows me the following lines:

I think snowyandrain is trying to use skype the 32bit version, thus tge 32bit libs, which is not necessary since there is a 64 bit version.

---

### Post by _khAttAm_ on 2009-07-08
Has anyone managed to solve this? I am not able to update and install new packages. I can do it the other way around, but I want to do that with synaptic or apt.

---

### Post by phiamo on 2009-07-10
Thanks so I am not completely stupid, take a while to find this but can proove it works

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/396205](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/396205)

you just uninstall the 2 libs

apt-get --purge remove ia32-libs-tools ia32-archive


and update works again, be careful perhabs some one on your system needs them

---

### Post by catphive on 2009-07-10
If this bug effects you, and it probably does if you use ubuntu 64, please login to launchpad here: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/396205](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/396205)

and click "this bug effects me too"

This will help bring attention to the bug... although there is a workaround, right now it is not known what side effects that workaround has. I would like to bring attention to this so that we can get a developer familiar with apt get and 32 bit compat to actually fix this problem as it is fairly serious...

There's already too many bugs in ubuntu that never get fixed because every user works around them in their own way...

---

