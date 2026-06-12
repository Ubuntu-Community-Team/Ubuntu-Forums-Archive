---
title: "Ubuntu 14.04 - Age Of Mythology (Could not load pidgen.dll, I checked other posts)"
date: 2014-06-01
forum: Wine
---

### Post by Madhav_Mohan on 2014-06-01
I recently installed Ubuntu 14.04 64 bit (That makes me a noob) and for the love of god I can't figure out how to install Age of Mythology.
It was confirmed to be working on previous versions of Ubuntu (I checked wineHQ).
Things I've done after checking on various posts- 
Copied pidgen.dll from disk 1 to system32 folder of wine C drive.
Downloaded mfc42.dll and put it in system 32 folder.
Yet it shows the same error as it did - 'Could not load pidgen.dll')
Does anyone on 14.04 still play this game? If so, how did you get it to work?
And if anyone has help to offer, ANYTHING, don't think twice :D

---

### Post by adec2 on 2014-06-01
I am using Kubuntu 14.04 64 bit but i use playonlinux with wine version 1.5.0 and it works fine. Playonlinux also has its own install script that you can run to install the game. Maybe its worth giving that a try?

Also did you make sure to do this part BEFORE running the game?

[COLOR=#000000][FONT=bitstream vera sans]Run "winecfg" from the command line.  Click the "Libraries" tab at the top of the window that appears.[/FONT][/COLOR]
[COLOR=#000000][FONT=bitstream vera sans]Type the name of the library into "New override for library:" (type "pidgen" for PidGen.DLL).  Click "Add",[/FONT][/COLOR]
[COLOR=#000000][FONT=bitstream vera sans]make sure that "(native, builtin)" appears next to the library you just added.  If it doesn't highlight the new[/FONT][/COLOR]
[COLOR=#000000][FONT=bitstream vera sans]override and click "Edit" select "Native then builtin" and click "OK" and finally click "OK".

Blatant copy and paste from the winehq sorry

Personally I find wine fantastic BUT i prefer running playonlinux as it makes working with different prefixes easier IMHO. Many of my older games work fine with older Wine versions but have broken in later releases so once I find it works ok (like Age Of Mythology for me with 1.5.0) i use playonlinux to always run it with that wine version that works even if my system always has the latest wine installed (Just for testing some games that previously didnt work)[/FONT][/COLOR]

---

