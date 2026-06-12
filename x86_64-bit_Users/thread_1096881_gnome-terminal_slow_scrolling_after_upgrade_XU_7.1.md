---
title: "gnome-terminal slow scrolling after upgrade XU 7.10-&gt;8.04.2"
date: 2009-03-15
forum: x86 64-bit Users
---

### Post by dakal on 2009-03-15
Ever since I upgraded my workstation Xubuntu installation from 7.10 to 8.04.2 (using the graphical system update utility), gnome-terminal is awfully slow on client application scrolling. This is particularly noticeable when I am scrolling through email in mutt; there is quite noticeable lag when using the up/down arrow keys to do so. Doing the same thing in xterm there is no lag. The hardware is certainly powerful enough that processing power shouldn't be an issue (Athlon64 3000+, 2 GB RAM, 64-bit install) and I am not running Compiz or anything else fancy like that.

I don't know what version of gnome-terminal I had before the upgrade (but it was an up-to-date 7.10 as of maybe a month ago - my primary reason for upgrading was that it was at the end of its supported life) but now I am running gnome-terminal 2.22.1 according to the about box.

Suggestions?

---

### Post by chkno on 2009-06-27
I noticed that switching metacity to compositing mode (something that probably happened in your update) makes gnome-terminal scroll much more slowly.  Try turning compositing off with ```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
``` and see if that helps.  (Replace 'false' with 'true' in that command to turn compositing back on after testing.)

---

### Post by dakal on 2009-06-27
> **chkno said:**
> ```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```
It's already false:
```
$ gconftool-2 -g '/apps/metacity/general/compositing_manager'
false
$ 
```

---

