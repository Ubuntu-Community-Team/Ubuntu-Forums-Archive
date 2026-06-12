---
title: "Age of Conan"
date: 2008-05-03
forum: Wine
---

### Post by myname on 2008-05-03
Well, after messing around trying to get the zip file unzip, I resorted to installing the Age of Conan beta client on my underpowered laptop.  The game installed fine, as I can even load up the slideshow.  

I connected my laptop to my home network, copied the files to my linux box(like I did for WoW), updated wine to the latest release, and then performed the following:

```

opened a terminal
cd games/conan
wine ConanPatcher.exe

```

The game starts to load ever so briefly, and then I get a popup that says:
> 
Unable to locate the client installation folder.  Please confirm the following path exists and is accessible.

c:\games\conan\


This was the directory from my windows box.  Any way to change it to ~/games/conan?

Has anyone else tried getting Age of Conan to work?

--Kevin

---

### Post by cb951303 on 2008-05-03
> **myname said:**
> Well, after messing around trying to get the zip file unzip, I resorted to installing the Age of Conan beta client on my underpowered laptop.  The game installed fine, as I can even load up the slideshow.  

I connected my laptop to my home network, copied the files to my linux box(like I did for WoW), updated wine to the latest release, and then performed the following:

```

opened a terminal
cd games/conan
wine ConanPatcher.exe

```

The game starts to load ever so briefly, and then I get a popup that says:


This was the directory from my windows box.  Any way to change it to ~/games/conan?

Has anyone else tried getting Age of Conan to work?

--Kevin
 why don't you just move conan files to /home/$userName/.wine/drive_c/games/conan ??

---

### Post by myname on 2008-05-03
I will try that.  THe reason they are not there now, is because I keep all my games in ~/games/<game name> folders.  It's just the way I have always done it (yes, former windows person).

I will also try installing the game from the original files too, to see if that helps.

thanks for the reply.

--k

---

### Post by cb951303 on 2008-05-03
> **myname said:**
> I will try that.  THe reason they are not there now, is because I keep all my games in ~/games/<game name> folders.  It's just the way I have always done it (yes, former windows person).

I will also try installing the game from the original files too, to see if that helps.

thanks for the reply.

--k

actually you link the directory to ~/.wine/drive_c

```
 ln -s ~/games/conan ~/.wine/drive_c/games/conan 
```

PS: make sure you create the dir ~/.wine/drive_c/games first ;)

---

### Post by schtufbox on 2008-05-03
I managed to unzip the beta in linux, but i had to get winzip 9 (winzaip 11 didn't work properly) and unzip using that in Wine. Installed the game, but it didn't work anyway, can't remember errors, and I uninstalled it since and let a friend use my key :p

---

### Post by endymon on 2008-05-03
This is the error I get when trying to start AoC.
If anyone have some tips what to do I'll happily try them out !

************
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
err:d3d:CheckTextureCapability Unhandled format=unrecognized
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x8353f588) : stub
fixme:faultrep:ReportFault 0x7f21e174 0x0 stub
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0xf7cf854c
************************

---

### Post by myname on 2008-05-03
Since the game is so new, when posting errors, or questions, can we post as much info as possible, so everyone can benefit.  IE, how you start the game, what version of WINE, version of UBUNTU, etc.

when I made the link to ~/.wine/drive_c/games/conan and then started conan with the following:

wine ConanPatcher.exe

I get the following:

```

~/games/conan> wine ConanPatcher.exe
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
Proxy: "":0
Files:0/0 (0.0/0.0 MB)  Idle
failed to open index file RDB/le.idx
failed to open index file RDB/le.idx.previous
ImportXML: could not parse xml: Error document empty. (line=0,0)
Resource 1030002:0 does not exist in any available RDB sources.
Loading category 14000 failed with errorcode: -99.
LDB: Category 14000 failed to load.
Memory in use[0 ]
Resource 1030002:0 does not exist in any available RDB sources.
Loading category 14000 failed with errorcode: -99.
LDB: Category 14000 failed to load.
Memory in use[0 ]

```

and then an OK dialog pops up with a red X in it, no text.

any ideas?

--Kevin

---

