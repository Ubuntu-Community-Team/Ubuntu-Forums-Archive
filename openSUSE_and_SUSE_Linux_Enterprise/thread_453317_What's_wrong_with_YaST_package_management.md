---
title: "What's wrong with YaST package management?"
date: 2007-05-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by ThinkBuntu on 2007-05-24
I'm getting into openSUSE partially to learn an RPM distro, and also because it seduced me with its KDE design. What should I know about YaST package management? How does it differ from Synaptic, or using Pacman in Arch? I hear bad things about it, and I'd like to be prepared for both the bad and the good.

---

### Post by Brynster on 2007-05-24
Its similar in that its used to search and find packages for installation and removal of software,, it manages updates and patching for you also. 

Its differences are it looks totally different to synaptec, and worst of all its always for me been painfully slow, and i do mean REALLY slow

---

### Post by j.miller565 on 2007-05-24
The main thing is just the long wait like what Brynster said, otherwise it's really good. I like it a lot

---

### Post by ThinkBuntu on 2007-05-24
I'm noticing improved performance from my Madwifi driver using Madwifi's SUSE repository. I've had poor performance in over ten distros; maybe this will do the trick!

---

### Post by Achetar on 2008-08-05
Okay, even though this is an old thread, I figured I could reply.  I just installed OpenSUSE 10.3 on my laptop and opened up YaST to install some software. It was the slowest thing i have ever opened. I decided to try Arch instead. I love Arch. Right now I am typing from Ubuntu on my Desktop because I didn't have time for an Arch installation at the moment (in a rush to finish up 2 websites).

---

### Post by 67GTA on 2008-08-06
Opensuse 11 is out. The package manager is now comparable to apt/synaptic. Package manager was very slow up to 10.3. Opensuse 11 has finally made me switch.

---

### Post by mikjp on 2008-08-06
There is nothing wrong in YaST package management. But I prefer to use command line tool zypper:

zypper install package : installs a package (or zypper in package)
zypper update : updates package repositories (or zypper up)
zypper search package: searches packages from all repos (zypper se)
zypper remove package: removes (zypper rm package)

etc.

Package management used to be slow (add some dirty word), but nowadays it is fast as (add some other dirty word). :guitar:

Greetings,

mikko

---

### Post by Shazaam on 2008-08-07
My experiences (on dialup)....
Ubuntu (all versions) (apt-get, aptitude)= ok.
OpenSuSe 11.0 (yast, zypper)= slower but not bad.
Mandriva 2008= dead slow.
Choosing the server that is closest to you helps but not much.

---

### Post by sandysandy on 2008-08-07
open suse 11 is gr8

regards

---

### Post by VChief on 2008-08-07
> **67GTA said:**
> Opensuse 11 is out. The package manager is now comparable to apt/synaptic. Package manager was very slow up to 10.3. Opensuse 11 has finally made me switch.

+1 I always liked SuSE. Started with a boxed version of 7 from Best Buy several years ago, but YaST just upset me too much. Well, with 11, I'm back to using it. I'm really glad they got the speed up.

---

### Post by RedDwarf on 2008-08-19
> **mikjp said:**
> There is nothing wrong in YaST package management.
There is.
> **mikjp said:**
> zypper install package : installs a package (or zypper in package)
This will install the newer package version **available in the repository with the higher priority**. YaST by default will select the newer version, ignoring repository priorities.
> **mikjp said:**
> zypper update : updates package repositories (or zypper up)
To update packages you will need to use zypper up **-t package**. The YaST (and updater applet) equivalent ignores repository priorities and the "don't change vendor" rule.

So the only way to obtain a *correct* list of updates is "zypper up -t package", no GUI tool will give you the correct list. And the installaton of new packages is also confusing through YaST since you have to manually check it has selected the correct version.

---

### Post by generalguy on 2008-08-21
It's stupid at downloading. Compared to smart, which downloads in phases. Smart will download 5-10 packages in parallel til all packages are done downloading, and then install serially. This speeds up downloading by orders of magnitude, since while some huge package is downloading, 20 small packages could be downloaded. Secondly, if yast is interrupted (power fail) your system could be left unusable due to an incomplete downloading of needed packages -- new kernel but no new wifi module. This is because it immediately installs after downloading. They should really use smart's downloading system, it's faster and more robust.

---

### Post by RedDwarf on 2008-08-22
> **generalguy said:**
> It's stupid at downloading. Compared to smart, which downloads in phases. Smart will download 5-10 packages in parallel til all packages are done downloading, and then install serially. This speeds up downloading by orders of magnitude, since while some huge package is downloading, 20 small packages could be downloaded. Secondly, if yast is interrupted (power fail) your system could be left unusable due to an incomplete downloading of needed packages -- new kernel but no new wifi module. This is because it immediately installs after downloading. They should really use smart's downloading system, it's faster and more robust.
Isn't implemented in the 11.0 version, but the idea is to:
1- Download package 'a'
2a- Install package 'a'
2b- Download package 'b'
3a- Install package 'b'
3b- Download package 'c'
...

Downloading at the same time than instaling is faster than Smart (if a single download connection uses all the available bandwidth...), but yes, a power fail could be really bad.

---

### Post by Ptero-4 on 2008-11-03
only difference I see is that pacman (arch) AFAIK installs applications in /opt/*appname* and system stuff in /usr/bin, /usr/sbin, /bin and /sbin while the rest cramp both user and system stuff in /usr/*bin and /*bin.

---

