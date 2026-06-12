---
title: "steam and wine help"
date: 2008-05-12
forum: Wine
---

### Post by North_Star_ on 2008-05-12
I'm pulling my hair out trying to get half life2, css, etc. to run in steam, hell I can't even get steam to run right. I'm doing something wrong. I have to be, I've installed wine-through terminal, deb(?) self installer thing, through package manager and symtec manager, and the add programs function. I have also tried wine-doors through various methods as well. Wine always seems to install fine but nothing installs right through it. Wine doors had the same results. IE6 would show just a white screen. When trying to play css or any game through steam it woulds say i need to install dx9c. I did install the ?Tahoma? font. I'm getting ready to try again. Someone here mentioned some other non wine programs but I didn't read much on em.

I have followed several guides from this forum and other places. Nothing works for me, or i don't work for it.

all i have installed now is wine ver 0.9.59

My errors, I used to get a "IE needs installed when trying to start up css through steam. (don't know how to through terminal)

I fixed that, kinda. Still can't see the web pages in steam or anything but my games list.

now i get a direct x error. says i need dx9.0c.

That would be where I'm stuck. I read your not supposed to install 9.c because it screws up wine. some mention replacing dll files, i don't have a working windows PC right now, there method involved pulling win files and copying them to wine. Well any opinions? if case i might have some well known hardware incompatibility, although I'm only thinking vidcard. I know, I'm reaching for answers at this point. never know.

abit at32x crossfire Skt 939
165 opteron
ati x1900xtx
corsair 2x 1gig ddr 400
Seagate perpendicular hdd



I just realized I don't have wine-dev files installed. Might that be a problem?

---

### Post by cogadh on 2008-05-12
You only need the wine-dev files if you intend to compile Wine yourself. They are not needed to simply use Wine.

To get Steam working properly, all you really need to do is install the Gecko HTML rendering engine and Flash player in Wine, then install Steam. Start with a clean .wine directory, then open a terminal and run this to install Gecko:
```
wine iexplore http://www.winehq.org
```
Follow the prompts, then exit out of iexplore once the WineHQ web page is displayed.
Next download the Flash player executable from Adobe, cd to the directory where you downloaded it and install it in Wine like this:
```
wine install_flash_player.exe
```
Then cd to the directory where you have the Steam installer and install it like this:
```
wine start SteamInstall.msi
```
The install will take a while as it updates Steam files. Once it is finished, you should go into Steam's settings and turn off the "Run Steam when Windows starts" option and the "Enable Steam Community in-game" option (that second one might not be required anymore, I still do it out of habit), then you can install HL2, CS:S, etc. as you normally would in Steam. 

Once your games are installed, quit out of Steam. In the terminal, cd to the directory where Steam is installed and launch it again with Wine's debug settings turned off:
```
cd .wine/drive_c/Program\ Files/Steam
WINEDEBUG=-all wine Steam.exe
```
You should be abe to launch HL2, CS:S, etc. normally now.

NOTE - Because you have an ATI video card, there may be additional Wine configuration items that are required to make things work perfectly. As I don't have an ATI card, I can't say for certain what those might be.

EDIT - Almost forgot, to launch HL2 without launching Steam first, run this:
```
WINEDEBUG=-all wine steam.exe -applaunch 220
```
For CS:S, run this:
```
WINEDEBUG=-all wine steam.exe -applaunch 240
```
For any other Steam games, just replace the applaunch number with the appropriate application ID number from here:
[http://developer.valvesoftware.com/wiki/Steam_Application_IDs](http://developer.valvesoftware.com/wiki/Steam_Application_IDs)

---

### Post by North_Star_ on 2008-05-12
thanks i'll try that, fast reply. i just tryed this install [http://fedorasolved.org/gaming-solutions/installing-steam-using-wine](http://fedorasolved.org/gaming-solutions/installing-steam-using-wine)

do you have to start games through terminal?

I now can see the web pages in steam but i still get the direct x error. I'm not sure if ultimate doom is compatible but i was getting the same error with css. Still waiting for that to download. Any ways when i try to launch any game in steam i get this error "The lastest version of Microsofts direct x is required to play the game" then theres a link to a download site. Is there a fix to this or do i need to start over again? also still can't see any web pages in wine iexplorer
 

thanks again

---

### Post by Sleaka J on 2008-05-12
While asking here isn't much of a problem, you'd be best checking out:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)

