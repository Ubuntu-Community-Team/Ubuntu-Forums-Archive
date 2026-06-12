---
title: "Office 2000"
date: 2008-09-07
forum: Wine
---

### Post by Patricrawley on 2008-09-07
I installed Office 2000 and it installed just fine. But when I run it it asks for my name and says please change your name in the system.reg file but I do and then it says  it doesnt have the needed the registry files and this process keeps repeating. What did I do wrong?

---

### Post by tuxxy on 2008-09-07
You read the Office guide?

[https://help.ubuntu.com/community/Microsoft_Office](https://help.ubuntu.com/community/Microsoft_Office)

---

### Post by Patricrawley on 2008-09-07
Yeah and I did all of that. Could it be because I added French support?

---

### Post by tuxxy on 2008-09-07
I dont think the language would have an effect but im not 100% on that, as I dont use WINE too often, I run all windows apps in virtual

Does it highlight a specific file that it needs?

---

### Post by Patricrawley on 2008-09-07
```
Required registry information is missing and this program cannot run. Please rerun setup to correst this problem.
```

---

### Post by Patricrawley on 2008-09-07
I tried reinstalling I even remove --purged and deleted my .wine and then REINSTALLED everything again and still the same problem.

---

### Post by a1z on 2008-10-14
PART 1/3:

Installing Office 2K in Hardy is done with Wine v1.1.2.

1) install wine 1.1.2
2) extract office 2000 ISO (or zip or rar file)
3) install using setup.exe

====================
PART 2/3:

My question:

MS Word 2000 uses CPU all the time. My CPU meter on the task applet bar shows full usage of CPU when MS Word 2000 is opened and being used. The performance is smooth, nonetheless. When I minimize the window, the CPU relaxes.

What is going on? Is there a way to control the workload of CPU by MS Word 2000? Will this affect the performance of the word processor?

====================
PART 3/3:

SUMMARY:

I see this heavy usage of CPU under these conditions:

1) Hardy + Wine1.1.2 + Office 2000
2) Hardy + Wine1.1.2 + Office 2003
3) XP + Office 2000 (mentioned above)

But it is okay when I open and edit a document under these conditions:

1) XP + Office 2003
2) Hardy + Wine0.9.59 + Office 2003

Thanks in advance!

-a1z

---

