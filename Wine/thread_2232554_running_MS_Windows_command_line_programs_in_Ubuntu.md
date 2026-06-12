---
title: "running MS Windows command line programs in Ubuntu"
date: 2014-07-02
forum: Wine
---

### Post by hill0093 on 2014-07-02
I have a windows .exe program file and a text file that 
it should use in a directory whose name I know and know the
location of. I can even prefix these with the directory tree.
I want to run these with Wine. 
I need to know if Wine is installed (I attempted installation).
How do I find out if Wine is installed?
How do I use Wine in this situation?
I have succeeded with a java .jar file on the command line, but
of course that is a different kind of situation.

---

### Post by deadflowr on 2014-07-02
> I need to know if Wine is installed (I attempted installation).
Simply open a terminal and type wine.
if wine isn't installed it'll tell you say something like no command found.
if wine is installed it'll list some options, like help, among others.
That, I think, is the quickest way to find out if wine is installed.

---

### Post by hill0093 on 2014-07-02
It had looked to me like Wine should be capitalized, but wine works.
I have my prog.exe file in a directory binDCH sitting on the Desktop.
But if I type the command binDCH/prog or binDCH/prog.exe, it says
No such file or directory

---

### Post by Mark Phelps on 2014-07-02
Wine is not a runs-anything-from-windows miracle cure; instead, it is a "hack" that will run only some Windows apps.

Since only you know the name of the app, you should do a search for it using the link:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

If it's not found, it most probably will NOT work in Wine.

---

### Post by ubudog on 2014-07-02
Try using:
```
wine Desktop/binDCH/prog.exe
```

---

### Post by oldos2er on 2014-07-02
Moved to Wine.

---

### Post by hill0093 on 2014-07-03
Thanks, 
wine Desktop/binDCH/prog.exe    and
wine Desktop/binDCH/prog
both worked.

---

