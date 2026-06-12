---
title: "SpiderSolitaire.exe Won't Execute"
date: 2012-11-01
forum: Wine
---

### Post by atothec on 2012-11-01
Hi,

I have copied the SpiderSolitaire folder from my Windows Vista machine and am trying to execute it on Ubuntu 11.10 using Wine but I get the following error in the terminal:

```

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:slc:SLGetWindowsInformationDWORD (L"Shell-InBoxGames-SpiderSolitaire-EnableGame") stub

```In the Configure Wine program I have Windows version set to XP (by default) but have tried changing it to Windows Vista but the same error appears.

Does anyone know a fix?

---

### Post by jerome1232 on 2012-11-01
What's wrong with the solitaire games included with Ubuntu?

---

### Post by atothec on 2012-11-01
I've tried the ones available for Linux but I prefer the Windows ones.

---

### Post by cottfcfan on 2012-11-01
Have you even checked that the Windows version of spider solitaire can be installed under Wine?

---

### Post by atothec on 2012-11-01
Apparently it can:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=164](http://appdb.winehq.org/objectManager.php?sClass=application&iId=164)

The screenshot looks like the Windows XP version but I can't seem to find a download for it so I'm trying to install the Windows Vista version.

---

### Post by jerome1232 on 2012-11-01
I checked, the last test was done in wine version 1.2, get a copy of the 32 bit version, I don't see anything about anyone trying to run the 64 bit one and 64 bit wine is still new.

It seemed to have a few issues, I just can't fathom what's so great about the windows version that makes it worth running in wine rather than simply playing the native one's included with Ubuntu, I tried them out and they didn't seem to be lacking anything obvious.

---

### Post by atothec on 2012-11-01
I'm not running a 64-bit version of Wine as far as I know. This computer isn't a 64-bit machine.

It seems strange that I must justify why I would like to install the Windows version of Solitaire on Ubuntu in a Wine forum, but PySol is full of bugs and hasn't been updated for around 8 years, AisleRiot solitaire plays differently to the Windows Spider Solitaire, and the other versions are just terrible.

I take it there is no solution to my problem?

---

### Post by jerome1232 on 2012-11-01
I'm sorry I got this confused with another thread that I was reading about getting spider solitaire to run, you don't have to justify it, I'm just saying I don't get it, I am actually searching around for ways to get it to run :P

Everything I've read says that it should just work so I have no suggestion for you since you are using a 32 bit version of spider solitaire.

---

### Post by atothec on 2012-11-01
Thanks. This must be a common problem and a popular request. I'll see if I can get hold of a Windows XP version - maybe I'll have more luck. In the meantime if you are able to find a solution please let me know :)

---

### Post by jarreboum on 2012-12-16
Be careful as the XP version plays differently than the Vista/Seven one. On XP you can't go back once new cards have been dealt or a full run has been completed.

---

