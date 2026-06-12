---
title: "messed up ole32.dll - HELP!"
date: 2008-09-10
forum: Wine
---

### Post by augabo on 2008-09-10
I inadvertently removed ole32.dll from the winecfg Libraries tab when I was assigning redirects for a new windows program. Now, when I try to run winecfg I get the following:

aug@aug-desktop:~$ winecfg
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
aug@aug-desktop:~$ 

..so, now I can't even run winecfg at all!

I tried uninstalling wine completely via the Synaptic Package Manager, and reinstalled wine.  But I still have the same problem.  HELP!

..Aug

---

### Post by Bios Element on 2008-09-10
Try going to your home folder, Viewing Hidden files and moving your .wine folder to your desktop or somewhere else. Then uninstall/re-install wine. It 'should' remake the .wine folder for you. Bad news is you'd have to re-install all your programs. But that's one way. I'm sure there's a better way though.

---

### Post by augabo on 2008-09-10
Thanks!  That brought back winecfg back to life.   Reinstalling the apps won't be hard at this point.

---

