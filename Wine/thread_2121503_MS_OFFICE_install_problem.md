---
title: "MS OFFICE install problem"
date: 2013-03-02
forum: Wine
---

### Post by jeebz on 2013-03-02
Hi, I'm running xubuntu 12.04 and trying to install MS office home and student 2007. I used playonlinux to try and install it and I got this error message "z:\media\OFFICE12\HomeStudentr.WW\OSETUP.DLL digital signature does not validate or is not present" any idea what this means or how I fix it? I don't know if its my DVD or not but last week I was able to install this onto another computer running windows no problem.

---

### Post by lisati on 2013-03-02
*Moved to **Wine***

---

### Post by prodigy_ on 2013-03-02
Actually [the installer should work](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) if you install Wine 1.5 from [Wine PPA](https://launchpad.net/~ubuntu-wine/+archive/ppa).

But some features in MS Office applications are known not to work under Wine yet. I'd recommend using LibreOffice unless you really, really need MS Office. To install LibreOffice, open Terminal and type:
```
sudo apt-get install libreoffice libreoffice-gtk -y
```

---

### Post by Mark Phelps on 2013-03-02
Perhaps the information in the link below will help:

[http://www.personalcomputerfixes.com/general-errors/steps-to-fix-osetup-dll-errors/]("http://www.personalcomputerfixes.com/general-errors/steps-to-fix-osetup-dll-errors/")

---

### Post by jeebz on 2013-03-02
I went to [http://www.personalcomputerfixes.com/general-errors/steps-to-fix-osetup-dll-errors/](http://www.personalcomputerfixes.com/general-errors/steps-to-fix-osetup-dll-errors/) and tried moving the set up files to my hard drive but I still get the error message. I know the CD works because I just tested it on a machine running windows and it installed no problem. I just updated my WINE so I am running version 1.5.

---

### Post by jeebz on 2013-03-02
Unfortunately I do really need to be running MS Office

---

### Post by jeebz on 2013-03-02
When I tried to use the wine installer I got the error message "G:\HomeStudentr.WW/OSETUP.DLL cannot be loaded This may indicate that the file is missing or damaged" except it should be fine if I was able to install it on a machine running windows

---

### Post by Mark Phelps on 2013-03-03
> **jeebz said:**
> Unfortunately I do really need to be running MS Office

Don't take this as a criticism --- but if you really NEED to use MS Office, then you need to be running MS Windows to do that. Wine, and its companions like PlayOnLinux and Winetricks can help smooth over some of the bumps in installation, but at the end of the day, the ONLY environment that runs all of MS Office well is MS Windows.

---

### Post by jeebz on 2013-03-04
Fair enough, I just thought of branching out and trying it to learn something but if there is now way to get it running I guess its back to windows for now

---

### Post by Mark Phelps on 2013-03-06
> **jeebz said:**
> Fair enough, I just thought of branching out and trying it to learn something but if there is now way to get it running I guess its back to windows for now

Understand ... but Linux is not positioned as a free VERSION of MS Windows, and while Wine does work miracles with some Windows apps, Office is not one of them.

If you really want to "learn something", then you should look into using Linux alternatives to MS Windows apps -- like, in this case, LibreOffice.

---

### Post by SeijiSensei on 2013-03-06
Another option is installing [VirtualBox](https://www.virtualbox.org/) and running a Windows virtual machine within Ubuntu.  You'll need a Windows CD/DVD with a valid license key for this.

---

