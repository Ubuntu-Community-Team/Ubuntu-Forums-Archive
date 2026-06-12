---
title: "world of warcraft on ubuntu"
date: 2012-11-10
forum: Wine
---

### Post by darkvexen on 2012-11-10
hey guys i am switching to ubuntu cause i like it alot better than windows but i am having trouble starting up wow. I copied my game from windows to ubuntu and tried starting it up the launcher with wine but when i do it says updating setup files then like 2 min later it says missing agent try again later blah blah blah. so then i try playing through wow.exe but then i get "wow is updating setup files for core game play blah blah blah" or something like that. anyone know how to fix this.

---

### Post by darkvexen on 2012-11-10
update i tried it through the launcher again and it got through updating launcher but now the launcher actually shows and says "failed to write required file. Please close all other applications, temporarily deactivate your anti-virus software, and try again". The funny thing is i dont have any anti virus installed. and the only thing running in the background is google crome.

---

### Post by LordXandor on 2012-11-10
It sounds like wine is having trouble accessing your partition. The anti-virus bit is just a suggestion they give because the program doesn't know what exactly is preventing it from accessing the files. Are your able to run other files in wine? Maybe try a text editor and save a text file to test whether wine can write to the partition, if not that can help tell us where to look for the problem.

---

### Post by darkvexen on 2012-11-10
should i use wine notepad to test?

---

### Post by LordXandor on 2012-11-10
Yes, that should be sufficient.

---

### Post by darkvexen on 2012-11-10
seems to work fine. i can open wine notepad just fine  but i cant seem to save. when i click save it just goes into the folder i want to save it in.

---

### Post by LordXandor on 2012-11-10
Then your issue is wine not wow. Maybe check for an update for wine in your package manager.

---

### Post by darkvexen on 2012-11-10
how can you decide that so quickly?

---

### Post by LordXandor on 2012-11-10
Because two separate programs have issues saving files. The issue should lie in the common ground between them, ie: wine. It sounds like wine cannot write to the partition. It could be a permissions issue. Are you running wine with sudo?

---

### Post by darkvexen on 2012-11-10
idk wgat sudo is. this is a fresh install. all i have is wine and samba.

---

### Post by darkvexen on 2012-11-10
i cecked the software store and it turns out its already installed

---

### Post by LordXandor on 2012-11-10
Alright that could be the issue. Do you know whether you're using KDE or Gnome?

---

### Post by darkvexen on 2012-11-10
uhhhhh, idk. any command i could put in the terminal to find out?

---

### Post by LordXandor on 2012-11-10
Actually try running code:
```
sudo wine
```
It will ask for root password. This is typically your login password. Enter it and then try using wine as normal. The wine GUI should pop up.

---

### Post by Nilladar on 2012-11-10
It is best to run WoW using wine1.5. Also it is important to install some software using winetricks. To do so hit the "super" key, aka the windows key, to launch your unity browser, that is assuming you are using the unity interface. This will bring up a window and I can't remember off the top of my head what the first options are, sorry not at my computer at the moment, but it should be on the correct option. Hit okay, it will ask you if you would like to summit data to the wine project, hit yes or no. One of the options will be install .dll click that and a list of software that can be installed will appear. install vcrun2005/2008/2010 vcrun6, ie8, mfc42, d3dx9_36 d3dx9_39 directplay. This should install files needed for wow to work.

The directx files are optional if you don't plan to use directx and prefer to use opengl. 

Currently I have a bug that crashes the game if i use Pulseaudio. So I have to run the game using WINENOPULSE=1 /path/to/game/wow.exe

Hope this helps and isn't to confusing

---

### Post by darkvexen on 2012-11-11
> **LordXandor said:**
> Actually try running code:
```
sudo wine
```
It will ask for root password. This is typically your login password. Enter it and then try using wine as normal. The wine GUI should pop up.
 woot! got it to work! ty bro!

---

### Post by cwwilson721 on 2012-11-11
> **Nilladar said:**
> [COLOR="Blue"]It is best to run WoW using wine1.5[/COLOR]. [COLOR="Red"]Also it is important to install some software using winetricks.[/COLOR] To do so hit the "super" key, aka the windows key, to launch your unity browser, that is assuming you are using the unity interface. This will bring up a window and I can't remember off the top of my head what the first options are, sorry not at my computer at the moment, but it should be on the correct option. Hit okay, it will ask you if you would like to summit data to the wine project, hit yes or no. One of the options will be install .dll click that and a list of software that can be installed will appear. install vcrun2005/2008/2010 vcrun6, ie8, mfc42, d3dx9_36 d3dx9_39 directplay. This should install files needed for wow to work.

The directx files are optional if you don't plan to use directx and prefer to use opengl. 

Currently I have a bug that crashes the game if i use Pulseaudio. So I have to run the game using WINENOPULSE=1 /path/to/game/wow.exe

Hope this helps and isn't to confusing

[COLOR="Blue"]This is spot on[/COLOR]
[COLOR="Red"]I NEVER run any of that. Not needed, EXCEPT vcrun6 (I think ver2 or something)[/COLOR]

---

### Post by Eskali on 2012-11-12
> **cwwilson721 said:**
> [COLOR=Blue]This is spot on[/COLOR]
[COLOR=Red]I NEVER run any of that. Not needed, EXCEPT vcrun6 (I think ver2 or something)[/COLOR]

