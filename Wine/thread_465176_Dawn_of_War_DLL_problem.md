---
title: "Dawn of War DLL problem"
date: 2007-06-05
forum: Wine
---

### Post by theredcross on 2007-06-05
Installed 0.9.38 and got this lovely message
```
$ env WINEPREFIX="/home/mahdi/.wine" wine "C:\Program Files\THQ\Dawn of War - Dark Crusade\DarkCrusade.exe"
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0xb57aec
$ fixme:exec:SHELL_execute flags ignored: 0x00000400

```
and I get a black screen that crashes. Anyone know what that means, or can tell me were I can find some documentation to translate that error? Looked at the wine wiki a bit and didn't find what I was looking for, but it could certainly be there. anyway, help?

---

### Post by justin whitaker on 2007-06-05
> **theredcross said:**
> Installed 0.9.38 and got this lovely message
```
$ env WINEPREFIX="/home/mahdi/.wine" wine "C:\Program Files\THQ\Dawn of War - Dark Crusade\DarkCrusade.exe"
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0xb57aec
$ fixme:exec:SHELL_execute flags ignored: 0x00000400

```
and I get a black screen that crashes. Anyone know what that means, or can tell me were I can find some documentation to translate that error? Looked at the wine wiki a bit and didn't find what I was looking for, but it could certainly be there. anyway, help?

It is part of .Net 2.0. No idea if it will install under WINE. I did find one download for the DLL, but apparently it is a Beta version, and should not be used.

---

### Post by hikaricore on 2007-06-05
I couldn't find Dawn of War in the Wine Application Database:  [http://appdb.winehq.org](http://appdb.winehq.org)


I may have overlooked it, but are you sure the game can run in wine?

If it's very new it may now be functional under wine at all.

---

### Post by justin whitaker on 2007-06-05
> **hikaricore said:**
> I couldn't find Dawn of War in the Wine Application Database:  [http://appdb.winehq.org](http://appdb.winehq.org)


I may have overlooked it, but are you sure the game can run in wine?

If it's very new it may now be functional under wine at all.

It's listed as Warhammer 40,000 Dawn of War, which is actually the correct title.

[http://appdb.winehq.org/appview.php?iAppId=1918](http://appdb.winehq.org/appview.php?iAppId=1918)

Listed as Gold, Silver, and Bronze, depending on release and installed system:

[http://appdb.winehq.org/appview.php?iVersionId=2576](http://appdb.winehq.org/appview.php?iVersionId=2576)

Hmmm....no mention of the missing DLL error.

---

### Post by theredcross on 2007-06-05
I should mention that it is Dawn of War retail, and I have had it working perfectly up until the point where I installed wine 0.9.38. probably should have mentioned that earlier. But now, even after downgrading back to 0.9.37 I get this error. Going to try taking out the wine repository and use the version in the default repo's.

Oh, and that DLL is in my Dawn of War install directory; I've had it not recognize DLL's in there and had to move one (dlltie.dll) into my home directory, for reasons I can't comprehend it was looking in there. No beans on this trick though.

---

### Post by theredcross on 2007-06-05
Ok, apparently the Fiesty repositories push 0.9.33, could be the problem. Now Dawn of War - Dark Crusade works perfectly, lets just see if I can get these patches working this time through. Thanks!

---

### Post by Spensawr on 2007-06-13
> **theredcross said:**
>  Oh, and that DLL is in my Dawn of War install directory; I've had it not recognize DLL's in there and had to move one (dlltie.dll) into my home directory, for reasons I can't comprehend it was looking in there. No beans on this trick though.

The reason this is happening is that your launcher isn't configured correctly. (or Dow doesn't receive it correctly, which is probably closer to the truth) If you, in the terminal, navigate to where you installed DOW and run ```
wine DarkCrusade.exe
```you won't get the missing dll problem but if you run, for example ```
wine '/home/user/Whatever/DarkCrusade.exe
``` from any other directory it looks for the files where your terminal is currently located, which by default is your home directory. I'm not sure if I explained it well enough, but this was the case on my computer.

---

### Post by axcairns on 2007-09-05
I usually cd into the directory containing the exe first.

---

### Post by cfehunter on 2007-10-12
Sorry to bring up a thread that's over a month old but i'm trying to make a launcher for Dark crusade myself and i'm having the same problem.

i've read through the thread and i can make the game run. But can anybody tell me how to put the command into a launcher please?

Install dir: /media/disk/drive_e/Program\ Files/THQ/Dawn\ of\ War\ -\ Dark\ Crusade/

install dir to wine: E:/Program\ Files/THQ/Dawn\ of\ War\ -\ Dark\ Crusade/

I've tried running a launcher with both:
wine E:/Program\ Files/THQ/Dawn\ of\ War\ -\ Dark\ Crusade/DarkCrusade.exe

and

wine /media/disk/drive_e/Program\ Files/THQ/Dawn\ of\ War\ -\ Dark\ Crusade/DarkCrusade.exe

Neither work, so if anybody can help me i'd be greatfull.  Thanks in advance :)

---

### Post by markackerman8@gmail.com on 2009-06-03
Solution for me

Extract all CD1 archives to a folder. Extract Data2.cab and Data3.cab from cd2 and cd3 in the same folder.
Run the setup.exe.
The installer will not ask for CD2 or CD3, but will ask for cd1 in a windows behind the installer main window in the end, move the installer window and press ok, no more trouble.

---

