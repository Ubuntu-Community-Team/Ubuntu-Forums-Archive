---
title: "ubuntu stopped loading :("
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by MrMJS on 2009-02-11
Hello,

I installed Ubuntu 8.10 64 last night, all was going fine until I did my updates and installed the nvidia driver. Im guessing this is from thr driver....

dual boot system, ubuntu loads but doesnt make it to the login screen, i get message.. kinit: no resume imagw, doing normal boot... then it asks me for my username and pw...i then get this... matthew@matther-desktop:~$

---

### Post by newagelink on 2009-02-11
Sounds like you're being brought to a terminal, rather than the thing that loads the stuff we like to click on.

Wish I could help, but I'm very new to all this as well. :(

---

### Post by SuperSonic4 on 2009-02-11
What happens if you boot into recovery mode and go to fix x server

---

### Post by newagelink on 2009-02-11
I'm not entirely sure what you're asking; I've tried ```
sudo dkpg-reconfigure xserver-xorg
``` and my xorg.conf file is posted at [http://ubuntuforums.org/showthread.php?p=6716160](http://ubuntuforums.org/showthread.php?p=6716160) ... The reconfiguring screens were very confusing, though, and I don't know if I've configured anything properly.

I've tried to provide as much information as I know in that thread.

Thanks.

---

