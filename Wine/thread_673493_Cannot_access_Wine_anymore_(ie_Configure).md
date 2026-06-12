---
title: "Cannot access Wine anymore (ie Configure)"
date: 2008-01-20
forum: Wine
---

### Post by Tredici on 2008-01-20
I recently was trying to install Bodog poker through wine and have receieved some problems in the process. I edited some of the library settings in the configurations but after reboot I no longer can access it nor any programs. The message I get at konsol is

err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:DelayLoadFailureHook failed to delay load ole32.dll.CoTaskMemAlloc
wine: Call from 0x7b840f9c to unimplemented function ole32.dll.CoTaskMemAlloc, aborting
wine: Unimplemented function ole32.dll.CoTaskMemAlloc called at address 0x7b840f9c (thread 000b), starting debugger...
Unhandled exception: unimplemented function ole32.dll.CoTaskMemAlloc called in 32-bit code (0x7b841016).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841016 ESP:0034f994 EBP:0034f9f8 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82c411 EBX:7b8ab8a0 ECX:00000000 EDX:0034fa20
 ESI:0034fa20 EDI:7ededd68

...
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135

Anyone know how I can reinstall it clean or fix these errors!? Thanks

Andrew

---

### Post by Black_Heart on 2008-01-20
i was having a similar problem when i tried to install quicktime to run itunes... i got it back up and running by doing a fresh install:

rename the .wine folder something else... like yo.wine or sumthin like that...

 then reinstall wine with *sudo apt-get install wine*

then i updated my opengl drivers for my video card through debian package search

if your video card drivers are up to date, try *wineprefixcreate* in terminal, which rebuilds all of the directories for wine.

if that dont work... look at [http://www.winehq.com](http://www.winehq.com) and try asking some questions in their forums and stuff.

---

