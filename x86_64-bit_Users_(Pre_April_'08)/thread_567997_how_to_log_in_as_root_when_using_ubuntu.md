---
title: "how to log in as root when using ubuntu"
date: 2007-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by hawkins_sg on 2007-10-05
I am trying to retrieve my information from my hard disk and save it to my external hard disk. How can I do that?

Still learning....Newbie

---

### Post by Kilz on 2007-10-05
There are lots of ways that dont require you to compromise security by logging in as root. In Ubuntu the root account is disabled. If you want to backup the entire disk you might want to try partimage. It will backup the entire disk, or only a partition to a file. If you just want to copy over files you could open a terminal and type in ```
gksudo nautilus
``` This will open nautilus in admin mode. You can copy and paste file all over, change file and folder permissions, etc. Just be careful because you can ruin your setup removing or moving the wrong thing. The advantage is there is no logging in and out. I even added a shortcut to gksudo nautilus to my menu with System >Preferences >Main Menu

---

