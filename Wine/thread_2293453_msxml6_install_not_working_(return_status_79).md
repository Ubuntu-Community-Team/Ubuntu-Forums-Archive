---
title: "msxml6 install not working (return status 79)"
date: 2015-09-05
forum: Wine
---

### Post by hne_ubu on 2015-09-05
EDIT:
I uninstalled wine and installed playonlinux. As I wanted to install Office 2010 I used playonlinux and it worked fine. :D


Hello!

I'm using Ubuntu 15.04 on a 64-bit system. My wine version is 1.6.2. I want to install msxml6 package via winetricks.
"
So I created a fresh wineprefix with win32 architecture ("WINEARCH=win32 WINEPREFIX=~/.wine winecfg").
However when I try to install msxml6 ("winetricks msxml6") it says:

> Executing w_do_call msxml6Executing load_msxml6
Using native,builtin override for following DLLs: msxml6
Executing winetricks_early_wine regedit C:\windows\Temp\_msxml6\override-dll.reg
Executing wine msiexec /i /home/hne/.cache/winetricks/msxml6/msxml6_x86.msi
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
Note: command 'wine msiexec /i /home/hne/.cache/winetricks/msxml6/msxml6_x86.msi' returned status 79.  Aborting.

I could not find anything on status 79. Please help, any help is appreciated. Thanks!

---

