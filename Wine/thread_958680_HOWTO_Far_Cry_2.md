---
title: "HOWTO: Far Cry 2"
date: 2008-10-25
forum: Wine
---

### Post by Sugi on 2008-10-25
HowTo: Far Cry 2



The installation went smooth.  I just loaded up Far Cry 2 within the explorer "wine explorer /desktop=..." (wine explorer /desktop=Far_Cry_2,1440x900 setup.exe) and I did not install PunkBuster or Desktop Shortcut.  The game may work with PunkBuster and Desktop shortcut, but I haven't tested that and I wanted to make sure the installation and the basics of the game worked first.

Then I loaded up the game, (wine explorer /desktop=Far_Cry_2,1440x900 /home/USR/.wine/drive_c/Program\ Files/Ubisoft/Far\ Cry\ 2/bin/FarCry2.exe) and I got a few errors about missing dlls.  And those are: d3dx9_38, gdiplus, iphlpapi, psapim, and xinput1_3.  So I applied them to them to the bin folder and I also applied a No-CD Patch because of SecuROM.  But After that, I loaded up Far Cry 2 again and it worked. :D





Shorten Version:

```
cd /media/cdrom0/ && wine explorer /desktop=DEFAULT,1440x900 setup.exe
```
Untick PunkBuster and Desktop Shortcut
use default installation path "Program Files/Ubisoft/Far Cry 2/"
Finish

After installation, use the dll files I uploaded within this thread "FarCry2.HOWTO.TheDLLp1.tar.gz" & "FarCry2.HOWTO.TheDLLp2.tar.gz".
and extracted them to the bin folder:

```
cd /home/USR/Desktop/
tar xvf FarCry2.HOWTO.TheDLLsp1.tar.gz && tar xvf FarCry2.HOWTO.TheDLLsp2.tar.gz
wget http://www.dll-files.com/dllindex/d3dx9_38.zip?0VEgWFWDkS
```
Extract the dll file form "d3dx9_38.zip?0VEgWFWDkS" to the "TheDlls" folder
```
cd TheDLLs && mv * /home/USR/.wine/drive_c/Program\ Files\Ubisoft/Far\ Cry\ 2/bin\
```

Load the Game:
```
cd /home/USR/.wine/drive_c/Program\ Files/Ubisoft/Far\ Cry\ 2/bin && wine explorer /desktop=Far_Cry_2,1440x900 FarCry2.exe
```

