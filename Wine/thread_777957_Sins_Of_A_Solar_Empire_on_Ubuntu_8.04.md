---
title: "Sins Of A Solar Empire on Ubuntu 8.04"
date: 2008-05-01
forum: Wine
---

### Post by Sniffer on 2008-05-01
Just want to share some screenshots with you:

Using

Ubuntu 8.04
PlayOnLinux
Wine 0.959

Pics In attach. Enjoy Ubuntu Power.

---

### Post by bilal.17 on 2008-05-01
does it work flawlessly?

---

### Post by Sniffer on 2008-05-02
So far so good, but let me test a little bit more and i will come with some feedback.

See ya.

---

### Post by Melhisedek on 2008-05-03
Keep us updated :) I'm trying to iron out some problems with my install and as soon that is done, installing games is next ;)

---

### Post by Sniffer on 2008-05-12
Ok after playing the tutorials, at least only one bug to take in consideration:

When you go to the keyboard menu, the letters don't appear correctly, i have managed to copy all vista fonts to wine dir but without sucess....


Besides that the game works OK, no big problems and no freeze, actually i'm with the follow software:

PlayOnLinux 2.72
Wine 1.0 RC1
Ubuntu 8.04

PS: Ok just managed to solve the fonts problem, download from here:

[www.honorguardonline.com/sins/sinsfontfix.tar.gz](www.honorguardonline.com/sins/sinsfontfix.tar.gz). 

and in the directory where you installed the game, ~/.wine/drive_c/Program\ Files/Stardock\ Games/Sins\ of\ a\ Solar \Empire/Font folder, go to the fonts folder and copy to there.

Even so the key bindings still don't appear, but the fonts now are inside the boxes, so far so good the game.

---

### Post by YokoZar on 2008-05-13
> **bilal.17 said:**
> does it work flawlessly?
Multiplayer didn't work when I tested it about 2 months ago, unfortunately.  Everything else seemed fine.

I filed a bug already. [http://bugs.winehq.org/show_bug.cgi?id=11640](http://bugs.winehq.org/show_bug.cgi?id=11640)

---

### Post by wedge98 on 2008-05-21
I'm pretty new to linux and for fun I am trying to get Sins of a solar Empire to run under Ubuntu 8.04.

In my first attempt I tried doing everything though wine... I was able to install the game and patch but when I went to try and play the game it did not work at all. So I added play on linux, then uninstalled sins of solar empire from wine. Then I reinstalled it through Play on linux and it ran once but when I went to run it again the game was not inside of play on linux. So I believe I messed up the order of installation of the game and now I need to uninstall everything and try again.

So I was thinking I should install the software in the following order:
1) wine rc1
2) PlayOnLinux 2.7.2
3) Sins of a Solar Empire(dvd) (through play on linux)
4) Sins of a Solar Emprie v1.04 patch (through play on linux)

Is this correct?

Thank you.

---

### Post by Silpheed2K on 2008-05-21
How did you even get that to work? it just changes my screen resolution and crashes on my Linux... what settings do i need to run that?

---

### Post by wedge98 on 2008-05-21
Under wine ensure the following:
Under the Applications tab I set the Windows Version to Windows XP

Under the Graphics tab:

I unchecked Allow DirectX Apps to stop the mouse leaving their window
Unchecked Allow the window manager to control the windows. 
I did check Emulate virtual desktop and set it at 1024x768 (adjust that to your own preference). This is not required but I recommend it so that if the game freezes up you still have use of your monitor to kill the process.

Under the Drives tab I just clicked Autodetect and accepted the defaults. 

Under the Audio tab I unchecked the OSS drivers and checked the ALSA drivers.

Then there's a link above for the font pack.

---

### Post by Sniffer on 2008-05-21
> **wedge98 said:**
> I'm pretty new to linux and for fun I am trying to get Sins of a solar Empire to run under Ubuntu 8.04.

In my first attempt I tried doing everything though wine... I was able to install the game and patch but when I went to try and play the game it did not work at all. So I added play on linux, then uninstalled sins of solar empire from wine. Then I reinstalled it through Play on linux and it ran once but when I went to run it again the game was not inside of play on linux. So I believe I messed up the order of installation of the game and now I need to uninstall everything and try again.

