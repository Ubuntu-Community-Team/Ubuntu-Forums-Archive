---
title: "EVE Online Launcher"
date: 2013-05-22
forum: Wine
---

### Post by Fahuadai on 2013-05-22
As some of you in the linux Eve online community will no doubt know, CCP upgraded EVE's launcher and it's stopped working.

I'm still about to login using 
```
wine "C:\Program Files\CCP\Eve\bin\exefile.exe"
```
and
```
wine "C:\Program Files\CCP\Eve\repair.exe"
```
to do the updates.

When I run the normal launcher though, it starts, but there's no EULA text or logon buttons. [Image]("http://is.gd/YQ8TZ6")

Anyone got it working?

---

### Post by Drenriza on 2013-05-23
It worked fine for me right after the update, but after closing the problem once i experience kinda the same problems.
The launcher opens, but i dont get the "launch" button to start the game.

---

### Post by Fahuadai on 2013-05-23
Are you able to update via the repair.exe and connect and play still?

---

### Post by Buddlespit on 2013-05-25
Once I got the launcher working, it gave an error code 7 *in the launcher itself*. I had to right click and drag across the error message because the text was black-on-black. I then ran repair.exe, then rebooted Kubuntu. Eve launched just fine afterwards.

---

### Post by Drenriza on 2013-05-26
> **Buddlespit said:**
> Once I got the launcher working, it gave an error code 7 *in the launcher itself*. I had to right click and drag across the error message because the text was black-on-black. I then ran repair.exe, then rebooted Kubuntu. Eve launched just fine afterwards.

What libraries are you using in wine?
Since i cannot launch EVE, even after the repair.exe is run.
And now i get a repair.exe error when i try run it again. Soooo something is not right.

---

### Post by Fahuadai on 2013-05-26
> **Drenriza said:**
> What libraries are you using in wine?

I've still not got the launcher working. My DLL override libraries as shown in winecfg are:

d3dx9_24  through d3dx9_42;
msvcr100 (native, builtin);
msvcr80 (native, builtin);
msvcr90 (native, builtin);
mscrt (native, builtin);

---

### Post by mentar on 2013-05-27
Having the same issue. It looks like the block that requests the login details fails somehow. You can see some text underneath:

> Error -7 when loading url https://login.eveonline.com/oauth/authorize/?client_id=eveLauncherTQ&lang=en&response_type=token&redirect_uri=https://login.eveonline.com/launcher?client_id=eveLauncherTQ&scope=eveClientToken"

If I find a way to go around this I'll mention it on this thread

---

### Post by Fahuadai on 2013-05-28
> **mentar said:**
> Having the same issue. It looks like the block that requests the login details fails somehow. You can see some text underneath:



If I find a way to go around this I'll mention it on this thread


Thanks. I've got it working in the way I described above (without the launcher) but if they change it in the future to require the launcher my workaround won't work.

---

### Post by Drenriza on 2013-05-28
I get the following error

cristian@cristian-ubuntu12:~$ wine "C:\Program File\CCP\Eve\bin\exefile.exe"
wine: cannot find 'C:\Program File\CCP\Eve\bin\exefile.exe'

---

### Post by Fahuadai on 2013-05-28
> **Drenriza said:**
> I get the following error

cristian@cristian-ubuntu12:~$ wine "C:\Program File\CCP\Eve\bin\exefile.exe"
wine: cannot find 'C:\Program File\CCP\Eve\bin\exefile.exe'

D'oh! Sorry I've missed the 's' in program files. Try this:

wine "C:\Program Files\CCP\Eve\bin\exefile.exe"

(I'll edit my original post)

---

### Post by Drenriza on 2013-05-29
> **Fahuadai said:**
> D'oh! Sorry I've missed the 's' in program files. Try this:

wine "C:\Program Files\CCP\Eve\bin\exefile.exe"

(I'll edit my original post)

Even if i do wine "C:\Program Files\CCP\Eve\bin\exefile.exe" wine say it cannot find the executable file :( How come is that?
I can start the launcher without trouble, just not enter the game.

Edit.
Figured it out, i needed to say 
```
wine "C:\Program Files (x86)\CCP\Eve\bin\ExeFile.exe"
```

---

### Post by YourOlympicHero on 2013-06-01
Myself, I just keep going in circles, launcher patches, I repair, start launcher, no where to log in but since I am there the launcher repatches.... I then repeat... I keep thinking I am missing something so I am going to sleep and hope I figure it out later.

---

