---
title: "Flash/Java not working properly in 9.10 64-bit."
date: 2009-11-09
forum: x86 64-bit Users
---

### Post by JayOne on 2009-11-09
Hi.

Whenever I go to Youtube, the videos work sometimes and other times they play but I can't pause or skip through them. In Hulu, (ALL OF THE TIME) I cant use any of the controls on the side of the video. Why is this happening? I've already tried reinstalling my graphics card (NVidia 185). I have a Compaq Presario CQ60-215DX notebook with AMD 64 bit. I just don't see a problem. Everything else works perfectly fine.

Please help.

---

### Post by lidex on 2009-11-09
You're using Firefox??
Run these commands in a terminal:
```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer
```
One line at a time please. You can find a terminal in accessories menu.

---

### Post by JayOne on 2009-11-09
Lol. I'm not Linux illiterate. I know how to work a terminal. I got this error

root@Compacked:~# apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package adobe-flashplugin

---

### Post by lidex on 2009-11-10
That's fine - the first four commands are removing packages so if not there no worries. Last one is an install. That needs to happen.;)

---

### Post by lidex on 2009-11-10
> Lol. I'm not Linux illiterate. I know how to work a terminal.Better to provide more info than necessary just in case. If I assume you know something you don't we could be playing tag for days when the goal is to get you fixed asap. So don't take it personally. BTW, welcome to the forums.

---

### Post by JayOne on 2009-11-10
Thanks and the last package was already installed and newest version.

---

### Post by efflandt on 2009-11-10
flashplugin-installer doesn't necessarily work properly in 64-bit, or at least it did not for me.  It is actually 32-bit with a wrapper.  When I would try to view newsclips it would play the commercial, but then hang indefinitely trying to start the news clip  So it would be best to uninstall that and follow instructions in the sticky at the top of this forum to install the 64-bit flash.

The only trouble I had with that is that the Athlon64 3200+ on my desktop is an older model cpu that apparently does not have an lahf instruction.  So some flash ads whacked Firefox until I added the lahf fix plugin linked to at the bottom of the sticky post.  Then 64-bit flash worked fine for me.

---

### Post by lidex on 2009-11-10
> **efflandt said:**
> flashplugin-installer doesn't necessarily work properly in 64-bit, or at least it did not for me.  
The first thing - out of many I tried - that worked for me. And probably the simplest. Jaunty_64/ Firefox 3.5.6

---

### Post by MelDJ on 2009-11-10
try this : [http://ubuntuforums.org/showthread.php?t=1321227](http://ubuntuforums.org/showthread.php?t=1321227)
see the last three posts and the links

---

### Post by JayOne on 2009-11-10
Didn't work.

---

### Post by lidex on 2009-11-10
Another fix [here]("http://ukanth.in/blog/?p=48")
[here]("http://ubuntuforums.org/showthread.php?t=891458&page=3") and [here]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html")

---

### Post by blueridgedog on 2009-11-10
This script removes the existing flash and downloads the alpha version (64 bit).  Note there is an issue with gmail, but there is a workaround if you use that.  Read through the script so you see what it is doing.  I used it and am satisfied with the outcome.

---

### Post by adibadi on 2009-11-16
The easiest solution to this problem is to disable the Compiz visual effects.

System -> Preferences -> Appearance -> Visual Effects -> none

Gmail won't crash, youtube will work properly, and there is no need to install any other flash plugin.  If you can't live without compiz effects, then I guess you should try the other suggestions.

---

