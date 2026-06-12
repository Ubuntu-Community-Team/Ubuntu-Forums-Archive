---
title: "[SOLVED] Command and Conquer 3"
date: 2008-07-17
forum: Wine
---

### Post by Plasma_NZ on 2008-07-17
ok, firstly, i've played it before using wine the same way i'm trying now..

Was using 7.10 then...

here's the go...

Installed cnc3 in windows, (reason for installing under windows is because there's not enough room left on filesystem, and during install proccess under wine it wont allow me to install it to another hdd) then boot'd into ubuntu - and issued the command to start cnc3 using wine, had it set for XP, also copied across the files required aswell..... the problems also attached

wine version 1.1.1
Ubuntu 8.04 64bit

```

physics@physics:~$ wine /media/hdb5/Installed_games/cnc3/CNC3.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
wine: Unhandled exception 0xc000000d at address 0x7bc80023:0x00457338 (thread 0019), starting debugger...
Process of pid=0018 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
physics@physics:~$ process  tid      prio (all id:s are in hex)
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
0000001a 
	0000001b    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```

---

### Post by LeXrius on 2008-07-17
with my limited understanding of wine, It looks like a audio issue. try setting the audio in winecfg to OSS.

---

### Post by Plasma_NZ on 2008-07-17
> **LeXrius said:**
> with my limited understanding of wine, It looks like a audio issue. try setting the audio in winecfg to OSS.

tried that, still get the same issue

---

### Post by lightstream on 2008-07-17
> **Plasma_NZ said:**
> tried that, still get the same issue

What directory are you in? Looks like your home directory - have you tried changing to the cnc directory?

I have installed cnc 3 under wine, it installed flawlessly and runs perfectly - except for wine's lack of animated cursor support. If you don't have the patch to add animated cursors, it still runs, but you have an invisible cursor. Which sort of adds an extra element to it

---

### Post by Plasma_NZ on 2008-07-17
> **lightstream said:**
> What directory are you in? Looks like your home directory - have you tried changing to the cnc directory?

I have installed cnc 3 under wine, it installed flawlessly and runs perfectly - except for wine's lack of animated cursor support. If you don't have the patch to add animated cursors, it still runs, but you have an invisible cursor. Which sort of adds an extra element to it

ok, i didnt install it under wine, had to do it via windows, because if i attempt to install it via wine and choose advanced install and specify install location to another drive, it asks for a language pack despite one being selected, known bug, the reason i havent installed it to the normal location is that partition doesnt have enough space....

---

### Post by Vitamin-Carrot on 2008-07-17
Doesht wine allow you to select where you want you c: when you first start it?

---

### Post by Sleaka J on 2008-07-18
C&C3 requires registry entries to run.

---

### Post by evets25 on 2008-07-18
just to clairify, you can safely ignore the audio messages. I get those messages all the time when running programs in wine, and it still works. The reason it's not running would be probably the part below that in your console output.

---

### Post by sandy8925 on 2008-11-28
Hey I'm having exactly the same problem too! (except for the alsa part.already set it to oss).

Can you please tellme how to fix this? And if I have to change some registry entries can you please tell me which ones ?

---

### Post by ideewoww on 2008-11-28
[img]http://www.ideewomen.com/index.jpg[/img][http://www.ideejewelry.com](http://www.ideejewelry.com/)

---

### Post by sandy8925 on 2008-12-02
Ok now I got it. Just copy the registry entries over.
After that I got some error about an unimplemented function in some directx dll.

So I copied over the native dlls from Windows for all files that were like d3dx*.dll

After the game ran pretty well.Only thing missing now is sound.

Tried enabling alsa but sound still wasn't there. Now going to try driver emulation.....

---