So I was thinking I should install the software in the following order:
1) wine rc1
2) PlayOnLinux 2.7.2
3) Sins of a Solar Empire(dvd) (through play on linux)
4) Sins of a Solar Emprie v1.04 patch (through play on linux)

Is this correct?

Thank you.

Nope...

1ST - after installing a fresh ubuntu 8.04, go to terminal and do this:

With hardy repository

Type the following commands :

sudo wget [http://playonlinux.botux.net/playonlinux_hardy.list](http://playonlinux.botux.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list

wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install playonlinux

This will install playonlinux and automatically install wine to solve the dependecies.

Then install SOASE And the Patch.

PS: I have all options as default with no problems

Sniffer Devil Inside:twisted:

---

### Post by wedge98 on 2008-05-22
reinstalled everything last night and it works.

Thank you :D

---

### Post by Sniffer on 2008-05-24
> **wedge98 said:**
> reinstalled everything last night and it works.

Thank you :D

Give us feedback of your experience.

Regards
Sniff.

---

### Post by jelly on 2008-06-03
I'm having slightly less luck it seems.  I'm on 8.04 with the latest Wine (rc1?), I've updated to the latest patch (1.05) and everything works flawlessly to start with.

Then, after an certain amount of time it just bombs.  It seems to be around the same amount of time actually.  I've just been trying to get through the tutorial, and I can never get much beyond trying to colonize the first planet thingy.

SO annoying!  I got the game based on what I read in the Wine AppDB - thought it was worth a gamble - now it's worse than not working.. I get to see how awesome the game is going to be, and not play it for more than 5 mins or so!

Any help or ideas about how I can get this working / identify the cause of the problem will be much appreciated.

Thanks,

- Jelly.

---

### Post by Sniffer on 2008-06-10
> **jelly said:**
> I'm having slightly less luck it seems.  I'm on 8.04 with the latest Wine (rc1?), I've updated to the latest patch (1.05) and everything works flawlessly to start with.

Then, after an certain amount of time it just bombs.  It seems to be around the same amount of time actually.  I've just been trying to get through the tutorial, and I can never get much beyond trying to colonize the first planet thingy.

SO annoying!  I got the game based on what I read in the Wine AppDB - thought it was worth a gamble - now it's worse than not working.. I get to see how awesome the game is going to be, and not play it for more than 5 mins or so!

Any help or ideas about how I can get this working / identify the cause of the problem will be much appreciated.

Thanks,

- Jelly.

Sorry for the delay, hate to answer after much time....

What is your graphic card - In my situation i'm talking of a GeForce 8400M GS and 2GB of RAM on my laptop, nVIDIA Driver 169.12.

Last Kernel 2.6.24-18

One last thing, sometime patch in Gnu Linux don't mean better, sometimes means WORST, try install the game without the patch and play.

Hope you dont rely on ATI graphic Card as well.

Sniff

---

### Post by dotmrt on 2008-08-27
I got Sins working with PlayOnLinux on Kubuntu 8.04, but it wouldn't patch it to the latest 1.05. So I installed the game into a VirtualBox virtual-Windows XP and patched it there. Then copied the whole game to ~/.PlayOnLinux/.. into the appropriate place and got it working with single play. 

Unfortunately the network doesn't work as mentioned before. And well that's a bummer, as the game itself works surprisingly well (at least I've had bad experiences with Wine and Supreme Commander and Warcraft3). But Sins is a multiplayer game, so it's really no fun playing only single play. 

I hope Wine will get better soon on that department.

---

### Post by jelly on 2008-08-29
Just a quick update on how I got on this.  I'm afraid I've had to turn to the dark side this weekend - and install Microsoft Windows dual boot as a gaming partition again.

With Spore coming out in a week or so, and Warhammer Online following closely behind - I thought I'd just bite the bullet and be sure that I can play them all as intended.

Shame, but there we go.

---

### Post by Takmadeus on 2008-08-31
There is nothing bad in installing windows, the problem is if there's the case that you do not know there are alternatives, and hey, you can keep windows and linux together so there's no real problem ;)

---

### Post by zami on 2009-01-24
Anyone currently playing this?  If so, what version of Wine are you using?

All I get upon launching the game is a black screen.

I installed into it's own Wine prefix so it's a vanilla wine install (so I know any registry tweaks I've done for other games aren't affecting SOASE).

Ubuntu 8.10
Wine 1.1.13
SOASE installed from DVD, 1.05 patch applied.

There's not a lot of info on installing this game at CrossoverGames or Wine.  I tried installing via PlayOnLinux, but couldn't get through the incredibly slow install process.  It took about 15 minutes to install via pure Wine, and I gave up when PlayOnLinux was maybe 5% installed after half an hour.

I'll be curious for an update on this game!

-zami

---

### Post by zami on 2009-01-24
My errors - 
the Windows error is

```

MiniDump
Saved MiniDump:
C:\windows\temp\Sins Dump\Sins-v1.06.......dmp

```
(it doesn't really say "....." but it's a very long string of numbers)

while terminal gives
```

laura@BelleBlue:~/.wine-sins/drive_c/Program Files/Stardock Games/Sins of a Solar Empire$ wine Sins\ of\ a\ Solar\ Empire.exe
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on AK5370          , disabling mixer
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f840,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3817
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
wine: Call from 0x7b8457a0 to unimplemented function d3dx9_36.dll.D3DXCreateLine, aborting
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs

```
then
```

fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

Let me know if you have any ideas, thanks!

-zami

---

### Post by deathromp on 2009-02-27
> **zami said:**
> My errors - 
the Windows error is

```

MiniDump
Saved MiniDump:
C:\windows\temp\Sins Dump\Sins-v1.06.......dmp

```
(it doesn't really say "....." but it's a very long string of numbers)

while terminal gives
```

laura@BelleBlue:~/.wine-sins/drive_c/Program Files/Stardock Games/Sins of a Solar Empire$ wine Sins\ of\ a\ Solar\ Empire.exe
err:module:find_forwarded_export function not found for forward 'd3dx8.D3DXGetImageInfoFromFileW' used by L"C:\\windows\\system32\\d3dx9_36.dll". If you are using builtin L"d3dx9_36.dll", try using the native one instead.
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on AK5370          , disabling mixer
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f840,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3817
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
wine: Call from 0x7b8457a0 to unimplemented function d3dx9_36.dll.D3DXCreateLine, aborting
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs

```
then
```

fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

Let me know if you have any ideas, thanks!

-zami


I recently had the same issue, it turns out my disk wasn't reading properly, I downloaded a new iso of the game and mounted it directly to the HD, ran the setup from the mounted iso, selected the repair option and it worked immediately. 

Running wine 1.1.15 under Ubuntu 8.10, I haven't tested the gameplay yet, but this should at least get you in.

---

### Post by oldrocker99 on 2009-06-02
<snip> I downloaded a new iso of the game and mounted it directly to the HD, ran the setup from the mounted iso, selected the repair option and it worked immediately.<snip>

I was unable to get it installed via filecopy the first time, so I edited the script to remove the mkdirs and tried again. This time the copy went smooth as silk.

I, uh, do hope that you BOUGHT the game...:-\"

:guitar:

---

### Post by NorthwesternWind on 2009-07-03
> **Sniffer said:**
> Nope...

1ST - after installing a fresh ubuntu 8.04, go to terminal and do this:

With hardy repository

Type the following commands :

sudo wget [http://playonlinux.botux.net/playonlinux_hardy.list](http://playonlinux.botux.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list

wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install playonlinux

This will install playonlinux and automatically install wine to solve the dependecies.

Then install SOASE And the Patch.

PS: I have all options as default with no problems

Sniffer Devil Inside:twisted:


I just installed Ubuntu for the first time and I think I've messed something up because now whenever I type "sudo apt-get update" I get the message:

E: Type '--17:32:52--' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list

Please help.

---

