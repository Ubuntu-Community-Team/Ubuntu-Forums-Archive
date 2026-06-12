---
title: "wine cannot find C:\\windows\\system32\\env.exe"
date: 2013-03-05
forum: Wine
---

### Post by 3Dizzy on 2013-03-05
Hello All,

Can someone shed a little light on a problem i have encountered?

When trying to load a PC application through wine, i recieve trhe below error log with an error box within Wine advising that StreamingFSD.sys failed to start.

Is anyone well enough versed in the arts of Linux to advise how i might be able to solve this problem? 

Many thanks in advance.

Ed

[PHP] 	 	   To run a command as administrator (user "root"), use "sudo <command>". 
 See "man sudo_root" for details. 
  
 admin@dizzy-System-Product-Name:~$ ~Desktop/env WINEPREFIX="/home/admin/.wine" wine C:\\Program\ Files\\Numecent\\Application\ Jukebox\ Player\\JukeboxPlayer.exe  
 bash: ~Desktop/env: No such file or directory 
 admin@dizzy-System-Product-Name:~$ sudo~ env WINEPREFIX="/home/admin/.wine" wine C:\\Program\ Files\\Numecent\\Application\ Jukebox\ Player\\JukeboxPlayer.exe  
 No command 'sudo~' found, did you mean: 
  Command 'sudo' from package 'sudo' (main) 
  Command 'sudo' from package 'sudo-ldap' (universe) 
 sudo~: command not found 
 admin@dizzy-System-Product-Name:~$ sudo env WINEPREFIX="/home/admin/.wine" wine C:\\Program\ Files\\Numecent\\Application\ Jukebox\ Player\\JukeboxPlayer.exe  
 [sudo] password for admin:  
 Sorry, try again. 
 [sudo] password for admin:  
 wine: /home/admin/.wine is not owned by you 
 admin@dizzy-System-Product-Name:~$ wine env WINEPREFIX="/home/admin/.wine" wine C:\\Program\ Files\\Numecent\\Application\ Jukebox\ Player\\JukeboxPlayer.exe  
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e740,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e73c,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e740,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,2,(nil),0,(nil)) - stub! 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e6d0,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e6fc,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e6fc,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:advapi:ImpersonateLoggedOnUser (0x5c) 
 wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 002a), starting debugger... 
 fixme:shell:_SHGetUserProfilePath unsupported for user other than current or default 
 fixme:shell:_SHGetUserProfilePath unsupported for user other than current or default 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e6fc,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e6fc,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:process:SetProcessShutdownParameters (000000ff, 00000000): partial stub. 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e684,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:ole:CoResumeClassObjects stub 
 fixme:advapi:RegisterEventSourceW ((null),L"StreamingCore"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0xa8e6f4,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 err:service:service_send_start_message service L"StreamingFSD" failed to start 
 fixme:service:scmdatabase_autostart_services Auto-start service L"StreamingFSD" failed to start: 1053 
 wine: cannot find L"C:\\windows\\system32\\env.exe" 
 admin@dizzy-System-Product-Name:~$  

[/PHP]

---

### Post by Toz on 2013-03-11
Moving to the wine subform.

I believe the command is incorrect. Try running it like this:
```
WINEPREFIX=/home/admin/wine wine C:\\Program\ Files\\Numecent\\Application\ Jukebox\ Player\\JukeboxPlayer.exe
```

What is the application that you are trying to run? You can get more info about its compatibility with wine by searching the WineHQ AppDB located [here]("http://appdb.winehq.org/"). 

And why are you trying to run it with sudo?

---

### Post by aarons6 on 2013-03-12
yeah dont run wine with sudo.. 
also why are you putting ~ infront of env

its just
[COLOR=#777777][FONT=monospace][/FONT][/COLOR][COLOR=#000000][FONT=monospace]env WINEPREFIX=~/.wine wine app.exe[/FONT][/COLOR][COLOR=#777777][FONT=monospace]


[/FONT][/COLOR][COLOR=#000000][FONT=monospace]also you dont need to specify the defualt prefix
you can just[/FONT][/COLOR][COLOR=#777777][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]wine app.exe[/FONT][/COLOR][COLOR=#777777][FONT=monospace]

[/FONT][/COLOR][COLOR=#000000][FONT=monospace]also i think your slashes are the wrong way.. its
C:\program/ files\something/ space\something\someapp.exe

you can also use quotes like this
"C:\program files\something space\something\someapp.exe"
[/FONT][/COLOR][COLOR=#777777][FONT=monospace]
[/FONT][/COLOR]

---

