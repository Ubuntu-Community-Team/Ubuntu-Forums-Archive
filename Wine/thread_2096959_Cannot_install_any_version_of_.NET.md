---
title: "Cannot install any version of .NET"
date: 2012-12-21
forum: Wine
---

### Post by szczurcio on 2012-12-21
Hi, 
I need .NET 4.0 for a game launcher. I've installed it just after I installed Wine, but, it doesn't exactly seem to work, because when I type winecfg, i does start, but I get this in the terminal:

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme: process:SetProcessDEPPolicy (1): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:module:import_dll Library MSVCR100_CLR0400.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscorsvw.exe") not found
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscorsvw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscorsvw.exe" failed, status c0000135
err:service:service_send_start_message service L"clr_optimization_v4.0.30319_64" failed to start
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_64" failed to start: 1053
fixme:service:scmdatabase_autostart_services Auto-start service L"dxregsvc" failed to start: 2
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory


Also, no other version of .NET will install (an unnamed error occurs during the installation). I'm using a 64bit Ubuntu 12.10. Any help would be greatly appreciated.

Thanks in advance.

---