### Post by ajackson on 2008-05-04
> **myname said:**
> Since the game is so new, when posting errors, or questions, can we post as much info as possible, so everyone can benefit.  IE, how you start the game, what version of WINE, version of UBUNTU, etc.
Don't preach if you don't do it yourself :)

> any ideas?
What windows version have you got it set for? If it is XP try 2000 and vice versa (those seem the two most stable), you could try vista as at least one application behaves only when vista is used.

The first fixme might be the killer here as it's only a stub but what follows may rely on that function doing it's job.

Is there a download link for AoC (it is in open beta now isn't it?)

---

### Post by myname on 2008-05-04
I'm running Ubuntu Herdy with the latest version of wine.  I will try the other compatibility modes in wine to see if that helps.

--k

---

### Post by Thoralex on 2008-05-10
Anyone got this working yet?
I just installed aoc and the patcher seems to be workingb (it's downloading something) but the patcher window is completely empty. Anyone know what the problem can be?
Oh and i'm running kubuntu 8.04 kde 4, q6600 2.4ghz core 2 quad, 2gb ram, nvidia 8800gt.

---

### Post by myname on 2008-05-10
did you install the game  under WINE, or did you copy over an installed on windows version of AoC?

I can't get the updater to work, per the message/error in my above post.  How did you get that far in the installation?  Inquiry minds want to know.

--Kevin

---

### Post by Thoralex on 2008-05-11
I unzipped the download in my laptop then copied it via an external drive to my home folder and installed it with wine. the installer was a little hard to get running but but starting two of it at the same time got it running and then ran perfectly.The game took a long time to install tho, 2+ hours
I get that message when trying to run simpleconfig.exe, but not wen running the patcher.

The update manager seems to be done (for now) but it's still all black, anyone know a solution to that?

---

### Post by myname on 2008-05-11
a solution I had to the black screen (in windows), was to run simpleconfig and move the Video down 2 settings (if it was on 1280x1024, I moved it back to 1024x768) then relaunch the game.  It would launch, and after the game was running I would put it back to 1280.  Though, this worked in windows, and I can't get that far to try it in linux.  :(

---

### Post by myname on 2008-05-13
bump...

has anyone had any luck?  I'm stumped and I would hate to install a new drive and windows to play.

--kevin

---

### Post by dokdoom on 2008-05-13
I am interested in this as well. Unless my googlefu is weak this is the only thread not over a year old with any information of AoC and wine. Hopefully everyone is as lucky as I was and will find this thread when looking for help.

---

### Post by myname on 2008-05-14
hopefully with the pre-release launching this weekend, and the games release next tuesday, we or someone can get it running in wine fairly quickly.

--Kevin

---

### Post by toyota_f1 on 2008-05-19
I'm going to give this a shot again today with my Hardy install and see if I can get anywhere.

Hardy 64 Bit
Wine 0.9.59
AMD 5000+ BE (OC to 3.2 GHz)
4 gigs of DDR800
ATI HD 3870

---

### Post by dokdoom on 2008-05-19
Awesome, let us non EA know how it goes.

---

### Post by toyota_f1 on 2008-05-20
> **dokdoom said:**
> Awesome, let us non EA know how it goes.

Poor. :)

But it was only a quick try.  I'm hoping I have more time tonite.

---

### Post by dokdoom on 2008-05-22
I read on the AoC wine page that things weren't looking good. Only because 3 people have documented it won't install properly. Or should I say they can install and patch but beyond that the game won't load. Once the main release comes hopefully we'll have some good documentation.

---

### Post by raba1der on 2008-05-23
I'm also trying to get AoC to run under wine. I'll try to provide more info if needed. 

Ubuntu 8.04 32bit running on a AM
Nvidia 8600GT running nvidia restricted drivers
wine 1.0rc1

Installing seemed to go fine. Just inserted dvd1 and ran wine setup.exe. Install continued trough disc 1. Had to eject drive by running "wine eject d:" when it asked for disc 2. (you can find out what letter your drive is labeled by running winecfg and checking the drives tab) Installation continued and seemed to complete without errors. Then I tried to run AoC.



and got the following output: 

>wine AgeOfConan.exe 
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"c:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:module:import_dll Library XINPUT1_3.dll (which is needed by L"C:\\Program Files\\Funcom\\Age of Conan\\AgeOfConan.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Funcom\\Age of Conan\\AgeOfConan.exe" failed, status c0000135


running wine ConanUpdater.exe brings up the wine desktop, but no actual content in the updaterwindow. The terminal spams lots of text. incl: 

fixme: xrender:X11DRV_AlphaBlend not a dibsection
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
[HTTPManager] [http://msgs.ageofconan.com/eula.php?UniverseName=AoCLiveEU&Language=en:](http://msgs.ageofconan.com/eula.php?UniverseName=AoCLiveEU&Language=en:) failed to connect

---

### Post by raba1der on 2008-05-24
Vanilla Hardy 8.04 32bit
Wine 1.0-rc2 with disabled audio in winecfg
Nvidia 8600GT videocard running the latest restricted drivers autodownloaded by Hardy.

I've been testing a little and come a little closer to Hyboria I hope :)

I downloaded the XINPUT1_3.dll file from the net and put inside the root folder of AoC. When I then try to run AoC by 

```

user@host:~/.wine/drive_c/Program Files/Funcom/Age of Conan$ wine AgeOfConan.exe 
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by L"c:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
raba1der@ardbeg:~/.wine/drive_c/Program Files/Funcom/Age of Conan$ fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:reg:GetNativeSystemInfo (0x33e868) using GetSystemInfo()

```

the wine desktop pops up and the updater starts. I still can't see anything in the updaterwindow, probably caused by the following error: 

```

fixme:xrender:X11DRV_AlphaBlend not a dibsection

```

If I randomly click within the lower middle part of the updaterwindow that I can't see the content of It seem to be launching the AoC client, but then it just crashes.

```

fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:reg:GetNativeSystemInfo (0x33e584) using GetSystemInfo()
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33ebbc,0x00000000), stub!
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x9ba9630) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x9ba9630) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0xa7448a0
fixme:faultrep:ReportFault 0x33e178 0x0 stub
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```

Hope this can be useful for someone, because I'm kinda out of ideas what to do next.

---

### Post by ajackson on 2008-05-24
Have you tried what it suggested?

```
err:module:find_forwarded_export function not found for
forward 'd3dx8.D3DXGetImageInfoFromFileInMemory' used by
L"c:\\windows\\system32\\d3dx9_36.dll". If you are using builtin
L"d3dx9_36.dll", try using the native one instead.
```

---

### Post by raba1der on 2008-05-24
I could'nt find any file with that name inside the windows folder at all. I downloaded a version of it from [www.dll-files.com](www.dll-files.com) and put inside the AoC folder and tried starting AoC, but no change. Also moved it to windows\system32 folder, without any change. I'm not sure however what they mean by "native" and if there is another version of it I might need.

---

### Post by Rplus9 on 2008-05-28
Install was a breeze, I chose to copy the install DVD contents onto disk for much faster install.

When I execute the "Update Management"  it gives me

"...requires 32-bit display depth
please change your settings and try again"

quick and dirty, is there any way to do change the display depth?
I've read the other posts about errors and "pseudo-32-bit windows conspiracy" I just want to know how it's changed.

---

### Post by Svopp on 2008-05-28
i installed AoC in windows xp.

Im running wine RC 1 ubuntu 8.04 64 bit, 8600 GT standard recommended rescricted drivers by ubuntu... thing ..

Iv copied some additional dll files into the wine system32 ... but i get this error

________________________________________________________
wine AgeOfConan.exe
err:winedevice:ServiceMain driver L"wzghui" failed to load
err:module:import_dll Library XINPUT1_3.dll (which is needed by L"Z:\\media\\disk\\Programmer\\Age of Conan\\AgeOfConan.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\disk\\Programmer\\Age of Conan\\AgeOfConan.exe" failed, status c0000135
________________________________________________________

---

### Post by pedro_orange on 2008-05-28
Guys, look at the winehq stance on AoC:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12101](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12101)

Installs?: Yes
Runs?: No
Rating: Garbage

Don't expect it work in WINE.
Get yourself a Windows partition for the time being.

---

### Post by ajackson on 2008-05-28
> **pedro_orange said:**
> Guys, look at the winehq stance on AoC:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12101](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12101)

Installs?: Yes
Runs?: No
Rating: Garbage

Don't expect it work in WINE.
Get yourself a Windows partition for the time being.
Very defeatist attitude, if everyone followed that style only the games rated platinum would ever work under wine.

---

### Post by Rplus9 on 2008-05-29
yeah I haven't bought the game yet, borrowed a copy to see if I could get it to install.  I didn't expect it to run right out of the box, good stuff never does, but I figure I could keep pinging it to let those smarter than me know that us lesser geeks would like it.  As stuff evolves I might be able to test and add info to the pool.

---

### Post by SBFC on 2008-05-29
I copied over my windows install and gave it a run. Looks as though the patcher is having trouble connecting.
```

[2008-05-29 07:34:16,0] [HTTPManager] http://aoc-us-control.live.ageofconan.com/
upm/AoCLiveUS/PatchInfoClient.txt: failed with error 403
[2008-05-29 07:32:28,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:32:33,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:32:38,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:32:43,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:32:48,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:32:53,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:32:58,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:33:03,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s
[2008-05-29 07:33:08,0] [HTTPManager] Files:1/2 (0.0/0.0 MB)  Speed:0.0 KB/s

```

Or rather, the server won't grant me access...

---

### Post by ajackson on 2008-05-31
Right to get it to the point where it starts the game and crashes.

- download d3dx9_36.dll & xinput1_3.dll and put them in the AoC directory
- start ConanPatcher.exe (I stick WINEDEBUG=-xrender to get rid of some of the spam)
- wait until it stops updating (could take a while)
- next you need to click a certain area of the AoC window, if you have a terminal open with a fair amount of text the window will have a snapshot of that, the area you need is dead centre about 4 lines of text up from the bottom (you need to wait as it is a cancel button until updating has finished)
- If this is your first run wait about 20 20 seconds then move the mouse down and left a bit and click (it is an accept button for the EULA)
- it should now start then crash

I have found that it passes these parameters to AgeOfConan.exe
```
-noconsole -clienthash (md5 of AgeOfConan.exe) =key (16 chars changed everytime under windows)
```

---

### Post by wylfing on 2008-06-06
> **raba1der said:**
> I could'nt find any file with that name inside the windows folder at all. I downloaded a version of it from [www.dll-files.com](www.dll-files.com) and put inside the AoC folder and tried starting AoC, but no change. Also moved it to windows\system32 folder, without any change. I'm not sure however what they mean by "native" and if there is another version of it I might need.

I don't have this game yet, so I'm kind of commenting blind. There are two kinds of libraries used by wine: native and builtin. The builtin libraries are the ones created by the wine team. The native libraries are actual DLLs from a Windows installation.

To change from one to the other, fire up winecfg and click the Libraries tab. Select a library from the list and specify that it should use the builtin or native version. I don't think it matters whether you put a native DLL in the application directory or system32, but it's been a while since I messed with that so I could be wrong.

---

### Post by duncan_nz on 2008-06-10
Please keep us informed of any updates!

I'd love to get AoC going in wine, then i can ditch xp

---

### Post by duncan_nz on 2008-06-11
I tried to run it, but it said that it doesn't support shader model 2.0...

---

### Post by wylfing on 2008-06-12
> **duncan_nz said:**
> I tried to run it, but it said that it doesn't support shader model 2.0...

Are you sure it isn't your hardware that doesn't support Shader 2.0?

---

### Post by duncan_nz on 2008-06-15
My 8800gt can support up to shader model 4.0 and Dx10...

---

### Post by keaton_guy on 2008-06-16
Please keep up the work guys, I for one am hoping to get this game for linux and I'm sure there's others out there lurking in this thread hoping you guys get it working

---

### Post by thenameisgabe on 2008-06-18
i'm lurking. this game is the only thing keeping me from uninstalling windows altogether.

---

### Post by duncan_nz on 2008-06-19
> **thenameisgabe said:**
> i'm lurking. this game is the only thing keeping me from uninstalling windows altogether.

Same here, I hate being tied to ms, just for the sake of one game that I would truly like to see going on linux :)

