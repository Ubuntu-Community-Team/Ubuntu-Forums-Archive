---
title: "Wine from source"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by patleamon on 2006-08-26
Ok, I've spent most of today trying to get a version of wine up and running and think I've gotten pretty close.  I've settled on using [these instructions]("http://wiki.winehq.org/WineOn64bit") with [some help]("http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/014dc737d64d660a/c6a0418f8bb469a5?lnk=raot").  I can build a version of wine from source using these instructions, but not a version with OpenGL support.  At the configure stage I get 

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

I'm guessing I haven't got the right 32 bit libraries for OpenGL but I've got no idea what they are.  Has anyone else had this problem?

My install is a fresh one using the latest k8 kernel with the nvidia-glx drivers and very little else, other than what I've added for wine.

---

### Post by Kilz on 2006-08-26
> **patleamon said:**
> Ok, I've spent most of today trying to get a version of wine up and running and think I've gotten pretty close.  I've settled on using [these instructions]("http://wiki.winehq.org/WineOn64bit") with [some help]("http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/014dc737d64d660a/c6a0418f8bb469a5?lnk=raot").  I can build a version of wine from source using these instructions, but not a version with OpenGL support.  At the configure stage I get 

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

I'm guessing I haven't got the right 32 bit libraries for OpenGL but I've got no idea what they are.  Has anyone else had this problem?

My install is a fresh one using the latest k8 kernel with the nvidia-glx drivers and very little else, other than what I've added for wine.

Why build wine when a .deb can be installed?

---

### Post by patleamon on 2006-08-26
I've tried the instructions from [the how to]("https://help.ubuntu.com/community/WineForAMD64").  When I try to run WoW in opengl I get a page fault, when I try to run it in direct 3d I get a page fault and the buttons showing up on screen, but no 3d - just black.

I figure I'm missing a dependent library or something and the sources are the easiest way to track that down (?).

---

### Post by Kilz on 2006-08-26
> **patleamon said:**
> I've tried the instructions from [the how to]("https://help.ubuntu.com/community/WineForAMD64").  When I try to run WoW in opengl I get a page fault, when I try to run it in direct 3d I get a page fault and the buttons showing up on screen, but no 3d - just black.

I figure I'm missing a dependent library or something and the sources are the easiest way to track that down (?).

You need wine with the wow patches I think. Its nice to see my entry in the wiki was found :)

---

### Post by patleamon on 2006-08-27
Looks like I needed an extra symlink.
ln -s libGL.so.1 libGL.so

With this I can run the ./configure without any warnings.

---

### Post by Kilz on 2006-08-27
> **patleamon said:**
> Looks like I needed an extra symlink.
ln -s libGL.so.1 libGL.so

With this I can run the ./configure without any warnings.

You can try to compile wine, make sure you have the wow patches for it. You will still only end up with a 32bit wine. If you find you cant build it, there is a link to my wine howto on the forums in my signature. It contains a link to the newest wine with the wow patches already installed.

---

