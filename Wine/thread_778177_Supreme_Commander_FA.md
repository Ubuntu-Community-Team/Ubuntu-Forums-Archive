---
title: "Supreme Commander: FA"
date: 2008-05-01
forum: Wine
---

### Post by Harkainos on 2008-05-01
Fortunately I was able to move an up to date System32 folder into the virtual one WinE provides.

I also moves the scfa folder into linux and have all the registry setup. I do run into a problem starting scfa: here is what terminal provides----


[COLOR="RoyalBlue"]nick@Compy386:/hive/games/scfa/bin$ wine ForgedAlliance.exe
preloader: Warning: failed to reserve range 00000000-00010000
err:module:import_dll Library WINSTA.dll (which is needed by L"C:\\windows\\system32\\faultrep.DLL") not found
err:module:import_dll Library faultrep.DLL (which is needed by L"E:\\scfa\\bin\\ForgedAlliance.exe") not found
err:module:import_dll Library X3DAudio1_2.dll (which is needed by L"E:\\scfa\\bin\\ForgedAlliance.exe") not found
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'd3dx9_36.D3DXGetImageInfoFromFileInMemory' used by L"C:\\windows\\system32\\d3dx9_35.dll". If you are using builtin L"d3dx9_35.dll", try using the native one instead.
err:module:LdrInitializeThunk Main exe initialization for L"E:\\scfa\\bin\\ForgedAlliance.exe" failed, status c0000135
nick@Compy386:/hive/games/scfa/bin$ [/COLOR]


I am not finding these particular dll's in the system32 folder, so the next outstanding question would be ---- where would they be located? Any help would be appreciated. As windows is now more borken and i will NEED to run these here - to avoid reinstall of a borken system.

---

### Post by Harkainos on 2008-05-02
bump :)

---

### Post by JoshuaRL on 2008-05-18
Search for the exact DLL name on google and it should find them for you.  Then just download and copy into the system32 folder.

---

