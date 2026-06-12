---
title: "Wine installed correctly?"
date: 2018-07-23
forum: Wine
---

### Post by plutokang on 2018-07-23
Hello,
Problem: Wine is installed, but does not appear in the list "all applications" and is not working.

I have on my hard disk:
- Bootable Linux Partition with Xubuntu 18.04
- NTFS Partition just with 2 portable exe programs, no Windows.
I installed wine (July 2018) with sudo apt-get install wine-stable

When I right click the exe program, open in wine is not offered.
What is the reason?
Thank you for help.

---

### Post by kc1di on 2018-07-23
there is a problem with wine in 18.04, until it gets fixed I would suggest using playonlinux  or you can use the terminal to install the program in wine. 
you may also have to install wine32 and ia32-libs to get 32 bit programs to work. 

to install via a terminl navigate to the folder the .exe file is in and use this command```
wine XXXX.exe
``` where XXXX is the name of the file being executed. 
Good luck. 

P.S. Playonlinux may be the easiest way at the moment.

---

### Post by plutokang on 2018-07-24
Terminal: wine XXXX.exe works perfect, thank you!
Where can I read about the commands  to integrate that to autostart?
Thank you

---

### Post by kc1di on 2018-07-24
Your Welcome,
any program you want to auto start can be added to the auto start menu under /home/<user name>/.config/autostart  (note it's a hidden file so you will have to click on show hidden files. ) Also wine directory itself is a hidden file in your home directory .wine. 

if you need to run wine config you can do so from the terminal also by entering ```
winecfg
```
this page may be helpful to you: [https://wiki.winehq.org/List_of_Commands]("https://wiki.winehq.org/List_of_Commands")

---

### Post by deadflowr on 2018-07-24
monkeybrain's solution should work:
[https://ubuntuforums.org/showthread.php?t=2382617&p=13766904#post13766904]("https://ubuntuforums.org/showthread.php?t=2382617&p=13766904#post13766904")
to add the *open with* option.

---

### Post by plutokang on 2018-07-26
Thanks deadflowr, works perfectly. Just double-click the exe file opens the exe program in wine.   :D

---

