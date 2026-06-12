---
title: "Backup/restore process to move from 32 to 64"
date: 2007-07-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by sot3 on 2007-07-09
I have a system running 7.04 very well right now, but the hardware is old and I finally got tired of its loud fans, etc., and bought a new Athlon64 box.  Over the last couple years I've loaded and configured so many things that I can't remember them all.  What's the best way to reproduce the same functionality on the new box?  Can I just generate a list of all of the packages I've installed, and load those on the new system and restore a few key directories for the config files?

If there's a FAQ on this, please point me to it - I didn't see one.  Thanks!

---

### Post by kuja on 2007-07-11
You can definitely fetch a text list with ```
dpkg --list | grep ii | cut -f3 -d' ' | tr '\n' ' ' > installedpackages
```. Then, afterward, just sudo apt -get install [insert list of packages here].

The second thing you'll want to do is back up any important files, config files included. Most of them are found in your home directory, as hidden files/folders. Anything else would be in /etc (most of those I reckon you won't have touched anyway though)

Have fun.

---

