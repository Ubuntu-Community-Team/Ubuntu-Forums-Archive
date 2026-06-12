---
title: "Unable to play World of Warcraft"
date: 2011-09-13
forum: Wine
---

### Post by davy jones on 2011-09-13
OK so I had read that WoW was one of the games that had been tested with Wine and could be played in ubuntu using that. So I installed Wine 1.3 in Natty and went to winetricks and downloaded the WoW trial thing that's there. It made me download 10 GB worth of data but now when I open the launcher and click on play, nothing happens. What do I do?
This is the screenshot of the launcher.

---

### Post by haqking on 2011-09-13
> **davy jones said:**
> OK so I had read that WoW was one of the games that had been tested with Wine and could be played in ubuntu using that. So I installed Wine 1.3 in Natty and went to winetricks and downloaded the WoW trial thing that's there. It made me download 10 GB worth of data but now when I open the launcher and click on play, nothing happens. What do I do?
This is the screenshot of the launcher.


I am not a game player.

However there is a WoW in WINE on Ubuntu HOWTO on [here ]("http://ubuntuforums.org/showthread.php?t=579378&highlight=world+warcraft")

---

### Post by seawolf167 on 2011-09-13
There is a wowwiki on installation through Wine located [here ]("http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine")as well ([here ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922")is the 'official' Wine article)

---

### Post by davy jones on 2011-09-14
I have seen these but they're not really relevant to my problem. I downloaded it from winetricks and these how-to's don't give instructions relating to that. I want to know what to do now to make it work because I've downloaded 10 GB worth of data and I'm still nowhere.

---

### Post by ubiquitin.jf on 2011-09-14
I'm having the same problem when launching the latest retail version. The attached error pops up after a couple of minutes.

---

### Post by davy jones on 2011-09-14
I've figured out how to open the game. The 'World of Warcraft' link at Applications->Wine->Programs->World of Warcraft is the launcher but its not the link to open the game. I went to Winetricks->Select WoW->Browse Files and the WoW.exe file which opens the actual game is there. It opened and everything but now the only thing I need to know is how to play for free because it asks for my battle.net account and password and that is not linked to World of Warcraft. To link it I need some sort of code. Any suggestions on how to get it for free? (This is WoW Cataclysm just fyi)

---

### Post by haqking on 2011-09-14
> **davy jones said:**
> I've figured out how to open the game. The 'World of Warcraft' link at Applications->Wine->Programs->World of Warcraft is the launcher but its not the link to open the game. I went to Winetricks->Select WoW->Browse Files and the WoW.exe file which opens the actual game is there. It opened and everything but now the only thing I need to know is how to play for free because it asks for my battle.net account and password and that is not linked to World of Warcraft. To link it I need some sort of code. Any suggestions on how to get it for free? (This is WoW Cataclysm just fyi)


for free ? you need an account to play it which you have to pay for dont you ?

---

### Post by davy jones on 2011-09-14
There are workarounds apparently which let you play for free. I've tried one but it didn't work for me

---

### Post by haqking on 2011-09-14
> **davy jones said:**
> There are workarounds apparently which let you play for free. I've tried one but it didn't work for me


endless trial mode is legal [http://www.pcgamer.com/2011/06/28/play-world-of-warcraft-for-free-forever-with-the-new-endless-trial-mode/](http://www.pcgamer.com/2011/06/28/play-world-of-warcraft-for-free-forever-with-the-new-endless-trial-mode/)

anything else would not be legal as far as i know

---

### Post by CharlesA on 2011-09-14
> **haqking said:**
> endless trial mode is legal [http://www.pcgamer.com/2011/06/28/play-world-of-warcraft-for-free-forever-with-the-new-endless-trial-mode/](http://www.pcgamer.com/2011/06/28/play-world-of-warcraft-for-free-forever-with-the-new-endless-trial-mode/)

anything else would not be legal as far as i know
^ That.

Take note of the restrictions - max level of 20 and 10 gold among others.

---

### Post by blueridgedog on 2011-09-14
> **davy jones said:**
> the only thing I need to know is how to play for free

There is no effective way to play for free.  The trial is so crippled to make it hard to effectively use the game.  You must have an account.

---

### Post by CharlesA on 2011-09-14
> **blueridgedog said:**
> There is no effective way to play for free.  The trial is so crippled to make it hard to effectively use the game.  You must have an account.
Agreed. I've heard of private servers, but those are against Blizzard's ToU so we are not even going to go there.

---

### Post by h4x0l2 on 2011-09-14
> **davy jones said:**
> OK so I had read that WoW was one of the games that had been tested with Wine and could be played in ubuntu using that. So I installed Wine 1.3 in Natty and went to winetricks and downloaded the WoW trial thing that's there. It made me download 10 GB worth of data but now when I open the launcher and click on play, nothing happens. What do I do?
This is the screenshot of the launcher.


Don't worry about it, you're better off!:P

---

### Post by davy jones on 2011-09-23
I'm playing the trial version and its running fine except for the sound which keeps going off and I've to exit the game and then start it again which is just very annoying. Any solutions?

---

### Post by jzakilla on 2011-10-22
first, you have to have an account to play full version, past level 20. I've been playing wow on ubuntu linux for quite some time now, had problems at first till i followed the instructions EXACTLY at this website: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

as far as your audio troubles go, try this:
1. go to your wine folder, it should be in your home folder, however it's hidden so you'll have open the home folder then hit CTRL+h on your keyboard to display hidden files.
2. browse through till your find your config.wtf file in the wow folder
3. find two entries that look like this:
SET Sound_SoundOutputSystem ""
SET Sound_SoundBufferSize ""
change to look like:
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

the soundbuffersize value isn't a constant, it goes from 50 to 300, and the optimal value will differ from system to system, try different values to see what works best for you. If you're getting no sound at all, take a look at the link i put in here and there is a section that addresses that problem as well.

---

### Post by rsvancara on 2011-10-23
The trick to playing this game from my experience is to launch it from the command line. By launching it from the command line, you can see any errors that pop up in launching the game.  This makes it easier to obtain assistance on the forums (be it this one or the wine forum).  

During the installation, depending on how it is installed, the game executable, WoW.exe is located most likely in your:

```
.wine/drive_c/Program Files
```

In there is probably a folder called World of Warcraft.  

In this directory, launch WoW like this:

```
wine WoW.exe -opengl 
```

The above command specifies WoW to use opengl rather than the default, direct3d.  In my experience again, this has yielded better results.  However, you may leave off the -opengl option in order for the game to run in direct3d mode.  There are settings to put in the wtf.config so that you do not have to specify -opengl...

Now some problems you may encounter.  First of all the Unity interface in conjunction with compiz usually takes over your graphics card and I have had problems in the past using Unity or any other compiz enabled window manager in conjunction with wine and opengl.  The solution is to disable all the compiz garbage by launching your window manager in basic mode or whatever it is called.  You can select this option when first logging in.  

If you experience 3d acceleration issues, it would be helpful to see the output of glxinfo as well.  Specifically the following command will tell most folks what they need to know:

```
glxinfo |grep  'direct rendering'
```

--Randall
[http://www.knowyourlinux.com](http://www.knowyourlinux.com)

---