---

### Post by fain on 2008-06-20
I also would like this game to be ported.....oops made compatible with wine :P

Truth is this isnt the only game that is keeping me from windows but it is a big reason I reboot into my wintendo64 all the time. I feel so insecure there....

---

### Post by wylfing on 2008-06-20
I don't have Windows at all. Wine is the only way I play anything that's not native, although I am often content with Angband :)

---

### Post by sendHalp on 2008-06-21
From what I  have been seeing based on user errors posted, wine is having difficulty with D3D function calls.  From my experiences wine likes to deal with opengl a heck of a lot more.  Dx10 may not be implemented far enough (or at all) in wine to be able to handle some of these graphic libraries or functions natively.

Please also note that this game is brand spanking new and may not necessarily run correctly in windows either.

---

### Post by ~Pyo~ on 2008-06-21
> From what I have been seeing based on user errors posted, wine is having difficulty with D3D function calls. From my experiences wine likes to deal with opengl a heck of a lot more. Dx10 may not be implemented far enough (or at all) in wine to be able to handle some of these graphic libraries or functions natively.

Please also note that this game is brand spanking new and may not necessarily run correctly in windows either. 

Well as far as I know, the game engine isn't stabilized even under Windows, and with the short amount of time given to Funcom for the release, they haven't done the DX10 engine either.

