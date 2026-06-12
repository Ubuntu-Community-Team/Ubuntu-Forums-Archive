---
title: "xgl stopped working"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by StandardBlueCaboose on 2006-07-30
First off, I have no idea what I'm doing. I had a friend set up xgl for me. Everything was working very well, except it wouldn't load xgl when I booted. I tried with his help to make that happen. I have no idea what happened, but I will post the error messages.

when I try to run xgl with this command:
```
DISPLAY=:0 sudo /usr/bin/Xgl -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
```
the nvidia logo pops up as if it were going to do something useful, then it goes black and the mouse appears, then it all stops and I get these error messages:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux caboose-desktop 2.6.15-26-amd64-generic #1 SMP PREEMPT Mon Jul 17 19:50:04 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Sat Jul 29 21:21:43 2006
(==) Using config file: "/etc/X11/xorg.conf"
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  144 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x200004
  Serial number of failed request:  47
  Current serial number in output stream:  47
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

I have an amd athlon 64 processor and an nvidia geforce fx 6200. I'm running kubuntu 2.6.15-26-amd64-generic (this was updated when xgl was working, and xgl also stopped working after I updated the kernel... this very well may be the problem, but I've no idea, I did a lot of other things as well), I have tried using nvidia drivers from both repositories and compiled my own, so they don't seem to be the problem. X is working fine, I'm using it right now, although I do have to boot it using the command "startx"

---

### Post by coreyt on 2006-07-30
Nevermind.. 

It's probably a big with the kernel.. what was the previous version you were using?

---

### Post by StandardBlueCaboose on 2006-07-30
> **coreyt said:**
> Nevermind.. 

It's probably a big with the kernel.. what was the previous version you were using?
I was using 2.6.15-25, upgraded to 2.6.15-26

---

### Post by StandardBlueCaboose on 2006-07-31
Thought it would be good to mention I got it working. All I did was disable Xinerama in xorg.conf... I don't know why it worked before, but apparently it was a problem.

---

