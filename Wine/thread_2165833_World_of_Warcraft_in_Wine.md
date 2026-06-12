---
title: "World of Warcraft in Wine"
date: 2013-08-06
forum: Wine
---

### Post by LinXNut on 2013-08-06
Hey guys! I know a couple people have messaged me about getting World of Warcraft to work and play correctly under wine. 
I have decided to make a simple step by step guide to ensure your World of Warcraft installation will be smooth and easy.

[SIZE=5]** Step 1**[/SIZE][SIZE=5]- Can my Graphics Card play this?[/SIZE]

To ensure your graphics drivers are able to play WoW, open a Terminal and type in....
```
glxinfo | grep rendering
```
You should see an output of something like
```
jonathan@Jonathan-LinuxBox:~$ glxinfo | grep rendering
direct rendering: Yes
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
jonathan@Jonathan-LinuxBox:~$ 
```

The important line is "Direct Rendering - yes." This will ensure all the available modules load correctly in-game. If your output shows "Direct Rendering - no", please consult the hardware forums for the best support.

[SIZE=5]
**Step 2** - [/SIZE][SIZE=5]Installing Wine
[/SIZE]

The official WineHQ website has shown that the wine version offered in the Ubuntu Software Center is NOT the one to install for World of Warcraft. Many individuals have tweaked and been able to play using the available package from the software center, but to be safe I will show you how to install wine version "1.6" instead.

First off, we will need to add a repository to the download manager. Open up a terminal and type in....
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
This will add a new repo to ensure your wine download of 1.6. (Current).
Next, run the following commands...
```
sudo apt-get update
sudo apt-get install wine1.6 ; sudo apt-get install winetricks
```
During the installation, screens may pop up asking to accept the agreement of terms, just hit TAB and press enter to accept them. 
Once the installation is finished, type in the Terminal...
```
winecfg
```
This command will create a new ".wine" directory and also bring up the configuration. Usually everything to run World of Warcraft is ready to go, but to be safe click on all the tabs in the configuration box. (Example: Clicking on the Audio tab will automatically detect settings and ensure your sound works.)

Congratulations you have installed Wine 1.6!!

[SIZE=5]
**Step 3** - Installing World of Warcraft[/SIZE]
To download World of Warcraft visit this site: [https://us.battle.net/account/download/](https://us.battle.net/account/download/)

Click on the World of Warcraft windows download and save the file to your "Downloads" folder. Once the download is complete, open up a terminal and type in....
```
cd Downloads 
wine World*
```
These commands should bring up the World of Warcraft installer. Once all questions are completed, the download of the game will begin and you can then proceed to hit "Play" on the launcher and begin your journey in Azeroth!



[I][SIZE=4]I hope this guide helps, please leave comments if anyone finds a bug or needs further help!
[/SIZE][/I][SIZE=5]
[/SIZE][SIZE=5]

[/SIZE]

---

### Post by 1s3ct0wn on 2013-08-06
Hello, thanks for your time and effort how about those who want to play on private servers? For example I don't like new expansions and I prefare to play on private TBC or vanilla servers.

Best regards.

---

### Post by LinXNut on 2013-08-06
To be honest I'm not really familiar with private servers, but I do know most of them don't go past the Cataclysm expansion. I would think the wine installation and everything else stays the same, you would just have to do a little modding to the World of Warcraft home folder.

For example: [URL="http://heroes-wow.com/page/connect"]http://heroes-wow.com/page/connect
[/URL]
This private server has their own patch created by them. They don't go past 3.3.5a Wotlk (Wrath of the Lich King). I would think if you follow the directions correctly with installing the patches and stuff, it SHOULD work. But again I'm not too familiar with private servers.

---

### Post by holastickboy on 2013-08-12
It's the same with private servers.  Difference is, you usually launch the wow executable directly, rather than through the launcher.  Something like "wine wow.exe" instead of "wine launcher.exe".

---

### Post by will1982 on 2013-08-12
Nice guide, thanks! Is the performance decent? My laptop can barely run WoW as is...

---

### Post by Gilad_Pellaeon on 2013-08-12
I want to point out that if you're using Intel Q963/Q965 integrated graphics there is a known system lockup bug in WoW that Blizzard has known about for a couple of years now but refuses to fix. I had tested WoW a few months ago when my machine had Windows XP on it. I could run around Stormwind and do whatever but the second I would watch an in game cinema movie, such as for example the one of Deathwing's death near the lake by stormwind where all the portals are, about 5-10 seconds after you were done watching the cinema the system would lock up hard, then a few seconds after that you'd hear a couple of beeps and you'd see the computer reboot. 

I seem to recall switching to OPENGL didn't help either in Windows and, knowing blizzard since I suspect it's a problem with their game code as my sister runs WoW on an even older system with different intel graphics chipset that came with an old Dell Dimension 3100 and she has no lockup problems. It's why I believe if you were to test this with WINE under *buntu you'd probably encounter that same system lockup that would probably at the least lockup WINE or worse yet screw up your *buntu system and make it reboot.

---

### Post by Toz on 2013-08-12
*Moved to the **Wine** Subform.*

---

