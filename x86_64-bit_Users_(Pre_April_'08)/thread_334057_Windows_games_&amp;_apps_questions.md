---
title: "Windows games &amp; apps questions"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkcyber on 2007-01-08
I'm installing Ubuntu 6.10 64 bit and have some questions.  I edited this and moved my game question to the game forum.  I just couldn't change the title of my post...sorry.

I have to use remote control software to log into my pc's at work.  I currently use Remote Administrator 2.2 as my main program and PC Anywhere as a backup (so to speak).  I have found that PC Anywhere does support Linux, but does anyone know if Remote Administrator has a linux version?  If not, then what is a good linux based remote control program that will work with Windows based pc's as well?

Thanks!

---

### Post by hal10000 on 2007-01-08
I dont' know if there exists a linux version of remote administrator, but there are a lot if remote tools you can try, e.g.:
tsclient
xvncviewer
rdesktop
grdesktop (gnome application for rdesktop client)
krdc (a kde tool)

---

### Post by darkcyber on 2007-01-08
So, will any of those work lets say on 1 linux pc and 1 windows pc?  Or must both pc's be linux?

Total noobie here...sorry!

---

### Post by hal10000 on 2007-01-08
The tools I mentioned above are all linux programs. On the windows side you have to enable the corresponding service (I guess it is terminal services or remote desktop services, don't know how it is called exactly).

Your windows then acts as a server which you can access by the linux tools.
If you use gnome, I suggest to try grdesktop, otherwise krdc (KDE tool).

---

### Post by hal10000 on 2007-01-08
During configuring yours connection you shoul shutdown your firewall on both PC's, just to avoid trouble with firewall settings, later you can add an appropriate entries to your firewalls and enable it again.

---

### Post by Aldrik on 2007-01-09
I use krdc/rdesktop (kde/kubuntu user ;)) to connect to my windows computer.

You just need to enable XP's remote desktop sharing (google will tell you how) & then you can connect to it with rdp:/username@ip.of.ur.comp. It's just that easy.

---

