---
title: "How Do I Play GD Through Wine?"
date: 2017-04-10
forum: Wine
---

### Post by refusiongaming on 2017-04-10
Hey Everyone, and basically trying to run geometry dash 2.1 on wine, with no success it always comes up with this error message

```
err:module:import_dll Library MSVCP120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libcocos2d.dll") not found
err:module:import_dll Library MSVCR120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libcocos2d.dll") not found
err:module:import_dll Library libcocos2d.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libExtensions.dll") not found
err:module:import_dll Library MSVCP120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libExtensions.dll") not found
err:module:import_dll Library MSVCR120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libExtensions.dll") not found
err:module:import_dll Library libExtensions.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\GeometryDash.exe") not found
err:module:import_dll Library MSVCP120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libcocos2d.dll") not found
err:module:import_dll Library MSVCR120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\libcocos2d.dll") not found
err:module:import_dll Library libcocos2d.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\GeometryDash.exe") not found
err:module:import_dll Library MSVCP120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\GeometryDash.exe") not found
err:module:import_dll Library MSVCR120.dll (which is needed by L"H:\\Desktop\\Geometry Dash\\GeometryDash.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\Desktop\\Geometry Dash\\GeometryDash.exe" failed, status c0000135
```

Then i checked those files and only MSVCR120.dll wasn't in there, then i searched my mac, and again it wasn't in there.
I tried to install Visual C++ 2013 32 bit, but it always errors:

```
fixme:heap:HeapSetInformation 0x0 1 0x0 0
fixme:heap:HeapSetInformation 0x0 1 0x0 0
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:heap:HeapSetInformation 0x0 1 0x0 0
fixme:heap:HeapSetInformation 0x0 1 0x0 0
fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:advapi:DecryptFileW (L"C:\\users\\ethanwoods\\Temp\\{f65db027-aff3-4070-886a-0d87064aabb1}\\", 00000000): stub
```
 
Im not sure how to fix this problem. Any ideas?

PS: I already tried to add vrun2013 from winetricks, still failed.:confused:

---

### Post by howefield on 2017-04-10
Thread moved to the *"Wine"* forum and code tags added to prevent parsing emoticons.

---

### Post by deadflowr on 2017-04-10
Look over the comments here:
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=32376]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32376")

---

