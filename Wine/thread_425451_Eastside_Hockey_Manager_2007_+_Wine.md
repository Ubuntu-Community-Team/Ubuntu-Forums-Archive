---
title: "Eastside Hockey Manager 2007 + Wine"
date: 2007-04-27
forum: Wine
---

### Post by boris yeltsin on 2007-04-27
Trying to run EHM2007 with wine off of the Windows partition, tried Emulating a virtual desktop that's the same size as the game itself, and tried running without the virtual desktop. When it runs with a virtual desktop it stays on screen for a second or two and then closes without any message. 

Help would be greatly appreciated.

---

### Post by SoggyCornflake on 2007-04-27
> **boris yeltsin said:**
> When it runs with a virtual desktop it stays on screen for a second or two and then closes without any message. 

Help would be greatly appreciated.

Did you try it from a command prompt or did you double click on the exe icon?  If  you clicked on the icon, you won't get any error messages. 

If you use a terminal session, navigate to the directory containing EHM2007.exe and type:```
wine EHM2007.exe
``` you should probably get some error messages in the terminal session.

If you could post whatever you get into a reply, probably a Wine expert could guide on fixing it.

---

### Post by boris yeltsin on 2007-04-27
> **SoggyCornflake said:**
> Did you try it from a command prompt or did you double click on the exe icon?  If  you clicked on the icon, you won't get any error messages. 

If you use a terminal session, navigate to the directory containing EHM2007.exe and type:```
wine EHM2007.exe
``` you should probably get some error messages in the terminal session.

If you could post whatever you get into a reply, probably a Wine expert could guide on fixing it.

Okay, I got

```
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
jesse@jesse-desktop:/media/E/Pelit/NHL Eastside Hockey Manager 2007$ 

```

---

### Post by SoggyCornflake on 2007-04-27
> **boris yeltsin said:**
> Okay, I got

```
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
jesse@jesse-desktop:/media/E/Pelit/NHL Eastside Hockey Manager 2007$ 

```
I am not a Wine expert, but am still holding out for one to notice this thread.

I did do some poking around the forums here and found this [link]("http://ubuntuforums.org/showthread.php?t=279754&page=2&highlight=C%3A%5C%5Cwindows%5C%5Csystem32%5C%5Cdrivers%5C%5CSECDRV.SYS%29+not+found")


I'm guessing Hockey Manager is made by the same people as Football Manager.  There's **LOTS** of discussion in that thread and it addresses several different aspects of getting a similar program running with wine.  What I gleaned from that thread is that your problem may be a copy protection issue with the program.  The advice given to in that thread was to find a no-cd patch.  There was also some advice about installing a Windows version of Java.

Another option would be to use **winecfg** and set your wine install to emulate windows 98. 

Hopefully one (or a combination) of those steps will get it up and running for you.

---

### Post by GGrimmelt on 2007-04-27
I'm trying to get EHM 2005 to work. It starts to run but then simply states: "Unable to load fonts"

Any help?

---

### Post by jasonditz on 2009-08-30
I know this thread's a zillion years old but I installed EHM 2007 on a vanilla install of 9.04 and it worked like a dream. Amazing because the OSX version runs like crap now (PPC binary only and really slow in Rosetta) and it won't run at all in Vista. Looks like if you want your EHM fix Ubuntu might be the way to go.

---

