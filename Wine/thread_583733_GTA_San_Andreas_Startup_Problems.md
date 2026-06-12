---
title: "GTA San Andreas Startup Problems"
date: 2007-10-20
forum: Wine
---

### Post by tghe-retford on 2007-10-20
I am trying out Kubuntu 7.10 x86_64 after trying out a number of distros. I am in the process of trying out two of the games I have on Windows which should work on Kubuntu 7.10 x86_64 (according to the Wine AppDB). SimCity 4 works fine with a minor graphic problem, but GTA San Andreas which according to the AppDB works on one testers Ubuntu 7.10 x86_64 setup will not work on my computer.

When I go to start the game, the EAX and NVidia logos appear, but when the Rockstar logo video should appear (which is logo.mpg), the game crashes and I end up back on the desktop with a lower resolution.

I ran the game through the terminal and the output is below, so hopefully someone can find out what the problem is.

```
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x178f794,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x13a5a0) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
wine: Unhandled page fault on read access to 0x00000002 at address 0x7cd39577 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000002 in 32-bit code (0x7cd39577).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7cd39577 ESP:0178f9b8 EBP:0178f9f0 EFLAGS:00010297(   - 00     RISAP1C)
 EAX:00000002 EBX:7cd75a8c ECX:0178fa9c EDX:00000000
 ESI:027be101 EDI:027be158
Stack dump:
0x0178f9b8:  025d6dd8 034e12f0 0299e728 025d74e8
0x0178f9c8:  7cb66860 e0f158e1 11d0cb04 a0004ebd
0x0178f9d8:  86ce11c9 ff0a0000 00000000 7cd75a8c
0x0178f9e8:  80040218 00000000 0178fb30 7cd46b61
0x0178f9f8:  027be158 00000001 0178fa9c 0178faa0
0x0178fa08:  00000000 00000001 00000001 0178fa60
Backtrace:
=>1 0x7cd39577 in quartz (+0x9577) (0x0178f9f0)
  2 0x7cd46b61 in quartz (+0x16b61) (0x0178fb30)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 8c2e96f8 in module L"gta_sa"
  3 0x00747725 in gta_sa (+0x347725) (0x7ed37d20)
  4 0x000248ec (0x81e58955)
  5 0x00000000 (0x00000000)
0x7cd39577: movl        0x0(%eax),%edx
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        240000-  249000       Deferred        ogg
PE        250000-  358000       Deferred        vorbis
PE        360000-  390000       Deferred        eax
PE        400000- 1577000       Export          gta_sa
PE      10000000-10011000       Deferred        vorbisfile
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7cb48000-7cb67000       Deferred        devenum<elf>
  \-PE  7cb50000-7cb67000       \               devenum
ELF     7cb67000-7cb99000       Deferred        uxtheme<elf>
  \-PE  7cb70000-7cb99000       \               uxtheme
ELF     7cb99000-7cc36000       Deferred        oleaut32<elf>
  \-PE  7cbb0000-7cc36000       \               oleaut32
ELF     7cc36000-7ccf4000       Deferred        comctl32<elf>
  \-PE  7cc40000-7ccf4000       \               comctl32
ELF     7ccf4000-7cd1b000       Deferred        msvfw32<elf>
  \-PE  7cd00000-7cd1b000       \               msvfw32
ELF     7cd1b000-7cd77000       Export          quartz<elf>
  \-PE  7cd30000-7cd77000       \               quartz
ELF     7cdd2000-7ce01000       Deferred        d3d9<elf>
  \-PE  7cde0000-7ce01000       \               d3d9
ELF     7d012000-7d048000       Deferred        dinput<elf>
  \-PE  7d020000-7d048000       \               dinput
ELF     7d048000-7d061000       Deferred        dinput8<elf>
  \-PE  7d050000-7d061000       \               dinput8
ELF     7d276000-7d28a000       Deferred        avicap32<elf>
  \-PE  7d280000-7d28a000       \               avicap32
ELF     7d28a000-7d2d3000       Deferred        dsound<elf>
  \-PE  7d290000-7d2d3000       \               dsound
ELF     7d2e3000-7d3c4000       Deferred        wined3d<elf>
  \-PE  7d300000-7d3c4000       \               wined3d
ELF     7d3c4000-7d419000       Deferred        ddraw<elf>
  \-PE  7d3d0000-7d419000       \               ddraw
ELF     7d62a000-7d63f000       Deferred        midimap<elf>
  \-PE  7d630000-7d63f000       \               midimap
ELF     7d63f000-7d666000       Deferred        msacm32<elf>
  \-PE  7d650000-7d666000       \               msacm32
ELF     7d666000-7d72c000       Deferred        libasound.so.2
ELF     7d9dd000-7d9f5000       Deferred        msacm32<elf>
  \-PE  7d9e0000-7d9f5000       \               msacm32
ELF     7d9f5000-7da2b000       Deferred        winealsa<elf>
  \-PE  7da00000-7da2b000       \               winealsa
ELF     7da2b000-7da30000       Deferred        libxfixes.so.3
ELF     7da30000-7da39000       Deferred        libxcursor.so.1
ELF     7da39000-7da56000       Deferred        imm32<elf>
  \-PE  7da40000-7da56000       \               imm32
ELF     7da56000-7da5c000       Deferred        libxrandr.so.2
ELF     7da5c000-7da5f000       Deferred        libxinerama.so.1
ELF     7dd1c000-7dd1e000       Deferred        libnvidia-tls.so.1
ELF     7dd1e000-7e6b6000       Deferred        libglcore.so.1
ELF     7e6b6000-7e74c000       Deferred        libgl.so.1
ELF     7e74c000-7e751000       Deferred        libxdmcp.so.6
ELF     7e751000-7e754000       Deferred        libxau.so.6
ELF     7e754000-7e845000       Deferred        libx11.so.6
ELF     7e845000-7e853000       Deferred        libxext.so.6
ELF     7e853000-7e85b000       Deferred        libxrender.so.1
ELF     7e868000-7e8f7000       Deferred        winex11<elf>
  \-PE  7e880000-7e8f7000       \               winex11
ELF     7e97a000-7e99a000       Deferred        libexpat.so.1
ELF     7e99a000-7e9c5000       Deferred        libfontconfig.so.1
ELF     7e9c5000-7e9da000       Deferred        libz.so.1
ELF     7e9da000-7ea4a000       Deferred        libfreetype.so.6
ELF     7ea4a000-7eaa3000       Deferred        rpcrt4<elf>
  \-PE  7ea60000-7eaa3000       \               rpcrt4
ELF     7eaa3000-7eb44000       Deferred        ole32<elf>
  \-PE  7eab0000-7eb44000       \               ole32
ELF     7eb44000-7eb57000       Deferred        libresolv.so.2
ELF     7eb57000-7eb75000       Deferred        iphlpapi<elf>
  \-PE  7eb60000-7eb75000       \               iphlpapi
ELF     7eb75000-7eba2000       Deferred        ws2_32<elf>
  \-PE  7eb80000-7eba2000       \               ws2_32
ELF     7eba2000-7ebeb000       Deferred        advapi32<elf>
  \-PE  7ebb0000-7ebeb000       \               advapi32
ELF     7ebeb000-7ec86000       Deferred        gdi32<elf>
  \-PE  7ec00000-7ec86000       \               gdi32
ELF     7ec86000-7edc4000       Deferred        user32<elf>
  \-PE  7eca0000-7edc4000       \               user32
ELF     7edc4000-7ee52000       Deferred        winmm<elf>
  \-PE  7edd0000-7ee52000       \               winmm
ELF     7ef90000-7ef9b000       Deferred        libnss_files.so.2
ELF     7ef9b000-7efa5000       Deferred        libnss_nis.so.2
ELF     7efa5000-7efbd000       Deferred        libnsl.so.1
ELF     7efbd000-7efc6000       Deferred        libnss_compat.so.2
ELF     7efc6000-7efeb000       Deferred        libm.so.6
ELF     f7cc8000-f7ccc000       Deferred        libdl.so.2
ELF     f7ccc000-f7e16000       Deferred        libc.so.6
ELF     f7e17000-f7e2f000       Deferred        libpthread.so.0
ELF     f7e44000-f7f58000       Deferred        libwine.so.1
ELF     f7f5a000-f7f78000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000b
        0000000c    0
00000008 (D) C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe
        0000000e    0
        0000000d   15
        0000000a    0
        00000009    0 <==
```

