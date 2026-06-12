---
title: "Nvidia Server X Issues"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by CandyKiller on 2008-11-21
I'm having some Nvidia Server X Issues and I'm not sure if they're related to the 64-bit version I'm using or not, I'm totally new to linux so there's a fair chance that it is operator error ;)

I'm going into Nvidia X Server Settings from my "Systems" tab and trying to get my computer to dual monitor.  I've been successful in that part, I'm able to take my windows and move them from one screen to another and then over to a new workstation making me have a total of 4 workstations. 

The problem I'm having is it won't let me save my new configuration to the /etc/X11/xorg.conf file.  This is the exact message it gives me when I try to:

**Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.**

So I got a preview of the actual configuration I had made, copied it and went to the file via "File System" and tried pasting it into the document and saving it.  This is the message I get when I try to save:

[B]Could not save the file /etc/X11/xorg.conf.

You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again.[/B]

What am I doing wrong?  I really need to be able to dual screen.

I'm using an Nvidia GeForce 8600GT with up-to-date drivers on it.

---

### Post by bford16 on 2008-11-21
Maaybe a dumb question...are you using 'sudo' or 'gksudo' to do whatever you are doing? For instance, if you want to edit /etc/X11/xorg.conf, you have to do something like:
Press Alt+F2
enter: gksudo gedit /etc/X11/xorg.conf
click Run
enter password

Or in a terminal, you can use a text editor like nano.
sudo nano /etc/X11/xorg.conf
enter password

As you can see, both actions require your password to make changes.  You cannot edit /etc/X11/xorg.conf without admin privileges.

---

### Post by CandyKiller on 2008-11-22
That would most likely be my problem, was only using sudo.  Thank you :)

---