and follow those instructions on how to get Steam and it's games working. The source is always better.

---

### Post by cogadh on 2008-05-12
Those WineHQ and Fedora instructions are quite out of date now and don't reflect what you need or don't need to do with more current versions of Wine and Steam.

You shouldn't be prompted to install DirectX at all (in fact, it is strongly recommended that you don't even try to install it). The only way that might happen is if you don't have the restricted drivers for your video card enabled, which will prevent Wine from being able to use its own DirectX.

Starting games through the terminal is not required, but it is recommended, at least until you have Steam and everything up and running normally. If you are having problems running a particular game, running it from the terminal without the "WINEDEBUG" option allows Wine to output error information to the terminal, which can help troubleshoot problems. Once you have everything configured and running, then you can just use the menu shortcuts that Wine creates.

---

### Post by North_Star_ on 2008-05-12
thank you, i had to uninstall everything and did it your way. You have know idea how much you made my day, although i'm still having abit of trouble. I was unable to install flash player but I used a fix I used earlier. Now I'm able to start up both half life 2 and css but all i reach is the loading screen. Then the game (eather of em) just shuts down. The loading screen stays up for about 15-20sec then just crashes. I mean the initial main menu load screen.

what do you think, i've looked to see if there were issues with my card and couldn't find anything

---

### Post by cogadh on 2008-05-13
Two things, one to verify video card functionality, the other to see if Wine is getting any errors. Open a terminal and run this:
```
glxinfo | grep direct
```
If it comes back saying "Direct Rendering: No", then we know the problem is your video card (specifically the restricted driver). If comes back saying "Direct Rendering: Yes", then everything as far as the video card is concerned should be fine. If that is the case, launch HL2 like this:
```
wine steam.exe -applaunch 220
```
Let it crash, then copy the contents of the terminal into a reply here. There may be a clue in Wine's error output that can point us in the right direction. Make sure you either use the forum [code] tags for the copied text or you turn off smilies in the reply post. Just pasting the text into a new post will produce a whole bunch of "smilies" and the forum may not let you submit the reply due to too many images.

---

### Post by North_Star_ on 2008-05-13
I have direct rendering
when i run wine steam.exe -applaunch 220 i get this error

louie@louie-desktop:~$ wine steam.exe -applaunch 220
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\steam.exe": Module not found
louie@louie-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

I can run doom 2 and ultimate doom. When i try any other the game, it starts then once in the intial load screen it crashes

---

### Post by cogadh on 2008-05-13
Ah, the preloader problem with Hardy. Here's the fix for that:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by kforum on 2008-05-14
this is what i get:

fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:exec:SHELL_execute flags ignored: 0x00000500
[email]name@pc:~/.wine[/email]/drive_c/Program Files$ fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:advapi:LookupAccountNameW (null) L"name" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"name" 0x13f890 0x33f7fc 0x13c368 0x33f800 0x33f7f4 - stub
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 2 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:advapi:SetEntriesInAclA 1 0x33fe68 (nil) 0x33fe60
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Steam" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 1 0x33fe68 (nil) 0x33fe60
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) (nil) (nil)
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:dsalsa:CheckXRUN Unhandled state: 0
wine: Unhandled page fault on write access to 0x001c0000 at address 0xf7d3b077 (thread 0036), starting debugger...
err:ntdll:RtlpWaitForCriticalSection section 0x19bfa4 "dsound.c: DirectSoundDevice.mixlock" wait timed out in thread 0031, blocked by 0036, retrying (60 sec)
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set


