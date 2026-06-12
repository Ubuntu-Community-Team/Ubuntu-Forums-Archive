---
title: "[SOLVED] Full change from ubuntu to kubuntu"
date: 2007-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luis Macias on 2007-11-15
Hi, is it possible to do this? i saw some forums but they have solutions for having both kde and gnome. This would be for ubuntu gutsy gibbon

Thanks

---

### Post by oneadvent on 2007-11-15
The only difference is that KDE is installed instead of gnome, are you meaning to do a full reinstall of the system, or to switch over?

You could always just install the KDE packages if you want to have both.

If not, download the cd, and copy your home over to the new system.

---

### Post by Luis Macias on 2007-11-15
Thanks for the answer, what i want is to completely change from ubuntu to kubuntu, i need to reinstall the whole oS?

---

### Post by oneadvent on 2007-11-15
If that is your goal, then the best bet is to copy your /home directory to another partition, or on a dvd, or cds and then burn a kubuntu iso and reinstall.

then you would just have to copy your home directory back.

PS: if your home directory is too large, simply make a partition with gparted and copy it there for safe keeping.

Let me know if I'm not making sense.

---

### Post by Luis Macias on 2007-11-15
Thanks i think i&#314;l do that. Thanks for your help!

---

### Post by oneadvent on 2007-11-15
I did that with my Ubuntu, and my advice is that you should slowly move any hidden folders you want to keep to the new install.

---

### Post by oneadvent on 2007-11-15
oh, and mark solved if it works out.

---

### Post by moparisthebest on 2007-11-15
Reinstalling your whole system is overkill and not needed.

'sudo apt-get install kubuntu-desktop'

Then after that finishes and you log into kubuntu.

'sudo apt-get remove ubuntu-desktop'

---

### Post by Luis Macias on 2007-11-19
Thanks, i finally decided to get both ubuntu and kubuntu

---

### Post by oneadvent on 2007-11-19
if you have the space its better.

that way you can run "only gnome" and "only KDE" apps on it.

(There really aren't that many of them anymore.)

Glad it all worked out.

---

