---
title: "Nautilus problem.I can't enter to the &quot;/&quot; directory"
date: 2007-07-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by brz20 on 2007-07-03
Hi guyz.
It's my first post here an i want help.
I have the following problem:
when i try to access the "/" directory with nautilus , nautilus don't respond and causes 100% CPU...
But when i try the same with nautilus as root it is OK...

thank you for your time

---

### Post by morgan_greywolf on 2007-07-03
What are the permissions on your root directory?

---

### Post by brz20 on 2007-07-03
ROOT:    rwx 
GROUP: r-x
OHERS: r-x

---

### Post by brz20 on 2007-07-03
Up  guyz i need help.
Please help me.

---

### Post by dabl on 2007-07-03
Why do you need to access "/" ?

You should be able to access it by opening a console window and typing```
 sudo su
```

then "cd .." takes you up a level, so two levels from /home/brz20 will get you to "/"

:)

---

### Post by brz20 on 2007-07-04
Before however it functioned regularly while now don't respond.
I know that also to enter in Place/Home Folder I can't change any file from root directory(it should I enter from the console and enter the command "sudo nautilus")but why before 2 days it worked and now doesn't work?
Exists way to fix it?
I thank for the interest that you show.

---

