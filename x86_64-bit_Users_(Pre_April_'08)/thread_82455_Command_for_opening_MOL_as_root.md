---
title: "Command for opening MOL as root"
date: 2005-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by tiagobt on 2005-10-26
I finally got MOL (Mac-on-Linux) working on my Mac Mini (Kubuntu 5.10). I can start it typing the command "sudo startmol -X" in a terminal, and typing my password after. What I want is to create an icon that opens MOL when I click on it. I tried to use the same command, but it doesn't work (probably because I have no chance to enter my password). I wanted to do something like Adept does: it pops up a window asking for your password when you try to open it, but I couldn't figure out how to do it. Any help?

---

### Post by Joe_lurker on 2005-10-26
Try 'gnome-sudo /usr/bin/startmol -X' for the command.

-Joe

---

### Post by tiagobt on 2005-10-26
[QUOTE=Joe_lurker]Try 'gnome-sudo /usr/bin/startmol -X' for the command.

-Joe[/QUOTE]
The problem is that I'm using KDE. Is there an equivalent command?

Thanks for the help

---

### Post by Joe_lurker on 2005-10-26
You are posting the the GNOME list!  I believe that the command is 'kdesu'.  So replace the command with 'kdesu /usr/bin/startmol -X'.

---

### Post by Entity on 2005-10-28
You can simply run MOL as a normal user also. Check out [https://wiki.ubuntu.com//MacOnLinuxHowto](https://wiki.ubuntu.com//MacOnLinuxHowto) for more info.

---

### Post by tiagobt on 2005-10-28
[QUOTE=Joe_lurker]You are posting the the GNOME list! I believe that the command is 'kdesu'. So replace the command with 'kdesu /usr/bin/startmol -X'.[/QUOTE]
The command "kdesu" does exactly what I wanted. Thanks for the help and I'm sorry for posting on the wrong forum. The only problem is that MOL is opened in full-screen mode (instead of window mode) for some reason when I click the icon I created,

[QUOTE=Entity]You can simply run MOL as a normal user also. Check out [https://wiki.ubuntu.com//MacOnLinuxHowto](https://wiki.ubuntu.com//MacOnLinuxHowto) for more info.[/QUOTE]
That worked! Thanks.

---

