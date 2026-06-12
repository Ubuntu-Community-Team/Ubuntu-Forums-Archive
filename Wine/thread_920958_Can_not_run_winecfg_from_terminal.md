---
title: "Can not run winecfg from terminal"
date: 2008-09-15
forum: Wine
---

### Post by outdoorsman14 on 2008-09-15
I am having trouble running Wine from console. I was trying to install Microsoft Office 2007 in Ubuntu and I followed this thread [http://ubuntuforums.org/showthread.php?t=844309&highlight=onenote](http://ubuntuforums.org/showthread.php?t=844309&highlight=onenote). I went through all of the steps and it went through the whole sequence of installing Office onto the computer, but it never showed up in the Programs Files, so thinking I might not have followed the directions carefully enough, I thought I would start from scratch, I re-installed Wine and followed the thread again, but now it won't let me do the winecfg in the terminal, this is what shows up:

err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\syst                                          em32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system3                                          2\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exi                                          t code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\syst                                          em32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\syste                                          m32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system3                                          2\\winecfg.exe" failed, status c0000135

I know it has to do with that rpcrt4.dll file that I had to modify and re-modify back, but what can I do to fix it? I even erased the .wine file from my computer and reinstated it through the link to configure Wine under the applications menu, but it still won't let me do anything that involves that file.
Any help would be great!!

---

### Post by outdoorsman14 on 2008-09-15
I got Office to load through the Wine emulator, so I can access word and Excel, but I can not get OneNote or PowerPoint to work, something possibly related?

---

