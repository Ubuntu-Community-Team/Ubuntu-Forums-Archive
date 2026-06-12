---
title: "[SOLVED] Assign compiz and XGL to second core"
date: 2007-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jouke74 on 2007-08-09
Hi, I just installed Compiz Fusion, XGL server with a ATI X1600 on my system. Both are running ok, accept for some video glitches here and there. However I noticed that my core 0 use is sometimes going through the roof (100% use), while my second core still seems on vacation (0% use). Is there any way to assign XGL to core 0 and compiz to core 1 for example (or other programs as well), to divide the CPU load a bit?

In Windows I can put the affinity of a program to either core, however I am to much of a Linux newbie to figure out how to do this on Ubuntu / Debian? Hence I am asking you. 

Thanks in advance, JJ.

---

### Post by nowhere.elysium on 2007-08-09
[https://answers.launchpad.net/ubuntu/+question/7777](https://answers.launchpad.net/ubuntu/+question/7777)
Unfortunately, most software is not written to parallel process yet. I guess we're all too used to i386 desktop architectures...
I have the same problem: one of my favourite pieces of software, called [Fluxus]("http://pawfal.org/fluxus") can't use two processors either, which is a real pity, because it would absolutely blaze along, if it could. I'm tempted to have a crack at the source code, but I don't know if I've got six months to spare, or not...

---

### Post by Jouke74 on 2007-08-09
To avoid confusion, the goal is not to have a single program running on two CPU's (also cool). But for now to have each separate program running on one CPU.

I think I might have something going, but I need still time to test it out.

---

### Post by nowhere.elysium on 2007-08-09
Well, if you get a result, gimme a shout: I'd love to be able to get that working for my own purposes...

---

### Post by michael37 on 2007-08-10
I wouldn't recommend messing with Linux scheduler, which is the kernel component assigning the processes on different CPUs.

---

### Post by Jouke74 on 2007-08-10
Hmm, this reply begs for the question why not?? 

Is far as I can see the kernel programing is made to be efficient in order to use as little CPU as possible. That means it only switches to using two CPU's when the first one cannot handle stuff anymore. Which is perfectly fine IMHO, however it does cause hickups when I am scrolling through my Abiword documents under Compiz+XGL (AMD X2 4200). I guess I can gain efficiency running XGL and Compiz, by putting that on the second core by default.

My thought was to use "apt-get install schedutils" and then use the "Taskset -c bla bla" program in front of my ususal startup script for compiz and XGL. I just reinstalled Ubuntu and this is not my production distro. So except when there is a serious probability that this action will screw up my hardware (which I sincerely doubt) I don't mind testing this, who knows something good might come out. Or something, bad. Either way I can report it and it will be a useful exercise I think. Now if I can only find some time somewhere this weekend to start messing around with files...

---

### Post by Jouke74 on 2007-08-11
OK after some testing, do the following:

1. Open a terminal and install schedutils with:

>sudo apt-get install schedutils

2. Then change the XGL startup script:

> sudo gedit /usr/local/bin/startxgl.sh				


**From:**

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

**To:**

#!/bin/sh
**taskset -c 1 **Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

and save it again.

Now logout and login, and you will notice that the XGL server only will work on CPU 1. (Linux starts counting from 0, so we have CPU 0 & 1).

The same command, now for CPU 0, we can use for compiz fusion. Which means we have to put "taskset -c 0" in front of the compiz --replace command, or startup command under sessions. 

In principle now Compiz will run on CPU 0 and XGL on CPU 1. Furthermore everything else does not seem to be affected that much until now. The other processes are divided over both CPU's. 

I did notice however that the overall effect is generally very small, ie. there is not much improvement on my computer and the linux scheduler does a good job on it's own. Checking out the system monitor in Gnome I did notice however that the CPU load flipping done by Linux is gone for XGL and compiz. 

As XGL and Compiz are still alpha software, and I don't have a clue what is the effect on all other processes when assigning cpu's under linux. I don't want to be responsible for any damage done by this (although the probability is likely small). If you feel like, test it to see if it improves stuff for you, however at your responsibility. 

Cheers...

---

### Post by nowhere.elysium on 2007-08-11
Haha! Top banana, dude! That's awesome. I shall try it out on fluxus presently...

:edit: And it works a treat :D

---

### Post by Jouke74 on 2007-08-12
It works better than I thought here as well.
No more serious hickups.

:lolflag:

---

### Post by jamesford on 2007-08-12
how would this work if im using fusion-icon ? that means i have no startxgl.sh or compiz --replace running at startup, only fusion-icon

---

### Post by Jouke74 on 2007-08-12
As far as I can see the fusion-icon program is a graphical shell to Compiz. Check if it links to another command when you right click on the icons within the Icon menu. If you are able to edit these commands, then you need to place the "tasksel -c 1" command in front of it. However, I don't have fusion-icon installed, so you have to test and fiddle with it yourself. 

Note that: If you are not running XGL server you don't have to do anything. 
The goal was to divide the heavy CPU load of Compiz (program1) and XGL-server (program2) over the two processors, so that the things that make up your desktop are divided over both cores (and stay there). If you are not running XGL server, just compiz (most Nvidia users) then it is unlikely that you will gain much. 

Dedicating just compiz to one core can be done also using the PIDs, but I can't magically make that happen without seeing any configuration and related installed programs for compiz etc. Sorry.

---

### Post by EXCiD3 on 2007-08-24
Wow, this is a pretty cool idea. Once there is smart assignment like this built into all apps everything will run smoother and faster. I may have to try this... Thanks guys!

---