---

### Post by SBFC on 2008-06-22
> **~Pyo~ said:**
> Well as far as I know, the game engine isn't stabilized even under Windows, and with the short amount of time given to Funcom for the release, they haven't done the DX10 engine either.

While there are some bugs, the game does run really well in windows. Quite imporessive graphically as well. I run settings on low and the graphics still look good. Can't imagine what they'd look like on high.

---

### Post by azeroth48 on 2008-07-07
Its advised by funcom to run the game in high graphics mode as it runs better then low

---

### Post by shivans on 2008-07-08
Still not played this game yet as I don't want to reinstall Windows back on my PC. 

The day it becomes playable in Wine is the day I head down to Game for a copy.

---

### Post by quarteryardline on 2008-09-24
[For Age of Conan Cheats, ](http://www.exploitsrus.com/aoc.html) [Age of Conan Dupes, ](http://www.exploitsrus.com/aoc/dupes.html) [Age of Conan Bots, ](http://www.exploitsrus.com/aoc/bots.html) [and Age of Conan Guides click here](http://www.exploitsrus.com/aoc/guides.html)

---

### Post by blastfemur on 2009-07-17
Anyone have an update on this?
I actually stopped playing AOC for awhile and just received my 'free 14 days' and signed up. Unfortunately (depending on how you look at it - fortunately), in the interim I switched to Linux (Ubuntu).
I really believed that, after a year plus that AOC has been out that there would be no problem with it working through Wine.
*shrug* ... I've been wrong before though ... probably happen again :)

---

### Post by gordtulloch on 2009-11-13
I just got the same "come back" message - I've moved from Windoze to Ubuntu 9.04 64bit so I'll try this on the weekend on both Cedega and Wine.

The Cedega page isn't hopeful:

[http://www.cedega.com/gamesdb/games/view.html?game_id=4535](http://www.cedega.com/gamesdb/games/view.html?game_id=4535)

However given I got Everquest to work on Wine when Cedega failed gives me some hope. In fact looking at the [www.winehq.org]("http://www.winehq.org") listing for the game looks really positive:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12101&iTestingId=45659](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12101&iTestingId=45659)

I'll post back here with my results.

Regards,
  Gord

---

### Post by gordtulloch on 2009-11-14
The install in Wine works fine, except for some reason Ubuntu absolutely refused to let me eject the DVD with "wine eject E:" - I finally ended up copying the DVDs to a directory on my hard drive and installing from there, which worked fine.

Now my problem is when I run the patcher it says "You need to upgrade your version of Direct X. Please download the DirectX Redist [November 2008] from [url]"

I guess it's time to dig into wine and see what version of DirectX it supports...

Regards,
  Gord

---

### Post by gordtulloch on 2009-11-14
Ah, found out you can just install DirectX of the right vintage, see instructions here:

[http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html)

The app is now patching, which as I recall is lengthy so I'll post what happens next!

Regards,
  Gord

---

### Post by gordtulloch on 2009-11-14
The game functions after patching but the frame rate is low even in 1024x768 windowed mode. Models are a bit iffy as well, since armor is popping in and out. I'd say unplayable now but I'll report this on winehq.org and see if someone has a solution...

Regards,
  Gord

---

