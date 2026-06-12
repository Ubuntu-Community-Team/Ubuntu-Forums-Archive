---
title: "ubuntu 18.04 will not run book database 2 on wine"
date: 2018-08-29
forum: Wine
---

### Post by jimbean on 2018-08-29
ubuntu 18.04 fresh install  will not run book database 2 ([http://www.spacejock.com/BookDB.html](http://www.spacejock.com/BookDB.html)) on wine
i run wine on my other ubuntu machine 18.04 upgraded from 17.10
and book database 2 runs fine (perfectly) 
any steps that i might take to figure out the problem would be a major time saver 
but im not good at figuring out what steps 
any help would be great
thanks for any directions

---

### Post by Holger_Gehrke on 2018-09-17
If you had started the program from the shell with 'wine BookDB2.exe' you would have seen what's missing. It's missing MSVBVM60.DLL, part of the VB6 runtime. Get it from [https://www.microsoft.com/en-us/download/details.aspx?id=24417](https://www.microsoft.com/en-us/download/details.aspx?id=24417) and install it (it's a self-extractor which unpacks the actual installer that you need to run to actually install the dll-files you need). After doing that it ran without any problems whatsoever on my machine.

Holger

---

