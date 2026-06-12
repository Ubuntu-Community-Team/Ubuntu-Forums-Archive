---
title: "Winsock errors??"
date: 2008-01-03
forum: Wine
---

### Post by FishEyes on 2008-01-03
Cheers - 

I am looking for some thoughts from anyone out there on a problem I am having with an application Trend InVue.  Invue is a telnet application that has been tweaked for cosmetic purposes for an ERP system.
It is an older application originally designed in the 3.1 - 98 era.  The application seems to install fine, and opens initially but it is when I try and establish a telnet session from it, that it fails and I get an error message:

Program Fault
        
        Program Fault: Access Violation
        
        Stack Trace
           0x7D35FD41
        
        Registers
           EAX= 0034FA10    EBX= 7D3696C8
           ECX= 0034FA48    EDX= 00027D6E
           ESI= 00027D6D    EDI= 00027D6D
           ESP= 0034F988    EBP= 0034FA20    SS = 007B
           DS = 007B    ES = 007B    FS = 0033    GS = 003B
           CS = 0073    EIP= 7D35FD41

I know this is a windows specific application error.

I have done some reading on the site as well as dropped a few Googles here and there but I am still stumped.:confused:
I have tried other OS versions to run it from and it still fails.
I am using Wine 0.9.51 on Gusty Gibbon.
There is a feeling that this is a Winsock error and am hoping that it is something obvious I am overlooking.

Here is a DLL debug log.
```
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\Invue40.exe" at 0x400000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msvcrt.dll" at 0x7ee30000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ed50000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7eda0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ec20000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\MFC42.DLL" at 0x5f400000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7XAXE.dll" at 0x10000000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\lz32.dll" at 0x7ebe0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\version.dll" at 0x7ebf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winmm.dll" at 0x7eb50000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shlwapi.dll" at 0x7e950000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comctl32.dll" at 0x7e890000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\shell32.dll" at 0x7e9b0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winspool.drv" at 0x7e860000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\comdlg32.dll" at 0x7eab0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7e740000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7e760000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ole32.dll" at 0x7e7c0000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7EEDF.dll" at 0x350000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7CIMG.dll" at 0x6a0000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7e700000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7e530000: builtin
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\explorer.exe" at 0x7ee60000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\advapi32.dll" at 0x7ed90000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\iphlpapi.dll" at 0x7edf0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\rpcrt4.dll" at 0x7ee10000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\gdi32.dll" at 0x7ebc0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\user32.dll" at 0x7ec60000: builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winex11.drv" at 0x7e9e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\imm32.dll" at 0x7dcb0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winealsa.drv" at 0x7d7b0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\wineoss.drv" at 0x7d6b0000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\winecoreaudio.drv" at 0x7d690000: builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\winecoreaudio.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "mmsystem.dll" : builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msacm32.dll" at 0x7d670000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\msacm32.drv" at 0x7d690000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\midimap.dll" at 0x7d650000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\uxtheme.dll" at 0x7d620000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ctl3d32.dll" at 0x7d3c0000: builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\ctl3d32.dll" : builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7reng.dll" at 0xe60000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7seng.dll" at 0x680000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7cchk.DLL" at 0xee0000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7nsoc.DLL" at 0x1180000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7cpit.DLL" at 0xe20000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7CCFG.DLL" at 0x10f0000: native
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\tapi32.dll" at 0x7d390000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7nmdm.DLL" at 0x1150000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7nrtr.DLL" at 0xef0000: native
trace:loaddll:load_native_dll Loaded L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7npic.DLL" at 0xf20000: native
fixme:imm:ImmGetDefaultIMEWnd (0x30028 - (nil) 0x13bb68 ): semi-stub
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\ws2_32.dll" at 0x7d350000: builtin
trace:loaddll:load_builtin_dll Loaded L"c:\\windows\\system32\\wsock32.dll" at 0x7d380000: builtin
fixme:winsock:NtStatusToWSAError Status code c0000022 converted to DOS error code 5
fixme:winsock:NtStatusToWSAError Status code c0000022 converted to DOS error code 5
fixme:winsock:NtStatusToWSAError Status code c0000022 converted to DOS error code 5
**********
This error repeats over and over until the program seems to crash about 2200 times.
**********
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7cchk.DLL" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7reng.dll" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7seng.dll" : native
fixme:font:WineEngRemoveFontResourceEx :stub
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\wsock32.dll" : builtin
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\ws2_32.dll" : builtin
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7npic.DLL" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7nrtr.DLL" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7nmdm.DLL" : native
trace:loaddll:free_modref Unloaded module L"c:\\windows\\system32\\tapi32.dll" : builtin
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7CCFG.DLL" : native
trace:loaddll:free_modref Unloaded module L"C:\\Program Files\\NxTrend\\InVue 4\\Trend\\HA7cpit.DLL" : native
```


If anyone has any ideas or input it would be greatly appreciated.
Thanks,
Sean

---

### Post by T3kn0m0nk3Y on 2009-10-28
Bump.

I have the exact same issue. Can someone offer any form of advice?

I noticed that invue program does not seem to be able to load the default.ses file that has the connection options and tries to recreate a new one each time.

Also, it errors out when "attempting to connect to host..." which tells me it's probably not writing the settings it does generate to anywhere it can access them due to wine permissions.

---

### Post by T3kn0m0nk3Y on 2009-10-28
I just realized that my errors were'nt quite exact.  I also solved the non loading Default.ses issue by taking a configured Default.ses from a windows system and dropping it in to the virtual c:\Program Files\NxTrend\SHIMS\ folder. It now loads those options by default:

error:

Program Fault
        
        Program Fault: Access Violation
        
        Stack Trace
           0x7DDC2F67
        
        Registers
           EAX= FFFFFFFF    EBX= 7DDCA114
           ECX= 00027E6F    EDX= 0032F640
           ESI= 00002719    EDI= 0133A398
           ESP= 0032F580    EBP= 0032F618    SS = 007B
           DS = 007B    ES = 007B    FS = 0033    GS = 003B
           CS = 0073    EIP= 7DDC2F67


hopefully someone can shed light.

---

### Post by T3kn0m0nk3Y on 2009-10-28
Hmm, more developments. I made sure that all the permissions on the icon launcher were set to both read AND write, and ran it from the command line so I could get some output, and it just repeated the following error about 30 times:

fixme:winsock:NtStatusToWSAError Status code c0000022 converted to DOS error code 5

This same error was in the logs posted above. Odd that it kept spitting it out so many times.

---

### Post by hockman5 on 2010-12-14
Well I have had the same problems in the past. The problem with this program is that is is written for windows and its network protocol uses WinSock, which you will not find to work on Ubuntu , or linux period. I use Invue on a regular basis on a windows machine, and this is one of the programs that has forced me to keep windows, since all other telnet terminal programs do not work to my liking as does InVue.
   I have been able to get InVue to work when running a Virtual Box in Ubuntu, but that is alot of work just to get one telnet program to run.

---

