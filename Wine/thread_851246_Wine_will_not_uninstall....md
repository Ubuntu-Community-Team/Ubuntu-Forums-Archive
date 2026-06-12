---
title: "Wine will not uninstall..."
date: 2008-07-06
forum: Wine
---

### Post by ludatha on 2008-07-06
Hi, I was trying to install Photoshop CS2, but I could not activate it, apparently the fix was to remove CS2 and Wine then install everything again.

So I did this:
```
sudo apt-get remove --purge wine
```

But wine still exists, and I cannot get rid of it...
It is in the applications menu, without an icon, it will not run anything...

Any ideas?

---

### Post by RequinB4 on 2008-07-06
quick google gave me this -- i'm not sure if this is just pre-dating apt-get purge

[http://ubuntuforums.org/showthread.php?t=207202](http://ubuntuforums.org/showthread.php?t=207202)

Though what you are experiencing is normal, i can tell you that

---

### Post by ludatha on 2008-07-06
I tried that, I get this is the terminal:
> adam@adam-desktop:~$ uninstaller
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\adam\\Local Settings\\Temporary Internet Files".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 0
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\adam\\Local Settings\\History".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 1
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\adam\\Cookies".
err:wininet:URLCacheContainers_CreateDefaults Couldn't get path for default container 2
err:msi:copy_package_to_temp failed to copy package L"c:\\windows\\Installer\\d4c9.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030003 for L"c:\\windows\\Installer\\d4c9.msi"


I need to uninstall wine altogether, because I deleted the .wine/drive_c directory

I still have drive_c in my wastebasket, so where shall I put it?

---

### Post by werries on 2008-07-06
put it back in /home/YOURUSRNAME/.wine

---

### Post by SBFC on 2008-07-06
You could also just run winecfg and it'll recreate your .wine directory.

---

### Post by cogadh on 2008-07-07
When you uninstall Wine, the menu entries are still left behind, but do not actually do anything, since Wine is actually uninstalled.  The same thing happens when you just uninstall an application from Wine, but not Wine itself. Also, uninstalling Wine does not remove the hidden .wine directory from your home directory. If you need to get rid of the menu shortcuts and the .wine directory, you just need to manually delete them. However, to fix your issues, you should only need to delete and re-create the .wine directory, not the menu shortcuts or uninstall Wine itself.

---

