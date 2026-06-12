---
title: "How to open .exe-files with Wine"
date: 2018-12-11
forum: Wine
---

### Post by MiscMau on 2018-12-11
Hi all

I'm trying to open an .exe-file with Wine, but it doesn't appear in the list of programmes to choose from when selecting "open with", and the "add" button is greyed out. Hope someone can help me.

M.

---

### Post by wildmanne39 on 2018-12-11
*Thread moved to **Wine for a more appropriate fit**.*

---

### Post by mc4man on 2018-12-11
Assuming 18.04 but post which wine package you installed (and if not on 18.04
Basically all the .desktops that wine used to install have been removed, pretty easy to fix, otherwise you'll have to run from command line.

---

### Post by oldrocker99 on 2018-12-11
You haven't tried PlayOnLinux, have you? If not,
```
sudo apt install playonlnux
```
PlayOnLinux has installation scripts for hundreds and hundreds of Windows programs, not just games.It makes installation easy-peasy for lots and lots of programs.

---

### Post by MiscMau on 2018-12-11
Thank you for your replies.

I'm on 18.04 and tried associating PlayOnLinux with .exe-files, but then it just opens the PlayOnLinux window, and nothing else happens. What is the terminal command line for executing .exe-files?

---

### Post by deadflowr on 2018-12-12
I posted this yesterday:
[https://ubuntuforums.org/showthread.php?t=2407890&p=13822719#post13822719]("https://ubuntuforums.org/showthread.php?t=2407890&p=13822719#post13822719")
It's a fairly easy fix to get the wine program loader action/function working again.

---

### Post by Dennis N on 2018-12-12
> **MiscMau said:**
> Thank you for your replies.

I'm on 18.04 and tried associating PlayOnLinux with .exe-files, but then it just opens the PlayOnLinux window, and nothing else happens. What is the terminal command line for executing .exe-files?

This relates best to the wine found in the Ubuntu repository, not play on linux:

Before you can run the Windows program, you have to install it to wine's virtual C: drive by running the Windows installer under wine. If you right-click on the installer, you may see **Open with > "Wine Windows Program Loader"**. If not, you can do install from the terminal* with a command like this:

**wine <path-to-installer>**

Then, if you are lucky, you will get an entry in your applications menu (depending on the flavor of Ubuntu you are using) to start the actual program. Otherwise, you can manually create a menu entry with a menu editor like menulibre, or even create your own .desktop file to launch it. 

Note: The virtual C: drive is at: **~/.wine/drive_c/** and the programs get installed to:  **~/.wine/drive_c/Program Files/**

*you can also run an installed program from the terminal with a similar command:

wine <path to installed program>

an example from my computer:
```
wine "/home/dmn/.wine/drive_c/Program Files/Litsoft/Across Lite/ACROSSL.EXE"
```

---

