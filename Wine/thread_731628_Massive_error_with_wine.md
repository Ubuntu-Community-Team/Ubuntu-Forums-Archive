---
title: "Massive error with wine"
date: 2008-03-22
forum: Wine
---

### Post by sudo panda on 2008-03-22
Hi, I'm a recent windows user who's just transfered over to ubuntu linux so bear with me if i'm lacking infomation here. :)
I recently started playing call of duty 4 in wine.
It runs quite smoothly except for the starting movie which stutters during the loading of the level.
When i get upto the part where i obtain my 'recommended' difficulty the game freezes and displays this:

Wine has crashed! 

To enable full error reporting, please run winefix with the flag 
"-d 1"

Errors:
err:seh:setup_exception stack overflow 0 bytes in thread 0017 eip 7eb5e348 esp 7c7be000 stack 0x7c7be000-0x7c8be000
err:ntdll:RtlpWaitForCriticalSection section 0x7e572600 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0009, blocked by 0017, retrying (60 sec)
wine: Critical section 7e572600 wait failed at address 0x7bc39838 (thread 0009), starting debugger...
Unhandled exception: wait failed on critical section 0x7e572600 X11DRV_CritSection
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39838
wine client error:13: write: Bad file descriptor
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'

Any Help would be great :)

---

### Post by chewearn on 2008-03-22
See here, Call Of Duty 4 seemed to be ok:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934)

The wine in ubuntu repo could be too old; I suggest update to latest version:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by sudo panda on 2008-03-22
Ok thanks. 
I've updated to the latest wine repo.
Just gonna test it now, will report what i find.

EDIT:
Nope, no luck :(
started a new game and it froze at the end of the beginning movie clip.
Wine error'd and reported this:

Wine has crashed! 

To enable full error reporting, please run winefix with the flag 
"-d 1"

Errors:
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:seh:setup_exception stack overflow 0 bytes in thread 0017 eip 7eb54348 esp 7c7b7000 stack 0x7c7b7000-0x7c8b7000
err:ntdll:RtlpWaitForCriticalSection section 0x7ebd2abc "d3d9_main.c: d3d9_cs" wait timed out in thread 0009, blocked by 0017, retrying (60 sec)
wine: Critical section 7ebd2abc wait failed at address 0x7bc39838 (thread 0009), starting debugger...

It then went on to say it had TOO many errors to report :S and displayed this:

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:seh:setup_exception stack overflow 0 bytes in thread 0017 eip 7eb54348 esp 7c7b7000 stack 0x7c7b7000-0x7c8b7000
err:ntdll:RtlpWaitForCriticalSection section 0x7ebd2abc "d3d9_main.c: d3d9_cs" wait timed out in thread 0009, blocked by 0017, retrying (60 sec)
wine: Critical section 7ebd2abc wait failed at address 0x7bc39838 (thread 0009), starting debugger...
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
	0000000b    0
0000000c 
	0000000f    0
	0000000e    0
	0000000d    0
00000010 
	00000012    0
	00000011    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'


any ideas? I'd really love to play the singleplayer of this :( seems the multiplayer is running fine..

---

### Post by sudo panda on 2008-03-22
anyone?

---

### Post by LoneWolfJack on 2008-03-23
Open the WINE config tool, go to the audio tab, uncheck ALSA and check OSS.

---

### Post by sudo panda on 2008-03-24
Fixed the problem.
Reinstalled wine with the newest release.
Works fine now.

---

