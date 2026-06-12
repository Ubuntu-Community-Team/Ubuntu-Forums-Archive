---
title: "[SOLVED] problems with installing .net framwork on wine"
date: 2008-09-05
forum: Wine
---

### Post by da.tiger on 2008-09-05
Hi

I ve tried to install the .net frame work, however, towards the end of installation, theres an error something like

X server is not running, please check that values in Display are set.............Aborted



 or something on those grounds. Not the exact error.

Please help

Edited to add info :

latest wine version, because i installed it only yesterday,

.net framework 2.0

Executing wine /root/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapiecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Note: command 'wine /root/.winetrickscache/dotnet20/dotnetfx.exe' returned statu s 43. Aborting.

---

### Post by ajackson on 2008-09-05
Posting the exact error message plus wine version and version of .NET that you are installing would be useful.

---

### Post by bubba_169 on 2008-09-05
Have you tried mono? Mono is a free implementation of the .net framework and I dont think you need wine to run it. Just open your .net program exe in mono and theres a good chance it will run!

---

### Post by da.tiger on 2008-09-05
latest wine version, because i installed it only yesterday,

.net framework 2.0

Executing wine /root/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Note: command 'wine /root/.winetrickscache/dotnet20/dotnetfx.exe' returned statu                                                                            s 43.  Aborting.

---

### Post by ajackson on 2008-09-05
> **da.tiger said:**
> latest wine version, because i installed it only yesterday
Humour me and do a
```
wine --version
```

Also have you checked the [AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754")?

---

### Post by da.tiger on 2008-09-05
here you go,

wine-1.0

Checked the AppDB, nothing on this error. :)

---

### Post by da.tiger on 2008-09-05
problem solved.

---

### Post by ajackson on 2008-09-05
> **da.tiger said:**
> here you go,

wine-1.0
Wine 1.1.3 is the latest version, that is why I asked you to post the version you have because 1.0 is in the official Ubuntu reps but you need to add the wine reps (see the wine site) to get the latest version.

Also you say you solved it, how? It could help others if you tell us what you did to fix the problem.

---

### Post by da.tiger on 2008-09-19
If you are facing the same problem, please do NOT run .net from Root terminal,.

---

### Post by ahmednasir91 on 2009-03-07
Well I have got SSH access and I am running it through putty as a root.. and getting same error, what you mean by not run as root user.
I have ubuntu 8.10 its a remote server.

Thanks

---