I'm using Wine 0.9.47.

It seems weird, because other people can get the game to work and I can't. :( I'm just wondering how people have managed to get the game to work? I have looked on the Wine AppDB and no-one else seems to have the same problem. :-k

---

### Post by tghe-retford on 2007-10-20
Found a fix, and I will post it here just so it can help others in future:

Go to ~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas/movies/ and remove both mpg files.

---

### Post by djrobthaman on 2007-10-21
Hi,

I'm trying to run gta san andreas as well and am having similar problems.  When I use the terminal and cd to the gta direactory and run wine gta_sa.exe I get a lot of similar output.

At first all that would happen is either when I executed that command or tried to start gta from the menu in the applications drop down a window (with no borders) about 50% the size of my desktop would appear and flash to white once or twice before staying black.  Then when I hit any key on my keyboard the window would flash to white one more time and then disappear.

Now I've tried deleting those mpg files and now when I use the terminal to start up gta the same thing happens except the box changes the screen resolution (or at least it looks that way) and takes up the whole screen except that both my panels are still visible.

But when I tried starting it up from the applications menu, my screen went black and then I got rerouted to the ubuntu login screen and I had to log in again.

Any ideas on how I could get it to actually work?

Thanks

EDIT:  Just tried running it from the terminal again and this time the panels weren't there.  I guess that might be a good thing, but the game still won't play.  errgghhh

---

### Post by Benedolt on 2007-12-16
I am having exactly the same problem as you, djrobthaman!

