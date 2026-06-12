---
title: "Warcraft III problem with wine"
date: 2007-11-08
forum: Wine
---

### Post by minhdinh on 2007-11-08
hi i am new to ubuntu and i am trying to install and get warcraft III frozen throne to work but i am having no luck. i am using the latest version of wine from the synaptic pakage manager and i am using ubuntu 7.10. 

i am using duel boot with vista so i installed warcraft3 on my vista partition and updated everything and i then copied the whole folder into my drive_c directory in wine on my ubuntu partition.

the problem i am having now is when i load warcraft 3 using this code
wine FrozenThrone -opengl
the splash screen comes up and then rite after that my whole screen goes black and i cant do anything and ive read all the other threads on this but its not helping me out cuz some people this game works perfectly but for me i can only go to the splash screen. 

the specs for my laptop are
Acer Aspire 5570-2094
intel pentium duel-core processor T2060 (1.6 GHz, 533 MHz FSB, 1 MB L2 cache)
intel graphics media accelerator 950
160GB HDD


someone PLEASE help me get warcraft to work because currently i am only playing war3 and starcraft broodwars on my vista partition and i want to continue using linux cuz i think it is a nice change from vista but without being able to run windows games properly im not sure if im gonna continue using it. btw i didnt install starcraft on linux yet cuz i want to get my problems with war3 fixed first

---

### Post by hakimaki on 2007-11-08
maybe this will help
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=897]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=897")

---

### Post by minhdinh on 2007-11-08
i already tried using the guide on the wine website but there is a step that i dont know wat to do

"It helps to add a device node symlink, so do the following. If your cd-rom drive letter in winecfg is d: and the corresponding device node to your mount point is /dev/hdc then run the following command:
$ ln -s /dev/hdc ~/.wine/dosdevices/d\:\:
Note, you *must* have two colons! You can tell what your device node is in /etc/fstab or by viewing your boot-log."

i dont know wat a node is but my cd drive is D: and for the drive mapping its /media/cdrom0


remember i am almost completely new to ubuntu and linux so if u think u know wat im doing wrong or wat i should be doing please give me a step by step instruction explaining exactly wat i have to do to get this game to work

---

### Post by minhdinh on 2007-11-08
i managed to get warcraft to load but after that im stuck again. anytime i try to play single player games it wouldnt work it will load and then it just freezes and battle.net doesnt work but i already know it wont work with the newest version of wine. so rite now all i want is someone to help me play single player without freezing on loading screen

---

### Post by tribut on 2007-11-10
Having the same problem. WC3 freezes when the loading-bar for a campaign szenario hits about 2/3. Playing a random single-player game against the computer works fine, though.
[IMG]http://secundus.stunet.tu-freiberg.de/~felix/temp/screenshots/wc3-freeze.png[/IMG]
After that, the window does not even redraw any more...

---

### Post by EtrnlApocaplypse on 2007-11-10
First of all do you switch to metacity before playing? Running compiz with games especially in Wine create issues. Other than that it sounds like everything should be fine.

---

### Post by tribut on 2007-11-10
> **EtrnlApocaplypse said:**
> First of all do you switch to metacity before playing?

Thank you for your input, but as I'm running KDE it's kwin. However, everything else works (except the freeze in the loading-screen) so I really don't think it is a environment-related problem...

---

### Post by sum][one on 2007-11-10
I've got the same problem  here ... campaign wont load and hangs after progress bar reaches 2/3 (like screeshot posted) ... I hope anybody have a solution for that... I'm not using compiz or xgl at all ... everything is disabled... since I use this laptop for 3D and comp works as well... 
any news on this issue?

Ubuntu 7.10 here.

---

### Post by terrukallan on 2007-11-12
As others have mentioned, when trying to load a campaign the bar freezes about two thirds of the way through.  Random singe-player games work fine, though I have no sound.

Also, I have intermittent trouble getting the game to start at all.  It seems to work best when I start it from the autoplay.exe, but even that is not 100% reliable.  When it doesn't work I get one of two problems:
1) Repeated requests to insert the Warcraft III cd despite it being in the drive.
2) The game loads, but justs gives an unresponsive black screen.

I'm running Ubuntu 7.04 without compiz and have observed the same issues in wine versions 0.9.38, 0.9.47, and 0.9.49.  This suggests to me that the problem is not with wine itself, but rather with something interacting with wine.
[COLOR="Red"]
EDIT[/COLOR] Console output on black screen failure:
```
ALSA lib pcm_dmix.c:803:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x34f1f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4a4,0x00000000), stub!

```

[COLOR="Red"]EDIT2[/COLOR]:
Tried wine 0.9.41 with no more success.  Also the game now seems to completely refuse to start--black screen failure every time.

---

### Post by hadeshorn on 2007-11-14
Yep I am having the EXACTLY same problem. Crashes 2/3rds of the way.

Using latest Wine. Warcraft3 is patched to 1.21a.

Using Gutsy X86 with an ATI x700. Compiz is disabled!

Any ideas?

---

### Post by ChaiTan on 2007-11-15
Even i have the same prob in gutsy....Warcraft III worked perfectly in feisty...no hangs ups
its only in gutsy that the campaigns stop loading at 2/3 of progress bar
someone should file a bug report

---

### Post by ChaiTan on 2007-11-15
I tried the feisty packages in gutsy but no luck....the prob is only with gutsy

---

### Post by minhdinh on 2007-11-18
man this really sucks warcraft III is a great game but if u cant play it in gutsy at all then i guess i have to stick to using vista more than ubuntu cuz i dont like to restart my laptop everytime i want to play warcraft or any game.

---

### Post by -gabe-noob- on 2007-11-18
My sound works fine, and the game loads great. I have horrid mouse lag and some graphical anomolies though. The units seem to move fine but the mouse is horribly slow. Also sometimes the unit's images come out white. I've tried launching the game in OpenGl but for somereason I cant. any sugestions?

---

### Post by Surtr on 2007-11-22
I had the same problem (loading campaign) on Feisty, after updating my Wine I think. Now I have the same problem again with Gutsy.

---

### Post by hadeshorn on 2007-11-24
I fixed my problems with Warcraft III.. I did this by reverting back to wine 9.40 or something. Apparently the latest wine kills some parts of warcraft III.

It runs beautifully now. The reason maybe it breaks under gutsy is that gutsy is loading the latest version of wine.

Trust me on the revert.

---

### Post by I have no job on 2007-11-25
Well, im using Gutsy and i cant play warcraft 3 in wine, but works fine in CEDEGA, i dont know why..... im using an intel 865g onboard video card and i can play teh game with fulll graphics and with compiz enabled using cedega, but with wine even with -opengl game runs with error graphics.....do you guys tried to use cedega ? problem is : cant play online with new cedega version too

---

### Post by kannho on 2007-11-27
I was using the latest wine from winehq when I had that particular problem.  The game loading bar just stop when reach the 2/3.  

I solved that by using the 0.9.43 version and now everything is working fine!  :)

---

### Post by hotweiss on 2007-11-28
It works perfectly on Cedega...

---

### Post by minhdinh on 2007-11-28
can someone tell me how to get a working version of cedega without paying for it. thank you

---

### Post by Ziox on 2007-12-24
Solution:

Install the LATEST version of Wine from WineHQ, and everything shall be fine!

---

