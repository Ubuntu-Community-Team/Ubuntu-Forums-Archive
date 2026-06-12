---
title: "Windows/Wine program error &quot;ReSize 32.ocx&quot; - PLEASE HELP :)"
date: 2015-12-24
forum: Wine
---

### Post by andy161 on 2015-12-24
Hello Everyone,

I have installed Wine to run a Windows application (Action! PC Baseball). The package unzipped and installed, but one critical file would not install correctly. And when I load the application, it gives me this error

**Component 'ReSize32.ocx' or one of its dependencies not correctly registered: a file is missing or invalid**

Does anyone know of a way to repair or install this file into Ubuntu? If I can get this file installed correctly, I believe my game will run. 

Any help is greatly appreciated...thank you!!!!

---

### Post by sweldon001 on 2016-01-04
[ATTACH]266537[/ATTACH] here is your much needed file.[ATTACH=CONFIG]266537[/ATTACH]

---

### Post by andy161 on 2016-01-04
Thank you!!

---

### Post by andy161 on 2016-01-04
Quick Question please...I am a newbie in Linux. How do I use this file? Sorry for the dumb question.

---

### Post by sweldon001 on 2016-01-05
you need to access the file manager program as Administrator / Root then place file in Wine directory for c:\ Windows \ system32\   and a copy in the Wine C:\Program files\"Program Folder Appropriate for it to function"

---

### Post by Edwin52 on 2016-01-11
I'm trying to do the same thing you are with Action.  These instructions didn't work.  Action did something in about 2013 and I've never been able to get the game to work since.  I did get earlier editions, like 2008, 09, 10, 11, and 12 to work just fine in Linux.

---

### Post by Edwin52 on 2016-01-13
Open winetricks and install mfc42.dll  
then from a terminal enter wine cmd
This brings up a Windows command line.  Enter regsvr32 ReSize32.ocx
You will get a ReSize registered result.  This fixes the ReSize problem.

But - game will still not run.  Now you will get 429 - ActiveX component can't create object.

I've been trying to fix this one for about 3 years now, no luck.  Dave did something to the game starting with the 2013 version and I haven't been able to get it to run in Linux.  I could before 2013, and it ran great, no problems at all.

---

### Post by sweldon001 on 2016-01-22
I dont know if you can do this is Wine , but here command to reregister DLL and OCX file to fix error/ or you can try to install the following.. Which is a Windows Xp Security problem they caused in SP3 
Command : 
regsvr32 c:\windows\system32\msrdo20.dll

 Application for possibly fixing it in Wine  Link :

[http://www.microsoft.com/en-ca/download/details.aspx?id=13255](http://www.microsoft.com/en-ca/download/details.aspx?id=13255)

---

