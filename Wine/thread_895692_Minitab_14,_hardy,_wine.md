---
title: "Minitab 14, hardy, wine"
date: 2008-08-20
forum: Wine
---

### Post by issueperson on 2008-08-20
I am a Wine newb so I am sorry if I am asking a question that should be obvious.

I am trying to get Minitab 14 to work in Wine (the AppsDB on Wine says it worked on an older version).  But after what seems like a normal install, Minitab will not run.  The icon appears on the taskbar like it is trying to run, then disappears.

Here is what happens in the terminal:

```
bash:~:$ env WINEPREFIX="/home/brady/.wine" wine "Z:\home\brady\Programs\.minitab\mtb14.exe" 
err:ole:CoGetClassObject class {78a51822-51f4-11d0-8f20-00805f2cd064} not registered
err:ole:CoGetClassObject class {78a51822-51f4-11d0-8f20-00805f2cd064} not registered
err:ole:create_server class {78a51822-51f4-11d0-8f20-00805f2cd064} not registered
err:ole:CoGetClassObject no class object {78a51822-51f4-11d0-8f20-00805f2cd064} could be created for context 0x7
err:ole:CoFreeUnusedLibrariesEx apartment not initialised
err:ole:CoUninitialize Mismatched CoUninitialize

```

Any help is greatly appreciated.

---

### Post by Unicast on 2008-08-24
I'll bump this for you as I'd like to see minitab up and running with wine on Hardy.

---

### Post by gilmesh on 2008-09-05
I'm having this exact problem.  Any help would be greatly appreciated.

---

### Post by llh11456 on 2008-09-06
If games like [buy wow gold](http://www.usfine.com/world-of-warcraft-usa-c-51.html) Quake and Doom defined action gaming in the gaming world, Need for Speed was the definition of racing games. Need For Speed, [maple story power leveling](http://www.usfine.com/Maple-Story-PowerLeveling-c-98.html) or NFS for short has been around since almost the beginning of when computer gaming gained importance. [runescape power leveling](http://www.usfine.com/runescape-powerleveling-c-90.html)Need For Speed is [runescape powerleveling](http://www.usfine.com/runescape-powerleveling-c-90.html) a racing game in which the player chooses cars and then races on various tracks.welcome to our website[wow gold](http://www.usfine.com/)

---

### Post by qwertymn on 2008-09-06
err:ole:create_server class {78a51822-51f4-11d0-8f20-00805f2cd064} not registered
err:ole:CoGetClassObject no class object {78a51822-51f4-11d0-8f20-00805f2cd064} could be created for context 0x7

I don't know if it's the cause for the crash, but apparently this app needs pdm.dll. You could try copy it from a windowspartition to ~/.wine/drive_c/windows/system32/
Then register it: 'regsvr32 pdm'

Maybe it helps , always worth a shot i'd say

---

### Post by Random Adam on 2008-09-27
Hi i'm trying to install minitab 14, i have wine 1.1.5 the installer starts and i get an error "1628: Failed to complete installation" after the 'preparing to install' dialog finishes. Any ideas?

---

### Post by costis on 2008-11-10
Has anyone found a solution for running Minitab?

I think it has something to do with ole32 DLL overrides, but I cannot figure it out.

Thanks in advance...

---

