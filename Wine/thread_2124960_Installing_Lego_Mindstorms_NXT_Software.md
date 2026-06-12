---
title: "Installing Lego Mindstorms NXT Software"
date: 2013-03-12
forum: Wine
---

### Post by schwarzer ritter on 2013-03-12
Hello,
I wanted to install LEGO® MINDSTORMS® Education NXT Software v1.1 (because we have to use it in school), but I'm facing a problem with WINE:
At first, I copied the files of the install CD in a directory, because the CD automatically got mounted as root and I wasn't able to run any of the files.
So, there are two files for install: autorun.exe and install.exe (as seen in the screenshot).
When I run the first one with wine, I get the error message, that I'm missing a version of the LabView runtime engine (screenshot, terminal produces nothing). I don't know how to get it or if it even is necessary.
The second one produces the following output (in a terminal): ```
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
err:ole:CoUninitialize Mismatched CoUninitialize

``` (there is also a screenshot with the graphical version)
I am using WINE version 1.4.1, I set it to imitate Windows XP and I have an Intel HD 3000 GPU (which shouldn't matter).

---

### Post by Mark Phelps on 2013-03-13
The link below is to the WineHQ website page for Minstorms NXT -- and it's not encouraging:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20789]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20789")

---

