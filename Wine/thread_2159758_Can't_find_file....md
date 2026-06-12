---
title: "Can't find file..."
date: 2013-07-04
forum: Wine
---

### Post by sal55 on 2013-07-04
I have a Windows program prog.exe at: /home/abc/def/prog.exe (together with all the other files it uses).

Typing 'wine prog.exe' or 'wine ./prog.exe' while in the current directory gives me this error:

wine: cannot find L"Z:\\home\\abc\\def\\prog.exe"

What does it mean?!

---

### Post by newbie-user on 2013-07-04
Make sure the program is executable:
```
chmod +x prog.exe
```

---

### Post by sal55 on 2013-07-04
> **newbie-user said:**
> Make sure the program is executable:
```
chmod +x prog.exe
```Thanks, but, that didn't seem to work.

It does work if prog.exe is copied to /home/abc (my normal home directory). (Or at least, it makes an attempt to execute it. But there are missing DLL files it's not picking up, which is why I'm copying the lot from the original Windows folder to Linux.)

Looking at it in file manager, it says I am not the owner, so can't change permissions (yet chmod didn't complain). The current permissions are read-write/read-only/none for Owner/Group/Others (I don't understand what these are...).

Why shouldn't I be the owner? It was me that copied it from Windows!

---

### Post by sal55 on 2013-07-04
> **sal55 said:**
> 
Looking at it in file manager, it says I am not the owner, so can't change permissions (yet chmod didn't complain). The current permissions are read-write/read-only/none for Owner/Group/Others (I don't understand what these are...).


I deleted that folder containing the application (eventually..). Then recreated it using the gui file manager. This time the permissions were set up properly.

However it's now moaning about mfc42.dll/MFC42.DLL which I've copied also and it still doesn't work.

Elsewhere it was suggested I use 'winetricks mfc42', but it gives a 404 error trying to download from the Microsoft site.

Somewhere else still, it was said I can get around that by using 'sudo add-apt-repository ppa:ubunto-wine/ppa' (who discovers all these incantations?). But that didn't work either ('Cannot access PPA'). I can't believe however I need to go to all this trouble just to install a file which as far as I know, I already have! Where does wine expect to load these support files from? (And why doesn't it already have them?)

I give up. (The application is not that important; it works in XP, but not in 64-bit Windows, yet I don't think it's a 16-bit app. It was worth spending a few minutes seeing if it ran on wine, bút no more, and I doubt that MFC42.DLL was the only  hurdle remaining.)

---

### Post by Lightning Dragon on 2013-07-05
Hi,

Don't give up yet.

> Looking at it in file manager, it says I am not the owner, so can't  change permissions (yet chmod didn't complain). The current permissions  are read-write/read-only/none for Owner/Group/Others (I don't understand  what these are...).

Instead, open up the terminal and sudo the following;

*sudo nautilus*
(assuming you are using Ubuntu)

This will bring up two windows, the terminal (still) and the file manager with admin/root rights. Now navigate to the folder of the .exe within the file manager window the sudo command brought up, and right click the .exe to enter properties. Now, on the _second tab_, you can check the the box to make it executable. You will know it is the box because it says "Execute: > [checkbox] allow executing files as program".

---