i used ur method after trying to get it installed form my OB cd...
it ran ok, and installed it i suposed, but then crashed it seemed... so i ran it again to 'repair' teh install and got that, same thing when it crashed.

any ideas?

---

### Post by cogadh on 2008-05-14
Looks like you have an audio issue. Not really surprising, since Hardy uses PulseAudio and Wine's ALSA driver does not get along with PA's ALSA plugin. Try changing your Wine audio driver to OSS.

---

### Post by North_Star_ on 2008-05-14
i tried the fix on link you provided, it doesn't work. Look, I can't figure out how to "CD" directory. I can get to cd /home/username/wine but then I don't  know what or how to sart games. I'm tring to play css, hl2,hl, tf2,etc. Games still crash on start up, well Half Life source is hanging on load but it might as well crash


so far i have working
doom
doom2
ultimate doom
quake
quake 2
counter strike

looks like it's just source games crashing, i tried to run GTA 3 but that won't even load up

---

### Post by cogadh on 2008-05-14
After applying the preloader fix, you need to reboot the PC for it to take effect. 

As for cd-ing to a directory, copy this into the terminal to cd to Steam's directory:
```
cd .wine/drive_c/Program\ Files/Steam
```
The to run a Steam game just do this (this example is HL2):
```
wine steam.exe -applaunch 220
```
Other Steam games have specific "applaunch" numbers that can be found on Steam developer Wiki page I linked to in my first reply. All you need to do is use the same command and change the number to match the game you are trying to run.

---

### Post by North_Star_ on 2008-05-14
i did the fix and rebooted, why the \ instead of /, does \ mean to end

anyways heres the error i get when trying to run hl2 from terminal like you showed me. bit long, sorry not sure what is important. Oh i have an ati x1900xtx, Apparently there are problems with the current drivers not sure how new that is though

---

### Post by North_Star_ on 2008-05-14
well heres the end of it

fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1cc4f258) : pBox=0x33e344 stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x142140) Event query: Unimplemented, but pretending to be supported
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!

---

### Post by cogadh on 2008-05-14
The "\" is an escape character. It tells the terminal to include the space between "Program" and "Files", which it would otherwise assume was the end of the cd command.

Well, the errors you posted are actually quite normal. The "fixme" messages are just developer notes about incomplete or unimplemented functions in Wine. Most of the time, you can't do a thing about them and most applications (especially games) run in Wine will get a few of those, but still work anyway. I assume there was more output than that, did any of the messages start with "err"? Those are the lines we really care about.

The ATI drivers are known for being difficult to work with (which is why I have an Nvidia card). I'm afraid my area of expertise does not extend to that. If this is an ATI related problem, I'll have to let someone else help with it.

BTW - When you post terminal output, use the [forum [code] tags](http://ubuntuforums.org/misc.php?do=bbcode), that allows the output to be displayed exactly as it was in the terminal, without half of it being turned into "smilies".

---

### Post by North_Star_ on 2008-05-15
Well you got me this far and for that I'm very great full. THanks man, The more i read the more this is pointing to a driver error. Guess I have no choice but to wait and see if there is a fix. Well thanks again. Oh, one more question. How do I run games in dx8 mode. Since I can run older games I'm figuring maybe i can run source in a lower mode. I used -dxlevel80 and I tried -dxlevel81 as launch options for both hl2 and css. The game didn't crash like normally but it froze on load screen leaving me with no choice but to end the program.

---

### Post by Sleaka J on 2008-05-15
> **North_Star_ said:**
> Well you got me this far and for that I'm very great full. THanks man, The more i read the more this is pointing to a driver error. Guess I have no choice but to wait and see if there is a fix. Well thanks again. Oh, one more question. How do I run games in dx8 mode. Since I can run older games I'm figuring maybe i can run source in a lower mode. I used -dxlevel80 and I tried -dxlevel81 as launch options for both hl2 and css. The game didn't crash like normally but it froze on load screen leaving me with no choice but to end the program.

Try -dxlevel 81 -window

I end up with black screens upon startup with AA enabled, so try turning off any AA that is enabled (usually is by default).

---

### Post by North_Star_ on 2008-05-15
Just in case you reconize this. THis is all "ERR" sections when runing HL2
also I was never able to run "wine install_flash_player"
says moddule not found. That couldn't have anything to do with this could it?
I also just tried -dxlevel 81 -window, didn't work.

[HTML]/.wine/drive_c/Program Files/Steam$ wine steam.exe -applaunch 220
CellID: Fetching server list from CSDS. . .
CellID: CSDS returned 165 servers.
CellID: Connecting to 69.28.151.170:27031. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: Connect to 69.28.151.170:27031 took 114 MS
CellID: Nothing beat our old best time of 19 MS
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1a8c10)->(1 00000002 0x11c3cb8)
[/HTML]

