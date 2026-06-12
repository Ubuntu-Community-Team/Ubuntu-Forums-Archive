---
title: "Warcraft III freezes and crashing"
date: 2008-07-19
forum: Wine
---

### Post by Horomancer on 2008-07-19
Hey there, I've done a number of searches on the forums about problems running warcraft III. I decided to make a new thread since most of the info i found was either for older versions of wine and the Warcraft patches, or for WOW.

I'm running TFT through the War3_CK.exe that was made after using the v1.22 patch. There is no pattern to the freezes or crashing. At random points (some times an hour into play sometimes only a minute or two) the game will either
1) Freeze the screen plating the last bit of sound on loop. The keyboard does not respond and leaves me with the option of a hard reboot
2) The screen goes black then pops up the monitor's Signal out of range sign meaning that the computer is no longer transmitting info. Again hard reboot.

Running Wine v1.1.1 and have not had this trouble with other games. Nothing about TFT seems buggy aside from the crashing.

---

### Post by zir0n on 2008-07-20
[http://ubuntuforums.org/showpost.php?p=5392394&postcount=35](http://ubuntuforums.org/showpost.php?p=5392394&postcount=35)

there seems to be a bug with the openGL in the newer versions of wine. View the whole thread for more details.

---

### Post by Horomancer on 2008-07-20
OK i did the patch work you have listed in your tutorial with the wine v1.1.1 tar.gz files. I'm also trying to run the WAR3_CK.exe file with the -opengl switch from the terminal.
The trouble i am having is that the terminal doens't like me typing in 'Program Files' in the file path and it doesn't recognize 'Program_Files' as a valid path.

If i run the .exe as of righ now i still have the same troubles as before.

EDIT:

I ended up changing the names of some of the dirs and amange to use the command

WINEDEBUG=-all wine /path/to/warcraft/warcraft_exe_name.exe -opengl

Will i have to open the .exe in the terminal with -opengl everytime i want to play or is it set to the -opengl switch by defualt now?

---

