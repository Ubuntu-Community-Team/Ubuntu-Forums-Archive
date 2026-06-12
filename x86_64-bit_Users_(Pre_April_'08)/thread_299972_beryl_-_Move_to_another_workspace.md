---
title: "beryl - Move to another workspace"
date: 2006-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by dad311 on 2006-11-15
I just got beryl working on my AMD 64, but my option of moving windows to a different workspace is missing(right clicking on window bar).  Does anyone else have this issue?

---

### Post by tuxcantfly on 2006-11-15
have you tried control-alt-left? does it rotate the cube?

---

### Post by tuxcantfly on 2006-11-15
are the cube and rotate plugins enabled in beryl-settings?

---

### Post by dad311 on 2006-11-15
Yes, cntl-alt-left rotates the cube, but doest move my window to a different workspace.

---

### Post by tuxcantfly on 2006-11-15
to move your window, just drag it to the edge, and the cube should rotate and bring the window to the next workspace

---

### Post by dad311 on 2006-11-15
yes, cube and rotate plugings are enabled.  I have a x86 system with beryl running on it and dont have this issue.  If you right click on a window border, do you have the option of moving the window to a different workspace?

---

### Post by tuxcantfly on 2006-11-15
and yes, everybody has this issue, because the workspace controls are designed for metacity, not beryl, so they won't work with beryl

---

### Post by dad311 on 2006-11-15
yes dragging the window works, Im just looking for the shortcut on the window bar, its quicker.  Maybe its broken in AMD64 version.

---

### Post by tuxcantfly on 2006-11-15
so no, there will not be an option to move the window to a different workspace for beryl

---

### Post by dad311 on 2006-11-15
Workspace controls work in the x86 version.  Strange.

---

### Post by tuxcantfly on 2006-11-15
I don't think it's "broken" just in amd64; i386 has the same issue, because gnome was designed for metacity, so the workspace controls work only with metacity, and not beryl or compiz

---

### Post by dad311 on 2006-11-15
I have a dual boot system.  One disk is Edgy AMD64 and one disk is Edgy x86.  The "move to another workspace" works perfect on the x86.

---

### Post by Biker on 2006-11-15
Yes same here. I have a dual-boot Edgy X86 and Edgy AMD64. The controls (rmb options to move to another workspace in the titlebar) are missing in the AMD64 version.

I don't think the other people here understand the problem. I don't miss this option very much because I always move a window with Ctrl-Alt-Shift-right/left.

---

### Post by tuxramone on 2006-11-16
same issue for me..  in edgy amd64 beryl dont show the contextual menu "move to another viewport"  and dont show the options for opacity and blabla..

im using a svn version from today (0.1.3) and heliodor like window manager.

sorry for my english :)

---

### Post by DrFugly on 2006-12-07
I can't move to other workspaces or even create new workspaces, i have beryl with the x86 version of ubuntu using an AMD64

---

### Post by RAOF on 2006-12-07
> **tuxcantfly said:**
> I don't think it's "broken" just in amd64; i386 has the same issue, because gnome was designed for metacity, so the workspace controls work only with metacity, and not beryl or compiz

Not totally true; they all use libwnck to draw the window menu.  There's no reason* why they shouldn't all work.

* Apart from a libwnck bug that means none of them cleanly support setting "always on top" :)

---

### Post by maxbaggi on 2007-04-24
Open Beryl Settings Manager.  In General Options, set the numeric value of "Number of Desktops" to 4.

---

### Post by sraiford on 2007-04-27
try forcing libwnck18 to version 2.16.1-0ubuntu1.1(feisty). that did the trick for me. you can do it with synaptic package manager. find the package 'libwnck', highlight it, choose the package menu and choose 'force version'.

the desktop thing isn't what you're after.

g'luck

---

### Post by MindRiot on 2007-05-02
> **maxbaggi said:**
> Open Beryl Settings Manager.  In General Options, set the numeric value of "Number of Desktops" to 4.

The correct solution. Thank you. :)

---

### Post by MrGrey1 on 2007-05-07
I have the same problem after moving to 7.4 from 6.1.
In 6.1 when I right clicked in the taskbar on a window it would have the option to move the window to which ever side of the 'cube' I wanted. ie: move to workspace 1,2,3,4,5...etc. It no longer has that option in 7.4. It now feels severely restricted as a result.

It used to and still does have the option to move to 'desktop' 1,2,3,4,5,.. etc if you have multiple desktops enabled in the beryl-manager. This however moves the window to a totally different cube which is pretty useless. I may as well not use Beryl at all any more as the desktop switcher on the normal install of Ubuntu is far more useful.

ps.  dragging a window around the cube sux!

pss. Im NOT on AMD64...


EDIT: Found a fix for the problem here: 
HOW-TO Beryl workspaces fix by starcraft.man
[http://ubuntuforums.org/showthread.php?p=2606972#post2606972](http://ubuntuforums.org/showthread.php?p=2606972#post2606972)

---

### Post by Kulgan on 2007-05-19
> 
EDIT: Found a fix for the problem here:

/me vouches for fix

---

