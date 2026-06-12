---
title: "Brothers Keeper Genealogy Software"
date: 2017-05-02
forum: Wine
---

### Post by Floppyjoe on 2017-05-02
Does anyone know if it's possible to get Brothers Keeper Genealogy software to work properly in Wine? 
I can't get the program to properly see the people in the database.

---

### Post by Dennis N on 2017-05-02
Depends on the version. A quick check finds a good report from Oct 2016 using Ubuntu 16.04:

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=33062](https://appdb.winehq.org/objectManager.php?sClass=version&iId=33062)

There are some suggestions there too.

---

### Post by Floppyjoe on 2017-05-02
> **Dennis N said:**
> Depends on the version. A quick check finds a good report from Oct 2016 using Ubuntu 16.04:

[https://appdb.winehq.org/objectManager.php?sClass=version&iId=33062](https://appdb.winehq.org/objectManager.php?sClass=version&iId=33062)

There are some suggestions there too.

Thanks, I tried the suggestions but still no joy.

---

### Post by mastablasta on 2017-05-03
you could try using playonlinux or use an alternative software such as gramps: [http://alternativeto.net/software/brother-s-keeper/?license=free&platform=linux](http://alternativeto.net/software/brother-s-keeper/?license=free&platform=linux)

---

### Post by Floppyjoe on 2017-05-07
> **mastablasta said:**
> you could try using playonlinux or use an alternative software such as gramps: [http://alternativeto.net/software/brother-s-keeper/?license=free&platform=linux](http://alternativeto.net/software/brother-s-keeper/?license=free&platform=linux)

I have gramps installed but the database I am using has over 1,100,000 names in it. When I try to import that database into gramps the file size of the import seemed exceedingly large and bloated and took up too much hard drive space.

Brothers Keeper doesn't seem to be on the playonlinux supported software list.

---

### Post by mastablasta on 2017-05-08
what abotu geneweb it says o wine it is another alternative.

anyway the program Brothers Keeper has gold rating, so it should easilly run.:

> [TABLE="class: table"]
[TR]
[TD]**Wine Version:**[/TD]
[TD]1.9.21[/TD]
[/TR]
[/TABLE]


> **Additional Comments**
Installed Brother's Keeper v7.1.16 on Wine 1.9.21 on Ubuntu 16.04 amd64

Requires MSVBM60.DLL which is not included. You may manually copy it from a Windows (XP or 7) partition to c:\windows\syswow64\ or you can install vb6run with WineTricks.

Runs datafile from folder under c: or z:

A printer must be installed in Linux before attempting to view reports otherwise the program will lock-up or give an error. Prints reports well.

where exactly do you get stuck?

also if gramps creates a large database, perhaps there is some data added that doesnt' have to be there. Did you explore the option of reducing the database? filter it in some way?

---

### Post by Floppyjoe on 2017-08-04
I managed to get it working by following these instructions:
> It can be a little tricky. I did something very similar to this to get it work on the Mac. This post from a Linux user on the Crossover site may help you.

I was unable to get BK6.6 to run in Crossover for the same reasons. However, I looked at WineHQ and found that the installation process must be changed.

Please try:

- Create a new bottle for Windows XP
- First install Runtime for Visual Basic 6
- Install Brother's Keeper, but notice:
* Select install directory of C:\BK6 with no spaces
- After installation is complete, run the program 1 time then exit
- Delete C:\Brother's Keeper directory
- Run the program again and it will ask if it should create a data directory. Answer Yes. It will then store data in C:\BK6 directory instead.
- Everything should now work. However, if you find things that do not, please post. I do not normally use Brother's Keeper, but it is a good program.

[EDIT] Sorry, I forgot to mention that I'm using CrossOver Linux 12.5, but the Mac version is normally very much the same. I will test on my Mac if/when I get it fixed.

I added a printer in Linux and so the pedigrees display the way they are supposed to.

---

