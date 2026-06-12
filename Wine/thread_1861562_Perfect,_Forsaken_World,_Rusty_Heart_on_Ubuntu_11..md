---
title: "Perfect, Forsaken World, Rusty Heart on Ubuntu 11.10?"
date: 2011-10-15
forum: Wine
---

### Post by TurtleKing on 2011-10-15
Anybody gotten any of these games to work under wine in Ubuntu 11.10?
I tried and failed with this error from terminal for Forsaken World:
```
wine: Unhandled page fault on read access to 0x00000000 at address 0xe1050b (thread 002f), starting debugger...
err:alsa:wine_snd_pcm_recover underrun occurred
err:ntdll:RtlpWaitForCriticalSection section 0x7e775d80 "gdiobj.c: gdi_section"
```

I did manage to be able to play Perfect World back in Ubuntu 10.10 64 bit.
Operating System: Kubuntu 11.10 64 bit
Wine 1.2.3
Video Card: Nvidia 8600 GTS
Games Downloaded: Forsaken World, Rusty Hearts

Links to the Free MMO Games:
[**Forsaken World Download**](http://fw.perfectworld.com/download)
[**Perfect World Download**](http://pwi.perfectworld.com/download)
[**Rusty Hearts Download**](http://rustyhearts.perfectworld.com/download)

---

### Post by TurtleKing on 2011-10-24
bump

---

### Post by Soulcage on 2011-10-25
You would probably have better luck using wine1.3.

---

### Post by TurtleKing on 2011-10-29
Tried wine 1.3 and get the follow error:
```
username@computer:~/.wine/drive_c/Perfect World Entertainment/Forsaken World$ wine patcher.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f930,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f868,0x00000000), stub!
```
:(

---

### Post by ergo-proxy on 2011-10-30
It doesn't look too good:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12391](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12391)

---

### Post by TurtleKing on 2011-10-31
"Rating: Garbage" :lolflag:
Thanks for the heads up.

---

