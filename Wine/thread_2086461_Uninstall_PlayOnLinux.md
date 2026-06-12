---
title: "Uninstall PlayOnLinux"
date: 2012-11-21
forum: Wine
---

### Post by czgirb on 2012-11-21
Firstly, in order to install iTunes, I installed WINE in my **Ubuntu 12.04**.
Since it often makes my system **FREEZE**, so I give **Play-On Linux (POL)** a try.
But the result is the same. So, now I wish to uninstall it.

**And the question is:**
If I do not want for having **iTunes** and **POL** in my system, is it means that if I installed POL, it also means that iTunes will be unistalled also. Or I should uninstall them one-by-one?
**Please guide me.**
[B]
Ubuntu 12.04
The iTunes is 7.0.x version[/B]

---

### Post by ibjsb4 on 2012-11-21
Simple way for POL would be to uninstall with the software center.

I have never installed itunes, but you could always do a manual removal.  In terminal:

gksudo nautilus

And go to your filesystem and do a search for itunes and remove all files.

---

### Post by zombifier25 on 2012-11-22
> **ibjsb4 said:**
> Simple way for POL would be to uninstall with the software center.

I have never installed itunes, but you could always do a manual removal.  In terminal:

gksudo nautilus

And go to your filesystem and do a search for itunes and remove all files.

Please don't use a shotgun to kill a fly :P

Simply open your home folder, press Ctrl+H to show all hidden files, locate the .PlayOnLinux folder and delete it. That'll get rid of all traces of PlayOnLinux on your computer.

---

### Post by ibjsb4 on 2012-11-22
> **zombifier25 said:**
> Please don't use a shotgun to kill a fly :P

Simply open your home folder, press Ctrl+H to show all hidden files, locate the .PlayOnLinux folder and delete it. That'll get rid of all traces of PlayOnLinux on your computer.

Over kill? hardly ..

If you don't know what files your dealing with, it an excellent way to find out.

Pea shooters don't aways get the job done :P

---

### Post by sahabcse on 2012-11-22
[LIST]
[*]press Alt-F2 on your keyboard and type the command "PlayOnLinux" in launch
[*]Then select all programs installed via PlayOnLinux from the list shown.
[*]Click Remove button for remove the programs one by one
[*]After removing all programs, go to Applications –> Ubuntu Software Center.
[*]Then search for and uninstall PlayOnLinux.
[/LIST]

---

