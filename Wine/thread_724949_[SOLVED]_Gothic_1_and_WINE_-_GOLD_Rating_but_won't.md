---
title: "[SOLVED] Gothic 1 and WINE - GOLD Rating but won't load!!!"
date: 2008-03-15
forum: Wine
---

### Post by cisforcojo on 2008-03-15
Gothic 1 has a GOLD rating: 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3000&iTestingId=19845](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3000&iTestingId=19845)

But I'm having a lot of trouble getting it to work!! I'd like to use this as an experience to become more familiar with WINE. I've followed cogadh's sticky on steps to try first. I've selected ALSA as my sound driver and the sound test works (about half the time, but it DOES work) and I've tried different OS settings for the app. I have other apps working perfectly under WINE however (Wenlin 3.3)

My setup:
Linux Mint 4.0 Daryna (Ubuntu Gutsy Gibbon 7.10)
Wine version 0.9.56 (Downloading 0.9.57 as I write this...)

Description of Problem:
In the best of runs, I've gotten the GOTHIC loading screen to come up but it'll crash saying the following:
```
C:zMusic_DM.cpp(zCMusicSys_DirectMusic::Init()     
) Failed to initialize synth!
```
After a crash, if I re-run the same command I just ran, the loading screen won't come up and it'll give me the ADVAPI32.dll error (see below).

Steps taken:
1. I've tried different OS settings.
2. I've tried OSS (instead of ALSA)
3. I've downloaded the DirectX .dll's recommended on the WineAppDB (dmband.dll, dmime.dll, dmloader.dll, dmstyle.dll, dmsynth.dll, dmusic.dll, dmcompos.dll) and have listed them as overrides in winecfg (native first then build). I just searched for them with Google and downloaded them from sites such as dlldll.com. Is there another way I should've gotten them?


The main error I'm getting is:
```
wine: Call from 0x4044e1 to unimplemented function ADVAPI32.dll.ControlTraceA, aborting
wine: Unimplemented function ADVAPI32.dll.ControlTraceA called at address 0x4044e1 (thread 0012), starting debugger...

```

I've also been getting errors with my sound setting (when I choose OSS it seems alright but I'd prefer to use ALSA):
```
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer

```

Any ideas?

UPDATE:
This is the wine output when I get the 'unable to initialize synth' error:
```
cojones@tipping-point:~/.wine/drive_c/Program Files/PiranhaBytes/Gothic1/system$ wine GOTHIC.EXE
fixme:win:EnumDisplayDevicesW ((null),0,0x12af208,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ddraw:PixelFormat_DD2WineD3D Don't know how to handle a 24 bit depth buffer with stencil bits
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x13d5b0)->(1,(nil)): Stub
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {aec17ce3-a514-11d1-afa6-00aa0024d8b6} could be created for context 0x1
fixme:dmsynth:IDirectMusicSynth8Impl_Close (0x21e6b8): stub
fixme:d3d7:IDirect3DImpl_7_EvictManagedTextures (0x13d5b0): Stub!
err:ddraw:PixelFormat_DD2WineD3D Don't know how to handle a 24 bit depth buffer with stencil bits
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x13d5b0)->(1,(nil)): Stub
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x5400005
  Serial number of failed request:  2290
  Current serial number in output stream:  2290

```

Suggests it's a graphic error and not a sound error???

---

### Post by cisforcojo on 2008-03-16
Bump!

Even some advice on troubleshooting with WINE would be great!
Is there a way to hardcode WINE to use OpenGL for fullscreen apps? It could just be WINE but some apps like Eschalon run really really slowly in Wine for me (fullscreen) and others like Warcraft 3 work perfectly (with the opengl flag).

---

### Post by cisforcojo on 2008-03-16
I finally got it working.
What I had to do was set my ALSA driver to 'Emulation'.

---

