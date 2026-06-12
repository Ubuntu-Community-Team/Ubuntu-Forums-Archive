---
title: "iTunes 8.01"
date: 2008-10-17
forum: Wine
---

### Post by TekNullOG on 2008-10-17
OK, I've heard and read that iTunes works with Wine. I've even seen posts in the Ubuntu forums that 8.0 work but when I go to Apple's site and download 8.01 (slightly newer version), the installation freezes... nothing. I wait and wait... and after about 15 mins, I try to cancel but nothing. Even X seems like it is lagging cuz i get black squares all over my screen during install. I end up having to kill Wine to get control back of my laptop.

Has anyone experienced this? Will Wine get updated and this version will eventually work?

Is there a place where I can get an older version of iTunes that will work with Wine?

Why do I want iTunes? I don't personally like it all that much but my radio station is apparently being added to the station listings tonight. I would prefer to not start up a Windows machine every time I want to check up on it.

Anyways, thanks for the help in advance!

P.L.U.R.

---

### Post by ooobuntooo on 2008-10-17
I get this output from the terminal when installing iTunes 8.

```
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:advapi:ImpersonateLoggedOnUser (0x6a8)
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 3 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 44 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 5 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveEnvironmentStrings -> 5 ignored L"Environment" table values
fixme:msi:msi_unimplemented_action_stub RemoveDuplicateFiles -> 1 ignored L"DuplicateFile" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 7 ignored L"CreateFolder" table values
fixme:msi:ITERATE_WriteEnvironmentString Not removing environment variable on uninstall!
fixme:msi:ITERATE_WriteEnvironmentString Not removing environment variable on uninstall!
fixme:msi:ITERATE_WriteEnvironmentString Not removing environment variable on uninstall!
fixme:msi:ITERATE_WriteEnvironmentString Not removing environment variable on uninstall!
fixme:msi:ITERATE_WriteEnvironmentString Not removing environment variable on uninstall!
fixme:win:EnumDisplayDevicesW ((null),0,0x7e1398c8,0x00000000), stub!
err:msi:HANDLE_CustomType34 Unable to execute command L"C:\\Program Files\\QuickTime\\QTTask.exe -atboottime"
fixme:advapi:LookupAccountNameW (null) L"greg" (nil) 0x33ed38 (nil) 0x33ed3c 0x33ed30 - stub
fixme:advapi:LookupAccountNameW (null) L"greg" 0xda19f8 0x33ed38 0xda18e8 0x33ed3c 0x33ed30 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 4 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 4 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 2 ignored L"ServiceControl" table values
fixme:msi:msi_unimplemented_action_stub SelfUnregModules -> 1 ignored L"SelfReg" table values
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 5 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 2 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 3 ignored L"CreateFolder" table values
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:shell:DllCanUnloadNow stub
fixme:winsock:WSCUnInstallNameSpace (0x1609f004) Stub!
fixme:winsock:WSCInstallNameSpace (L"mdnsNSP" L"C:\\Program Files\\Bonjour\\mdnsNSP.dll" 0x0000000c 0x00000001 {b600e6e9-553b-4a19-8696-335e5c896153}) Stub!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:msi:ITERATE_InstallService Dependency list unhandled!
err:msi:ITERATE_StartService Failed to start service L"Bonjour Service"
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:custom_get_thread_return Invalid Return Code 1627
err:msi:ITERATE_Actions Execution halted, action L"InstallPackages" returned 1603
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
```

---

### Post by Kinst on 2008-10-17
The black squares thing is caused by quicktime. It's normal. You have to open quicktime and change the preferences to use safe mode (GDI only) for video. Hope that helps.

---

### Post by YokoZar on 2008-10-18
You need to use iTunes 7, unfortunately.  There's something Apple changed in 8 that Wine isn't compatible with just yet.

---

### Post by TekNullOG on 2008-10-18
thanks guys. I'll give it a try.

Cheers

---

### Post by ouilsen on 2008-11-05
If you are able to compile Wine you can use [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=13739&iTestingId=31143") hack. It actually works. But iTunes still doesn't detect my iPod touch.

---

### Post by ColinZeal on 2008-11-05
Have you guys tried installing TinyXP under VM and trying to connect to a Ipod Touch?

How well would that work?

---

### Post by cogadh on 2008-11-05
Uh, TinyXP is not legal, its a pirated version of Win XP.

---

### Post by ColinZeal on 2008-11-05
Uhh.. Did I violate the license agreement here? Didn´t mean to. I´m just desperate for finding a way to get Ipod Touch to connect to iTunes under Ubuntu. (I do have licensed copies of both 32bit and 64bit of XP Pro so...)

---

### Post by cogadh on 2008-11-05
Discussion of illegal software like TinyXP is not tolerated here. 

Not to mention, if you have legit licenses for XP, why can't you just use one of them to run iTunes? Or use one of them in a VM to run iTunes?

---

### Post by ColinZeal on 2008-11-05
1) Ok, sorry about that. Won´t happen again.
2) I was thinking that full XP would be heavy to run under VM.. or?
3) I´m looking to solve all problems (Football Manager 2009, iTunes, Ipod Touch) in theory before trying out Ubuntu to run beside my current OS. When there seems to be a solution to all those problems, then i´m ready to take the leap over to the other side full time... 
:)

---

### Post by cogadh on 2008-11-05
Normal XP can be run under a VM fine, as long as your system is powerful enough to do it. XP doesn't actually have huge system requirements; 300 MHz processor, 128MB RAM and 2GB (?) disk space minimum, so you can set up the VM running XP as low as that and it will still work. 

Of course, if your system can handle it, it is best to set up the VM with something more than that. On my system which has a 3GHz P4, 2GB of RAM and more disk space than I can use, I set up a VM with XP using 512MB of RAM and 8GB of disk space. It ran perfectly fine, though because I was trying to run 3D games, it didn't work out for me (accelerated graphics don't work in VMs).

---

### Post by huanix on 2008-11-08
I have two things that may help you all out!

First, is a script that will allow iTunes 8.0.1 to run on Ubuntu 8.10. Find that here: [http://www.huanix.com/2008/11/07/itunes-8-running-natively-in-ubuntu-810-with-wine/](http://www.huanix.com/2008/11/07/itunes-8-running-natively-in-ubuntu-810-with-wine/)

I still haven't been able to recognize iPhone/iPod's while running in Wine, so I'm using VirtualBox - here's a script to enable synching with XP running as a VirtualBox virtual machine in Ubuntu 8.10 (it takes a kernel tweak to get usb working): [http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/](http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/)

---

### Post by huanix on 2008-11-13
I can see the iPod now... sort of..

[http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/](http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/)

---

### Post by jessiesnchz on 2008-11-13
so did it work?

---

### Post by huanix on 2008-11-13
I mean.. it did work from the perspective that I can now compile wine and install iTunes 8 to the point that I can see a the pod attached, but i am still a long way from smooth running and syncing an iPhone. I don't expect any more quick breakthroughs, but who knows?

---