[HTML]fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1a9238)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32c2dc,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x21dc00)->(1 00000002 0x11d3bb0)
[/HTML]
[HTML]from Loading the PBO test texture
 @ directx.c / 3413
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x142158) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x142158) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x142158) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x142158) Event query: Unimplemented, but pretending to be supported
err:alsa:ALSA_copyFormat calculated 50 bytes, capping to 40 bytes
fixme:wave:wodOpen unimplemented format: WAVE_FORMAT_ADPCM
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x142158) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x142158) Event query: Unimplemented, but pretending to be supported
[/HTML]

---

### Post by cogadh on 2008-05-15
You can get rid of these:
```
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
```
by installing the winbind package:
```
sudo apt-get install winbind
```
These ones:
```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
```
are due to Flash Player not being installed, but that only affects some of the advertising on the Steam store, not running games. Installing Flash Player should be easy, you just need to make sure you download the Windows version of it. When you go to the Adobe website, it will automatically present you with the Linux version, you need to click on the "Different operating system or browser?" link to get the Windows executable. Once you have it, just cd to the directory where you downloaded the file to and run "wine install_flash_player.exe".

---

### Post by kforum on 2008-05-30
2 things...

1: the whole -applauch method does NOT work, not for me anyways.
it still boots up steam.

2: half-life seems to no be working atm, with latest wine build.
it loads, then crashes.
for me at least, once again.

---

### Post by cogadh on 2008-05-31
> **kforum said:**
> 2 things...

1: the whole -applauch method does NOT work, not for me anyways.
it still boots up steam.
That is what it is supposed to do. Games purchased and installed through Steam use Steam as their copy protection check. You cannot run Steam games without also having Steam running (well, there are ways to do it, but that is a legal grey area that I won't really discuss here). Having the shortcut that uses the "-applaunch" option just allows you to skip a step and go straight to launching the game as soon as Steam is up and running without having to use Steam's "My Games" browser.
> 
2: half-life seems to no be working atm, with latest wine build.
it loads, then crashes.
for me at least, once again.
It would help if you could provide some details, like your hardware specs/configuration, Wine's terminal output, etc. We can't really offer any valid suggestions without any of the pertinent details.

---

### Post by ngrieb on 2009-07-09
I have a random question that I hope someone can answer. First here are my specs:

AMD Athlon 3000+
1 GB RAM
DLink DWL500 Rev. B (Atheros)
ATI Radeon X1650
Ubuntu 8.10 & WINE 1.01

When I run CS:S under wine with the pixel shader on my system slows way down (FPS like around 17-40 say). It still runs slowly when I play without the pixel shader as well (maybe around 45). 

I was wondering if this has to do with my graphics card or perhaps my wireless card (I found out that the Atheros chip for the wireless card was not very well supported)? Either way, WINE seems to freeze sometimes during play even with no pixel shader on. 

Is there any way to boost my FPS performance?

---

