---
title: "How to run wine in 256 colour monitor"
date: 2014-05-29
forum: Wine
---

### Post by dad4 on 2014-05-29
Hi there. Hope you can help,

I am replacing my winXP with Ubuntu 14.4 LTS on Intel® Atom™ CPU N455 @ 1.66GHz × 2 
with Intel® IGD x86/MMX/SSE2 graphics.

I can run wine OK but a program I want to run falls over saying it wants a 256 color screen.

It used to do this in windows too but there I could easily change the monitor to 256 colors.

I am an IT pro but new to NIX.

I found a command to run a 8bit monitor inX windows but have to do that as su. However when I run that it won't let me run wine - of course.

xinit /usr/bin/wine "CMapEcs.exe" -- :1 -ac -depth 8

So how do I run X windows as my login?

many thanks in anticipation
Dad.

---

### Post by adec2 on 2014-05-31
I have used xinit to force a 16bit display using the command:

xinit /usr/share/playonlinux/playonlinux --run "Moto Racer" %F -- :1 -ac -depth 16

I use playonlinux hence the command difference, that works well but I have yet to find a way to force an 8bit display using any of the 8bit workarounds on the wine 256 color page

Maybe try using playonlinux? The "Moto Racer" in my command is just the name you give the container during installation

---

### Post by oat.eskelinen on 2014-06-01
I had this problem with some old games and Wine 1.6.2, but after updating to the latest 1.7.X beta everything worked without a hitch. No need to set up additional screens or anything.

Give it a go: [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by dad4 on 2014-06-14
Thank you for this adec2.
I installed playonlinux and tried to run the program as above but get the same answer I was getting in terminal....
[I]         X: user not authorized to run the X server, aborting.
[/I]Any ideas how I can do this[I] please?
[/I]regards
Greg

---

### Post by adec2 on 2014-06-14
If i remember correct editing the file etc/X11/Xwrapper.config and changing the line to

allowed_users=anybody

that did it for me.

You will have to be root to edit and save that file

It may happen it may not but you might not get sound then again it may be ok..if you dont get sound you will have to add yourself to the audio group with:

[COLOR=#204063][FONT=Helvetica]sudo add username audio

replacing username with your own username

If everything is ok then dont bother with the last command :)[/FONT][/COLOR]

---

