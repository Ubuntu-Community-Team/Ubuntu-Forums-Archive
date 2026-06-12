---
title: "Problem running game on virtual desktop"
date: 2015-10-11
forum: Wine
---

### Post by aless3466 on 2015-10-11
Hello! I'm getting issues on running Sonic Adventure DX with Wine.

On a console, executing "wine start /unix ~/SADX/sonic.exe" runs the program fine, but the resolutions screw up and the desktop gets wrongly positioned, so it becomes unplayable. Setting the virtual desktop to 800X600 on winecf, the game runs perfectly fine, but I need to always disable the virtual desktop to run others programs, and this is annoying.

I tried to run the game with "wine ~/SADX/sonic.exe" and it fails with:

> wine: Unhandled page fault on read access to 0x00000b12 at address 0x40e380 (thread 0023), starting debugger..

Running with wine explorer /desktop=SADX,800x600 ~/SADX/sonic.exe" gives me the same error and the game won't start.

I doubt what the "start /unix" does that maked the game run.

Thanks!

---

### Post by Ubunterrific on 2015-10-11
Just thinking out loud here, so this might not be right. I'm afraid i can't remember the quicker way of doing this :confused:

When sonic.exe's running in the virtual environment, can you instead open the 'system monitor' over on linux and hover over the process running - it should give you the full command being run. 
Let me know if that gets us any step closer.

---