TWEAKS:
Within the Regedit:
wine regedit
[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"UseGLSL"="enabled" 

Enjoy

Troubleshooting:
 - FarCry2.exe
Make sure you are loading FarCry2.exe not the FC2Launcher, because the launcher isn't working at the moment.
 - Video Drivers are too old
I get this error "Your Video Drivers are too old..." when loading FarCry2.exe.  I hit OK and it loads the game.  I am unsure on how to fix this yet.


PS: I will continue to update this thread to fix any issues and slowness with the Game.



Spec:
Nvidia Card - 7700 GO
Wine 1.1.4 (Not Compiled)
Ubuntu Hardy Heron
Gnome i386




As always, 
Enjoy
Sugi

---

### Post by Jepperen on 2008-10-25
Nice! thank you for this guide! Hope i get the game with the mail on monday.

---

### Post by LokeTheDog on 2008-10-25
Hmm, doesn't seem to work for me. This is what I get:

fixme:win:EnumDisplayDevicesW ((null),0,0x90f6a8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:dxgi:CreateDXGIFactory riid {7b7166ec-21c7-44ae-b21a-c9ae321ae369}, factory 0x90f4bc partial stub!
fixme:dxgi:dxgi_factory_EnumAdapters iface 0x1bd6a8, adapter_idx 0, adapter 0x90f4d4 stub!

Which says nothing to me, but maybe someone can translate?

---

### Post by Sugi on 2008-10-25
LokeTheDog, are you running FarCry2.exe or FC2Laucher.exe?  Because I couldn't get the Launcher working for some reason.  Make sure you got your Video drivers updated and have those dlls in your bin folder.  I am using a Nvidia Card 7700 GO.  ATI cards are a pain in the butt to get working with Linux and Wine (at least for me and a lot of other people.)  Be sides from that, are you using a correct version and working copy of a No-CD patch?

Also, does anyone know how to enable frames per second within the game?  console key (~) comes up, but I don't know the command for enable FPS.

---

### Post by relaxedcrazyman on 2008-10-25
thx for the info, just wondering how is the gameplay working? like does it run smoothly or are their problems with it?

---

### Post by Sugi on 2008-10-25
relaxedcrazyman, it's kinda slow, but it's maybe my specs.  I am unsure. i am working on some kind of fix or workaround.  nice -20 could help, but it's just a crappy workaround.  I am working on the some regedits right now.  

for nvidia user try the following:
OffscreenRenderingMode = fbo
DirectDrawRenderer = opengl
VideoMemorySize = 512
Let me know if it helps or makes it worse. I am currently using OffscreenRenderingMode = fbo but It doesn't seem help much.

Please, if anyone knows how to enable FPS within the game Far Cry 2.  Let me know, I can test my FPS before.

---

### Post by lundman on 2008-10-26
Thanks for all the files, trying with Crossover on Osx, but alas, it ends with:
```

wine: Call from 0x102e26df to unimplemented function iphlpapi.dll.IcmpCreateFile, aborting

```

Thanks for the Howto though.

---

### Post by LokeTheDog on 2008-10-26
> **Sugi said:**
> LokeTheDog, are you running FarCry2.exe or FC2Laucher.exe?  Because I couldn't get the Launcher working for some reason.  Make sure you got your Video drivers updated and have those dlls in your bin folder.  I am using a Nvidia Card 7700 GO.  ATI cards are a pain in the butt to get working with Linux and Wine (at least for me and a lot of other people.)  Be sides from that, are you using a correct version and working copy of a No-CD patch?

Also, does anyone know how to enable frames per second within the game?  console key (~) comes up, but I don't know the command for enable FPS.

I am using a cracked (razor 1911) FarCry2.exe, I've got the files in the right places, I'm using Nvidia 8800 GT (later edition). I think I've got the latest drivers, not sure how to check that.

---

### Post by knurpht on 2008-10-26
anybody knows why i cannot download the tarballs? Have the game, would like to try on openSUSE

---

### Post by opsi on 2008-10-26
Hello, 
You don't have an issue with the MSVCR80.dll ? I install it by using winetool, but it doesn't work ... :-(
Someone can provide me help ?
Thx,
Opsi

---

### Post by Sugi on 2008-10-27
knurpht, Make sure you are logged in.  That's my only guess.

opsi, Try wget the MSVCR80.dll file and putting it also in the bin and let me know what happens after that.
wget [http://www.dll-files.com/dllindex/msvcr80.zip?0VEhOBZFgU](http://www.dll-files.com/dllindex/msvcr80.zip?0VEhOBZFgU)
and extracted it to the bin folder. (only the .dll file)

---

### Post by asdfoo on 2008-10-27
Installed and followed the instructions + set dxgi.dll to native for Wine 1.1.7.  

If I set OffscreenRenderingMode to fbo then the game does not launch, if I leave it as default the game starts, begins to load a level in story mode but then exits.

OpenGL version string: 2.1.2 NVIDIA 177.13, 8800 GTS.

---

### Post by asdfoo on 2008-10-27
> **asdfoo said:**
> Installed and followed the instructions + set dxgi.dll to native for Wine 1.1.7.  

If I set OffscreenRenderingMode to fbo then the game does not launch, if I leave it as default the game starts, begins to load a level in story mode but then exits.

OpenGL version string: 2.1.2 NVIDIA 177.13, 8800 GTS.


tried upgrading my drivers, still crashes with fbo and if i use backbuffer it runs out of memory while loading.  but if i put the game on very low setttings then it barely runs but there are issues with the graphics

oh well. will probably have to install windows to play this game properly

---

### Post by spwnt on 2008-10-28
```
spwnt@spwnt-desktop:~$ regedit
spwnt@spwnt-desktop:~$ cd /home/spwnt/.wine/drive_c/Program\ Files/Ubisoft/Far\ Cry\ 2/bin && wine explorer /desktop=Far_Cry_2,1440x900 FarCry2.exe
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x13a79ec,0x00000004,0x13a79e8) Unknown information class
fixme:exec:SHELL_execute flags ignored: 0x00000500
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x13a67d8): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x13a6724,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x613e50, 0x1385abc) stub
fixme:psapi:EnumPageFilesA (0x613e50, 0x13503d8) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x137eee0,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11c6,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x13bf894): Stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags
fixme:win:EnumDisplayDevicesW ((null),0,0x13befdc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:dxgi:CreateDXGIFactory riid {7b7166ec-21c7-44ae-b21a-c9ae321ae369}, factory 0x13bedf4 partial stub!
fixme:dxgi:dxgi_factory_EnumAdapters iface 0x1cc0b8, adapter_idx 0, adapter 0x13bee0c stub!

```

any ideas?

I'm running an AMD Core 3ghz 9800 GTX with 4 gigs of memory so i don't think it's my specs.

i downloaded all the DLL's and put them in the Far Cry Bin folder. I did the registry tweak. What to you mean by applying them? i'm a noob sorry.

could it have anything to do with the fact that I replaced the FC2.dll with the NOCD crack?

Should I put those DLL's in their proper place in windows system 32 etc?

---

### Post by spwnt on 2008-10-28
Update

> Installed and followed the instructions + set dxgi.dll to native for Wine 1.1.7.

that fixed my problem. Now my game is running, but with no sound. I know beggers can't be choosers, but has anyone managed to get sound working? Or know how to?

/edit/

pardon my double post I didn't see the edit button until after my second post.

Well I've gotten the sound working

though the game is crashing while it's loading up the level. i'm gunna keep  messing with it to see if i can fix it. .

/edit2/
Well I've got the game running now at currently all on medium hdr and bloom disabled. if you run the far cry 2 exe without the parameters you can run it full screen, though it doesn't seem to be able to work in any resolution other than 800x600 either way.

And the loader seems to work just fine for me.

---

### Post by haswig on 2008-10-28
Hi,

I also tryed to get the Game running with a mixture of this and the Howto at winehq. (they are pretty the same)
And it seems to run.
"Seem" , because i only see a black screen, but i hear the sound of the game. I started in Win to play so i know that the Game menu is loaded.

I think the problem is my Ati FireGl 5200.

I know ATIs sucks with gameing in linux, but has anyone of you got it to run on an ATI?


Whats the Parameter for playing it windowed? For now i did with winecfg.


edit: While search for windowed mode I found in GamerProfil.xml an entry ShowFPS maybe that helps.
      windowed -> Fullscreen="0"

---

### Post by Sugi on 2008-10-28
haswig, Actually the command is in my first post to make any game play in a emulated desktop aka windows mode use the following command
```
wine explorer /desktop=Windows_Mode,1440x900 FarCry2.exe
```

Also thanks for the tip on the section of "ShowFPS".  I ended up using a wine command to show the FPS though. If you are interested, the command is:  ```
WINEDEBUG=+fps
``` Put that command in front of your wine command as in: ```
WINEDEBUG=+fps wine FarCry2.exe
```

spwnt,  Look over this quote from the appdb.
> In your home directory, there is a folder called "My Games" or something similar. Open the "GamerProfile.xml" and edit some settings (etc: resolution can be changed here, not in the game - IT WILL CRASH)

Widescreen Resolutions:

ResolutionX="1440"ResolutionY="900"
ResolutionX="1280"ResolutionY="768"
ResolutionX="1280"ResolutionY="720"
ResolutionX="720"ResolutionY="480"

Standard Resolutions:

ResolutionX="1024"ResolutionY="768"
ResolutionX="800"ResolutionY="600"
ResolutionX="640"ResolutionY="480"
ResolutionX="320"ResolutionY="240"

Everything above these resolutions seem to make the game much slower. 

asdfoo, If you haven't given up yet.  You should remove the fbo from regedit. It has been reported as a bug and crashes the game like you said. Try this tweak > [HKEY_CURRENT_USER\Software\Wine\Direct3D]
"UseGLSL"="enabled"  Remember though, I am using Wine 1.1.4, and you are currently using a different wine version.  This could be the cause for some of your problems.


NOTE: Just letting everyone know, I am trying the appdb's HOWTO get far cry 2 running as well.  I will let you know if it is any better or worse until then.

Good Luck,
Sugi

---

### Post by G-Dub on 2008-10-28
I got a C++ runtime error...
I did all of the previous steps except i installed the game through windows onto a windows partition. Any thoughts?

---

### Post by spwnt on 2008-10-28
now I'm getting a new error. I was  getting resolution problems so I ran (not related to the game.)

```
dpkg-reconfigure xserver-xorg
```

and since then it hasn't been working. I reinstalled it and readded all the DLL's to the bin folder along with applying the crack but now I get this error when I try to run it.

```
spwnt@spwnt-desktop:~$ cd /home/spwnt/.wine/drive_c/Program\ Files/Ubisoft/Far\ Cry\ 2/bin && wine explorer /desktop=Far_Cry_2,1440x900 FarCry2.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Program Files\\Ubisoft\\Far Cry 2\\bin\\Dunia.dll") not found
err:module:import_dll Library Dunia.dll (which is needed by L"C:\\Program Files\\Ubisoft\\Far Cry 2\\bin\\FarCry2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Ubisoft\\Far Cry 2\\bin\\FarCry2.exe" failed, status c0000135
```

MSVCP80.dll and Dunia.dll are in the bin folder. i'm not sure what to do.

---

### Post by asdfoo on 2008-10-28
> **Sugi said:**
> 
asdfoo, If you haven't given up yet.  You should remove the fbo from regedit. It has been reported as a bug and crashes the game like you said. Try this tweak   Remember though, I am using Wine 1.1.4, and you are currently using a different wine version.  This could be the cause for some of your problems.


Good Luck,
Sugi

Yeah... I disabled fbo and it either crashes with an out of memory message while loading or while playing the game with stuff set to the lowest settings.

btw, GLSL has been enabled by default since 0.9.46 or something

i gave up in frustration and resized my main partition to make room for windows, installed it and farcry 2 and that works perfectly.

---

### Post by LokeTheDog on 2008-10-29
> **haswig said:**
> Hi,

I also tryed to get the Game running with a mixture of this and the Howto at winehq. (they are pretty the same)
And it seems to run.
"Seem" , because i only see a black screen, but i hear the sound of the game. I started in Win to play so i know that the Game menu is loaded.

I think the problem is my Ati FireGl 5200.

This is where I'm at too. The game says something about me using old drivers (I'm not) and then the screen (in the emulated desktop) goes black. I can hear the music though. But I'm using a Nvidia 8800GT, so were either having different problems with similar results or it has nothing at all to do with our specific cards or drivers.

Edit:

Progress! Ok, I tried starting the game through the launcher now, and that worked! Still get complaint about old drivers, but it works, so... Had to put all settings on low for now though, when I turned everything up, it crashed. Anyway, you try using the launcher, maybe it'll work for you too.

Edit2: Hmm, sometimes it's as if the whole world was filled with thick, brown smoke, i can only se stuff that's really close. Then it suddenly goes away. Anyone know whats causing this?

---

### Post by haswig on 2008-10-30
> **LokeTheDog said:**
> 

Edit2: Hmm, sometimes it's as if the whole world was filled with thick, brown smoke, i can only se stuff that's really close. Then it suddenly goes away. Anyone know whats causing this?

Maybe that is the Malaria blur FX. Its normaly a bubbly, blury brown layer. It comes up when you should take your Malariameds. Dont know how to disable this one.

---

### Post by rlhawk on 2008-10-31
> **LokeTheDog said:**
> fixme:win:EnumDisplayDevicesW ((null),0,0x90f6a8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:dxgi:CreateDXGIFactory riid {7b7166ec-21c7-44ae-b21a-c9ae321ae369}, factory 0x90f4bc partial stub!
fixme:dxgi:dxgi_factory_EnumAdapters iface 0x1bd6a8, adapter_idx 0, adapter 0x90f4d4 stub!


> **LokeTheDog said:**
> I am using a cracked (razor 1911) FarCry2.exe, I've got the files in the right places, I'm using Nvidia 8800 GT (later edition). I think I've got the latest drivers, not sure how to check that.

Exact same setup here, and the exact same error.  What no cd patch are you using Sugi?  And how did you get past this LokeTheDog?

---

### Post by LokeTheDog on 2008-11-01
Try using the regular launcher under "Wine" in "Programs". That works for me now. It's possible I changed something else too, can't remember.

As for the malaria effect, don't think that's the problem, seems more area related. Like, in the shack where you wake up after the first gunfight, that's one place where its brown. If I exit, it goes away, but comes back when I get closer to the shack again. Oh well, this seems to be a pretty buggy game, maybe it's just a regular bug.

---

### Post by cooljeff3000 on 2008-11-01
I applied all the dlls to both the bin file and /windows/system32 for good measure but it still wont start. If I click on farcry2.exe nothing happens, if i try the autorun I get a launcher but when i press play it goes through some downloading thing then dissapears, and under the wine bit under applications, if i go under Programs there's no ubisoft. The install was fine except for punkbuster

---

### Post by cooljeff3000 on 2008-11-01
I found out that it not starting was a problem with my drivers so i reinstalled them and it started only to get stuck on the online release date thing. So i downloaded the patch, but that didn't work, so i downloaded a cracked farcry2.exe and when i  open that it says that my drivers are too old and when i click ok it closes

---

### Post by Faelh on 2008-11-02
I have the same problem than lundman:

```
wine: Call from 0x102e26df to unimplemented function iphlpapi.dll.IcmpCreateFile, aborting
```

How can I fix it?

---

### Post by Speechless on 2008-11-29
> **G-Dub said:**
> I got a C++ runtime error...
I did all of the previous steps except i installed the game through windows onto a windows partition. Any thoughts?

I got the same error :\ how to fix that?

---

### Post by Weppes on 2008-12-10
Hi guys,

I have the same error : 
C++ runtime error R6034
while trying to launch FarCry.exe

My config : 
Ubuntu 8.04 / wine 1.1.10 , AMD64 X2, Geforce 8800 GT.
No matter with drivers, Call of duty 2 and 4 are working fine.

I searched google for this error, it seems the problem is about msvcr80.dll
Got it on DLL-files, but I still have this error.
A message on DLL-files says this is not the good version of the file. Actually it seems like the only way to get the good dll is to install Microsoft Visual C++ .

I downloaded a tool called VCRedist.exe from microsoft. I think it aims at installing the latest libraries for C++ applications.
I can launch it, but it fails copying dll files from a TEMP directory ( not present on my c: drive) to wine system32 folder.

has anyone find how to get the good C++ libraries for windows ? Or an easyer way to install Visual C++ environment ? 

I continue searching, I'll tell you if I have news.

---

### Post by SketchyLlama on 2008-12-15
I'm getting the game up and running, not at max resolution but I'm crossing bridges by importance, right now I can deal with the resolution problem.

I'm having problems past the main menu. I can select story mode, choose a character, and get to a loading screen. But the game always crashes during that loading screen. 

I've got a LOT of information in the terminal so I won't paste the entire wall of text, but here's the last few lines before the crash.

```
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #1168: "Fragment info\n-------------\n(0) : error C9008: malloc failed in \"mem_CreatePool\"\n"
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_OUT_OF_MEMORY (0x505) from Find glsl program uniform locations @ glsl_shader.c / 3265
fixme:d3d_shader:set_glsl_shader_program >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB(programId) @ glsl_shader.c / 3277
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3114
fixme:d3d_shader:hardcode_local_constants >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Hardcoding local constants
 @ glsl_shader.c / 3114
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3406
fixme:d3d:state_blend >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glEnable GL_BLEND @ state.c / 258
fixme:d3d:sampler >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glActiveTextureARB @ state.c / 3433
Segmentation fault

```

I assume the malloc error in the first line relates to the C function malloc(), which would imply there are problems with allocating memory. I'm freshly converted to Linux, so I'm unfamiliar with this jargon.

Any advice?


Thanks in advance,
Paul.

---

### Post by oskanaan on 2008-12-16
Thanks!
with a little bit of help from winehq
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14254&iTestingId=32839](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14254&iTestingId=32839)
i am not facing any performance issues or any crashes but i still have to deal with the brown screen i get when there is the character comes across water in the game.. any ideas?

---

### Post by Newnewbie on 2008-12-18
Ive seen a thread where you have 2 set the geometry up on high in order to fix the brown problem... but sadly i cant get it to launch past the download screen :(
figured out part of my problem... was using the "stable" wine... installed .10 and Farcry2 will run for a little while, but not long enough to get past the first cut-scene.

---

### Post by obsrv on 2008-12-25
Sweet thread! Installing my brand new Far Cry 2 on Ubuntu 9.04 A2 at the moment :)

---

### Post by obsrv on 2008-12-26
Please help. I really want to play this game since I bought it :( I dont wanna pay money for Windows now to be able to play it. Here is what I get:

```
obsrv@PIRATE:~$ wine /home/obsrv/.wine/drive_c/Program\ Files/Ubisoft/Far\ Cry\ 2/bin/FarCry2.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Ubisoft\\Far Cry 2\\bin\\FarCry2.exe" failed, status c0000142
obsrv@PIRATE:~$ 

```

MSVCR80.dll is in Far Cry 2 bin direcotry.

---

### Post by oskanaan on 2008-12-29
Please read this guide, it worked for me..
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14254&iTestingId=32839](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14254&iTestingId=32839)

---

### Post by yoga on 2009-02-17
Hi.
I've followed your tutorial to make far cry2 runs in my laptop, but i was unlucky...

This is what i get when i try to sart the game:

diogo@diogo-laptop:~$ env WINEPREFIX="/home/diogo/.wine" wine "C:\Programas\Ubisoft\Far Cry 2\bin\FarCry2.exe" 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCP80.dll (which is needed by L"C:\\Programas\\Ubisoft\\Far Cry 2\\bin\\Dunia.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programas\\Ubisoft\\Far Cry 2\\bin\\Dunia.dll") not found
err:module:import_dll Library Dunia.dll (which is needed by L"C:\\Programas\\Ubisoft\\Far Cry 2\\bin\\FarCry2.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Programas\\Ubisoft\\Far Cry 2\\bin\\FarCry2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programas\\Ubisoft\\Far Cry 2\\bin\\FarCry2.exe" failed, status c0000135
diogo@diogo-laptop:~$ 

What's wrong?:(

---

### Post by manamann on 2009-03-20
Hi(i use google translator), i have openSUSE , wine 1.1.2 , wine-doors (all avable dll's font's .net etc) , PlayOnLinux but.. it's not working. I have all dll's (FarCry2.HOWTO.TheDLLsp[1-2].tar.gz ) but in regedit i did not find [HKEY_CURRENT_USER\Software\Wine\**_Direct3D_**] , i create this folder.. and string "UseGLSL" with "enabled". When i lounch(start) shortcut fc2.desktop with  ```
wine explorer /desktop=Far_Cry_2,1280x1024 /home/manamann/.wine/drive_c/Program\ Files/Ubisoft/Far\ Cry\ 2/bin/FarCry2.exe
``` it made the wine desk with "Your Video Drivers are too old" - i press OK - he close(quit). When i press button [x] - he close "Your Video Drivers are too old" but wine desktop is workin. 
p.s.  nvidia 8600gt 
p.s.2 any games worked(or working.. [in this moment]) good? and better then in winxp :)

please help my ) if possible - Remind by e-mail [email]manamann@mail.ru[/email]

---

### Post by manamann on 2009-03-20
YES ! It work ! I update my wine to 1.1.9 :^)

---

### Post by markackerman8@gmail.com on 2009-05-06
WORKING FINALLY

OK after tearing my hair out for a week, it came down to using playonlinux with wine 1.1.6 instead of 1.1.20.  It doesn't like my 1360x768 resolution and is running at slow FPS but its a start.

---

### Post by markackerman8@gmail.com on 2009-05-06
WORKING FINALLY

OK after tearing my hair out for a week, it came down to using playonlinux with wine 1.1.6 instead of 1.1.20.  It doesn't like my 1360x768 resolution and is running at slow FPS but its a start.

---

### Post by ofccs993 on 2010-10-19
WTF!! on the Photo in the left corner down it says "Connected as jesus" :confused:

---

### Post by DerH0ns on 2012-05-14
```
wget http://www.dll-files.com/dllindex/d3dx9_38.zip?0VEgWFWDkS
```

The file doses't extist anymore can you reupload it?

---

