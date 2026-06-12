---
title: "Gnome session not working"
date: 2004-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dylanby on 2004-12-26
I was trying to install Doom 3 on my computer.
When I went to start the game the screen went black for a moment & changed my desktop resolution to the lowest setting & hung my mouse.

I did a ctrl+alt+backspace & tried to log back in from gdm. The Ubuntu splash screen loads but does not animate (I get the start up sounds). It just hangs with a plain brown background & I have to ctrl+alt+backspace again.

At the moment I'm logged in under XFCE4. I can use xffm, but not nautilus.

---

### Post by Dylanby on 2004-12-26
I tried to start Nautilus in a terminal under XFCE. Nothing happens for a long time. Then there's this:

> (nautilus:14066): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition
looking for type: got text/plain
looking for type: got text/plain
looking for type: got application/x-gnome-app-info

(nautilus:14066): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition 

& the terminal just sits there with a blinking cursor.


---

Nevermind. I rebooted & was able to log in under the default system setting (Gnome). Only now I'm afraid to try & play Doom 3...for the wrong reasons.
Oh well...

---

### Post by ahyden on 2004-12-26
The problem with the gnome session seems to occur when some gnome processes does not shutdown. This can be "fixed" by killing them nicely in the console after you logged out, or just reboot as you did.

I get this error all the time when running Hoary, with latest gnome development version. I have to kill any gnome process, nautilus and gconf almost everytime or it wont load when I log back in again.

About doom 3, it happens when it cant find the correct opengl files. This worked for me:
ln -s /usr/lib32/libGL.so.1.0.6629 /dir_to_where_doom3_is_installed/libGL.so.1
ln -s /usr/lib32/libGLcore.so.1.0.6629 /dir_to_where_doom3_is_installed/libGLcore.so.1
ln -s /usr/lib32/libnvidia-tls.so.1.0.6629 /dir_to_where_doom3_is_installed/libnvidia-tls.so.1

replace 6629 with your version of nvidia (6111 in warty)

Hope it works

Oh and if you're afraid to mess up gnome while trying to get doom 3 working you can just login with another window manager like blackbox until you get doom 3 working.

---

### Post by ahyden on 2004-12-26
By the way, instead of ctrl+alt+backspace in gnome after doom 3 mess up your resolution and mouse, you can logout by first changing resolution with ctrl+alt+ + or - and then ALT + F1 for gnome menu to select Logout  :)

---

### Post by Dylanby on 2004-12-27
ahyden, thanks for the response. I learned more new stuff!

However I've decided to try & install a 32bit chroot with debootstrap using some tutorials I found. There are other apps & games I plan to install which aren't fully compatible with AMD64 & 64bit libs (e.g. Cedega). To save myself some headaches I'm going to try this path instead.

---

### Post by ahyden on 2004-12-27
Yes a good thing about things not working is that you learn alot while trying to fix them :) 

Installing 32bit chroot is a good idea, I have done this myself, so I can use cedega, flashplayer and mplayer with w32codecs. Here is an excellent guide I followed (but you have probably already found this): [http://digital-conquest.ath.cx/wiki/index.php/Ubuntu](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu)

---

### Post by songochain on 2005-02-28
Hi, i've a problem with doom3. I wrote a post [here](http://ubuntuforums.org/showthread.php?t=17275)  Can someone help me?
Thanks

---

### Post by piedamaro on 2005-02-28
If ctrl+alt+ + or - don't work, issue a:
xvidtune -unlock

first.

About gnome processes hanging around: it's so true (and it sucks), I even made a script, it's called 'killgnomedaemons' :D

---

