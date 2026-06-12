---
title: "Ubuntu 12.04 LTS Question"
date: 2012-07-07
forum: Wine
---

### Post by Lightning Dragon on 2012-07-07
Hello community,

I have a question regarding folders and files within it, rather, installed programs etc etc.  Through lots of trial and error, I managed to get RPG Game Maker VX and ACE to install on the machine and get passed those pesky DRM errors, DirectX errors, and the sound card and MIDI errors, but the folder I installed the programs into using WINE, appear empty, so I can not find the exe to run the program anymore.

ACE made a shortcut on my desktop, but VX did not, so that is why I am searching for it. Even though they appear empty, they are not. I know this because going into Uninstall WINE Software, winetricks and all the other WINE programs, I can see everything in it.

For example if I look for it without WINE through the HOME FOLDER option:

[IMG]http://i50.tinypic.com/vxown9.png[/IMG]

And this is what it looks like through the WINE programs:

[IMG]http://i49.tinypic.com/mwebfs.png[/IMG]

So the folder isn't empty, right? I can't find the files to run. :(

Is there any way to find them, or see them? And maybe make a shortcut on the desktop, or a command that I can use to launch it?

Thank you all for reading,

Lightning Dragon!

---

### Post by sffvba[e0rt on 2012-07-07
*Thread moved to **Wine**.*


404

---

### Post by madjr on 2012-07-07
this might help you show hidden stuff:

[http://linux.about.com/od/ubuntu_doc/a/ubudg10t7.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t7.htm)

[http://www.liberiangeek.net/2011/01/set-nautilus-to-always-show-hidden-files-and-folders-in-fedora-14-laughlin/](http://www.liberiangeek.net/2011/01/set-nautilus-to-always-show-hidden-files-and-folders-in-fedora-14-laughlin/)

[http://askubuntu.com/questions/116802/hidden-files-in-nautilus-after-extracting-iso](http://askubuntu.com/questions/116802/hidden-files-in-nautilus-after-extracting-iso)

---

### Post by Lightning Dragon on 2012-07-07
Thank you for the reply, madjr. :)

The shortcut did not work (CTRL+H) and I don't have an option to be able to edit preferences and right clicking the background for a list of commands does not list anything for it either. (None of the links helped)

I will try uninstalling and reinstalling, and then will try the shortcut and see if it works.

---

### Post by Bucky Ball on 2012-07-07
LD, there seems to be an RPGVX.exe file in your 'Select an executable file' screenshot. Isn't that what you are looking to launch? You could open a terminal and do a search for that with something like:

```
locate RPGVX.exe
```... and take it from there for the shortcut creation.

Wine can be problematic. Have you checked WineHQ to see how your programs have been performing in Wine?

---

### Post by Lightning Dragon on 2012-07-07
Yes, it does have the launcher in it, but I could only see the contents of the folder when I was searching through the WINE program. I tried that command, and it did nothing. Well, it did something, gave me a "no such file or directory exists".

However, I just uninstalled everything related to the game makers, deleted the folder and reinstalled and then tried that command, and it showed me the location. 

> /home/LD/.wine/drive_c/Program Files/Common Files/RPG Maker/RPGVX.exeI guess something went wrong with my first install? 

I also tried the shortcuts and the links before I reinstalled everything and it took the option to close the programs by clicking the little "x" away. Like GIMP, Terminal, Home Folder and the WINE programs. :(

No, I have not checked that site. I will now, though. ;)

---

### Post by madjr on 2012-07-07
if you're using unity the menus are at the top of the screen (globalmenu) but hidden.

or you can use the HUD, here's how:

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-basic-unity-interface-desktop-tutorial)

---

### Post by Lightning Dragon on 2012-07-08
Thank you for the link. I'm reading over it now! :D

I actually meant "x"s (this [IMG]http://i47.tinypic.com/i3i2b6.png[/IMG]) on the programs seemed to have disappeared. Sometimes they do that in my Ubuntu and I have to restart the PC to restore them. :( The link helped me be able to close Firefox and stuff though without the buttons. (:

A couple things like this has been happening since I updated from 11.10 to 12.04. Not being able to see files (fixed now), the disappearance of the x etc etc buttons, slowness, crashes (12.04 asking me to send reports in about it) and now it has Timidity problems like this keeping me from logging in:

[IMG]http://i48.tinypic.com/2vlnyvd.png[/IMG]

I have looked into the TiMidity problem, and it seems a lot of people encountered it but nothing but a fresh install would help the problem. TiMidity is needed for what I'm doing, too. Is there a way to fix this problem and keep TiMidity, or do I have to remove and reinstall my system?

---

### Post by madjr on 2012-07-09
> **Lightning Dragon said:**
> Thank you for the link. I'm reading over it now! :D

I actually meant "x"s (this [IMG]http://i47.tinypic.com/i3i2b6.png[/IMG]) on the programs seemed to have disappeared. Sometimes they do that in my Ubuntu and I have to restart the PC to restore them. :( The link helped me be able to close Firefox and stuff though without the buttons. (:

A couple things like this has been happening since I updated from 11.10 to 12.04. Not being able to see files (fixed now), the disappearance of the x etc etc buttons, slowness, crashes (12.04 asking me to send reports in about it) and now it has Timidity problems like this keeping me from logging in:

[IMG]http://i48.tinypic.com/2vlnyvd.png[/IMG]

I have looked into the TiMidity problem, and it seems a lot of people encountered it but nothing but a fresh install would help the problem. TiMidity is needed for what I'm doing, too. Is there a way to fix this problem and keep TiMidity, or do I have to remove and reinstall my system?

yeah i would probably reinstall, so you can have a stable working system. Sometimes upgrades from a previous version can bring in some stability problems.

then to make sure there're no future errors or even as a "test development enviorment", you can try testing in virtualbox (which can be installed inside ubuntu too):

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

[http://www.wikihow.com/Install-Ubuntu-on-VirtualBox](http://www.wikihow.com/Install-Ubuntu-on-VirtualBox)


developers here also use it to test new "unstable" ubuntu features they're developing while keeping a working main OS, so is a handy tool.

Good luck ):P

---

### Post by Lightning Dragon on 2012-07-09
Thank you for the reply, madjr!

Do you have a link I may ask for telling how to do a fresh install of Ubuntu 12.04 LTS? I've never reinstalled before [SIZE=1](I've been using since 2001-2002; first OS I ever had)[/SIZE] and I've never seen my mother do it either, because it has always worked smoothly for us. 

As for VirtualDrive, is it possible to run it even if I have Ubuntu on a 250 GB drive and Windows on a 500GB drive? If not, I don't think my computer would be able to handle the VirtualDrive or have the space on the Windows HDD to manage it.

LD,

---

### Post by madjr on 2012-07-09
> **Lightning Dragon said:**
> Thank you for the reply, madjr!

Do you have a link I may ask for telling how to do a fresh install of Ubuntu 12.04 LTS? I've never reinstalled before [SIZE=1](I've been using since 2001-2002; first OS I ever had)[/SIZE] and I've never seen my mother do it either, because it has always worked smoothly for us. 

As for VirtualDrive, is it possible to run it even if I have Ubuntu on a 250 GB drive and Windows on a 500GB drive? If not, I don't think my computer would be able to handle the VirtualDrive or have the space on the Windows HDD to manage it.

LD,

this might help you for your fresh install:

[http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)


as for the hdd space, don't worry, ubuntu doesnt need that much , specially in a virtual machine. 20gb should be fine and no partitioning is needed either.

test it out and since its virtual, you can erase it completely when ever you want, even install another version of ubuntu or linux.

---

### Post by Lightning Dragon on 2012-07-09
Thank you for the link. I don't have a USB big enough, but before I saw this link, I did burn it successfully to a DVD. Well, I had the system test the burn and it came back with no errors and then I reinstalled over Ubuntu 12.04 and the install went nicely, I assume since nothing was reported as broken.

However, I can't seem to install WINE correctly; I can install it through the terminal, but when I run the program, I am told two things are not installed and that it would install it by itself. The two packages were:

WINE Mono Package
WINE Gecko Package

Both of which fails. I can't install Microsoft .NET Framework 2.0 either, which all of this I could do before. I tried installing through WINE, and then with a sudo command and then this: " sh winetricks dotnet20" but they all still fail. I still get lots of crashes and errors as well.

Here is a list for the terminal errors when installing:

```


LD@Lightning Dragon:~$ sh winetricks dotnet20 
 Executing w_do_call dotnet20 
 Executing load_dotnet20 
 Executing w_do_call fontfix 
 Executing load_fontfix 
 Setting Windows version to win2k 
 Executing winetricks_early_wine regedit C:\windows\Temp\_dotnet20\set-winver.reg 
 Executing mkdir -p /home/LD/.cache/winetricks/dotnet20 
 Executing unzip -o -q -d /home/LD/.wine/dosdevices/c:/windows/system32 l_intl.zip 
 Executing mkdir -p /home/LD/.cache/winetricks/dotnet20 
 Executing wine dotnetfx.exe 
 fixme:advapi:DecryptFileA "C:\\users\\LD\\Temp\\IXP000.TMP\\" 00000000 
 fixme:advapi:LsaOpenPolicy ((null),0x33f31c,0x00000001,0x33f344) stub 
 fixme:advapi:LsaClose (0xcafe) stub 
 fixme:storage:create_storagefile Storage share mode not implemented. 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 err:mscoree:LoadLibraryShim error reading registry key for installroot 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\cscomp.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsn.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorwks.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\system32\\mscoree.dll", "C:\\windows\\system32\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorjit.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorpe.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\vbc.exe", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:imagehlp:BindImageEx (0, "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\diasymreader.dll", "C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\", (null), (nil)): stub 
 fixme:mofcomp:wmain stub 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17 
 fixme:advapi:RegisterEventSourceW ((null),L"ASP.NET 2.0.50727.0"): stub 
 fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0001,0x400003f9,(nil),0x0002,0x00000000,0x33ecec,(nil)): stub 
 fixme:advapi:DeregisterEventSource (0xcafe4242) stub 
 fixme:loadperf:UnloadPerfCounterTextStringsW (L"u \"ASP.NET_2.0.50727\"", 1): stub 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 fixme:thread:SetThreadStackGuarantee (0x33fc78): stub 
 fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices" 
 fixme:shell:URL_ParseUrl failed to parse L"System" 
 err:ole:CoGetClassObject class {ecabb0c8-7f19-11d2-978e-0000f8757e2a} not registered 
 err:ole:CoGetClassObject no class object {ecabb0c8-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1 
 err:ole:CoGetClassObject class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered 
 err:ole:create_server class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {6eb22881-8a19-11d0-81b6-00a0c9231c29} could be created for context 0x15 
 fixme:process:FlushProcessWriteBuffers : stub 
 err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered 
 err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd58) 
 err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:CoGetClassObject class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 err:ole:create_server class {a9e69610-b80d-11d0-b9b9-00a0c922e750} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {a9e69610-b80d-11d0-b9b9-00a0c922e750} could be created for context 0x17 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x152dd50) 
 fixme:mscoree:GetRealProcAddress ("InitializeFusion", 0x120dd50) 
 fixme:thread:SetThreadStackGuarantee (0x33fc78): stub 
 fixme:shell:URL_ParseUrl failed to parse L"System.EnterpriseServices" 
 fixme:shell:URL_ParseUrl failed to parse L"System" 
 err:ole:CoGetClassObject class {ecabb0c8-7f19-11d2-978e-0000f8757e2a} not registered 
 err:ole:CoGetClassObject no class object {ecabb0c8-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1 
 err:ole:CoGetClassObject class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered 
 err:ole:create_server class {6eb22881-8a19-11d0-81b6-00a0c9231c29} not registered 
 fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
 err:ole:CoGetClassObject no class object {6eb22881-8a19-11d0-81b6-00a0c9231c29} could be created for context 0x15 
 fixme:process:FlushProcessWriteBuffers : stub 
 err:rpc:I_RpcGetBuffer no binding 
 err:rpc:I_RpcGetBuffer no binding 
 fixme:imm:ImmDisableIME (-1): stub 
 err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded 
 err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded 
 fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub 
 fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub 
 err:ole:CoUninitialize Mismatched CoUninitialize 
 err:ole:CoUninitialize Mismatched CoUninitialize 
 fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub! 
 ------------------------------------------------------ 
 Note: command 'wine dotnetfx.exe' returned status 67.  Aborting. 
 ------------------------------------------------------ 

```I have tried downloading the file and installing through WINE that way, but I get a "repair/remove" option. If I say repair, it says it finished its repair, but it doesn't really repair anything. So I tried removing the program and reinstalling, but still nothing. Now I have a ".wine" folder and a ".wine-old" folder.

I'll try completely uninstalling WINE, restart PC and attempt all again. But this is my fourth time trying this and no answers through google searching helps.

---

### Post by PaulInBHC on 2012-07-09
Over at WineHQ forums is a sticky post about problems with Wine and 12.04

Not sure if 1.5.8 fixes things.

I haven't had any luck with .Net in Wine.

---

### Post by Lightning Dragon on 2012-07-09
It is weird because I had it installed and working before, but the TiMidity problem kept me from logging in, so I had to install. :(

I'll check out the forum now. 

EDIT:

I don't have any of those bugs. It seems updating WINE made most of those problems...

---

### Post by madjr on 2012-07-09
hmm, I wonder if Rpg maker is worth the trouble.

I believe you can also try playonlinux for better wine compatibility:

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)


If you would like to try alternatives to rpg maker (am wondering if you just want to make a simple rpg as a hobby or become a **real game developer**?)

anyway you might like these:

"scratch":
[http://vimeo.com/29457909](http://vimeo.com/29457909)
[http://info.scratch.mit.edu/Support/Get_Started](http://info.scratch.mit.edu/Support/Get_Started)


Alice. use 2.0 (2.2 is not needed):
[http://www.alice.org/index.php?page=what_is_alice/what_is_alice](http://www.alice.org/index.php?page=what_is_alice/what_is_alice)

game editor:
[http://game-editor.com/Main_Page](http://game-editor.com/Main_Page)

rpg-game-maker-java (havent tested this)
[http://www.scorchsoft.com/tools/rpg-game-maker-java/](http://www.scorchsoft.com/tools/rpg-game-maker-java/)

python is very accessible too:
[http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers)
[http://ubuntuforums.org/showpost.php?p=12061185&postcount=10](http://ubuntuforums.org/showpost.php?p=12061185&postcount=10)

Html5 quick tutorial:
[http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/](http://www.lostdecadegames.com/how-to-make-a-simple-html5-canvas-game/)

for 3d:
[http://www.panda3d.org/](http://www.panda3d.org/)
[http://www.sandboxgamemaker.com/](http://www.sandboxgamemaker.com/)



not saying you should quit on RPGM, but Imho most of these are native and will be better alternatives in the long run as they'll teach you better **game developer skills**.

Cheers !!:o

---

### Post by Lightning Dragon on 2012-07-09
I deleted my .cache folder for winetricks and tried reinstalling, and it  'worked' but didn't at the same time. Said its already installed, but  it doesn't come up in the Uninstall WINE Software. I guess it moved this along a little bit, but still would like to install it again. 

I would love to use other programs, but I don't have a computer strong enough to run anything other than RM at the moment and I've put in a lot of work on my game. I am trying to get this to work for my brothers and some friends as well, because a lot of them bought the program but can't install [SIZE=1]*they do not have Windows and some won't want to buy Windows for this*[/SIZE].

I had the game running everything perfectly fine before TiMidity decided to kill my install. The only thing that didn't work with RM was playtesting with events on the map that had music in it.

I have never heard of PlayOnLinux, so I will try it now.

---

### Post by madjr on 2012-07-10
Ah I see.

yeah i used rpg maker back in the day, it was pretty nice for a while.

then I started creating different type of games (2d and some 3d) so I grew over it.

When you ready to move on I believe the ones I mentioned earlier might come in handy. Also **Scratch and Alice** are used in college for real program logic teaching and they are free so I would recommend those first. Most are low on resources too.

anyway I hope you can get it working with POL, specially since you paid for it is worth taking some time.

cheers!

---

### Post by Lightning Dragon on 2012-07-10
I will definitely check them out. I actually played around in Unity before, and loved it. Though I had no idea what I was doing, creating fields and mountains was absolutely amazing. I'll check those two out first while I'm waiting on the installer. :)

I was updating my Ubuntu, since it never did before, so I just got back to it. I deleted my .cache for winetricks again, but did not run anything yet. Then I went into home>username>.wine>drive_c>windows and then deleted the Microsoft.NET folder, though I suppose I shouldn't have (but I made a backup just in case), and then I went and ran Winetricks and installed Gecko and Mono (finally!), and then still got the "Microsoft.NET already installed on this computer" error and went to install the RM system anyways, just to see if it works.

It worked like a charm. I'll test out if putting the folder back ruins everything. Running WINE removes those "x" buttons again though, so its kinda annoying, but oh well.

Now its just TiMidity or finding a way to play MIDI files, and I can't seem to find something for WINE or Ubuntu to support the sound files. That's the only thing in the way, and OGG files.

---

### Post by PaulInBHC on 2012-07-10
Try audacity. Free cross platform sound editor. Not sure that is what you are looking for.

---

### Post by Lightning Dragon on 2012-07-10
I'm looking for a way to play back MIDI files. I've been searching it up, and only three things can do it. But I can't find a site explaining how to properly install and setup TiMidity, since my last attempt failed (or it was because of I upgraded by updating instead of freshing installing).

EDIT:

Does PlayOnLinux need a Windows installed on the the computer, or can it operate without Windows? Because if its works me, then it might not work for Ubuntu only users... :(

---

### Post by madjr on 2012-07-10
> **Lightning Dragon said:**
> I'm looking for a way to play back MIDI files. I've been searching it up, and only three things can do it. But I can't find a site explaining how to properly install and setup TiMidity, since my last attempt failed (or it was because of I upgraded by updating instead of freshing installing).

was this the instructions you used for timidity?

[https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo)

> 

EDIT:

Does PlayOnLinux need a Windows installed on the the computer, or can it operate without Windows? Because if its works me, then it might not work for Ubuntu only users... :(

it does not need windows, it just setups and configures wine easier for you, and some game/apps, but if you already did that, then you probably dont need it now.

---

### Post by Lightning Dragon on 2012-07-10
I did not find that link! Thank you! 

The file it gives for download is broken ('eawpatches'), and I can't seem to find it in the Synaptic Packager Manager or the Software Center so I can't continue setting up TiMidity or the sounds.  :(

EDIT:

Finished trying PlayOnLinux. It crashes if I attempt to play any music, so it has the same audio problems.

---

