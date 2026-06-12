---
title: "Lost sound"
date: 2009-05-10
forum: x86 64-bit Users
---

### Post by simonlugi on 2009-05-10
I am running Ubuntu 9.01 on an amd64 computer. Tried to install skype and now have lost all sound.
Can someone tell me how to get my sound back without complete reintall

---

### Post by pixel :-) on 2009-05-10
I never installed skype but, if the problem is trivial

on the volume controler open "volume control..." its the mixer

check that pcm is not muted, have a look in the preferences.

You have no sound at all? At the login screen? create a new user account, still no sound?

---

### Post by simonlugi on 2009-05-11
i have no sound at all and my icon for the volume control has disappeared

---

### Post by pixel :-) on 2009-05-11
right click on the upper panel
click "add to panel"
add "volume control"

in the mixer:
then check in the mixer if pcm isn't muted, some rude programs instaid of modulating there sound, they modulate pcm, others are less rude but simply modulate the master volume.
theres a scroll down menu, that let you set the devices, have a look at that too
play with the preferences if it dosn't help

If this isn't the problem, i recomend you go at the sound and multimedia forum,
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

the sticky there seems good
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If you tried to install skype with a installation script, it will probably be the hard fix, if it was a package it will probably be the trivial fix.

---

### Post by gewitty on 2009-05-11
I suspect you have the same problem as I do.

I've tracked the sound loss down to the fact that when you install Skype, it un-installs lib32asound2-plugins for some reason. When you re-install lib32asound2-plugins, it un-installs Skype (plus anything using WINE). SO you can have Skype or sound, but not both.

I have another thread running about this, but so far have not had any suggestions other than to try using the Skype static version. This doesn't cure the problem either.

---

### Post by pixel :-) on 2009-05-11
Just follow the other thread, i think its solved now.

---

