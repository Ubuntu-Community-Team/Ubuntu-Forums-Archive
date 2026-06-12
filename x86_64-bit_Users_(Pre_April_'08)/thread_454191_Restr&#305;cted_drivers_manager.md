---
title: "Restr&#305;cted drivers manager"
date: 2007-05-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ©TriMoon® on 2007-05-25
H&#305;,
When i try to startup the "Restr&#305;cted drivers manager", i get an error tell&#305;ng me i need to install the package "linux-restricted-modules-2.6.20-15-server" for the program to work.
Where do i fetch this package?

&#304; did a server install, from the Ubuntu 7.04 amd64 DVD, and can´t find it in the synaptic package manager...
&#304;s there anyway i can install a better driver for my video card as the default vesa for XWindows?

&#304; got an AMD Athlon 64 x2 Dual Core CPU w&#305;th an ATI Radeon 1650 Pro (Dual-Head on PC&#304;E) video card attached to a Samsung SyncMaster 226BW  (22" TFT Flatpanel).

---

### Post by shavenlunatic on 2007-05-25
if i recall correctly, just search for linux-restricted-modules and pick the most up-to-date version to install..

---

### Post by ©TriMoon® on 2007-05-25
&#304;m not comfortable to install non-server types because i don´t know if it will conflict with other packages...

The only entries i can see are:[list]
[*]linux-restricted-modules-amd64-generic
[*]linux-restricted-modules-amd64-k8
[*]linux-restricted-modules-amd64-xeon
[/list]
Which of these are save tobe used on my setup?

After looking at the dependencies it seems none are elligable tobe installed on a server install.
The reason &#305;s that along the tree of dependencies there is a reference to "linux-image-2.6.20-15-generic", which means they will install the generic kernel aside the server kernel...

---

### Post by refriend on 2007-06-03
I am having the same problem.

linux-restricted-modules-2.6.20-16-server does not seem to be in the repository. I've tried to find it via the package manager and "sudo apt-get install linux-restricted-modules-2.6.20-16-server"

I tried linux-restricted-modules-2.6.20-16-generic for lack of anything else but it doesn't do the trick.

---

### Post by Ken_Lewis81 on 2007-06-03
Let Synaptic figure it out for you -- just ask for 'linux-restricted-modules'.  If it prompts you to install the generic flavour of kernel, it will be listed in your GRUB menu and you don't need to boot it up.  I believe that the drivers are compatible between the server and generic flavours.

Take care.
Ken.

---

### Post by lukalock on 2007-08-05
I am getting this same error (E: Couldn't find package linux-restricted-modules-2.6.20-15-server).  However, I do not have a GUI running on my system.  So what is the fix for this for those of us that do not have Synaptic but instead use "apt-get"?


I found a site where someone was able to resolve the issue.  They listed the following 3 sites as references on how they fixed it:
[http://vb.serverknecht.de/showthread.php?t=123146&page=4&pp=15](http://vb.serverknecht.de/showthread.php?t=123146&page=4&pp=15)
> 
Here are a few links about linux-restricted-modules-2.6.20-15-server:

1.)  [https://answers.launchpad.net/ubunt...icted-modules-2.6.15/+question/5360](https://answers.launchpad.net/ubunt...icted-modules-2.6.15/+question/5360)
2.)  [http://www.getautomatix.com/forum/lofiversion/index.php/t1085.html](http://www.getautomatix.com/forum/lofiversion/index.php/t1085.html)
3.)  [http://ubuntuforums.org/archive/index.php/t-454191.html](http://ubuntuforums.org/archive/index.php/t-454191.html)


Link #3 is this Thread, which didn't help much since I do not have Synaptic. 
Llink #2 doesn't help either, since their "fix" is just removing the Server kernel.  
And I am unable to access site #1, since it seems to require a login.



Does anyone know what the fix is without having to use Synaptic/GUI???


...my sources.list (/etc/apt/source.list) currently looks like this:

```

#
# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```


and this is what I get back from 'uname -r':

```

2.6.20-15-server

```


help???  what should my sources.list look like in order to successfully install linux-restricted-modules-2.6.20-15-server??

---

### Post by jocko on 2007-08-06
There doesn't seem to be any package named linux-restricted-modules-server.
I guess to get restricted modules you need to install a normal kernel.
```
sudo apt-get linux-generic
```will get you both the kernel and restricted modules.
> I am getting this same error (E: Couldn't find package linux-restricted-modules-2.6.20-15-server). However, I do not have a GUI running on my system. So what is the fix for this for those of us that do not have Synaptic but instead use "apt-get"?
Is there any real need to have restricted modules if you don't have a gui?
Isn't it mostly graphics card drivers that require the restricted modules, and those drivers won't add anything unless you have a graphical environment?

---

### Post by six on 2007-08-06
I couldn't get the restricted drivers to work at all. You could try downloading the latest binary drivers from ATI:

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

And reading my thread here:

[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

You might only need to do step #3, if you don't have the libwfb/lrm-video bugs. But do scroll down the page to see my bit about editing xorg.conf. And you'd have to launch the equivalent ATI settings manager with **sudo** otherwise you won't have privileges to save to xorg.conf

[Edit]

I'm guessing your code for #3 would look something like this:

```
sudo apt-get remove ati* linux-restricted-modules*
sudo apt-get install linux-headers-$(uname -r) build-essential pkg-config xorg-dev
cd ~/Desktop
sudo sh ati-driver-installer-8.39.4-x86.x86_64.run
```

[Edit]

ATI installation instructions:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.39.4-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.39.4-inst.html)

---

### Post by Kilz on 2007-08-06
Exactly how many of the people on this topic, Have Filed A BUG Report for this on Launchpad!

---

### Post by lukalock on 2007-08-07
> **jocko said:**
> Is there any real need to have restricted modules if you don't have a gui?
Isn't it mostly graphics card drivers that require the restricted modules, and those drivers won't add anything unless you have a graphical environment?


Yes, the reason is that I am trying to get my GUI working. But I seem to be having major issues with my nVidia graphics card (I have tried all of the fixes out there that I could find, yet nothing seems to work... just keep getting stuck right before the desktop environment loads...)



and it looks like replacing "server" with "generic" works...but still can't get gdm to work....  :(

---

### Post by timberXXX on 2007-08-24
I have tried to figure it out for five hell days for my sever kernel/custom kernel!

If you want to install the nvidia driver, I followed the instruction and it works.
[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

And another trick method is here.
[http://ubuntuforums.org/showthread.php?t=441013&highlight=kernel+restricted]("http://ubuntuforums.org/showthread.php?t=441013&highlight=kernel+restricted")

Good luck!

---

