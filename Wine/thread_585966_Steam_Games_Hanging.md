---
title: "Steam Games Hanging"
date: 2007-10-21
forum: Wine
---

### Post by joshL on 2007-10-21
OK, I bet everyone is getting tired of the Steam questions however I'm to new to fix this.  So here goes... After spending 3 hours getting steam and wine installed last night I played portal for about 4 hours. Some time later Ubuntu told me there was an update to wine so I had it installed. Now all the games lock up after about 5 sec of play? I have already tried reinstalling wine. Is there a way to remove the update that was installed last night?

Thank you for any help you can give!

Josh

---

### Post by esodin on 2007-10-21
Could you confirme what Ubuntu version you are running? I had the same issue under 7.04 (Feisty) and ended up getting wine directly from wineHQ.

After I uppgraded to Gutsy (7.10) I have no problems. I'll check my settings when I get home and post what workes for me.

---

### Post by aoanla on 2007-10-22
If you remember what the previous version of wine you installed was, you can download the deb package from the links here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

then a 

sudo dpkg -i <name of file you just downloaded>

will restore you to that version of wine.

Note that the most recent release of wine, 0.9.47 seems to be rather unstable for a lot of people playing Source engine games, so that's probably the version you're running now.

---

### Post by esodin on 2007-10-22
Ok, here is what works for me:

I am running Gutsy and wine 0.9.46 (out of the box).

**In wine config:**
- Applications > Add application: [COLOR="Blue"]hl2.exe[/COLOR]
- Applications: select [COLOR="Blue"]hl2.exe[/COLOR] then Windows Version: [COLOR="Blue"]Windows 98[/COLOR] (if I try Win XP the system crashes)
- Applications > Add application:[COLOR="Blue"]steam.exe[/COLOR]
- Applications: select [COLOR="Blue"]steam.exe[/COLOR] then Windows Version: [COLOR="Blue"]Windows XP[/COLOR] (Steam will not install under 98 )

- Audio > Sound Drivers > [COLOR="Blue"]ALSA Driver[/COLOR] (and only ALSA!)
- Audio > Hardware Acceleration: [COLOR="Blue"]Full[/COLOR]
- Audio > Default Sample Rate: [COLOR="Blue"]44100[/COLOR] and Def. Bits Per Sample: [COLOR="Blue"]16[/COLOR]
- Audio > Driver Emulation: [COLOR="Blue"]checked[/COLOR] 

- Graphics > [COLOR="Blue"]Check the 2 top boxes[/COLOR]
- Graphics > Direct3D: [COLOR="Blue"]Hardware[/COLOR]
- Graphics > Check [COLOR="Blue"]Allow Pixel Shader[/COLOR]

**Starting Steam**
I start the game I want to run directly. Earlier this was the only way I could get it to work righ because I use 2x19' monitors and TwinView and the game would start trying to fill both monitors (both in full screen and windowed mode). Steam  seems to have updated something, because now the window for the game stays the way it should even if you switch (through Steam) from, say, CSS to Portal.

I use the following command line to start a game:
```
:~$ env WINEPREFIX="/home/jomar/.wine" WINEDEBUG="-all" wine "C:\Program Files\Steam\steam.exe" -applaunch 240 -window -width 1240 -gl -dxlevel81
```
[LIST]
[*]The [COLOR="DarkRed"] env WINEPREFIX="/home/jomar/.wine"[/COLOR] part is there so if you put it in the "Launcher" under icon - it will know where to run the program from.
[*]The [COLOR="DarkRed"]WINEDEBUG="-all"[/COLOR] part turn off the error messages from wine. Not turning this off is the main reason ppl only get 1-5 FPS. (the system is too busy producing error messages)
[*][COLOR="DarkRed"]wine "C:\Program Files\Steam\steam.exe"[/COLOR] starts the game
[*][COLOR="DarkRed"]-applaunch 240[/COLOR] tells it to start CS:S (exchange with 440 for TF2, 400 for Portal, etc)
[*][COLOR="DarkRed"]-window[/COLOR] starts the game in windowed mode (rather than fullscreen)
[*][COLOR="DarkRed"]-width 1240[/COLOR] sets the window to 1240 by 930 (you can also use -hight xxx but you don't have to give both width and hight. The game defaults to 4:3)
[*][COLOR="DarkRed"]-gl -dxlevel81[/COLOR]sets the DirectX to use (-dxlevel7, -dxlevel80 and -dxlevel9 are also valid) 81 worked for me.
[/LIST]

Hope this can be of help :)

---

### Post by joshL on 2007-10-22
Thanks for all the replys.  I'm sorry I did not post my version before a little bone headed of me.  I just install 7.10 a couple of nights ago.  I am not sure what version of wine 9.47 I think.  I will check when I get home.

Thanks again.:)

-----------------------------

"I am running Gutsy and wine 0.9.46 (out of the box)."

AH HA, I bet I was running 9.46 and it upgraded to 9.47.  I will try and downgrade when I get home.

With any luck I will not have to reboot and log into that "other" OS.

---

### Post by Kekk0 on 2008-06-05
Omg, thank you, thank you, thank you! :D

---

