---
title: "I am getting dll errors where do I get and put them all?"
date: 2008-02-25
forum: Wine
---

### Post by Shadowmeph on 2008-02-25
these are the errors it is all foreign to me 
> fixme:ntoskrnl:KeInitializeTimerEx 0x110ad8 0
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\CommonLibs.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\CommonLibs.dll") not found
err:module:import_dll Library CommonLibs.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
err:module:import_dll Library d3dx9_35.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\The Witcher\\System\\witcher.exe" failed, status c0000135
[email]dallas@Shane:~/.wine[/email]/drive_c/Program Files/The Witcher/System$ wine witcher.exe
fixme:ntoskrnl:KeInitializeTimerEx 0x110ad8 0
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\CommonLibs.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\CommonLibs.dll") not found
err:module:import_dll Library CommonLibs.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
err:module:import_dll Library d3dx9_35.dll (which is needed by L"C:\\Program Files\\The Witcher\\System\\witcher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\The Witcher\\System\\witcher.exe" failed, status c0000135
[email]dallas@Shane:~/.wine[/email]/drive_c/Program Files/The Witcher/System$ 


---

### Post by Bruce M. on 2008-02-25
> **Shadowmeph said:**
> these are the errors it is all foreign to me

Dis you check the [WineHQ App List]("http://appdb.winehq.org/") to see if your program runs with wine?

---

