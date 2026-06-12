---
title: "Wine installaton error"
date: 2007-12-29
forum: Wine
---

### Post by bharadwaj on 2007-12-29
The last night while I was trying to install Photo Shop CS3 extended I was getting this error 
> This software can not be installed because JScript is not properly registered. Please repair the JScript and restart the installer

Can anybody help me out in repairing the JScript please. The last time I remember, I had to install java for running Limewire but it was unsuccessful. Right now when I try to un-install it from the add/remove progs of wine nothing seems to be happening.

---

### Post by eagledrc on 2008-01-03
I had the exact same problem.  Someone help please!

---

### Post by FishEyes on 2008-01-03
Have you checked to make sure you have a jscript.dll in the "C:\windows\system32\" of your .wine?

---

### Post by eagledrc on 2008-01-04
[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb401521&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb401521&sliceId=1)
Do that to register jscript.dll on your C:\windows\system32\ of your wine.

---

### Post by eagledrc on 2008-01-04
[http://ubuntuforums.org/showthread.php?t=621980&page=2](http://ubuntuforums.org/showthread.php?t=621980&page=2)

---

### Post by bharadwaj on 2008-01-08
> **eagledrc said:**
> [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb401521&sliceId=1](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb401521&sliceId=1)
Do that to register jscript.dll on your C:\windows\system32\ of your wine. But I ain't getting any clue to install proceed through the walkthruogh. I found this link useful but same problem here, Iam not that familiar to linux or wine as much as i'am to windows

---

### Post by eagledrc on 2008-01-08
someone said to copy the content of the DVD to your HD...

---

### Post by hikaricore on 2008-01-08
Errmm.... you are aware of how badly PS CS3 runs under WINE correct?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

From what I can tell no one has even been able to install it, so unless you have a beta version you're SOL for now.
Perhaps you should look into running a virtual machine?

---

### Post by eagledrc on 2008-01-08
I am going to keep trying to install it...It will happen eventually and I am very determined.
I am also working on the virtual machine.

---

### Post by yariver on 2008-02-24
THanks for the info up to now
But when I tried the same solution I got this message:
"yariv@yariv-laptop:~/.wine/drive_c/windows/system32$ regsvr32 jscript.dll
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Failed to load DLL jscript.dll
[email]yariv@yariv-laptop:~/.wine[/email]/drive_c/windows/system32$ 
"
Anyone can help?
Thanks

---

### Post by bharadwaj on 2008-03-06
I am tired of trying to install finally got back to PS 7 it is perfect and has very few bugs ....

---

