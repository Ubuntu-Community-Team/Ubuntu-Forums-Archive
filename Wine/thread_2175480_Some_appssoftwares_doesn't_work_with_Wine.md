---
title: "Some apps/softwares doesn't work with Wine"
date: 2013-09-19
forum: Wine
---

### Post by kiran1247 on 2013-09-19
[FONT=trebuchet ms]
Hi Friends,

Not each and every app/softwares work with wine. I mean with the help of wine , I'm NOT able install some softwares on Ubuntu.

For example , I want to execute/run a software called rufus.exe on ubuntu , and I've tried with wine. But the software doesn't launch even. Not able to execute.

Can someone please help me to understand why , and what's happening over here ?

Or please let me know if we have any other app in ubuntu , where i can install any software on ubuntu ?

thanks.
[/FONT]

---

### Post by TheFu on 2013-09-19
Ubuntu is not Windows. It is a different OS. WINE is an API layer that implements portions of the MS-Windows API, but not all of it and not completely.  That is why some programs - I'd even say - MOST programs do run work under WINE.

You should check out the WINEHQ.org website for help with setups needed for any specific program.  Oddly, it seems that games get the most love with configuration help. If the program isn't in the WINEHQ DB, I can only recommend that you look for a native Linux alternative for what rufus does.  If rufus is just a USB boot drive maker, then there are definitely alternatives under Linux, though I've found [YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/") to work very well under Windows.  Under linux, scripts will do the same job.

To install software in Ubuntu, use "**software center**" or **synaptic** or **aptitude** or **apt-get**. All of these programs work with the "APT" repository on a system.  Linux uses a package manager and APT to handle installation, dependencies and updates to software on the system. If the package manager was used to install a program, then the package manager will update it, if asked to update all software. NOT using the package manger is asking for trouble. Definitely do not download a "setup" program and install it when you are a beginner.

Expecting Linux to behave like any other OS will lead to frustration. Linux is most like UNIX, not MS-Windows.

I hope this was helpful.

---

### Post by kiran1247 on 2013-09-19
Great explaination.

thanks.

---

