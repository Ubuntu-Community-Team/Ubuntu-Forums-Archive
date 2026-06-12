---
title: "Morrowind: to bug or not to bug..."
date: 2014-07-24
forum: Wine
---

### Post by Johyn on 2014-07-24
Greetings all! :p

Does someone knows if, with Morrowind, that's normally bugging at the loading pages, with darkening and askew screens, or caused by a bad installation, files having been extracted with the archive manager, and not 7zip, as they are, eh?

---

### Post by mastablasta on 2014-07-25
at least you got something. mine didn't even run. anyway.... it appears you need d3d9x corefonts and Tahoma preinstalled. I couldn't get Tahoma through winetricks but I am trying to do the other two like that. and see if it will ruin then. after that it should be smooth install with game being awarded a platinum rating.

I too had to extract the files form iso images since I do not have a CD on the netbook.

---

### Post by mastablasta on 2014-07-25
it seems this is caused by widescreen. try using morrowind FPS optimizer and set the resolution before launch. it's windows applciation but also works in wine. just got it to work. no scewed screen anymore.

---

### Post by Johyn on 2014-07-25
Cheers! 

I just started the game, working perfectly, thanks to that wondrous FPS optimizer. Thanks to you also, and wishing you such a good start on your game! :)

---

### Post by mastablasta on 2014-08-01
how did you solve the minimized windows bug? conversation windows are always minimized. apparently this is an issue in morrowind.ini and this is always reset on start. solution is to block access to .ini file for writing. but I am not sure what this will have as consequence. also I am not sure why this get's rewritten. the folder mounted as CD rom has no effect, so I moved the video files to video and now there is no issues with starting the game. IMO this definitely should not be platinum rating...

---

