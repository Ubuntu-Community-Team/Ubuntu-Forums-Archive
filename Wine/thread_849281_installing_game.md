---
title: "installing game"
date: 2008-07-04
forum: Wine
---

### Post by jwalters on 2008-07-04
Finally got COD to work...now when trying to install cod united offensive through wine using the cd it balks and quits with a validation key message....this is what I get when trying to use the terminal

jwalters@jwalters-desktop:/media/cdrom$ wine ./setup.exe
fixme:advapi:LookupAccountNameW (null) L"jwalters" (nil) 0x32be7c (nil) 0x32be80 0x32be74 - stub
fixme:advapi:LookupAccountNameW (null) L"jwalters" 0x138da8 0x32be7c 0x13c608 0x32be80 0x32be74 - stub
err:msi:ITERATE_DuplicateFiles Failed to copy file L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\9\\Intel 32\\IDriver.exe" -> L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\9\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
fixme:advapi:LookupAccountNameW (null) L"jwalters" (nil) 0x33cecc (nil) 0x33ced0 0x33cec4 - stub
fixme:advapi:LookupAccountNameW (null) L"jwalters" 0x1733f0 0x33cecc 0x172ef0 0x33ced0 0x33cec4 - stub
fixme11drv:X11DRV_SetWindowRgn not supported on other thread window 0x10040
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-3200-00001e000000}
err:rpc:I_RpcReceive we got fault packet with status 0x80010108

Any help?????
jwalters is online now Report Post   	Edit/Delete Message

---

### Post by Vadi on 2008-07-04
The appdb entry said you should be OK if you got cod itself to run, and trying to google for this problem was too hard since the linux server kept coming up (they have a linux server and no client? wth?)

Anyway try posting it in the wine forum, it's the proper place for wine help: ([click]("http://ubuntuforums.org/forumdisplay.php?f=313")) or the appdb entry ([click]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5601&iTestingId=16480"))

---

### Post by p_quarles on 2008-07-04
Moved to the Wine section at poster's request.

---

