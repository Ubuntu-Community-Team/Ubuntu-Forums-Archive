---
title: "Using wine with ubuntu"
date: 2017-03-31
forum: Wine
---

### Post by jakenewomer on 2017-03-31
I think I have wine installed. I copied and pasted a bunch of commands into terminal and it appeared to download and install wine asking me to install mono speaker and geko which it seemed to do. How do I access it? I don't see any icons in applications that start it. There are four black boxes with ping in them in applications but they do not start a program. by the way I did install that 32 bit enabler.

---

### Post by howefield on 2017-03-31
Thread moved to the "*Wine*" forum for a better fit.

---

### Post by jakenewomer on 2017-04-01
I'm sorry I didn't see that.

---

### Post by Perfect Storm on 2017-04-01
try type **winecfg** in the terminal.

You might want to check: [https://www.playonlinux.com/en/](https://www.playonlinux.com/en/)

---

### Post by Dennis N on 2017-04-01
> How do I access it? I don't see any icons in applications that start it.

The configuration has a GUI, but wine itself doesn't - it works in the background to install and then run Windows programs.

You can install a Windows program by right clicking on its .exe installer, and select Open with > "Wine Windows Program Loader" to start the installer.

After installing, there should be a menu entry for the Windows program just installed, possibly in your Applications menu. Depends on the desktop environment. My Xubuntu shows a separate menu category for Wine. You can also install and run them from a terminal - here is an example of a terminal command:

wine "/home/dmn/.wine/drive_c/Program Files/Litsoft/Across Lite/ACROSSL.EXE"

basically wine followed by path to the executable.
 
As suggested by A.I. above, play on linux is a good choice for installing the selection of programs they present, and may be the best bet for those.

---

### Post by jakenewomer on 2017-04-01
Thanks for trying to help. I got to something that told me to install wine again and I clicked install and it seemed like it was being done but wine does not show up in open with other applications or in the right click menu. It doesn't sound like it would work for my very old microsoft pinball game as it has no install files. I got it from NT install disk a long time ago and it still works even in  windows 10 64 bit. I feel very lucky to get to where I am in using Linux

---

### Post by pdv4 on 2017-04-28
The winecfg usually brings up the graphical box. That was a good suggestion. 

I have been using Mageia a red hat variant and PinGuy after years of going back and forth from Ubuntu and Linux Mint. However, I have finally settled on Ubuntu Gnome along with Pinguy. I notice you use Elementary OS. I have read a lot of nice things about that OS as well.

---

