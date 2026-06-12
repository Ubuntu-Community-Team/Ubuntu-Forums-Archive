---
title: "disk boot error"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ayushjsh on 2008-01-01
i have ubuntu gutsy installed and suddenly today on the very new year day..i try to boot my system and it says problem loading from root.
/dev/sda3 contains a file system with errors, check forced. 

it completes to about 61% and then fails
automatic filesystem check of root filesystem failed.

root file system is in read mode. a maintenance shell will now be started. give root password for maintenance. after i type in my root password

bash:no job control in this shell
bash:groups:command not found
bash:lesspipe:command not found
bash:command:command not found
bash:the :command not found
bash:dircolors:command not found
 and then it boots me into my root@deepred~#

if i try "cal" or "who" command it states that /usr/bin is not in the path
if i type ls it displays nothing

then i tried pwd that works fine
also if i give shutdown now-r
it works fine exept for the part where i states that GDM could not be launchd due to an internal error . so i reach my command promp again.
im a newbie learner and this serious trouble is bugging me and im afraid that i might not loose my important data....
please help:confused::confused:

---

### Post by dcstar on 2008-01-03
> **ayushjsh said:**
> i have ubuntu gutsy installed and suddenly today on the very new year day..i try to boot my system and it says problem loading from root.
/dev/sda3 contains a file system with errors, check forced. 

it completes to about 61% and then fails
automatic filesystem check of root filesystem failed.
......
im a newbie learner and this serious trouble is bugging me and im afraid that i might not loose my important data....
please help:confused::confused:

Boot off the live CD, open a terminal and manually run a fsck on the partition:

```
sudo fsck /dev/sda3
```

---

