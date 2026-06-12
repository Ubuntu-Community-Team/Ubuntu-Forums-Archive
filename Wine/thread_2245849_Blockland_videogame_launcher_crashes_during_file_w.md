---
title: "Blockland videogame launcher crashes during file writing"
date: 2014-09-26
forum: Wine
---

### Post by Ethan_Arns on 2014-09-26
Blockland is a 3D videogame that starts up with a launcher. Basically, it downloads any missing files and then overwrites all the base files. While it is doing this for me, about 1/4th of the way through file writing, it turns grey. It still runs while grey, but as soon as the program opens (and it looks perfectly good at first) it crashes. The console reads this:
```
err:ole:CoGetClassObject class {25e609e0-b259-11cf-bfc7-444553540000} not registered
err:ole:CoGetClassObject no class object {25e609e0-b259-11cf-bfc7-444553540000} could be created for context 0x1
err:dinput:DirectInput8Create CoCreateInstance failed with hr = 0x80040154
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
ethan@h4ck1nt0sh64:~/.wine/drive_c/Program Files/Blockland$ err:ole:CoGetClassObject class {25e609e0-b259-11cf-bfc7-444553540000} not registered
err:ole:CoGetClassObject no class object {25e609e0-b259-11cf-bfc7-444553540000} could be created for context 0x1
err:dinput:DirectInput8Create CoCreateInstance failed with hr = 0x80040154
err:console:AllocConsole Can't allocate console
fixme:thread:start_thread Started native thread 00000018
fixme:thread:start_thread Started native thread 00000019
fixme:thread:start_thread Started native thread 0000001a
wine: Unhandled page fault on read access to 0x00341008 at address 0x424b73 (thread 0016), starting debugger...
err:seh:start_debugger Couldn't start debugger ("winedbg --auto 21 148") (2)
Read the Wine Developers Guide on how to set up winedbg or another debugger
AL lib: ReleaseALC: 1 device not closed
```

---

### Post by Ethan_Arns on 2014-09-27
I upgraded to the most recent version (1.7) and installed PlayOnLinux, then used the Nvidia-produced graphics driver. It seems to work fine now.

---

