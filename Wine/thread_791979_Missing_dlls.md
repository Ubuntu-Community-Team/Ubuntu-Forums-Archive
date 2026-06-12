---
title: "Missing dlls?"
date: 2008-05-12
forum: Wine
---

### Post by cminicooperj on 2008-05-12
I'm new with wine and I'm not completely sure what the problem is. I think some of the dlls are missing.  When I try to run any program, I get this error:

err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\home\\distortion\\Desktop\\HackTheGame121\\HackTheGame.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\distortion\\Desktop\\HackTheGame121\\HackTheGame.exe" failed, status c0000135

I ran these programs a few days ago, including 7zip, Hack: The Game and Visual Basic Portable.  All give me the same error now.  I'm sorry if this is a newbish post but could someone tell me how to fix this?

---

### Post by happysmileman on 2008-05-12
I just downloaded Hack the game and got the same error.

Assuming you have a copy of Windows installed just copy the file C:\WINDOWS\System32\MSVBM60.dll (or whatever it's called) into /home/<username>/.wine/drive_c/windows/system32

If you don't have a copy of Windows: i'm not too Sure about thE legality of usiNg the winDows dll files, MaybE you could buy A copy of windows to solve your ProbleM

---

### Post by Kinst on 2008-05-12
Put this in windows/system32, then try setting it to native and see what happens.

[link]("http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60")

---

### Post by cminicooperj on 2008-05-12
Ok thanks, I guess I'll just have to install windows on my other hard drive.  The only thing I dont get is that it was just running.  There wasnt one problem with it. And then it stopped and asked for the dll.  But thanks for the help, I appreciate it.

---

### Post by Kinst on 2008-05-12
Um what, you don't need to install windows, it's so easy to find dll files. I gave you a link, here it is again: 

[http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60]("http://www.dll-files.com/dllindex/dll-files.shtml?msvbvm60")

I don't know why your thing broke, but probably you updated wine to a new version? If that's the case you can always delete your wine folder and reinstall everything with the old version.

---

### Post by cminicooperj on 2008-05-18
Allright thanks alot.  And I figured out that my friend updated the game on me.  The older version runs fine.  Sorry for the trouble.

---

