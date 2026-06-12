---
title: "Photoshop CS2 Stuck"
date: 2008-03-18
forum: Wine
---

### Post by LavaWarrior on 2008-03-18
I am trying to install photoshop cs2 with wine, i installed it correctly once, but i couldn't activate over phone, so i read posts on this forum saying reinstall wine, and delete photoshop and retry. So i did, but now i am having trouble reinstalling photoshop cs2.

I type wine '/home/james/Desktop/Adobe(R) Photoshop(R) CS2/setup.exe' in terminal to run it, cause i've tried the setup.exe which didn't work. And this is what i get(posted the whole termial log)

```
james@james-desktop:~$ wine '/home/james/Desktop/Adobe(R) Photoshop(R) CS2/setup.exe' 
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:msi:copy_package_to_temp failed to copy package L"Z:\\home\\james\\Desktop\\Adobe(R) Photoshop(R) CS2\\Adobe Photoshop CS2.msi"
fixme:advapi:LookupAccountNameW (null) L"james" (nil) 0x34e974 (nil) 0x34e96c 0x34e970 - stub
fixme:advapi:LookupAccountNameW (null) L"james" 0x135408 0x34e974 0x134a58 0x34e96c 0x34e970 - stub
err:msi:ITERATE_Actions Execution halted, action L"ISSetupFilesExtract" returned 1627
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi1231.tmp"
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi1230.tmp"
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msidbf.tmp"
```

Any help would be greatly appreciated.

---

### Post by Ralphie on 2008-03-20
Do you have the latest version of Wine? (0.9.57) 
This version has the best support of Photoshop cs2.

I'd say delete everything, the folder that has all the applications -- everything having to do with Wine and start over, making sure you are using this newest version of Wine. 
With this version of Wine I installed it straight from the CD, no hassles. 

I also activated over the internet just fine, so maybe just do it that way instead of over the phone.

---

