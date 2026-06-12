---
title: "Problem installing a windows .exe file"
date: 2019-04-29
forum: Wine
---

### Post by cearlp2 on 2019-04-29
When trying to install a Windows .exe file I right click it, choose Open With Other Application and then select Wine from the options listed.
Wine installs but it is never listed as an application to use to open the .exe. 
How do I use it as the application to open the .exe?

---

### Post by Dennis N on 2019-04-29
> How do I use it as the application to open the .exe? 
Wine itself doesn't have a GUI to launch applications. You need to make a command to launch it. The command then can be used from the terminal, or to create a program launcher. The pattern is:

**wine path-to-exe-file**

The wine package installed from the repos installs programs somewhere in the folder ~/.wine/drive_c/

Here is an example of a command to launch a program:
```
wine /home/dmn/.wine/drive_c/'Program Files (x86)'/'Parsons Technology'/'Family Origins'/FOWin32.exe
```
Linux doesn't like spaces in the path, so you put quotes around any folder name in the path containing a space.
For Ubuntu, if you want to create a launcher with an icon that will appear in the applications menu or activities screen search, you make a .desktop file in **~/.local/share/applications** for your program. A menu editor can be used for this. Sometimes, the installation process also makes a menu launcher, but don't count on it.

---

### Post by cearlp2 on 2019-04-29
Are you saying I need to put the .exe file in (in my case) /home/earl/.wine/drive_c/ ?
I am trying to run the install.exe on a DVD that contains the files needed by install.exe.
This has worked in the past by just installing wine from Ubuntu Software and then right-clicking the install.exe and selecting wine as the application to open it.
I no longer get the option to select wine as the application to open it, Archive Manager is the only selection available.

---

### Post by cearlp2 on 2019-04-29
Dennis N, I tried your first example of wine path-to-exe and see what you mean by the .wine/drive_c/ notation.
The first thing I got was a message saying wine was creating those directories.
After that things went as expected...the install.exe executed and the program was installed successfully .

---

