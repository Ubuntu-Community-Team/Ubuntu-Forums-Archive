---
title: "Irfanview in Wine"
date: 2013-09-07
forum: Wine
---

### Post by Mdh3MHY on 2013-09-07
Hi all,

I am having some trouble trying to install Irfanview into wine. I've only just started using ubuntu 12.04, having installed it on my laptop earlier this week (as a dual-boot set-up alongside my existing Windows 7 installation). I have followed instructions online: installed wine; downloaded the Irfanview installer (iview430_setup.exe) and copied the mfc42.dll from the System32 folder to the wine equivalent folder. Then I followed the instructions to launch the installation from terminal but it came up with these errors - suggesting to me that mfc42.dll isn't there but it is:

```

:~$ cd /home/[user]/Downloads
:~/Downloads$ wine iview430_setup.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:module:import_dll Library KERNELBASE.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Debug-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ErrorHandling-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-File-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Handle-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Interlocked-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-LibraryLoader-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Localization-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-LocalRegistry-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Memory-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Misc-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ProcessEnvironment-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-ProcessThreads-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Profile-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-String-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-Synch-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library API-MS-Win-Core-SysInfo-L1-1-0.dll (which is needed by L"C:\\windows\\system32\\MFC42.DLL") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\[user]\\Downloads\\iview430_setup.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\[user]\\Downloads\\iview430_setup.exe" failed, status c0000135

```

Apologies if I have missed anything obvious - I'm still getting to grips with the new setup. ;)

Any help will be greatly appreciated. 
[I]
If anyone else is wondering I have no idea why I have such a random username, I logged in using my cloud account and I wasn't given the option to choose otherwise... [/I]:-s

---

### Post by GwL3eNC on 2013-09-07
Hi,

i has had a look at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834).
They call 

winetricks mfc42

to install the dll. Have you tried that? Open a terminal window and go 
to the place where the mfc24 is stored (cd command) and try the winetricks
commmand.

---

### Post by ajgreeny on 2013-09-07
Yes, when I tried to install irfanview in my Ubuntu 10.06 a couple of years ago I had exactly that same problem and had to solve it with wine-tricks.  Copying the mfc42 file directly from the winXP did not work as I recall, though it was a long time ago.

Instead of irfanview under wine have a good look at gthumb, which I find is the nearest dedicated linux application, and the nearest thing I have found to irfanview, which I now don't miss at all.

---

### Post by Mdh3MHY on 2013-09-08
> **GwL3eNC said:**
> Hi,

i has had a look at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7834).
They call 

winetricks mfc42

to install the dll. Have you tried that? Open a terminal window and go 
to the place where the mfc24 is stored (cd command) and try the winetricks
commmand.
I've just tried out that command and it doesn't seem to have worked - I get this:
```
:~$ cd /home/[user]/.wine/drive_c/windows/system32:~/.wine/drive_c/windows/system32$ winetricks mfc42
Executing w_do_call mfc42
Executing load_mfc42
Executing mkdir -p /home/[user]/.cache/winetricks/vcrun6
Downloading http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe to /home/[user]/.cache/winetricks/vcrun6
--2013-09-08 09:32:28--  http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe
Resolving download.microsoft.com (download.microsoft.com)... 213.120.161.243, 217.32.26.16
Connecting to download.microsoft.com (download.microsoft.com)|213.120.161.243|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-09-08 09:32:29 ERROR 404: Not Found.


------------------------------------------------------
Downloading http://download.microsoft.com/download/vc60pro/update/1/w9xnt4/en-us/vc6redistsetup_enu.exe failed
------------------------------------------------------
:~/.wine/drive_c/windows/system32$ 
```

[QUOTE=ajgreeny][COLOR=#000000]Instead of irfanview under wine have a good look at gthumb, which I find is the nearest dedicated linux application, and the nearest thing I have found to irfanview, which I now don't miss at all.[/COLOR][/QUOTE]
I'll have a look at that.

---

### Post by carl4926 on 2013-09-08
If you have that version of crossover they gave away not long ago, you could use that
In the Community Supported list it lists Irfranview 4.33
I have used it, it does work.
But I prefer native apps

---

### Post by Mdh3MHY on 2013-09-08
I had not heard of Crossover before, but I looked on the software centre and it appeared to be free so I downloaded it - I followed the instructions on there and although it wanted me to register the edition the Irfanview installer started and I now have it working. I think the factor that allowed it to work was that Crossover downloaded and installed Microsoft Visual C++ 6.0 (so I presume mfc42.dll was then recognised: now just to sort out the shortcut to the program.

---

### Post by howefield on 2013-09-08
> **Mdh3MHY said:**
> I had not heard of Crossover before, but I looked on the software centre and it appeared to be free.

Most likely free for 14 days, then you would need to purchase.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

---

### Post by GwL3eNC on 2013-09-08
Hello,

why dont you try downloading 

vc6redistsetup_enu.exe 

manualy and install it before you do the winetricks command.

---

### Post by Mdh3MHY on 2013-09-08
> **howefield said:**
> Most likely free for 14 days, then you would need to purchase.

[http://www.codeweavers.com/](http://www.codeweavers.com/)
Ah yes, I had a message pop up asking to register and that this edition would terminate after a fortnight.

---

### Post by Mdh3MHY on 2013-09-08
I currently need to delete a folder in [COLOR=#000000]/usr/share/doc[/COLOR] so that I can reinstall an app - the options to delete or cut it are greyed out so how can I delete it successfully (is there a terminal command that can be used)?

EDIT: Managed to do it with "[COLOR=#000000]sudo nautilus"[/COLOR]

---

### Post by rai_shu2 on 2013-09-08
Probably would help to have the latest [winetricks]("http://winetricks.org/winetricks"), you know. That vcrun6 helper is an older version.

---

### Post by Mdh3MHY on 2013-09-09
I've managed to get it working now - thanks guys for all the help; I really appreciate it.

---

### Post by carl4926 on 2013-09-09
> **Mdh3MHY said:**
> I've managed to get it working now - thanks guys for all the help; I really appreciate it.
Well done

---

