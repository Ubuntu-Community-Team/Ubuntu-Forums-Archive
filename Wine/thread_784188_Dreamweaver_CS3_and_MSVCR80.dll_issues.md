---
title: "Dreamweaver CS3 and MSVCR80.dll issues"
date: 2008-05-06
forum: Wine
---

### Post by Jamina1 on 2008-05-06
Trying to run Dreamweaver CS3. I've followed the tutorial to the letter on the wineappDB but I still receive this error:

```
err:process:init_windows_dirs directory L"c:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"c:\\windows\\system32" could not be created, error 3
preloader: Warning: failed to reserve range 00000000-00010000
err:process:init_windows_dirs directory L"c:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"c:\\windows\\system32" could not be created, error 3
err:wineboot:main Cannot set the dir to L"c:\\windows" (2)
preloader: Warning: failed to reserve range 00000000-00010000
err:process:init_windows_dirs directory L"c:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"c:\\windows\\system32" could not be created, error 3
preloader: Warning: failed to reserve range 00000000-00010000
err:process:init_windows_dirs directory L"c:\\windows" could not be created, error 5
err:process:init_windows_dirs directory L"c:\\windows\\system32" could not be created, error 3
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\AdobePSL.dll") not found
err:module:import_dll Library AdobePSL.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Fireworks Library.dll") not found
err:module:import_dll Library Fireworks Library.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\NetIO.dll") not found
err:module:import_dll Library NetIO.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\CoreTypes.dll") not found
err:module:import_dll Library CoreTypes.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\LIBCURL.dll") not found
err:module:import_dll Library LIBCURL.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\ahclient.dll") not found
err:module:import_dll Library ahclient.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\xerces-c_2_6.dll") not found
err:module:import_dll Library xerces-c_2_6.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Workspace.dll") not found
err:module:import_dll Library Workspace.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MFC80U.DLL (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"H:\\.wine\\drive_c\\Program Files\\Adobe\\Adobe Dreamweaver CS3\\Dreamweaver.exe" failed, status c0000135

```

The tutorial didn't mention anything about these DLL's.. What do I do?

---

### Post by crc294 on 2008-12-23
Found the solution: I just deleted the WinSxS from my wine windows folder, and copied it again from my XP installation. Didn't touch anything else, and it started right up. Hope this helps ...

---

### Post by marlboro05 on 2009-01-27
I had the very same problem. 
After deleting the WinSxS folder and copied it again it worked fine!!!!

---

### Post by murphyb on 2009-03-20
That worked great for me.  I was trying to install TomTom Home.  I wonder what it is that is wrong in the SxS directory?  What do the poor folks without an XP installation do?

---

