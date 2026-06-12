---
title: "Unable to run programs (Auto-start service failed to start)"
date: 2016-02-28
forum: Wine
---

### Post by Ritwik_Garg on 2016-02-28
Hi all,
I'm trying to run the game Injustice : Gods Among Us on my Linux (Ubuntu Gnome 15.04). But, I receive the following error : 
```

fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stubfixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub

```
Also,  tried installing mono which gives the following error : 
```

fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet

```

Any help would be appreciated in this regard.

---

### Post by Scout_Roden on 2016-03-01
We also have a similar error. We have been attempting to install Unity3d development platform onto Ubuntu14.. for the past 3 days. 
I have tried every .deb package from Unity for native install, and it just fails. There are two packages.. one for Ubuntu, one that is agnostic Linux. Both yield failures to complete installation.

So, I attempted to use Wine/PlayOnLinux, since many forums state this is a succesful roadmap to install Unity3d 5. I keep running into an error like yours, and also a DNSAPI.DLL error. I manually downloaded a new DNSAPI.DLL file and the DNSAPI.DLL.MUI file into their corresponding directories, and CHOWN and CHMOD both files to match the DLL's alongside them in their locations. #NoJoy:(

***Here are the logs from PlayonLinux:***

> [03/01/16 02:19:00] - Running wine-1.9.4 wineboot (Working directory : /usr/share/playonlinux/python)
fixme:process:SetProcessDEPPolicy (1): stub
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
fixme:ntdll:NtConnectPort (0x5b0c1170,L"\\ThemeApiPort",0x33d09c,(nil),(nil),(nil),0x33d0ac,0x33d0a8),stub!
wine: Unhandled page fault on write access to 0x00000000 at address 0x6a5824e2 (thread 0028), starting debugger...
[03/01/16 02:19:15] - Running wine-1.9.4 wineboot (Working directory : /usr/share/playonlinux/python)
fixme:process:SetProcessDEPPolicy (1): stub
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
[03/01/16 02:19:24] - Running wine-1.9.4 Unity.exe (Working directory : /home/scoutroden/.PlayOnLinux/wineprefix/Unity3d_5/drive_c/Program Files/Unity/Editor)
[03/01/16 02:19:31] - Running wine-1.9.4 Unity.exe (Working directory : /home/scoutroden/.PlayOnLinux/wineprefix/Unity3d_5/drive_c/Program Files/Unity/Editor)
fixme:process:SetProcessDEPPolicy (1): stub
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
err:module:import_dll Loading library DNSAPI.dll (which is needed by L"C:\\Program Files\\Unity\\Editor\\Unity.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Unity\\Editor\\Unity.exe" failed, status c0000135


---

### Post by Eva_Bouwman on 2016-04-21
> **Ritwik_Garg said:**
> Hi all,
I'm trying to run the game Injustice : Gods Among Us on my Linux (Ubuntu Gnome 15.04). But, I receive the following error : 
```

fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stubfixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub

These messages you can ignore, they seem to be used for development.

fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053

this means you have to install .net 4.0 using winetricks is the easiest way, [URL="https://wiki.winehq.org/Winetricks"]https://wiki.winehq.org/Winetricks
[/URL]
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub

```

Also,  tried installing mono which gives the following error : 
```

fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:process:SetProcessDEPPolicy (1): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub


fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053

This is the same error as above it is missing .net v4

fixme:ntdll:NtLockFile I/O completion on lock not implemented yet

```

Any help would be appreciated in this regard.

Good luck in this log there are not more serious errors, I suspect you will be up and running soon.

---

### Post by Eva_Bouwman on 2016-04-21
[03/01/16 02:19:00] - Running wine-1.9.4 wineboot (Working directory : /usr/share/playonlinux/python)
fixme:razz:rocess:SetProcessDEPPolicy (1): stub
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub

Also ignore ;) 

fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053

Also missing .net v4

fixme:ntdll:NtConnectPort (0x5b0c1170,L"\\ThemeApiPort",0x33d09c,(nil),(nil)  ,(nil),0x33d0ac,0x33d0a8),stub!
wine: Unhandled page fault on write access to 0x00000000 at address 0x6a5824e2 (thread 0028), starting debugger...
[03/01/16 02:19:15] - Running wine-1.9.4 wineboot (Working directory : /usr/share/playonlinux/python)
fixme:razz:rocess:SetProcessDEPPolicy (1): stub
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
Ignore above
fixme:service:scmdatabase_autostart_services Auto-start service L[PHP]> "clr_optimization_v4.0.30319_32" [/PHP] .net 
failed to start: 1053
[03/01/16 02:19:24] - Running wine-1.9.4 Unity.exe (Working directory :  /home/scoutroden/.PlayOnLinux/wineprefix/Unity3d_5/drive_c/Program  Files/Unity/Editor)
[03/01/16 02:19:31] - Running wine-1.9.4 Unity.exe (Working directory :  /home/scoutroden/.PlayOnLinux/wineprefix/Unity3d_5/drive_c/Program  Files/Unity/Editor)
fixme:razz:rocess:SetProcessDEPPolicy (1): stub
fixme:wer:WerSetFlags (2) stub!
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
Ignore above
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization> _v4.0.30319_32" still missing .net 

failed to start: 1053
err:module:import_dll Loading library>  DNSAPI.dll (which is needed by  L"C:\\Program Files\\Unity\\Editor\\Unity.exe") failed (error c000007b). Your unity editor is missing dnsapi.dll you can download it online, but probably winetricks has it also available, extract it to ~/.wine/drive_c/windows/system32 and in terminal go to dir and run command
```
wine regsvr32.exe dnsapi.dll
```
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Unity\\Editor\\Unity.exe" failed, status c0000135 			 		 


Good luck I hope you will be up and running to.

---

