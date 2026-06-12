---
title: "Running Windows Programs in Ubuntu"
date: 2012-04-09
forum: Wine
---

### Post by galaxion2 on 2012-04-09
Hi everyone,

I recently intalled Ubuntu 11.10 on my computer with Wubi. I love Linux, but I can't figure out how to run some of the programs that I have installed on Windows. I have tried using Wine, but after I download it, I can't find the application. I've tried searching for it using the dash, but it doesn't come up. However, I can right click on a .exe file and select "Open with Wine Windows Program Loader," but the program either never runs or runs incompletely (for example, I tried doing this with GTA- Vice City, but when it loads and takes me to the main menu, the whole screen is black except for the highlighted option.) I have also tried just double-clicking on the .exe file, but to no avail. Am I doing something wrong with Wine? If not, can I fix the problem, and are there any alternatives to Wine? By the way, I did manage to install a program (7-Zip) successfully with Wine, if that helps. I have tried using Wine 1.2 and 1.3. Nothing works.

---

### Post by Basher101 on 2012-04-09
wine uses a virtual graphics card, in other words if you already have a mid-end graphics card, then the virtual one is not enough for your games (while using the actual hardware, it runs fine)

---

### Post by Cheesemill on 2012-04-09
When you are using Wine you have to reinstall the program that you want to use in Ubuntu, you usually cannot run programs that you have installed in Windows.

For your GTA example just insert the CD, then right-click on setup.exe and choose 'Open with Wine'.

---

### Post by Cheesemill on 2012-04-09
> **Basher101 said:**
> wine uses a virtual graphics card, in other words if you already have a mid-end graphics card, then the virtual one is not enough for your games (while using the actual hardware, it runs fine)

Wine doesn't use virtual anything. It uses your actual hardware by translating API calls.
Wine is not an emulator or a virtualization solution.

---

### Post by Mark Phelps on 2012-04-09
To run Windows apps or games, you should first check the WineHQ application compatibility site for ratings and tips.

The page below is for the version of GTA you want to use:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1369]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1369")

Read the info in the Test Results areas for tips.

---

### Post by Basher101 on 2012-04-09
> **Cheesemill said:**
> When you are using Wine you have to reinstall the program that you want to use in Ubuntu, you usually cannot run programs that you have installed in Windows.

For your GTA example just insert the CD, then right-click on setup.exe and choose 'Open with Wine'.

i do not use wine. Thats what dualboots are for. Anyways thanks for the correction.

---

### Post by oldos2er on 2012-04-09
Thread moved to Wine.

---

### Post by forrestcupp on 2012-04-09
> **Basher101 said:**
> i do not use wine. Thats what dualboots are for. Anyways thanks for the correction.

You were probably thinking of virtual machines. Things like VirtualBox *do* use virtual hardware.

---

