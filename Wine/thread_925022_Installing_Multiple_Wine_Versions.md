---
title: "Installing Multiple Wine Versions"
date: 2008-09-20
forum: Wine
---

### Post by Sugi on 2008-09-20
Can I just install one version of wine (IE Wine 1.0) and then install another version of wine (IE Wine 1.1.5).  So first, install wine 1.0 to directory /.wine.  After the installation, change /.wine to /.wine1.0.  Next, I will install Wine 1.1.5 to /.wine.  After the installation, i then change that directory to /.wine1.1.5.  So now I have two wine directory: wine1.0 and wine1.1.5.  Would that work with the two different wine versions on one computer?

Spec:
Ubuntu Hardy
Current version 1.0
Reason: Spores (but still kept starcraft installation :D

Thanks,
Sugi

PS: Sorry, I know this subject is a overdone, but when I was researching this I kept getting post form couple of years ago.

---

### Post by Sugi on 2008-09-20
oh yea, a lots and lots of wineprefixes :p

---

### Post by asdfoo on 2008-09-20
> **Sugi said:**
> Can I just install one version of wine (IE Wine 1.0) and then install another version of wine (IE Wine 1.1.5).  So first, install wine 1.0 to directory /.wine.  After the installation, change /.wine to /.wine1.0.  Next, I will install Wine 1.1.5 to /.wine.  After the installation, i then change that directory to /.wine1.1.5.  So now I have two wine directory: wine1.0 and wine1.1.5.  Would that work with the two different wine versions on one computer?



hi

I think you're confusing wine prefix's with wine versions.  A prefix is largely independent of the Wine version used.

If you want to keep applications separate from each other, then you can use a different prefix for each application install.

eg.  You want to install starcraft, so you run:

WINEPREFIX=/home/sugi/wine-starcraft wine /media/cdrom/setup.exe

Then, change the prefix for each different application you want to keep separate.


As for keeping multiple wine versions around, you need to build each wine version and then run that version of wine by specifying the full path to it.  

So if you have extracted and compiled wine 1.0 to /home/sugi/wine-1.0

You would then use that version by say /home/sgui/wine-1.0/wine instead of 'wine':

WINEPREFIX=/home/sugi/wine-starcraft ~/wine-1.0/wine /media/cdrom/setup


If you have any further questions, please ask.

---

### Post by binbash on 2008-09-20
Playonlinux does this with a gui.

---

### Post by david_kt on 2008-10-09
> **Sugi said:**
> Can I just install one version of wine (IE Wine 1.0) and then install another version of wine (IE Wine 1.1.5).  So first, install wine 1.0 to directory /.wine.  After the installation, change /.wine to /.wine1.0.  Next, I will install Wine 1.1.5 to /.wine.  After the installation, i then change that directory to /.wine1.1.5.  So now I have two wine directory: wine1.0 and wine1.1.5.  Would that work with the two different wine versions on one computer?

I just make an installer for this purpose, complete with gui. You just need to double click and click to have multiple wine version. See below link:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK

---

