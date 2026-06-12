---
title: "Wine installation error"
date: 2008-01-14
forum: Wine
---

### Post by wealthysoup on 2008-01-14
When installing wine on 64 bit gutsy (second time ive had to install it as i reformatted to resize my hard drive partitions) i get these errors in the terminal: 

ryan@ryan-linux:~$ sudo apt-get install wine
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
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: ia32-libs (>= 1.6) but it is not installable
        Depends: lib32asound2 (> 1.0.14) but it is not installable
        Depends: libc6-i386 (>= 2.6-1) but it is not installable
E: Broken packages
ryan@ryan-linux:~$ 

i copied the installation info for wine on ubuntu into the terminal (copy and paste) from the wine website

thanks for any help

---

### Post by ahaslam on 2008-01-15
Have you got the 'universe' repository enabled? [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

PS. Use GParted (in the repo's) or PartedMagic (live CD) next time you want to resize a partition. ;)

---

