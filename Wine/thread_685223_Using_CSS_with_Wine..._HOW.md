---
title: "Using CS:S with Wine... HOW?"
date: 2008-02-02
forum: Wine
---

### Post by wolterh on 2008-02-02
Hi. I've got the latest version of WINE. I DON'T have wine configured.
I would like to configure it for games, specially Counter-Strike Source and Condition Zero.

I have these 2 games installed on windows. Can I use them from there? Or do I have to install them under linux...?

---

### Post by wolterh on 2008-02-02
Nevermind. Now I now you can do it. My question is, how do I change the "fake" windows folder by my real widows folder? That way I will dodge many dll errors.
Also. In My windows system I have programs installed on one drive, and my windows system is in another drive. Is this OK with wine?

I've only been able to run WinRAR archiver from wine till now. Can't run steam, nor photoshop (I takes mileniums to load and it crashes in the end), nor xfire.

Thanks

---

### Post by Poyntz on 2009-06-08
As for CS:S you'll probably need to disable steam. I haven't heard anywhere of anyone being able to get it working. 
From there run CS:S from terminal using ```
cd <path of CS:S>; wine launcher.exe
```
or 
```
cd <path of CS:S>; wine hl2.exe -game cstrike
```.

If the game crashes, it will dump the error in terminal. It will probably say some .dll file is missing or something like that. Google the .dll file. Should be easy to find it and download it. Then put it in either your system32 folder or system folder
ie, inside ~/.wine/drive_c/windows/. Also look up where the .dll file belongs on google. Chances are it belongs in the system32 folder though.

Good luck

---

