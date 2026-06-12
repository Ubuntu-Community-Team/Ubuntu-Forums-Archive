---
title: "Dark Ages - Errors in terminal"
date: 2008-04-12
forum: Wine
---

### Post by Spoken on 2008-04-12
So, im trying to play one of my favorite games from the ol days when i used windows.  its called Dark Ages, found at [Http://www.darkages.com]("http://www.darkages.com")

So, i download their client (the .exe file) and add it to the wine applications section in the wine configuration.

i then open terminal and drag the .exe file on my desktop to it.  i move the cursor to the beggining of that line and add wine, so that it looks like this

wine '/home/spoken/Desktop/DarkAges719single.exe' 

then i hit enter, and this pops up in terminal

fixme:spoolsv:serv_main (0 (nil))

then  the installation wizard from windows pops up and installs the game, then when its done installing, i get this error in terminal

fixme:shell:IShellLinkA_fnGetPath (0x142098): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
fixme:shell:IShellLinkA_fnGetPath (0x142098): WIN32_FIND_DATA is not yet filled.
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\thidchk.dll") not found
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\KRU\\Dark Ages\\Launch.dll") not found



WHAT DO I DO NOW???

:confused:

---

