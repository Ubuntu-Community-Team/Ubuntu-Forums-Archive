---
title: "Impossible to run wine"
date: 2008-05-02
forum: Wine
---

### Post by radiumfox on 2008-05-02
can someone help me I'm desperate:
my pc is running hardy
i installed wine 0.9.59 through synaptics and everything worked.. (eg. dreamweaver, ms office 2003) Then I tried to install Photoshop CS3 and did some manipulations as described on [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584")
> 1. Copy mshtml, shdocvw, urlmon, shlwapi, mlang and jscript.dll from an XP partition to ~/.wine/drive_c/windows/system32

2. Do 'regsvr32 jscript.dll'

3. Do 'wget kegel.com/wine/winetricks && sh winetricks msxml3'

4. Set mshtml, shdocvw, urlmon, shlwapi, mlang to native in winecfg

All this is only needed to make the installer happy and finish fine. The actual Photoshop.exe doesn't need any native dlls set here, you only need gdiplus:

5. Do winetricks gdiplus (in console of choice)

Note: If Photoshop CS3.exe crashes, update to the very latest git, got it running there

 

Thanks to Louis Lenders for this step-by-step guide. 
Anyhow the setup.exe didn't work and after an hour all the programs didn't start neither. The console gave me out:

> 
simon@simon-laptop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135



i now that this is has already been questioned [http://ubuntuforums.org/showthread.php?t=234071]("http://ubuntuforums.org/showthread.php?t=234071") but they didn't solve the problem. So i deinstalled it and updated the repositories as they are given on the official wine hq page. I didn't know if the process would also delete the drive_c folder or not so i moved(!) it to my home folder. Then I deleted the menu entries of wine because they were still present.
Wine had been definitely deleted because the bash command wine couldn't be used anymore.

Afterwards I installed the new 0.9.60 but menu entries didn't appear. 
the console gave out the same again.

So I moved the old drive_c into /home/myname/.wine as I noticed that the installation process didn't create a new drive_c

Although the drive_c is now present it gives the same message as posted above.. 

I need help! Maybe I'm so stupid...???!!! Isn't there a way to fix this problem and get wine running again without reinstall Ubuntu just because of such a damn error??

---

### Post by radiumfox on 2008-05-02
can just give me someone an idea how to fix that:
> simon@simon-laptop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library comdlg32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

---

### Post by tech9 on 2008-05-02
you could always try to delete the .wine directory under your home directory - it's a hidden folder - Ctrl-H

---

### Post by cogadh on 2008-05-02
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

