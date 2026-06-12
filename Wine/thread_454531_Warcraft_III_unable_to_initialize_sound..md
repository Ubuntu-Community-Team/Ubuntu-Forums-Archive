---
title: "Warcraft III unable to initialize sound."
date: 2007-05-25
forum: Wine
---

### Post by the_it on 2007-05-25
I'm trying to run warcraft 3 from a cracked folder on my wine.  Video seems okay, but the sound doesn't come on so far.  I've tried following the appdb instructions but they don't seem to have listed any problems about it yet, so I thought I'd ask here first.

I startup warcraft by going to the warcraft folder then issuing a 

```
$wine war3.exe -opengl
*warcraft starts*
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x191ff8) : stub, simulating 64MB for now, returning 64MB left
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
markd@trixie:/home/wine/drive_c/Program Files/Warcraft III$ wine war3.exe -opengl
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f67c,0x00000000), stub!
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub

```

In warcraft I get the message at the start:
unable to initialize base sound services, sound is disabled.

Im guessing those alsa fixmes are problems.

I am running this of wine and ubuntu:
```
Ubuntu Linux Feisty 7.04 64-bit edition
2.6.20-15-lowlatency kernel
wine-0.9.37
```
It's a 64-bit wine, but I don't think that matters.

I'm running starcraft/broodwar and macromedia flash 8 flawlessly.

Here are my wine settings for audio
```
Alsa Driver - checked
OSS Driver - checked
Hardware Acceleration - Full
Default Sample Rate - 22050
Default bits per sample - 16
Driver Emulation - checked

```

I don't experience sound problems with my other wine applications.

Here's my wine output when running starcraft with working sounds.

```
$ wine starcraft-desktop #a small script that mounts my starcraft iso, see http://ubuntuforums.org/showthread.php?t=451387
umount: /media/cdrom0 is not mounted (according to mtab) #part of script
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x172998) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1720c8)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1720c8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```
===

On a possibly unrelated but possibly related issue, I can't start jackd via qjackctl.  jackd complains that something is using the soundcard.  Maybe the driver that my wined warcraft is using is also unable to use the same access method that jack uses, but for some reason my starcraft uses a different access method to my sound so that works.  Here is what jack says.

```
03:32:08.451 Patchbay deactivated.
03:32:08.478 Statistics reset.
03:32:08.540 Startup script...
03:32:08.540 artsshell -q terminate
03:32:08.580 MIDI connection graph change.
can't create mcop directory
Creating link /home/markd/.kde/socket-trixie.
03:32:09.251 Startup script terminated with exit status=256.
03:32:09.255 JACK is starting...
03:32:09.257 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
03:32:09.284 JACK was started with PID=22303 (0x571f).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
03:32:09.489 MIDI connection change.
no message buffer overruns
03:32:09.536 JACK was stopped successfully.
03:32:09.539 Post-shutdown script...
03:32:09.540 killall jackd
jackd: no process killed
03:32:09.785 Post-shutdown script terminated with exit status=256.
03:32:11.501 Could not connect to JACK server as client. Please check the messages window for more info.
```

I am guessing there is some permission or file or something that I need checked that stops both jack and wine from using ALSA properly OR that they are unrelated and perhaps a specific wine rollback will solve my warcraft problem.

Could you direct me to the config file or setting I need to review?

---

### Post by Bright Hammer on 2007-05-25
I am having the same problem in Starcaft. I get fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture. The odd thing is that I get sound when the cut scenes play.

---

### Post by the_it on 2007-05-25
Sound works fine for me on starcraft though.  Never got a problem with it.

---

### Post by the_it on 2007-05-27
Oops never mind, turns out my installer was borked, since it gave the same problem on windows.

Warcraft is okay now, although I do have a problem with the brightness (adjusting the in-game controls don't work) and sometimes the shroud flickers, but that's about it.

---

### Post by myromance123 on 2008-06-19
After installing alsagui, my wc3 started giving me the error "unable to initialize base sound, sound disabled". Iam guessing its something to do with that alsa program OR alsa overall.

---

### Post by myromance123 on 2008-06-20
I was getting this error "unable to initialize base sound services, sound is disabled." as well and I managed to fix it with reinstalling PulseAudio Device Chooser. Try it and see if it works, cos everything is running smoothly now.

---

### Post by vexorian on 2008-12-25
Just in case anyone finds this thread from google like I did, I had to mention that this problem happens even in windows if you just move the warcraft III folder to some place other than the default installation and try to run it from there, not sure why exactly this happens. The solution is to play warcraft III from the installation place, reinstall if necessary.

Of course, this message could also happen if your sound card has issues, but that's improbable, so first verify the folder is correct.

---

