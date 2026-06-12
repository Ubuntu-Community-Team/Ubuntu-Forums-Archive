---
title: "This Wine program wotn open! Net framework needed?"
date: 2012-12-25
forum: Wine
---

### Post by ironcomics on 2012-12-25
im making a game using windows programs (Rpg maker xp, Blizz abs) Blizz abs wont open because apparently i need net framework 2.0 or 
above. Im using wine 1.4 and ubuntu 12.04 lts

Heres is the blizz abs program, Can you ttell me if it works
or if it closes straight away :(
  [http://downloads.chaos-project.com/scripts/Blizz-ABS%202.84.zip](http://downloads.chaos-project.com/scripts/Blizz-ABS%202.84.zip)  
If you got net framework and wine installed can u test it?

I got it from this site:
  [http://forum.chaos-project.com/index.php?topic=106.0](http://forum.chaos-project.com/index.php?topic=106.0)

And i also trying to install netframework 4.0 but this is my terminal log:
```
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 2b on event 0        
fixme:console:CONSOLE_DefaultHandler Terminating process 33 on event 0
Using native override for following DLLs: mscoree
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet40\override-dll.reg
ADD - HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full Install 0 REG_DWORD 0001 1
The operation completed successfully
ADD - HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full Version 0 REG_SZ 4.0.30319 1
The operation completed successfully
------------------------------------------------------
Working around wine bug 30707 -- Manually registering assemblies
------------------------------------------------------
gacutil.exe
gacutil.exe.config
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\temp\\_dotnet40\\gacutil.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\_dotnet40\\gacutil.exe" failed, status c0000135
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\temp\\_dotnet40\\gacutil.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\_dotnet40\\gacutil.exe" failed, status c0000135
cp: cannot stat `/home/moe/.wine/dosdevices/c:/windows/Microsoft.NET/Framework/v4.0.30319/System.EnterpriseServices.dll': No such file or directory
------------------------------------------------------
Note: command 'load_dotnet40' returned status 1.  Aborting.
------------------------------------------------------
moe@eM250:~$ bash winetricks dotnet40
Executing w_do_call dotnet40
Executing load_dotnet40
------------------------------------------------------
dotnet40 does not yet fully work or install on wine.  Caveat emptor.
------------------------------------------------------
Executing mkdir -p /home/moe/.cache/winetricks/dotnet40
------------------------------------------------------
Working around wine bug 30707 -- Need to get gacutil.exe
------------------------------------------------------
Executing w_do_call remove_mono
Executing load_remove_mono
------------------------------------------------------
Mono does not appear to be installed.
------------------------------------------------------
DELETE - HKLM\Software\Microsoft\NET Framework Setup\NDP\v4 (null) 0 0 1
The operation completed successfully
Executing rm -f /home/moe/.wine/dosdevices/c:/windows/system32/mscoree.dll
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:clusapi:OpenCluster ((null)) stub!
fixme:clusapi:ClusterOpenEnum (0xdeadbeef, 4) stub!
fixme:clusapi:ClusterEnum (0xdeadbeef, 0, 0x32f860, 0x138c60, 261) stub!
fixme:clusapi:ClusterCloseEnum (0xdeadbeef) stub!
fixme:clusapi:CloseCluster (0xdeadbeef) stub!
fixme:advapi:DecryptFileW L"C:\\4d0fd97310bbb64f9b02731939cd\\" 00000000
fixme:advapi:RegisterTraceGuidsW (0x6cd15f38, 0x6cd20180, {e2821408-c59d-418f-ad3f-aa4e792aeb79}, 1, 0x33fca0, (null), (null), 0x6cd20188,): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ver:RtlGetProductInfo (6,1,1,0,0x33fa08): stub
fixme:advapi:LsaOpenPolicy ((null),0x33f474,0x00000001,0x33f49c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:msxml:domdoc_putref_schemas (0x17ef68)->({VT_DISPATCH: 0x74c160}): semi-stub
fixme:msxml:domdoc_get_readyState stub! (0x17ef68)->(0x33f3a0)
fixme:propsheet:PROPSHEET_SetHeaderTitleW (0x1006a, 0, L".NET Framework 4 Setup"): stub
fixme:propsheet:PROPSHEET_SetHeaderSubTitleW (0x1006a, 0, L"Please accept the license terms to continue."): stub
fixme:propsheet:PROPSHEET_SetHeaderTitleW (0x1006a, 2, L"Installation Progress"): stub
fixme:propsheet:PROPSHEET_SetHeaderSubTitleW (0x1006a, 2, L"Please wait while the .NET Framework is being installed."): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:wuapi:automatic_updates_Pause 
wine: cannot find L"C:\\windows\\system32\\wusa.exe"
fixme:wer:WerReportCreate build report information from scratch for 0x146e48
fixme:wer:WerReportSetParameter (0x146e48, 0, (null), L"Microsoft .NET Framework 4 Setup") :stub
fixme:advapi:LsaOpenPolicy ((null),0x33f2c0,0x00000001,0x33f2e8) stub
fixme:advapi:LsaClose (0xcafe) stub
Using native override for following DLLs: mscoree
Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet40\override-dll.reg
ADD - HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full Install 0 REG_DWORD 0001 1
The operation completed successfully
ADD - HKLM\Software\Microsoft\NET Framework Setup\NDP\v4\Full Version 0 REG_SZ 4.0.30319 1
The operation completed successfully
------------------------------------------------------
Working around wine bug 30707 -- Manually registering assemblies
------------------------------------------------------
gacutil.exe
gacutil.exe.config
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\temp\\_dotnet40\\gacutil.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\_dotnet40\\gacutil.exe" failed, status c0000135
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\temp\\_dotnet40\\gacutil.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\_dotnet40\\gacutil.exe" failed, status c0000135
cp: cannot stat `/home/moe/.wine/dosdevices/c:/windows/Microsoft.NET/Framework/v4.0.30319/System.EnterpriseServices.dll': No such file or directory
------------------------------------------------------
Note: command 'load_dotnet40' returned status 1.  Aborting.
------------------------------------------------------

```
and also on the net framework programm it says file not found wusa.exe 

I really wanna get blizz abs so i can finish my game please help thanks.
Oh and this is my first post i bet its in the wrong category and mistakes and stuff :(

---

