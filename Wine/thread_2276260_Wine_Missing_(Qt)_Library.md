---
title: "Wine Missing (Qt) Library"
date: 2015-05-01
forum: Wine
---

### Post by tuathan on 2015-05-01
I am trying to use wine in Ubuntu 12.04 to open a Windows (XP) executable but get the following error. Anyone know how to fix this? Thanks!

$ wine "program.exe"

[B]err:module:import_dll Library qt-mt338_vc80.dll (which is needed by L"Z:\\home\\tuathan\\Desktop\\program.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\tuathan\\Desktop\\program.exe" failed, status c0000135[/B]





3.2.0-77-generic #114-Ubuntu SMP Tue Mar 10 17:26:03 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by tuathan on 2015-05-01
Solved: I located the Qt library file "qt-mt338_vc80.dll" and placed it in the same directory as the .exe which now runs fine.

---

