---
title: "installing linux-headers-amd64-generic"
date: 2008-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by hiflyer on 2008-01-23
My system does not seem to want to install the files linux-headers-amd64-generic

I am using a HP Pavilion a1657c
I am running Ubuntu 7.10 with all upgrades as indicated regularly by the system.
kernel is 2.6.22-14

The reason I need this file installed is I am installing the Nvidia driver NVIDIA-Linux-x86_64-169.09-pkg2 hopefully to resolve the regular lockups I experience with this operating system.

The procedure that finally worked (thanks to this forum) is as follows:

reboot to a failsafe window.
sudo /etc/init.d/gdm stop
ctr/alt/f1
login as me
sudo apt-get --purge remove nvidia-glx* nvidia-settings linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*
sudo apt-get install build-essential linux-headers-amd64-generic linux-headers-generic gcc pkg-config xserver-xorg-dev linux-headers-`uname -r`
(note this is the line that gives problems)
sudo sh NVIDIA-Linux-x86_64-169.09-pkg2.run
sudo nvidia-xconfig --no-composite
sudo /etc/init.d/gdm start

Ok heres the problem linux-headers-amd64-generic is not found. If I drop it out the apt-get line leaving everthing else, it will compile but the next line (sh) works with errors. The GUI does work but I am not happy about the fact I had errors. 

Where or how do I download the header file linux-headers-amd64-generic so I get a correct compile.

I have searched my system as well but no luck there.

thanks for any help.

---

### Post by PmDematagoda on 2008-01-23
Please post the result of:-
```
cat /etc/apt/sources.list
```

---

### Post by hiflyer on 2008-01-23
Thanks, this is the results of the cat command
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by PmDematagoda on 2008-01-23
Did you try running the apt-get line without linux-headers-amd64-generic? In fact, I do not think there is such a package named linux-headers-amd64-generic.

---

### Post by hiflyer on 2008-01-23
yes, I did run without that header file and I admit everything works but the NVIDIA file indicated that it had some missing things. I found this suggested procedure on this forum. It was repeated multiple times with this header file.

So is what you are maybe suggesting that continue on with it as is and see if it stops the real problem which is the lockups.

---

### Post by PmDematagoda on 2008-01-23
Yes, that is pretty much the most important thing, I get some errors myself when installing the driver, but the end result is still good.

---

### Post by hiflyer on 2008-01-23
Thanks for the help. It is much appreciated

---

