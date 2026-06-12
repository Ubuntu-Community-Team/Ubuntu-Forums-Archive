---
title: "Steam (Wine!); Star Wars Force Unleashed (Ultimate Sith Edition)"
date: 2013-05-06
forum: Wine
---

### Post by Lightning Dragon on 2013-05-06
Hello community!

I have had this problem for days now...and that isn't say much about my experience so far, let me tell you! So at first I had the long, tedious task of getting Microsoft Framework 3.5 to work (and finally I did) which took me two days, but now I that I have passed all those stupid NET/Framework issues I have been hit with something I can't find anything on the internet for. When I start SWFU through any of the launchers from the folder or in Steam, I get two different error popups. The first I have pasted into Paste Bin

[http://pastebin.com/kkvta3dZ](http://pastebin.com/kkvta3dZ)

And the second pops up after I either send or don't send the above bug;

[IMG]http://s21.postimg.org/4w7rmh15z/ERROR.png[/IMG]



Installing the game works, the requirements it needed to install worked, and now this remains, so far, to be the only issue I have.

I am very disappointed I cannot play via Wine. I know it said it was only for Windows and I do have Windows, but my drive is SUPER full and I have seen/heard people play this game via Wine, so I am curious if anyone knows the solution to the problem I have?

Thanks!

P.S

[SIZE=1] If anyone needs help with installing NET 3.5 or NET at all, please follow these instructions[SIZE=1]. [/SIZE][/SIZE][SIZE=1]Add:

*$ wget [http://winetricks.googlecode.com/svn/trunk/src/winetricks*](http://winetricks.googlecode.com/svn/trunk/src/winetricks*)

Then install .NET 2.0 prerequisite:*

$ bash winetricks dotnet20
$ bash winetricks dotnet20sp2(only do this one if the above doesn't work)

Run the .NET 3.5 installer:

*$ bash winetricks dotnet30

It should ask you to download something (it will link you to it) and place it in the folder it opens up, and then rerun the bash script for dotnet30 after you have placed the file. Reboot and it should work.[/SIZE] [SIZE=1]If it doesn't, try this and reboot (and do as it prompts!);


$ wget [http://winetricks.googlecode.com/svn/trunk/src/winetricks](http://winetricks.googlecode.com/svn/trunk/src/winetricks)

*$ bash winetricks dotnet35*[/SIZE]

(during the install, it might ask you to set echo 0|sudo tee /proc/sys/kernel/yama/ptrace_scope to 0, do it or nothing will work.)

**My system:**

Linux Mint Maya & Ubuntu 12.04 LTS
AMD CPU
3GB Ram
EVGA Geforce 8600 gt 1GB

---

### Post by deri on 2013-05-06
I just bought this game and newer star wars game. I haven't tried it to work, but I doubt that I face same difficulties. So any help is appreciated.

---

### Post by Lightning Dragon on 2013-05-06
Hi,

I would be willing to get you as far as I got, but beyond that I can offer no assistance. Right now I've got Steam installed via Wine and via PlayOnLinux, each had the same problems.

---

### Post by deri on 2013-05-08
Have you reported a bug to wine database? They don't accept reports if the wine is not pure. Meaning you should not use playonlinux...I wonder how people notice what items to install via winetricks.

---

### Post by Lightning Dragon on 2013-05-09
Hi,

No, I haven't tried that yet, I'm not sure how to unless making a thread on their forums counts as a report? Oh, I use both Wine and PlayOnLinux, or at least was trying to, so they were seperate. 

They know, at least I assume, based on the requirements of the game. For example, SWFU requires "Directx 9.0", so I guess they just go to winetricks and find the component.

---

### Post by deri on 2013-05-10
You have very old wine and linux kernel. Try to upgrade both?

---

### Post by deri on 2013-05-10
I have playonlinux, latest wine. I have been able to play css go, dota2, some assasin creeds. But this is because of playonlinux. I tried to install steam with wine. How do you do it? It didn't accept .deb and it seems that exe is not good either.

---

### Post by deri on 2013-05-10
BTW I JUST RELEASED THE GAME IS ON THE LIST OF PLAYONLINUX. You should install it via playonlinux! It knows how to get it work. Trying myself later, after I have downloaded the game.

---

### Post by Lightning Dragon on 2013-05-10
Hi,

I believe I just installed the latest kernel, but I am unsure how to check. Also, I installed wine via terminal, so it didn't tell me which version it installed either. I will try and update wine now. And PlayOnLinux only has the CD/DVD version of the game, and my copy is via Steam. I'll see if they have an option for Star Wars via Steam in a moment.

edit

Yes, I have Wine 1.4, the stable version.

> I have playonlinux, latest wine. I have been able to play css go,  dota2, some assasin creeds. But this is because of playonlinux. I tried  to install steam with wine. How do you do it? It didn't accept .deb and  it seems that exe is not good either.

I installed the .msi file from the Steam website via Wine. I right-clicked the file, made it executable and then loaded it through Wine Program Loader, and it installed. I also made it so it opened in a graphic desktop (1000x614) and set it to Windows XP compatibility. But it runs without those settings as well.

---

### Post by deri on 2013-05-10
I believe wine shows the version running wine --version. 1.5.30 is the latest, released just now! uname -r shows the kernel version you are running.

---

### Post by deri on 2013-05-10
Here is how to upgrade wine
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by Lightning Dragon on 2013-05-10
Hi,

Thank you! That certainly did it, though I had do a fresh install of 1.4 to upgrade to 1.5. Weird!

The upgrade helped me passed my previous errors (yay!), but made it so I can't see text*see end notes. It stayed on step 2 of the installation for SWTFU for about an hour and then closed at its finish, which I assume to be the success of the install of the components. Clicking "play" resulting in nothing happening though, but reports the game is already running.

*I fixed this by either disabling DWrite in winecfg or through the regedit in Steam's folder (setting it to 0 in the folder) via Winetricks. I did the later, but either will work.

---

### Post by deri on 2013-05-11
I am still downloading the game. Have you read this? [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18673&iTestingId=47444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18673&iTestingId=47444)

---

### Post by Lightning Dragon on 2013-05-11
Hi,

Yes, I have read that. Unfortunately it is only for the DVD/CD version of the game so the patch doesn't work. I will try the resolution fix by one of the commentors to see if it will work.

edit

Nope, didn't work. I am now running through the Terminal for an output. Here is what it reports when trying to launch the game;

```

LightningDragon@LDH:~$ env WINEPREFIX="/home/LightningDragon/.wine" wine "C:\Program Files\Steam\Steam.exe"
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2013-05-11 19:00:55] Startup - updater built May  3 2013 15:10:13
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0055a0, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0055a0, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0055a0, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0055a0, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0055a0, 0x3f036be8, 0x3f036be0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
[2013-05-11 19:00:56] Verifying installation...
[2013-05-11 19:00:56] Verification complete
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0055a0, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0055a0, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0055a0, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0055a0, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0055a0, 0x3f036be8, 0x3f036be0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:iphlpapi:NotifyAddrChange (Handle 0x5add6bc, overlapped 0x58ead48): stub
fixme:winsock:WSALookupServiceBeginW (0x5add7bc 0x00000ff0 0x5add804) Stub!
[0511/190057:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
Assert( Assertion Failed: (::DeleteObject( hOldBitmap )) ):surface_gdiwin32.cpp:1839

fixme:dbghelp:elf_search_auxv can't find symbol in module
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_SetBlanket 0x7c9bbfb8, 0x1cf178, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7c9bbfb8
fixme:mountmgr:harddisk_ioctl The DISK_PARTITION_INFO and DISK_DETECTION_INFO structures will not be filled
fixme:wbemprox:enum_class_object_Next timeout not supported
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:CoGetClassObject class {dff32fea-3331-48da-a272-ccfc238695be} not registered
err:ole:create_server class {dff32fea-3331-48da-a272-ccfc238695be} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {dff32fea-3331-48da-a272-ccfc238695be} could be created for context 0x17
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:RegisterDeviceNotificationA (hwnd=0x20052, filter=0x32e2dc,flags=0x00000004) returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationW (hwnd=0x1011c, filter=0x18dfe9ac,flags=0x00000000) returns a fake device notification handle!
fixme:win:UnregisterDeviceNotification (handle=0xcafeaffe), STUB!
fixme:win:RegisterDeviceNotificationW (hwnd=0x2011c, filter=0x18dfe9ac,flags=0x00000000) returns a fake device notification handle!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ddc8,0x00000000), stub!
fixme:winsock:WSALookupServiceBeginW (0x76fe1fc 0x00000ff0 0x76fe244) Stub!
[0511/190106:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:volume:GetVolumePathNameW (L"\\\\?\\C:\\", 0x32dd28, 260), stub!
fixme:volume:GetVolumePathNameW (L"\\\\?\\D:\\", 0x32dd28, 260), stub!
fixme:volume:GetVolumePathNameW (L"\\\\?\\E:\\", 0x32dd28, 260), stub!
fixme:volume:GetVolumePathNameW (L"\\\\?\\Z:\\", 0x32dd28, 260), stub!
The entry point method could not be loaded (< What it displays when I click play)

```

---

### Post by deri on 2013-05-13
I tried those commands, it just gives a link and download. And 1st exe I tried it complained that it should be 64bit, when I was installing 32 or via versa. Then I installed playonlinux, steam and copied the game from another steam install. Double clicked the game and it starts to install some files but it feels like it's doing nothing. Cannot be sure. But I am too unpatient to wait.Tried to install those netframework files from playonlinux, but it crashes while installing newer package than 2.0...

---

### Post by deri on 2013-05-13
> And PlayOnLinux only has the CD/DVD version of the game, and my copy is  via Steam. I'll see if they have an option for Star Wars via Steam in a  moment.

How is that possible? 

I do have steam version there too!

Going to try that. Playonlinux has a patch for the game too...

---

### Post by deri on 2013-05-13
What's your playonlinux version? Newest is 4.21. 

Got error when launching...

---

### Post by Lightning Dragon on 2013-05-13
Hi,

I have the latest PlayOnLinux, which I got via the terminal commands on their website under "Ubuntu" > "Precise". And they have no patch or anything for Star Wars: The Force Unleashed for Steam in their game directory either it seems.

> 
 			 				[INDENT] 					I tried those commands, it just gives a link and download. And 1st  exe I tried it complained that it should be 64bit, when I was installing  32 or via versa. Then I installed playonlinux, steam and copied the  game from another steam install. Double clicked the game and it starts  to install some files but it feels like it's doing nothing. Cannot be  sure. But I am too unpatient to wait.Tried to install those netframework  files from playonlinux, but it crashes while installing newer package  than 2.0... 				[/INDENT] 			
  			   		

Which commands? And when it is installing the needed components via Steam for the game you have to let it finish. It will take a while, but it will close be itself without any errors or whatnot. Installing newer components via PlayOnLinux never seems to work for me, so I wouldn't advise that.

---

### Post by deri on 2013-05-13
PlayOnLinux: [PlayOnLinux_4.2.1.deb]("http://www.playonlinux.com/script_files/PlayOnLinux/4.2.1/PlayOnLinux_4.2.1.deb") Seems to be the latest. You can install Star wars force unleashed, ultimate sith edition via steam using playonlinux. And they have a 1.2 pactch for The force unleashed so I assume it's the same game. I don't know how to get this game playable. Is it even possible anymore...

---

### Post by Lightning Dragon on 2013-05-13
Hi,

Yes, it is the same game and the patch is for it, but that patch isn't for Steam version of the game. If you attempt to use the patch, it reports the game is not installed because it needs the CD/DVD version of the game. And it is playable, someone on youtube was playing it in Fedora, so it has to be playable.

---

### Post by deri on 2013-05-13
How can it be so hard to find installation instructions for the game? The stuff that is in wine's db don't seem to help.

---

### Post by Lightning Dragon on 2013-05-13
Hi,

It takes a lot of testing, and even then it takes even more testing on other systems to make sure it is a fix and whatnot. I have no doubt in time wine will find a way to fix its issues. And if not that, Steam for Linux will have caught up with ported games.

---

### Post by deri on 2013-05-14
Do you have any idea how to fix even some of these error messages?

[05/14/13 15:54:09] - Running wine-1.5.30-1.5.30-1 Steam.exe (Working directory : /home/jarkko/.PlayOnLinux/wineprefix/Steam/drive_c/Program Files/Steam)
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:module:GetModuleHandleExW should pin refcount for 0x79000000
fixme:thread:SetThreadStackGuarantee (0x33fc54): stub
fixme:shell:URL_ParseUrl failed to parse L"PresentationFramework"
fixme:shell:URL_ParseUrl failed to parse L"WindowsBase"
fixme:shell:URL_ParseUrl failed to parse L"PresentationCore"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:advapi:RegisterTraceGuidsW (0x540e6616, (nil), {a42c77db-874f-422e-9b44-6d89fe2bd3e5}, 26, 0x33becc, (null), (null), 0x54188798,): stub
fixme:advapi:RegisterTraceGuidsW (0x1ac17f2, (nil), {a42c77db-874f-422e-9b44-6d89fe2bd3e5}, 1, 0x33e538, (null), (null), 0x33e540,): stub
fixme:shell:URL_ParseUrl failed to parse L"System.Core"
fixme:ntdll:NtSecureConnectPort (0x338e84,L"\\BaseNamedObjects\\FontCachePort3.0.0.0",0x338e6c,(nil),0x1eb3f8,(nil),0x338e80,0x1e8a068,0x338e78),stub!
fixme:process:FlushProcessWriteBuffers : stub
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"PresentationFramework.Aero"
fixme:shell:URL_ParseUrl failed to parse L"AWL.net"
fixme:shell:URL_ParseUrl failed to parse L"msvcm90"
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:gameux:GameExplorerImpl_VerifyAccess (0x1eefd0, L"C:\\Program Files\\Steam\\SteamApps\\common\\Star Wars The Force Unleashed\\AWL_Release.dll", 0x33e764)
fixme:win:EnumDisplayDevicesW ((null),0,0x33df78,0x00000000), stub!
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:driver:GdiEntry13 stub
fixme:win:EnumDisplayDevicesW ((null),0,0x666e358,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x666e558,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x666e558,0x00000000), stub!
fixme:shell:URL_ParseUrl failed to parse L"PresentationFramework.classic"
fixme:msg:ChangeWindowMessageFilter c067 00000001
fixme:msg:ChangeWindowMessageFilter c069 00000001
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_access_from_pool Unhandled pool 0x6.
fixme:d3d_surface:surface_init Unknown pool 0x6.
fixme:d3d:resource_access_from_pool Unhandled pool 0x6.
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:shell:URL_ParseUrl failed to parse L"UIAutomationProvider"
fixme:shell:URL_ParseUrl failed to parse L"UIAutomationTypes"
fixme:shell:URL_ParseUrl failed to parse L"SlimDX"
fixme:shell:URL_ParseUrl failed to parse L"msvcm80"
fixme:win:EnumDisplayDevicesW ((null),0,0x33ce38,0x00000000), stub!
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:wincodecs:ColorTransform_Initialize ignoring color contexts
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:d3d9_device_CheckDeviceState iface 0x66c6b38, dst_window (nil) stub!
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f0055a0, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f0055a0, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f0055a0, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f0055a0, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f0055a0, 0x3f036be8, 0x3f036be0
err:d3d:context_restore_gl_context Failed to restore GL context 0x20005 on device context 0x3005c, last error 0x6.
fixme:process:SetProcessShutdownParameters (000003ff, 00000000): partial stub.
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:msvcrt:__clean_type_info_names_internal (0x4e9c134) stub
fixme:msvcrt:__clean_type_info_names_internal (0x7842e65c) stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:iphlpapi:NotifyAddrChange (Handle 0x55ed6bc, overlapped 0x53fbb30): stub
fixme:winsock:WSALookupServiceBeginW (0x55ed7bc 0x00000ff0 0x55ed804) Stub!
[0514/155435:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8 
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:iphlpapi:CancelIPChangeNotify (overlapped 0x53fbb30): stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub

---

### Post by Lightning Dragon on 2013-05-14
Hi,

Unfortunately, besides recongizing this "[0514/155435:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8", I do not know how to fix it. How did you install the game? It would help to know your steps.

---

### Post by deri on 2013-05-14
Actually I have 3 setups of steam. Native client, playonlinux and wine. I think I tottaly swap to playonlinux and native. It gets too complicated to have multiple installs. I don't see any advantage to having pure wine over playonlinux so far. I noticed that on this game's install there is support directory which contains framework 3.5 directx files. 

Do you have any other games that we could together solve? The project, what was it called? Desura? No...what's the name? It's basically wine, but you pay for it to have a support. You can try it free for some weeks or was it a total month? It has this game and the status is working. So I remember. I tried to install it but it says about depencies problem. So I didn't go any further with that.

---

### Post by Lightning Dragon on 2013-05-14
Hi,

I have three as well, same for me. I keep them named and organized on the desktop called "Steam", "Steam WINE", and "Steam POL". It makes it far easier to keep track of things. I have gotten the same setup on Wine that I did with PlayOnLinux for Star Wars: The Force Unleashed. The same exact problem. I think it has something to do with the NET installs or something, or a missing DLL.

It believe it is called Crossover? I'm not entirely sure.

---

### Post by deri on 2013-05-14
Yes it's crossover. Installed it while waited for some reply. There is no script for this game. You have to manually install the game. So I didn't bother. I think I should install steam, then stop the process for a moment and copy paste the game to crossover steam install and try to run it. Copying this game takes a while. You can freely try the program for 2 weeks.

---

### Post by deri on 2013-05-15
I installed crossover, steam on it. Restored the game on steam. I got error message not using swap. Got same error on playonlinux, but I was able to fix it there. Don't know how to fix the error on crossover, don't see registery editor anywhere. I was able to install some dotnet frameworks on playonlinux install, but still got some errors on launch. I am not going anywhere.

---

### Post by Lightning Dragon on 2013-05-15
Hi,

I have been looking at, for example, my error logs and I think one of the mentioned DLLs is the cause. This weekend I'll try and enable/disable or install some of them and see if that fixes the error. Short of that, I don't think we'll get any further than we are at the moment. :(

---

