---
title: "Bioshock in wine"
date: 2008-07-22
forum: Wine
---

### Post by 2LSS on 2008-07-22
Hi I'm trying to run the Bioshock demo in wine (wine-1.1.1) but I keep getting this Microsoft Visual C++ Runtime Library error. 

[IMG]http://i300.photobucket.com/albums/nn34/2lss/Screenshot.png[/IMG]

```
frank@frank-laptop:~$ wine "/home/frank/.wine/drive_c/Program Files/2K Games/BioShock_Demo/Builds/Release/Bioshock.exe" 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\2K Games\\BioShock_Demo\\Builds\\Release\\Bioshock.exe" failed, status c0000142
```

I have used winetricks to install vcrun2005, vcrun2005sp1, and vcrun2008 packages but with no success.
After hours of searching I'm stumped, any help would be appreciated. :confused:

---

### Post by kdorf on 2008-07-22
You should've spent 30 seconds searching the Wine AppDB instead.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8962](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8962)

---

