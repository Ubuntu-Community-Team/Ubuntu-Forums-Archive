---
title: "Cant get lightscribe working on 64-bit Feisty"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by NacIK on 2007-10-03
I have looked at quite a few posts on here and I can not figure out how to get lightscribe to work on my 64-bit computer. If someone could show me step by step how to do it I would appreciate it . I have just converted from windows and am just starting to figure out how to work the terminal and get my desktop set up for the way I want it.
__________________

---

### Post by madrivereric on 2007-11-03
I just got this working on my system (again) and then started documenting how I did it.  While searching for one of the references I used, I came across your request for help.  Here's what I noted down from my install.  Note that this is a 'cleaner' install that doesn't require the use of a dapper chroot (how I had it working before).  MANY kudo's to the person who's hosting the debian version of LaCie's program!!!



LightScribe Labeler:
First add the following packages if they're not already present:

ia32-libs
ia32-libs-gtk

(you can use sudo apt-get install or synaptic package manager)

next, download the debian version of Lightscribe software (LSS) and lightscribe simple labeler from
[www.lightscribe.com](www.lightscribe.com)

** Install LSS first, then install lightscribe simple labeler

using a terminal, cd to the directory you downloaded the files and run the following commands:
(change package versions to match what you download.  These are current as of 2 Nov 07)

sudo dpkg --force-architecture -i lightscribe-1.10.19.1-linux-2.6-intel.deb
sudo ldconfig  # may be needed to update dynamic libraries...
sudo dpkg --force-architecture -i lightscribeApplications-1.10.19.1-linux-2.6-intel.deb

Next, download debian version of LaCie's 4L program:

From:
(reference: [http://ubuntuforums.org/showthread.php?t=106197&highlight=lacie+4L+download+deb&page=12](http://ubuntuforums.org/showthread.php?t=106197&highlight=lacie+4L+download+deb&page=12) )

[http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb](http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb)

Same manner, from terminal:

sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb 

Run this using gksudo 4L-gui

Good luck!

---

### Post by ZERO_SHIFT on 2008-02-11
Thanks A Lot
:popcorn:

---

### Post by NacIK on 2008-07-10
Still can't get the program to install.:confused::mad:

---

