---
title: "installing wine"
date: 2006-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by weird_c00kie on 2006-10-12
hi there
allow to me to apologise in advance for creating this topic when there are already others treating the issue.
i've looked through all the ones i could find though and i still can't get wine to work on my amd64 :(

i've looked here
[http://www.ubuntuforums.org/showthread.php?t=274916&highlight=install+wine](http://www.ubuntuforums.org/showthread.php?t=274916&highlight=install+wine)
and here
[http://www.ubuntuforums.org/showthread.php?t=53824&highlight=install+wine](http://www.ubuntuforums.org/showthread.php?t=53824&highlight=install+wine)
and here
[http://ubuntuforums.org/showthread.php?t=5458&highlight=install+wine](http://ubuntuforums.org/showthread.php?t=5458&highlight=install+wine)
and here
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

but i always run into problems :(
files missing, commands not working etc etc

i'm about as n00bish as you can be in the world of linux and of not installing things just by double-clicking the exe file, so don't make any assumptions about my knowledge of the OS.

if it is at all possible to be shown a clear, step-by-step guide on how to do it, i would be forever grateful... and be ready for questions and posts with errors in them :p

thanks in advance for any help you can provide :)

---

### Post by weird_c00kie on 2006-10-12
FINALLY!
i followed the guide here:
[http://ubuntuforums.org/showthread.php?t=185557&highlight=wine](http://ubuntuforums.org/showthread.php?t=185557&highlight=wine)

and got it working!

*dances around*

---

### Post by weird_c00kie on 2006-10-12
well now that it's installed, i have a different question


is there any way to run *.msi setup files as well, or does wine only handle *.exe files?

---

### Post by kuja on 2006-10-12
I'm not sure. Why not give it a shot? What's the worst that could happen?

---

### Post by weird_c00kie on 2006-10-12
well, i tried. wine doesn't see msi files :(

no matter. the only reason i needed it was to install my windows email client (thebat) and then use that to export my emails to Evolution
awfully painstaking process, having to export each folder individually :/

---

### Post by Sanne on 2006-10-12
The wine package comes with a tool called msiexec, I used it to install msi files like this:

Open a terminal, cd to the folder where your msi file resides (must be somewhere under the fake windows drive wine set up for you, default in ~/.wine/drive_c), and install it with the command:

```
msiexec /i msifile.msi
```

You can get command line options of msiexec with

```
msiexec /h
``` 
or
```
msiexec /?
```

Sanne

---

### Post by weird_c00kie on 2006-10-13
oh. thanks for that :D

---

### Post by Sanne on 2006-10-13
You're welcome :)

---

### Post by weird_c00kie on 2006-10-23
hmm... tried the msiexec thingy, but i keep getting this error message:

> \err:module:import_dll Library msi.dll (which is needed by L"c:\\windows\\system32\\msiexec.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\msiexec.exe" failed, status c0000135

---

### Post by Sanne on 2006-10-23
Usually when this happens, it means wine can't find a dll it needs to run a program, in this case msiexec, which needs msi.dll. I have a mse.dll (10.9 KB) in my ~/.wine/drive_c/windows/system32 folder, can't remember to do anything specific to make the msi installer work. Do you have such a file?

If the file is not there, you have two options you can try: first, if you have a Windows install, search for msi.dll there, copy it over and try again. The second option would be to install it yourself. Here's a page you might want to follow that should help with that at [linuX-gamers]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine"), scroll down to point 5: Installshield Installers.

EDIT: Try just point 5.2 MSI first, without the DCOM stuff. I also don't need to do the dll overrides, so skip that also first. Just install msi and after that try 'msiexec /h' in a terminal.

Hope it helps, tell me how it goes.
Sanne

---

### Post by weird_c00kie on 2006-10-25
hmm... i copied the dll from my XP installation on the other drive. now when i try it it gives me this:

> 
err:ole:create_server class {000c101c-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {000c101c-0000-0000-c000-000000000046} could be created for context 0x4
fixme:advapi:RegisterEventSourceW ((null),L"MsiInstaller"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x000003f7,0x19ce38,0x0004,0x00000000,0x617a4f84,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


---

