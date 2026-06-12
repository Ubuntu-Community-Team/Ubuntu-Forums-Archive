---
title: "Angels Online?"
date: 2008-03-01
forum: Wine
---

### Post by foug on 2008-03-01
Has anyone tried installing this game? The winehq database says it works but when I try to install it I get the following error;

wine: could not load L"c:\\windows\\system32\\install.exe": Module not found

Does anyone have an idea on how ot fix this?

---

### Post by pytheas22 on 2008-03-01
Is there a file name install.exe at c:\windows\system32 within the wine filesystem?

---

### Post by foug on 2008-03-01
No, there is not.

---

### Post by pytheas22 on 2008-03-01
How are you trying to install the program?  Are you sure that when you run the executable, you are pointed at the correct directory?  Also, if the game comes on a CD (I don't know anything about the game so sorry if I'm asking dumb questions), are you installing from the CD or did you copy the files to your hard disk for some reason?

If you think that the above is not the problem, take a look at this thread [http://ubuntuforums.org/showthread.php?t=538430&page=2](http://ubuntuforums.org/showthread.php?t=538430&page=2) and especially the last post; it looks very similar to your problem.

---

### Post by foug on 2008-03-01
I am in the directory of the .exe, it's not on a CD, it's a downloadable game. I have the c:\windows\system32 but there's no install.exe ;\

---

### Post by pytheas22 on 2008-03-02
I don't think there's supposed to be an install.exe in the system32 directory (there's not one in my virtual install of XP), so that's not the problem.  Try doing the stuff outlined in the last post of the thread that I linked to above.

---

