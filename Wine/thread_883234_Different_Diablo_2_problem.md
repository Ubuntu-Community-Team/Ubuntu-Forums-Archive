---
title: "Different Diablo 2 problem"
date: 2008-08-07
forum: Wine
---

### Post by gettingfrustrated on 2008-08-07
I have been a happy Ubuntu user for 6 months now...with the exception of one problem---Wine

I have not been able to get 1 game to work on my system (through Wine) since I switched to Ubuntu (despite many platinum ratings on the wine site)

Diablo 2
CnC tiberian sun
Ceasar 3
Civ 3 and 4
CnC Generals Zero Hour

The problem is never the install, which every game does effortlessly.
Its in the starting, loading etc..Heres an example:

after 2 hours (not including install) I have given up on Diablo 2, 
As usual it installs fine...When i right click DiabloII.exe and click openwith...wine program loader I get Blizzard opening page than another blizzard screen and then only music and a blank screen.

I installed the latest patch (1.12) and glide 14b

Im on Hardy 8.04
Kernel 2.6.24-19
pent 4 2.8 ghz 
nvidia geforce 6200 128 mb ddr
wine 1.0

using this guide step for step:
[http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+installation](http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+installation)

using the terminal commands helps some people here however im fairly new to ubuntu and do not know hardly any commands for the terminal, So im not very comfortable using it.

Generally im having the same problems with every one of the games listed above (they are all original disks I purchased with serial numbers)

If anyone can help out a noob I would greatly appreciate it... Warzone 2100 is a great game but its wearing on me.

---

### Post by werries on 2008-08-07
your problem is probably glide. why would you install that?

---

### Post by gettingfrustrated on 2008-08-07
Thanks for responding... I dont remember where i got that from (glide) but I took it off and rebooted and still same problem

---

### Post by werries on 2008-08-07
do you have the drivers for your graphics cards? like for nvidia graphics cards, nvida-glx-new or nvidia-glx. or by using envy-ng

---

### Post by gettingfrustrated on 2008-08-07
Yes, videocard and drivers are good...Just tried reinstalling very slowly and meticulously and... new problem... While applying the patch I get error cant find binkw32.dll I tried reinstalling binkw32.dll...same problem even though the file is right in the same folder...I think I'm going to give up on wine, it has never worked on ANY program i have tried and I have spent waaaay too much time trying to get any games going (6 months and no success)


I will never put that pos resource hog windows back on my system again... So dual booting is out of the question for me. Are there any other alternatives to wine?

---

### Post by aoanla on 2008-08-08
Forgive me if this sounds insulting, as it's not meant to be:

I find it very very confusing that you're having so many problems getting things to work in Wine. 

(There is, by the way, essentially nothing that competes with Wine - Cedega and CrossOver are both based on Wine themselves).

So, I'd like to see if we can diagnose what must be a common problem with your configuration of Wine, or your system, which is breaking games you try to run (since, we *know* that Wine is quite capable of running those games, as they have multiple platinum ratings ;) ).

Firstly, can you please tell me the /version/ of the nvidia drivers you have installed?

Have you tried setting Desktop Effects to "none" (in System->Preferences->Appearance, I think), which should turn off Compiz, and then running your game?

Have you (and this is /very important/ so that we get information to help you) tried running them from the terminal, so we get some debugging information from Wine?
For Diablo II, if it's installed in the default location, you'd want to do:

cd ~/.wine/drive_c/Program\ Files/Diablo2
wine "Diablo II.exe"


and then tell us about any error messages that appear in the terminal.

Frankly, this looks, considering it's happening with /all/ your games, an awful lot like a graphics-driver/wine interaction issue, that can probably be fixed.

---

### Post by gettingfrustrated on 2008-08-08
No offense taken...Actually I appreciate the help

I'm still a noob so please bear with me..I dont like asking for help, So this is my first time doing so

to answer your questions 

1. Driver info nvidia unix x86 kernel module 169.12 (I assumed that the driver works as I have been playing native linux games with no problems. Savage 2, Glest, Warzone Etc..)

2. yes, turned off compiz...same result (this is the first time i have heard of trying this..Does this apply always when running games on wine?)

3. As I have stated in my OP Im not comfortable running the terminal mainly because I have not learned command lines nor have I found a place that adequately describes command lines for beginners. (IMO this is the biggest problem with drawing people from windows to linux.. along with the games)
This is the error I have from the terminal:

john@Johns-Rig:~$ cd ~/.wine/drive_c/Program\ Files/Diablo2
bash: cd: /home/john/.wine/drive_c/Program Files/Diablo2: No such file or directory

Also tried with Diablo II that is what the folders name is on my system (not Diablo2)...Got the same result no such file or directory

My config in wine:

Added Diablo II.exe windows xp (also tried 2000 as in the tutorial)
alsa enabled (sound works fine)
unclick allow windows manager to control windows (also in tute)
I also tried emulate virtual desktop (on seperate occasion) It seems that its trying to play full screen and i have noticed that most are playing the game in windowed mode

one last thing:
Should I even be trying to use wine without a proper knowledge of how to use the terminal commands?

Thanks for the help!

---

### Post by werries on 2008-08-08
Wine should barely ever need a terminal command.
but if you want to learn the terminal, try [www.linuxcommand.org](www.linuxcommand.org)
:)
This is weird. Try uninstalling wine, then delete the hidden .wine folder. then reinstall wine and try a game again.

---

