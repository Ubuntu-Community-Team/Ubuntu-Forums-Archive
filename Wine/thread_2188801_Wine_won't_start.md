---
title: "Wine won't start?"
date: 2013-11-19
forum: Wine
---

### Post by Toni_Vines on 2013-11-19
Hi, I'm running Ubuntu 12.04 32 bit on my Intel® Pentium(R) 4 CPU 2.80GHz. I've installed Wine and WineTricks because I need to run Microsoft Access Runtime to access a database. Wine flashes open for a split second and then it's gone! I've done searches on this problem but I'm not getting anywhere.
Can anyone help please?
Thanking you,
Toni.

---

### Post by grahammechanical on 2013-11-19
What are you launching? Wine config? When an application is installed under wine we usually launch the application and wine launches as part of the process of launching the application. Perhaps it is the application that is crashing. You can try launching the application through the terminal and watching for error messages. That may give you some idea what is going wrong. It is a long time since I laucnhed an application in wine and ina terminal. So, I cannot tell you the correct commands. Sorry.

Regards.

Edit: I found this from my copy of the wine manual

>  How to run Wine
You can simply invoke the wine command to get a small help message:

Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
        The first argument should be the name of the file you want wine to execute. If the executable is in the Path environment variable, you can simply give the executable file name. However, if the executable is not in Path, you must give the full path to the executable (in Windows format, not UNIX format!). For example, given a Path of the following:
Path="c:\windows;c:\windows\system;e:\;e:\test;f:\"
      You could run the file c:\windows\system\foo.exe with:
$ wine foo.exe
      However, you would have to run the file c:\myapps\foo.exe with this command:
$ wine c:\\myapps\\foo.exe
      (note the backslash-escaped "\" !)
For details on running text mode (CUI) executables, read the [section]("http://ubuntuforums.org/#CUI-PROGRAMS") below.




---

### Post by Toz on 2013-11-19
*Moved to the **Wine** subforum.*

---

### Post by Mark Phelps on 2013-11-19
Sorry to say this, but you're unlikely to get Access working;

The link is to the WineHQ webpage for Access.  A Bronze rating is very poor -- indicating that very little functionality works:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=12]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=12")

---

