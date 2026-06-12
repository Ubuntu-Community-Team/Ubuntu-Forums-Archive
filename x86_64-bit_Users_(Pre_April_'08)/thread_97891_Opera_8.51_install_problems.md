---
title: "Opera 8.51 install problems"
date: 2005-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by kadymae on 2005-12-01
Grrr that life has kept me from playing with Ubuntu these past few weeks.

Opera is my favorite browser.  I had no problems getting it installed, running, and tweaked to my preferences in 4.10.

5.10 has been a nightmare.

Here's what I'm doing --

Download Opera 

Open terminal

sudo dkpg -i name of opera file here  (I'm typing o and then hitting tab for complete)

cthuluspeak

via the GUI i navigate to /usr/bin and double click on the opera.sh file I find there.

I'm asked if I want to run Opera or display its contents.

I choose run.  Nothing happens.

I choose run in terminal.  Nothing happens

I choose display.  Nothing happens.
---

Suggestions?

If I'm missing a library or key file, how do I find that out?  I've run synaptic with all repositories selected and told it to make updates as needed.

Thanks.

---

### Post by pvz on 2005-12-02
Download the opera-static version, install with dpkg -i and it should work fine. It works on my iBook.. I can run it (in KDE) from the alt+F2 application launcher or a terminal by typing opera, but I added a menu entry which works fine as well. The important thing is to install the static version, not the shared, since that one has unmet dependencies. From the drop-down box choose Other/Static Deb.

---

### Post by ngms27 on 2005-12-02
Actually I installed the Opera 8.51 deb for Ubuntu and have had no issues. It was however an upgrade from 8.50 and the installer recognised this fact.

---

### Post by deathshadow on 2005-12-12
Try THIS:
[http://ubuntuforums.org/showthread.php?t=78468]("http://ubuntuforums.org/showthread.php?t=78468")

Works Flawless, even walks you through adding the icon to gnome's app menu... Even worked with the vanilla linux 9.0 beta so...

---

