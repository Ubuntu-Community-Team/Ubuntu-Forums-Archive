---
title: "Fallout New Vegas No In Game Sound"
date: 2011-07-22
forum: Wine
---

### Post by M1ttenz11 on 2011-07-22
Okay, so i got fallout new vegas installed on wine 1.3.24 and it sort of runs fine, how ever once ive started new game/continue game i lose the sound. 
i did manage once to have ALL the sound, i then quit game and rebooted my computer and lost the 'In game sound' again.
I believe i got the sound working whilst faffing on in wine.cfg > Libraries > winegstreamer > disabled, and a mix of Audio ALSA and JACK.
However i have read something on some one saying that they got it to work but they needed Jack2d program and i can't seem to find a download anywhere.
Im just wonder if anyone can help me. im running ubuntu 10.04 if it makes a difference ;P.

and those screen shots are my wine.cfg

Thanks!

---

### Post by jacksaff on 2011-07-23
Try setting 'direct sound' to 'emulation' in the wine configuration widget.

---

### Post by M1ttenz11 on 2011-07-23
Great thanks! got sound no lag runs fine.. Except...
I just ran a whole new game..
Doc' Mitchells house worked so well, so and everything no having to tap escape etc [previous problem i've had]  it crashed when i exited the house, loaded back up and left and it worked, then about 20-30mins of playing it crashed again and i had to re insert ram.. any idea of fixing this ^^? thanks :)

---

### Post by M1ttenz11 on 2011-07-23
Think ive fixed it. Emulator for the sound! works fine.
and then run the NVLauncher.exe dont click play, but then open FalloutNV.exe

>FalloutNVLauncher.exe 
>FalloutNV.exe

works with sound no lag. played for about 2hours game crashed, loaded it back up and worked fine!
this may be problem solved so i will close this tomorrow morning if i have no further problems other than this minor crash. 

also before I forget, adding the d3d9dll to your fallout folder might help. just extract the .rar, copy and paste file to your fallout new vegas folder in C:/programme files/ Bethesda Games/Fallout new vegas folder hope this helps. You can get the d3d9dll from here [http://www.megaupload.com/?d=SBKTSC88](http://www.megaupload.com/?d=SBKTSC88) I uploaded this myself and its virus free check the screen shots.

Regards to Jacksaff for directing me to emulator sound in wine.cfg
for in game sound.

---