Did you or anyone else figure out how to solve this?

Here is my output:
```
$ wine gta_sa.exe 
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x178ee28,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glClearColor @ context.c / 332
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x153c48) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d_surface:flush_to_framebuffer_drawpixels >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glDrawPixels @ surface.c / 1090
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
   err:quartz:FilterGraph2_AddSourceFilter Load (80070002)
Initialised SoundManager
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x1e9710,0,(nil),(nil)): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)

```

---

### Post by Hungerer on 2007-12-20
:guitar: yo man i have same problems its just it startes and when it starts loading white color filling bar under picture and 1/5 its say SA error what to do :(

---

### Post by saz on 2008-02-23
> **tghe-retford said:**
> Found a fix, and I will post it here just so it can help others in future:

Go to ~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas/movies/ and remove both mpg files.

THANK YOU SO FU***** MUCH!!! i was getting sick and tired... had tried everything

THANKS!!

---

### Post by CDrewing on 2008-03-19
Well I have the same problem, but deleting the both mpg files did not help.

I receive:

```
cdrewing@ubuntu:~$ wine "C:\Programme\Rockstar Games\GTA San Andreas\gta_sa.exe"
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)


```

And then nothing happens.

**Please help anybody!!**

---

### Post by tghe-retford on 2008-04-05
> **CDrewing said:**
> Well I have the same problem, but deleting the both mpg files did not help.

I receive:

```
cdrewing@ubuntu:~$ wine "C:\Programme\Rockstar Games\GTA San Andreas\gta_sa.exe"
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)


```

And then nothing happens.

**Please help anybody!!**
Bizarrely I now have exactly the same problem.
```
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
```
I will try whatever I can do to get it working and report back.

---

### Post by tghe-retford on 2008-04-05
Bug report produced for this problem:

[http://bugs.winehq.org/show_bug.cgi?id=12013](http://bugs.winehq.org/show_bug.cgi?id=12013)

---

### Post by tghe-retford on 2008-04-05
> **CDrewing said:**
> Well I have the same problem, but deleting the both mpg files did not help.

I receive:

```
cdrewing@ubuntu:~$ wine "C:\Programme\Rockstar Games\GTA San Andreas\gta_sa.exe"
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)


```

And then nothing happens.

**Please help anybody!!**
I restarted my computer and that seemed to have got it working again.

---

### Post by Gwijde on 2008-04-11
Hi guys,

I have exactly the same problem as Benedolt above, and am quite agitated :-(

So basically I run gta_sa.exe in 3 different ways:
 
1) Desktop shortcut: results in a screen that flashes twice, closes when button is pressed
2) Applications menu: again, the flashing screen
3) Straight from the terminal : gives me the screen and the same output as Benedolt's

Please help me, what do I do? I love this game so much!

Thanx from beforehand

--Gwijde

---

### Post by Tomatz on 2008-04-11
Don't bother the sound is very buggy once you get it running. There are fixes but they don't work effectivly.

That was my experience ;)

---

### Post by Gwijde on 2008-04-11
Fixes? 

Could you possibly point them out to me? I'll try anything :)

--Gwijde

---

### Post by Tomatz on 2008-04-11
> **Gwijde said:**
> Fixes? 

Could you possibly point them out to me? I'll try anything :)

--Gwijde


What i meant was sound fixes. Actually it installed via wine perfectly. The problem is once it is installed the sound is very laggy and it makes the game unplayable.

Also if you were hoping to use the multi theft auto mod. This doesn't work either (in wine or cedega).

Basically i suggest you install it in xp ;)

---

### Post by Gwijde on 2008-04-11
Funny you should say that. As a matter of fact, I just installed XP in virtualbox, and GTA SA in it, but I get an error: A required security module could not be executed...

After checking this out, it turns out it was detected that I was running an emulator...

So that didn't get me any further...

Thanx for the suggestion though, but I want to stay as far away from XP as possible, as I know it IS possible to play this in ubuntu.

--Gwijde

---

### Post by Tomatz on 2008-04-12
> **Gwijde said:**
> Funny you should say that. As a matter of fact, I just installed XP in virtualbox, and GTA SA in it, but I get an error: A required security module could not be executed...

After checking this out, it turns out it was detected that I was running an emulator...

So that didn't get me any further...

Thanx for the suggestion though, but I want to stay as far away from XP as possible, as I know it IS possible to play this in ubuntu.

--Gwijde

You wont be able to play 3d games in virtualbox :(

---

### Post by Tomatz on 2008-04-12
Ahhhh!

I installed it from an .iso ;)

If you are installing from the original gtasa disk maybe the copy protection is preventing you from installing successfully via wine.

Make an .iso of the disk, extract it then install that way.

---

### Post by stinkinrich88 on 2008-04-27
no 3d games in virtualbox?! weeeaaak! Cause I can't get sanan working in wine either. I managed it before! But now I'm using ATI instead of nvidia. Last time I ever get an ATI card, I swear. Nothing but trouble.

---

