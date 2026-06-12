---
title: "Breezy Badger"
date: 2006-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by PandabeaR on 2006-02-03
```
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20amd64%20(20051012)_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
 
```

:( somethings wrong and I dont know what it is...

---

### Post by MartinG on 2006-02-03
Apt seems to have "lost" your installation CD. Try commenting out the relevant lines in /etc/apt/sources.list, and then running```
sudo apt-cdrom add
```You will need the CD in the drive, and this command will re-scan and add it to sources.list.  If this all works and you don't get the errors you referred to you can remove completely the lines you earlier commented.

---

### Post by PandabeaR on 2006-02-03
how do I comment out lines?

---

### Post by bonzodog on 2006-02-03
You need to edit the sources.list file,
Open a terminal, and type in 
```
$sudo gedit /etc/apt/sources.list
```

it will ask for your password, just type that in (you won't see it on the screen).

The very first line in the file is the cdrom line. To comment it out just put a '#' at the beginning. You do not need cdrom sources at all. while you are there, enable the universe repositories, by uncommenting the lines that mention them. at the end of the lines where universe is mentioned, add the word 'multiverse'.

Save the file, and in the terminal enter 
```
$sudo apt-get update
```
this will update your repos list of software.

---

