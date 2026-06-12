---
title: "have a problem with age of mythology"
date: 2007-12-23
forum: Wine
---

### Post by darkskye on 2007-12-23
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:imm:ImmGetDefaultIMEWnd ((nil) - (nil) 0x134d08 ): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x10002a, 0x134d08): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x134d08): semi-stub
fixme:imm:ImmGetIMEFileNameA (0x4090409, 0x33f694, 260): stub
fixme:imm:ImmNotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetCompositionStringW Unhandled index 0x8
fixme:imm:ImmGetCompositionStringW Unhandled index 0x10
fixme:imm:ImmGetCompositionStringW Unhandled index 0x8
fixme:imm:ImmGetCompositionStringW Unhandled index 0x10
fixme:win:EnumDisplayDevicesW ((null),0,0x33eefc,0x00000000), stub!


is what my in-terminal run command spits out

i installed AOM without any problems, but trying to run it proves to be difficult. at the splash screen, i get this happy little message..

Cannot create log file. Please make sure you have the full file rights on the directory you have installed Age of Mythology into, and you have available disk space.
Error: Sharing violation


any help would be very appreciated

---

### Post by cogadh on 2007-12-23
1. What version of Wine are you using?
2. Did you change directories to the game's install directory before running it?
3. Have you ever used sudo or a root account to run anything in or with Wine?

---

### Post by darkskye on 2007-12-23
sorry for not being able to pull the exact model, im  replying from my work computer.


i run the absolute newest version of wine,

during setup, i did not change the directory

I dont *believe* I have ever run wine as root, though while troubleshooting, i did set the "my games" folder to root, which appeared in my home folder when i installed the game.


thanks for trying to help! this means a lot :P

---

### Post by cogadh on 2007-12-23
You should definitely reset the permissions on that "My Games" folder back to you, not root. That could be the reason it is having a problem creating the log file. When you try to run the game, run it like this:
```
cd .wine/drive_c/Program\ Files/<game directory>/
wine <game executable>.exe
```

---

### Post by darkskye on 2007-12-23
will definantly try running via given command.


will set the permissions back to what they were, but i messed around with the permissions a lot, and same problem with every time, from the original setting all the way to root.

could this have something to do with RTS3banglog.txt? i think its the log, and ive tried deleting it, ive tried changing the permissions to read & write, ive even tried the following code

ln -s /dev/null RTS3Banglog.txt

and still nothing.


any ideas? thanks again :P

---

### Post by darkskye on 2007-12-23
hmmm.... headway


i got AOM to sort-of work by

reinstalling AOM, and alt+f2 ing to run the program in VIDEO SAFE mode. this allows me to play in a tiny window 1/4th of my screen.


but it is a start, anyone have any input?

---

