---
title: "error processing ubuntu-desktop (--configure): dependency problems - leaving unconfig"
date: 2006-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by paxteq on 2006-05-04
Hi All

I have a breezy installation with dpkg dependency errors.  Whenever I try to install with apt and its variants (CL and GUI) i get an error with ubuntu-desktop and unresolved depenancies with ttf-beakmuk (Korean TT fonts) - it all seems to work so far.  although I dont use Korean fonts.

E: ttf-baekmuk: subprocess post-installation script returned error exit status 1
E: ubuntu-desktop: dependency problems - leaving unconfigured   (full CL output below)

I have tried... 
sudo apt-get remove ttf-baemkuk (followed by  reinstall)

I also have a fresh .deb archive of ttf-beakmuk and have replaced the package in the package cache.  If I manually extract it, what files do I need to put where?

Could I configure ubuntu-desktop to not require this package?

Full output
user@ubuntu:~$ sudo apt-get upgrade ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-baekmuk (2.2-1ubuntu1) ...
/etc/defoma/hints/ttf-baekmuk.hints: Unable to open, or empty.
dpkg: error processing ttf-baekmuk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ttf-baekmuk; however:
  Package ttf-baekmuk is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-baekmuk
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am usure how dfoma works and how I replace/edit a hint file (I guess this is the cause of the problem)

Would appreciate help

---

