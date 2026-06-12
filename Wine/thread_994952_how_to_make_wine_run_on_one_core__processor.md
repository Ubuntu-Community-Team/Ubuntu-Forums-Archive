---
title: "how to make wine run on one core / processor"
date: 2008-11-27
forum: Wine
---

### Post by finito on 2008-11-27
I am trying to run RA3 and I am stuck at this point point of the game where the game crashes, you can follow up the post at.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14371](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14371)

It is the one called I think I finished the game.

Well anyway I have come to the conclusion that this may be an issue related to Dual/Quad core. 

Any help is appreciated.

---

### Post by finito on 2008-11-27
WTH this should be an easy thing to do?

---

### Post by happyhamster on 2008-11-27
- It's possible with the taskset command. Run wine like this:

taskset -c 0 wine program_name.exe

- to get rid of debug-messages:

WINEDEBUG=-all taskset -c 0 wine program_name.exe

- The "-c 0" part will set cpu affinity for core 1, "-c 1" would set it for core 2, etc. See "man taskset" for some more info.

Good luck.

---

### Post by finito on 2008-11-29
Thanks for the help but It didnt help.

---

