---
title: "[SOLVED] installing a program with Wine"
date: 2008-06-10
forum: Wine
---

### Post by fmpfmpf on 2008-06-10
i used wine to install a Windows program. 
At the end of the installation, it says:- 

"The publisher of the data "C:\windows\temp\VSD5ba.tmp\dotnetfx\dotnetfx.exe cannot be verified." 

i looked through the files and found out that "C:\windows\temp\VSD5ba.tmp\dotnetfx\dotnetfx.exe" does not exist. 
there isnt any dotnetfx.exe, instead there is dotnetchk.exe. 

what should i do to solve this?

tq

---

### Post by Sef on 2008-06-10
Moved to WINE forum.

---

### Post by cogadh on 2008-06-10
It would help to know what program you are trying to install and what terminal output Wine produced. 

BTW - Wine has an excellent database of applications that are known to work and not work with Wine, plus details on what you might need to do to install and run your application: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by fmpfmpf on 2008-06-10
terminal output?

---

### Post by cogadh on 2008-06-10
When installing applications with Wine, you should use the terminal to run it, instead of simply double-clicking on the executable. Wine outputs its error messages to the terminal, so if Wine is encountering a problem, that is the only way you will find out about it. Once you have an application installed and running properly, then you can use the normal shortcuts to run the actual application.

To run an install executable in the terminal, open a terminal and do this:
```
wine /path/to/exeutable/<executable name>.exe
```
Obviously, change the path and executable name to match where you have the install executable and the actual executable name.

---

### Post by fmpfmpf on 2008-06-11
yes, that is what i did and i got that problem

---

### Post by cogadh on 2008-06-11
But the error message you posted was not Wine's error output, it is the application's own error, which is basically useless for troubleshooting purposes with Wine. If you ran the application with Wine from the terminal, there should have been numerous messages output from Wine itself, one of which may point to the actual source of the problem. I've attached a screenshot of what I get when I run a game through Wine from the terminal, as an example of what I mean.

BTW - You never answered when I asked what application you are trying to run. Not everything works with Wine and some things need some very specific Wine configurations before they will work. It would really help if you told us that info, since we could then offer some very specific solutions to the problem.

---

### Post by fmpfmpf on 2008-06-12
nevermind, i have suceeded with what i need to do with other methods
thanks :)

---

