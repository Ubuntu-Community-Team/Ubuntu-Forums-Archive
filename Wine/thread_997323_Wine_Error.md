---
title: "Wine Error"
date: 2008-11-29
forum: Wine
---

### Post by Saytr on 2008-11-29
Help! Wine is going out weird to me. First I couldn't play any games or run programs because of the programs not recognizing the video output. And I thought the solution of that was to install Direct X 9 into Wine. I installed DX 9 into Wine and now I cannot run any Windows Programs (Basiclly it opens and then it closes down). Then to fix that i tried to open winecfg and then this happened...

```
ilkan@ilkan-desktop:~$ winecfg
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

```

What can I do to fix this error to run winecfg and my programs again ?? Thanks if you reply...

Ilkan

---

### Post by cogadh on 2008-11-29
Installing DX is probably what did it. From the Wine FAQ:
> **8.1. Does Wine support DirectX? Can I install Microsoft's DirectX under Wine?**

Wine itself provides a DirectX implementation that, although it has a few bugs left, should run fine. Wine supports DirectX 9.0c at this time. Plans for DirectX 10 are underway.

**/!\ If you attempt to install Microsoft's DirectX, you will run into problems.** It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)
Unfortunately, the only way to fix it is to delete your .wine directory and start all over again with re-installing everything you already had running in Wine.

---

