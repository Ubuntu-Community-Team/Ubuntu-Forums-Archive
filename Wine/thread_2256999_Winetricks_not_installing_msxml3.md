---
title: "Winetricks not installing msxml3"
date: 2014-12-16
forum: Wine
---

### Post by mprswk on 2014-12-16
Hi guys!
First of all, sorry if I'm using the wrong forum. Please, tell me where should I go if that's the case.

I've tried to install msxml3 in wine via winetricks. During the first phase winetricks asked me to download the file from Microsoft's website and place it in a specific folder. So far so good. So I re-run the script and I get this message:

```
Executing w_do_call msxml3
Executing load_msxml3
rm: cannot remove ‘/home/peter/.wine/dosdevices/c:/windows/system32/msxml3.dll’: No such file or directory
Using native override for following DLLs: msxml3
Executing winetricks_early_wine regedit C:\windows\Temp\_msxml3\override-dll.reg
Executing wine msiexec /i msxml3.msi
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
fixme:storage:create_storagefile Storage share mode not implemented.
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
err:msidb:get_tablecolumns column 1 out of range
err:msidb:get_tablecolumns column 2 out of range
err:msidb:get_tablecolumns column 3 out of range
------------------------------------------------------
Note: command 'wine msiexec /i msxml3.msi' returned status 79.  Aborting.
```

Ok, I use latest 32-bit wine (14.10) with all updates installed. Is there any manual way to do it? I've seen some tutorials or answers but for me it's esoteric so I would really appreciate any help that you can provide me with. Thanks!

---

### Post by slickymaster on 2014-12-16
*Moved to the ***Wine*** sub-forum*

---

### Post by mprswk on 2014-12-16
I will. Thanks!

---

