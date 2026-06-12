---
title: "dotnet20 and Winetricks"
date: 2008-05-23
forum: Wine
---

### Post by Swalchy on 2008-05-23
I seem to having the most awful problem trying to install dotnet20 using winetricks on Ubuntu 7.10 and Wine 0.9.59. This is what I always keep getting:

```
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:DelayLoadFailureHook failed to delay load ole32.dll.CoTaskMemAlloc
wine: Call from 0x7b840fc8 to unimplemented function ole32.dll.CoTaskMemAlloc, aborting
err:module:attach_process_dlls "shell32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\cmd.exe" failed, status 80000100
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
Setting Windows version to win2k
Executing wine regedit /home/<username>/.wine/drive_c/winetrickstmp/set-winver.reg
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
Executing cp -f /home/<username>/.winetrickscache/dotnet20/l_intl.nls /home/<username>/.wine/drive_c/windows/system32/
Executing wine /home/<username>/.winetrickscache/dotnet20/dotnetfx.exe
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\explorer.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\explorer.exe" failed, status c0000135
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\advpack.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\setupapi.dll") not found
err:module:import_dll Library setupapi.dll (which is needed by L"c:\\windows\\system32\\advpack.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\temp\\IXP001.TMP\\install.exe") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\oleaut32.dll") not found
err:module:import_dll Library OLEAUT32.dll (which is needed by L"C:\\windows\\temp\\IXP001.TMP\\install.exe") not found
err:module:import_dll Library rpcrt4.dll (which is needed by L"c:\\windows\\system32\\setupapi.dll") not found
err:module:import_dll Library SETUPAPI.dll (which is needed by L"C:\\windows\\temp\\IXP001.TMP\\install.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\temp\\IXP001.TMP\\install.exe" failed, status c0000135
Note: command 'wine /home/<username>/.winetrickscache/dotnet20/dotnetfx.exe' returned status 53.  Aborting.
```

Any suggestions?

edit: Managed to sort that out. But now, when the dotnet20 installer tries to install, I keep getting a message about "setup has detected that the following prerequisite programs are not installed: Microsoft Internet Explorer 5.01. YOu must first install these programs before Microsoft .NET Framework 2.0 can be installed"

The text given out by the console is the following:

```
fixme:spoolsv:serv_main (0 (nil))
Setting Windows version to win2k
Executing wine regedit /home/<username>/.wine/drive_c/winetrickstmp/set-winver.reg
Executing cp -f /home/<username>/.winetrickscache/dotnet20/l_intl.nls /home/stephen/.wine/drive_c/windows/system32/
Executing wine /home/<username>/.winetrickscache/dotnet20/dotnetfx.exe
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:advapi:LsaOpenPolicy ((null),0x33f3c0,0x00000001,0x33f39c) stub
fixme:advapi:LsaClose (0xcafe) stub
Note: command 'wine /home/<username>/.winetrickscache/dotnet20/dotnetfx.exe' returned status 25.  Aborting.
```

---

### Post by Swalchy on 2008-05-25
Nevermind - I should've learned about Gecko before attempting this :)

---

### Post by dingfelder on 2008-06-16
can you post what you did to solve this?

It doesn't help other users to say you sorted it out but not list how :P

---

### Post by sdowney717 on 2008-07-16
Here's how to get a simple .net application running (see bug 10467) using wine-0.9.59 and winetricks-20080402:

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts dotnet20 

About one in five tries, this will hang with " err:seh:setup_exception_record nested exception on signal stack". If this happens, press ^C and try again.

Now pray, and start your app ;) 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

works for me to install net framework Hardy with wine 1.1

---

### Post by Breanainn on 2009-12-05
Excellent, this worked for me with wine 1.1 and koala, cheers

---

### Post by mrmcgibby on 2010-11-12
For me, this was the solution:

I figured out how to solve it. Not sure what's going on though. I was trying debug some install instructions so I kept running rm -rf .wine/*, which kept around .update-timestamp . When I just rm -rf .wine, it works fine.

---

### Post by doctorzeus on 2010-11-12
If all else fails you could try deleting the /home/(user)/.cache/winetricks/ folder...


Doctorzeus

---

### Post by embain14 on 2010-12-26
> **sdowney717 said:**
> Here's how to get a simple .net application running (see bug 10467) using wine-0.9.59 and winetricks-20080402:

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts dotnet20 

About one in five tries, this will hang with " err:seh:setup_exception_record nested exception on signal stack". If this happens, press ^C and try again.

Now pray, and start your app ;) 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

works for me to install net framework Hardy with wine 1.1

Thank you so much this worked perfect for me!!!

---

