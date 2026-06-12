---
title: "I Did Something Really Stupid"
date: 2007-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by everythingsused on 2007-06-25
So, I was trying to install a program that requires PyQt4 and I'm still running 6.06 so it wasn't in the repositories. I should've taken this as a sign that I need to update already, but instead I tried to install PyQt4 manually. At some point, one of the dependencies (sorry, I don't remember which for sure) said it conflicted with the python package - so I removed it assuming it would be replaced with whatever I was using. I didn't pay attention to what other packages synaptic graciously offered to remove for me... and now when I rebooted the computer I have no xserver, only the command line! 

Can anybody guess as to what packages I need to replace with apt-get in order to have a GUI back? I really really don't want to end having to reinstall. Thanks!


Edit: I'm really sorry, I have no idea why I put this in the 64-bit area. I'm flustered and linuxless - the computer's a 32-bit.

---

### Post by tillo on 2007-06-25
You probably want the "xorg" package. It will take care of installing all software needed by gnome or whatever you are using as graphical environment. Run "dpkg -p xorg" for more infos.

---

### Post by everythingsused on 2007-06-25
Hmmm... for some reason it says xorg is unavailable. And apt-get can't find it either. I ran apt-get update and I looked at /etc/apt/sources.list and I'm pretty sure everything's there, but which repository is needed for xorg?

---

### Post by everythingsused on 2007-06-26
Well, I don't know what the deal with xorg is, but after reinstalling gdm and gnome-desktop-environment I'm back in - even though I'm still missing a lot of random things. Thanks for the nudge in the right direction!

---

