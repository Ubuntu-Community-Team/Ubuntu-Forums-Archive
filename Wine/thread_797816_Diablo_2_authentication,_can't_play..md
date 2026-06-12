---
title: "Diablo 2 authentication, can't play."
date: 2008-05-17
forum: Wine
---

### Post by drgnfang on 2008-05-17
i installed Diablo 2 (no expansion pack) by right clicking the install icon in the cd and clicking open with "wine windows emulator" and went through the full installation the way one would do it on windows. installation was successful. 

when i try to start up the game (with the play disk in, of course), i get a black screen with a little white rectangle in the upper left corner and a window pops up saying "UNHANDLED EXCEPTION: AUTHENTICATION_VIOLATION." no cinematic starts. that is all that happens. i looked everywhere for the same problem but nobody had the same one as me. is it the way i installed it?

if you could tell me how to run it in the terminal so I could tell you the output it would be appreciated. thank you.:popcorn:

Me wine version is 0.9.59

---

### Post by edv on 2008-05-20
> **drgnfang said:**
> if you could tell me how to run it in the terminal so I could tell you the output it would be appreciated. thank you.:popcorn:Open a terminal, then use the command cd to get to the directory you installed the game in. By default the command would probably be:```
cd ~/.wine/drive_c/Program\ Files/Diablo\ II/
```When there type:```
wine Game.exe
```If that doesn't work, you can also try:```
wine Diablo\ II.exe
```

---

