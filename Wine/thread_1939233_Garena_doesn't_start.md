---
title: "Garena doesn't start"
date: 2012-03-11
forum: Wine
---

### Post by Chares on 2012-03-11
```
1@1-A7N8X-E:~$ wine '/home/1/.wine/drive_c/Program Files/Garena Plus/GarenaMessenger.exe'  
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CommonLib.dll") not found 
err:module:import_dll Library CommonLib.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\log4cxx.dll") not found 
err:module:import_dll Library log4cxx.dll (which is needed by L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\DibModule.dll") not found 
err:module:import_dll Library DibModule.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\VersionModule.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CommonLib.dll") not found 
err:module:import_dll Library CommonLib.dll (which is needed by L"C:\\Program Files\\Garena Plus\\VersionModule.dll") not found 
err:module:import_dll Library VersionModule.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\FileLoader.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CommonLib.dll") not found 
err:module:import_dll Library CommonLib.dll (which is needed by L"C:\\Program Files\\Garena Plus\\FileLoader.dll") not found 
err:module:import_dll Library FileLoader.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CxImage.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\DibModule.dll") not found 
err:module:import_dll Library DibModule.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CxImage.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\FileLoader.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CommonLib.dll") not found 
err:module:import_dll Library CommonLib.dll (which is needed by L"C:\\Program Files\\Garena Plus\\FileLoader.dll") not found 
err:module:import_dll Library FileLoader.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CxImage.dll") not found 
err:module:import_dll Library CxImage.dll (which is needed by L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\PluginUpdate.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\CommonLib.dll") not found 
err:module:import_dll Library CommonLib.dll (which is needed by L"C:\\Program Files\\Garena Plus\\PluginUpdate.dll") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\PluginModule.dll") not found 
err:module:import_dll Library PluginModule.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\PluginUpdate.dll") not found 
err:module:import_dll Library PluginUpdate.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Garena Plus\\PluginModule.dll") not found 
err:module:import_dll Library PluginModule.dll (which is needed by  L"C:\\Program Files\\Garena Plus\\GarenaMessenger.exe") not found 
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program  Files\\Garena Plus\\GarenaMessenger.exe" failed, status c0000135
```

---

### Post by lite1979 on 2012-03-12
I simply googled "dll's needed for garena" and [this winehq thread]("http://forum.winehq.org/viewtopic.php?t=14041&view=next&sid=da57625e4184f0d74bf196436b863e65") was the first result. Cheers.

> ```
winetricks vcrun2008
```

---