^^ You need the beta Wine to get Agent.exe to launch when using the WoW Launcher to play, do;
Sudo add-apt-repository ppa:ubuntu-wine/ppa
Sudo apt-get update
Sudo apt-get install wine1.5

---

### Post by Tweak42 on 2012-11-16
> **darkvexen said:**
> woot! got it to work! ty bro!

Wine should NOT be run with sudo:
[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

> 3. **Never run Wine with sudo** - Do not run Wine as root or by using sudo. Doing so doesn't help anything and will break your fake Windows installation entirely.




Reasons why: 
[http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014](http://wiki.winehq.org/FAQ#head-96bebfa287b4288974de0df23351f278b0d41014)
> Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permissions on your ~/.wine folder in the process. 

---

### Post by Aarbron on 2012-11-16
Hi,

So if you guys are able to grt the Launcher rubbing, this means automatic updates? I've recently gotten back into Linux and installed 12.04 on another HDD in my Winbox. Are updates still a point of major contention,  and will need to drag the updated Windows version across to Ubuntu? 

Also, do oyu guys have problems with viewing your character on the map (when pressing 'M')? Are you able to preview your character when  attempting to preview an item?

---

### Post by Tweak42 on 2012-11-16
> **Aarbron said:**
> Hi,

So if you guys are able to grt the Launcher rubbing, this means automatic updates? I've recently gotten back into Linux and installed 12.04 on another HDD in my Winbox. Are updates still a point of major contention,  and will need to drag the updated Windows version across to Ubuntu? 

Also, do oyu guys have problems with viewing your character on the map (when pressing 'M')? Are you able to preview your character when  attempting to preview an item?

The Wow launcher / updater has been running on wine since at least mop launch.  Make sure you are using latest version from the PPA if you are having problems.

The character preview and map problem is a Blizzard bug with opengl mode they refused to fix.   There is a work around for the map by using an addon. [http://us.battle.net/wow/en/forum/topic/6712862205](http://us.battle.net/wow/en/forum/topic/6712862205)

Or you can take the performance hit and run using d3d9.

---

### Post by Aarbron on 2012-11-17
> **Tweak42 said:**
> The Wow launcher / updater has been running on wine since at least mop launch.  Make sure you are using latest version from the PPA if you are having problems.

The character preview and map problem is a Blizzard bug with opengl mode they refused to fix.   There is a work around for the map by using an addon. [http://us.battle.net/wow/en/forum/topic/6712862205](http://us.battle.net/wow/en/forum/topic/6712862205)

Or you can take the performance hit and run using d3d9.

Hi Tweak42,

Wow, thanks! I'll look into the launcher issue tonight! I'll also check out that workaround, too!

Spewing about the general opengl issue, however. When playing in Ubuntu, the sound (I do have a Xonar Essence STX and Audioengine A5's mind) is simply sensational. Hearing the water, POHHHHHHHHHHH!

Unfortunately, when I first installed, d3 was causing black artefacts all over the screen :( (nvidia 550).

But, thanks for the heads up!

---

### Post by vamp774 on 2012-11-24
> **Nilladar said:**
> It is best to run WoW using wine1.5. 

Thank you!  I had been looking for a few days now on this fix.  I wiped my disk and put Ubuntu 12.04 on and was having trouble getting the new WoW expansion to run.  I did a sudo apt-get install wine and got wine 1.4.  I added the repositories another poster listed and I'm now installing!

From Terminal I did:
 
1.  Start Agent.exe
cd ~/.wine/drive_c/users/Public/Application\ Data/Battle.net/Agent
wine Agent.exe ( I think I also did --nohttpauth & )

2. Start installer.
wine setup.exe ( I renamed )

Much appreciated everyone!
Now on to fixing it if the GFX are messed up....

---

### Post by donaldhall on 2012-11-27
Try Play On Linux. 

Here is a tutorial on how to install WoW on PoL

[https://www.youtube.com/watch?v=zpNjeddqIz4&list=UUDd39wOar9fVJM6qp4pyOOQ&index=2&feature=plcp](https://www.youtube.com/watch?v=zpNjeddqIz4&list=UUDd39wOar9fVJM6qp4pyOOQ&index=2&feature=plcp)

---

### Post by cwwilson721 on 2012-11-27
I've said it before, and I'll say it again:
POL isn't needed for WoW.
At all
Ever

WoW installs, runs, and updates in wine.

Added layers of complexity just adds that much more that can "go wrong"

---

### Post by vamp774 on 2012-11-30
Since my previous post I have gotten WoW to work perfectly without Play on Linux using Wine 1.5 ( the Beta ; 1.4 didn't work. )  .  I just finished building another computer and put Ubuntu 12.04 on it and goin' for round 2.  I ended up finding all the clues/pieces scattered around.  I ended up needing the registry fix on the WoW Ubuntu page and setting it to OpenGL etc.  On my laptop I had to play WoW windowed or else when I quit part of my desktop was cut off and had to reboot.  No biggie.  We'll see how it goes this time, now that I've done it once xD

---

### Post by vamp774 on 2012-12-01
For anyone interested I have installed WoW on another machine running Ubuntu 12.04 LTS and this time installing with Wine1.5 I didn't even have to start the Agent.exe separately.  I just ran the setup with Wine and installed.  Then once again I just got a black screen and copying config.wtf over from a Windows machine solved everything.  Both times I needed my config.wtf file from my Windows 7 computer.  Maybe somewhere online you can find the default values for the file as this seemed to be the root of a lot of problems.  Then I just set the graphics from Direct X to OpenGL.

---

