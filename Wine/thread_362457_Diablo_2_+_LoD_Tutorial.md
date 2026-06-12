---
title: "Diablo 2 + LoD Tutorial"
date: 2007-02-15
forum: Wine
---

### Post by cb951303 on 2007-02-15
UPDATE: With newer Wine versions running Diablo 2 + LoD on linux is much more simpler, here is how I do it...

_**Requirements**_
[LIST]
[*]Wine 0.9.39 ( [Website here]("http://www.winehq.com") )
[*]Working OpenGL drivers (Nvidia/Ati)
[*]Diablo 2 and/or LoD (I used a pirate copy, but hey I have my original cd keys)
[*]Latest LoD or Diablo 2 patch (1.11b)
[*]D2Loader for 1.11b ([Website here]("http://d2loader.blizzsector.net/")) EDIT: It looks like Blizzard started to ban D2Loader users ...
[/LIST]

**_Step 1_**
[LIST=1]
[*]Put the INSTALL cd and run the "INSTALL.EXE".  (It's a good idea to choose FULL INSTALL)
**Problem 1: **A very common problem here is that the progress window blocks the CD swap dialog so you think that it doesn't install anything. A quick fix is to selecet "Emulate a virtual desktop" from winecfg.
**Problem 2: **Here you may have an other little problem. If you run "INSTALL.EXE" form a bash command when the setup asks for you to change the disc, you won't be able to eject it because bash is making the cdrom busy. Here there is 2 solutions. Weather you type "wine eject" in the console or you just run "INSTALL.EXE" by double clicking it and choosing "wine" as the appropriate application.
[*](Optional) Now that the setup is over you put the expansion disc (LoD) and install it just like before.
[*]Copy all the missing *.mpq files from cds to your Diablo 2 directory.
[*]Apply the latest patches according to your install. (Use just one patch, Diablo 2 or LoD)
**Problem 3: **Patch should work flawlessly but if you're using a pirate copy, after upgrade, it will ask for the expansion cd no matter what you put in. Don't worry, just hit the cancel to complete the upgrade process. (It may say that patching is unsuccessful. It's not important)
[*]Unzip the D2Loader to the Diablo 2 directory.
[/LIST]

_**Step 2**_
[LIST=1]
[*]Run "D2VidTst.exe". It will find the  installed drivers. Choose Direct 3D.
[*]Run "winecfg" and create a new application profile.
[LIST]
[*]Add Application -> Choose "D2Loader-1.11b.exe"
[*]Windows Version -> Windows 2000 or Windows XP
[*]Audio -> Select just ALSA
[*]Graphics -> Unselect "Allow the window manager to control the windows"
We do that to be able to press Alt/Shift and mouse buttons at the same time while playing. It's a must-do for Diablo :)
[*]Leave anything else unchanged (I assume you already set the "Drives" properly)
[/LIST]
[*]Run "D2Loader-1.11b.exe" and enjoy :)
**Problem 4: ** You may get an error while connecting BNET saying that your exe is unrecognized. It's simply because you run it from outside of Diablo 2 directory.
Here is how my desktop entry looks...
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Diablo II - Lord of Destruction
Exec=env WINEPREFIX="/home/cosku/.wine" wine "C:\\Program Files\\Diablo II\\D2Loader-1.11b.exe" -sleepy -skiptobnet
Type=Application
Path=/home/cosku/.wine/dosdevices/c:/Program Files/Diablo II
Icon=/home/cosku/.wine/drive_c/Program Files/Diablo II/d2x.ico
GenericName[en_US]=

```
[/LIST]

**UPDATE: If you want to run D2 in resolutions higher than 800x600, try this mod: [http://www.moddb.com/games/diablo-2/news/d2multires](http://www.moddb.com/games/diablo-2/news/d2multires)**

---

### Post by Sqwishy on 2007-02-15
> **cb951303 said:**
> (I smells windozz yeah) EIIWW! windows smellz nasty!
Thanks for the guide, for troubleshooting you can go to the wine app db [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by JensenDied on 2007-02-16
Anyone know of blizzards policy on using this no-cd on bnet? 

(Doesn't matter much since wine works fine with the cd)

---

### Post by cb951303 on 2007-02-16
> **JensenDied said:**
> Anyone know of bli22ards policy on using this no-cd on bnet? 
(sorry about the misspelling there, but i have a broken key on my laptop)

i don't think they still bother banning diablo II cd keys, but that's just an assumption
it's been said that if you use a no-cd crack for the first time, you're banned for 1 month if it's the second time then you're gone for good. I think I read it on battle.net/diabloexp

---

### Post by cb951303 on 2007-02-18
> **JensenDied said:**
> Anyone know of bli22ards policy on using this no-cd on bnet? 
(sorry about the misspelling there, but i have a broken key on my laptop)
You can also use D2Loader which is not a cracked diablo exe. It's a third party exe which let you play diablo 2 without a cd. 
Quote from [http://d2loader.blizzsector.net/](http://d2loader.blizzsector.net/)
> 
Q. Will I get banned for using D2Loader / is D2Loader detectable?

A. Ask Blizzard. **So far to my knowledge, no one has ever been banned for using D2Loader by itself**. However, it is a 3rd party modification and thus against the EULA to use. D2Loader is trivial for Blizzard to detect with their new hack detection system in v1.11 (Warden), so they could very easily detect and ban anyone using it. It's really up to them, I have no idea. You take a risk as with any 3rd party hacks. I assume no responsibility for any lost accounts, cdkeys, etc.

It's good enough for me :P also it works great with wine

---

### Post by le_vainqueur on 2007-03-07
The link to the glide wrapper does not work for me.  Is there somewhere else I can get this?

---

### Post by le_vainqueur on 2007-03-08
> **le_vainqueur said:**
> The link to the glide wrapper does not work for me.  Is there somewhere else I can get this?

Nevermind...the site worked today.

---

### Post by le_vainqueur on 2007-03-08
I experienced an error when trying to run the loader.  The error said:
 > No useful pixelformat found!  Please check your graphiccard-driver

There ar two things in the guide that I am unsure as to whether or not I completed correctly:
> Working OpenGL drivers (Nvidia/Ati)
I assumed I had the correct drivers running since I have had no problems thus far.  In the hardware section of my system setting I am set to the driver "nv" for my graphics.  Is this appropriate.

Secondly, I have never used wine before so the portion of the guide that says:
> I assume you already set the "Drives" properly
is confusing to me.  If I have it configured incorrectly, what do I need to do to configure it?

Additionally, I am in Kubuntu.  I don't know if that affects anything or not.  It seems to me that it should not, but I don't know for sure.

---

### Post by disturbedite on 2007-03-08
i just thought i'd mention a few things here... (i'm on kubuntu feisty herd 5 and this applies to wine 0.9.31+)

i don't have to use a glide wrapper cuz d2/lod runs at full framerate/speed without the glide wrapper and i have a crappy integrated intel 845g video chip!

and i don't know whether anyone else has experienced this, since no one has confirmed it on the wine appdb, but it appears that there was a change of some kind with wine 0.9.31 that b0rked wine's alsa support for blizzard games. the audio lags and echoes. ***it works almost flawlessly with the oss driver tho***. this still is not fixed with wine 0.9.32.

oh, and a tip that might help!:

(i have an actual copy with my own cd key, not a pirated copy).  i didn't install d2/lod for a while cuz whenever i'd stick the install disc in it would just keep asking me to insert the disc, even while my drives were properly configured AND i was using an actual copy!  this made me really frustrated for a while.  then i tried it again and i finally realized the problem:  apparently, with that version of wine at least, the little window that pops up asking you to insert the next disc was invisible, it DIDN'T show up, visually that is, its actually there.  (i didn't realize this for that all those times before).  i had also forgotten that when you stick the install disc in and start the install, it pretty quickly asks you to insert the next (i believe play) disc, and i thought it was asking me to put the install disc in cuz i couldn't see the window that was actually asking for the play disc.

so i posted this in case it might help someone.

---

### Post by Vexed Arcanist on 2007-03-08
A further expansion on the tip about CD drive funkyness and such...

I had the "hidden" CD swap prompts once too.  The "trick" I used to alleviate this was to run winecfg and set it to emulate a window (any size is fine, 640x480 is the default).

---

### Post by disturbedite on 2007-03-09
ah, great tip!   i didn't know that.   of course, the window is actually there,  (at least it was in my case), so you can just wait for it to automatically detect the disc or hit enter.  but my problem was that i didn't remember that it asks you for the play disc so quickly, so i thought it was asking for the install disc i already had in the drive.  go figure...

---

### Post by Maver1k on 2007-03-09
> Run "winecfg" and create a new application profile.
Add Application -> Choose "D2Loader-1.11b.exe"
Windows Version -> Windows 2000 or Windows XP

Sorry but where can i run this "winecfg"?
My problem is this ... I already have Diablo II installed and i played with my Cd in the Cd-rom... today my Cd-rom crashed and now i'm left without my game so ... i copied the Crack u sayd.
I copied the D2Loader-1.11b in my Diablo II directory and i downloaded the "gl32ogl14.zip" to and extrated into the game director. The problem is i can't find the "winecfg" to create the application proflie to chose the "D2Loader-1.11b.exe" so i quess that's a stupid question but if you can help me that would be great !

---

### Post by disturbedite on 2007-03-09
run winecfg from a command prompt/command line dude.

---

### Post by cb951303 on 2007-03-10
> **le_vainqueur said:**
> I experienced an error when trying to run the loader.  The error said:
 

There ar two things in the guide that I am unsure as to whether or not I completed correctly:

I assumed I had the correct drivers running since I have had no problems thus far.  In the hardware section of my system setting I am set to the driver "nv" for my graphics.  Is this appropriate.

Secondly, I have never used wine before so the portion of the guide that says:

is confusing to me.  If I have it configured incorrectly, what do I need to do to configure it?

Additionally, I am in Kubuntu.  I don't know if that affects anything or not.  It seems to me that it should not, but I don't know for sure.

It seems that you don't have accelerated drivers. Ubuntu/Kubuntu doesn't come bundled with nvidia/ati drivers. you have to download and install them via repositories and then you should set "nv" in xorg.conf.

"Drives" part is not an issue for you since you succesfully installed diablo :)

cheers

---

### Post by Mahiko on 2007-03-12
"No useful pixelformat found! Please check your graphiccard-driver"
Help?

Also for the D2Loader I get an error in the terminal saying something like Library STORM.dll not found.

---

### Post by cb951303 on 2007-03-13
> **Mahiko said:**
> "No useful pixelformat found! Please check your graphiccard-driver"
Help?

Also for the D2Loader I get an error in the terminal saying something like Library STORM.dll not found.

look up

---

### Post by Mahiko on 2007-03-14
> **cb951303 said:**
> look up
Nothing above helps me, someone else had the "No useful pixelformat found! Please check your graphiccard-driver" problem but I don't see anyone answering him, and no one above me had the missing Library Storm.dll so...

---

### Post by Prisoner_97p904 on 2007-03-18
Hi.

I also followed this guide and ended up with "No useful pixelformat found! Please check your graphiccard-driver", and i ran the Video-Test again and choose the DirectDraw, but its VERY laggy in the menu (and also in the game :P).

Another problem is when i click on Battle.net it cant connect... If I try US West, then it works, but Europe (which I need), Asia and US East is dead for me :( Can somebody help?
The problem with no connection to Europe-Battlenet also occurs in Cedega.

---

### Post by adarkmethod on 2007-03-25
i got the D2 to work after some minor tinkering, but when i got to install LOD it says i dont have D2 installed.. any suggestions?

---

### Post by Hasen_A on 2007-04-02
Hi guys im running the installer with wine-0.9.30. I am able to start the installation, but up choosing FULL INSTALLATION the percentage window pops up and nothing gets installed: no Tasks are being started and the window just stands still with no progression.

When trying to install by right-clicking the install.exe and chosing wine, I get the message to insert the INSTALL CD altough it is already in the driver. Pressing OK will not work.

Any ideas?

---

### Post by arron on 2007-04-10
I posted this in a new thread, but I will post here in hopes one of you ubuntu-diablo masters can help.

I have D2 and LOD installed and running great on wine.  I copied over the mpq files from the lod cd, full installs and use the loader as posted above.

When im in the expansion chapter, there is no music or voices in town, like for reading about the quest and stuff.  Is there any way i can get the music and vices to work in the expansion?  It works fine in the rest of the game.

Thanks

---

### Post by intwingedhumor on 2007-04-15
Hi,

I am sorta new to Linux, I have Ubuntu and have been messing around a bit to try understanding the basics. I want to try installing Diablo 2 inwhich I have looked at a few of the guides which tell my that i need wine (got it), and set the winecfg (which I did).
I can get up to the point that the progress bar says to insert the play disc, and yet when I "wine eject" and insert the play disc it doesn't read it and won't go on loading. Any help?

---

### Post by dbzsephiroth on 2007-04-21
Hey guys!

OMG Seph is posting his 2nd ONLY post! =P


Anyway, i figured out a little trick to help u guys out with some installation problems. Please not that this will most likely not solve ALL installation problems but its woth posting.

My delema was that during the LOD installation, It will ask me for the "Play" CD, fair enough, i would insert the second disc, then let ubuntu do whatever the hell id does when u insert a new CD (mounting presumibly) then click ok, window pops up again, ok......OK.....OK! damn it! >_<...etc etc.

Well after experimenting with multiple ways of insatlling this, i found that the way that helped with no errors is installing the program WITHOUT using "wine eject". Now ur all probably wondering "How can u insert the next disc without using wine eject?", yes true ubuntu doesnt like mounted media being removed while its it use. (that really annoying "device is busy" message comes to mind) To overcome this, its simple:

Replace
```

cd /media/cdrom (or /mnt/cdrom or whereever the cd mount point is)
wine setup.exe

```

With

```

wine /media/cdrom/setup.exe

```

The reason y u cant eject the cd while the installation is running is becase the terminal you are using is in turn using the CD, the terminals directory is in the cd drive. By doing it this way you avoid makeing the terminal go to the mount point. and because u use wine setup.exe, while wine is running the terminal is unuseable. Using this method, u can still use the terminal with wine running (even though wine debug messages are still going to be displayed in it) and the cd mount point is free.



Putting it slimply, use wine /media/cdrom/setup.exe so u can eject the cd by pushing the cd button, instead of using "wine eject" all the time which can mess up the installation.

I never got any problems using this method, hope it helps guys.

phew, now i can give my hands a break.....

---

### Post by meldroc on 2007-05-17
Whee!, got it working!

I got stuck for a bit thanks to the invisible Insert CD dialogs during the install, but once I read some of the previous posts, I figured it out.

One thing I noticed is that it has a hard time dealing with my display.  I'm running on my Asus A8Js, which has a 1440x900 LCD display.  It does scale it down to 800x600 or 640x480 (I have those modes set up in my xorg.conf) but the bottom of the screen seems to be cut off.  It may be a glitch with the hardware resolution scaling, and maybe I can get it to switch graphics modes so it isn't a problem.

Also, you don't have to use the no-cd cracks.  It will run straight perfectly well if you're willing to put your precious Diablo II CD in the drive and mount it as you play.  That might save you from getting banned on bnet.  I was surprised to see WINE correctly handle the copy protection.

---

### Post by eilu on 2007-05-18
I have a problem with scaling too- wine redraws the sceen to 800x600, then something else (maybe X) redraws it to my present resolution (1280x800) so D2 is in a (relatively) dinky window in the corner. Any ideas?

---

### Post by meldroc on 2007-05-18
Not sure.  I resolved my problems by switching in-game to 800x600, which my system scales just fine (though the aspect ratio's wrong because my laptop uses a widescreen, and the image is stretched all the way to the edges.)  I guess the 640x480 is the only mode that gets scaled wrong and cuts off the bottom of the screen.

---

### Post by Dr Gryme on 2007-06-01
I'm having trouble with playing. Allow me to elaborate. It wont let me go into single player mode, it shuts down. Also, when i sign into my d2 account, it loads, and blinks, then shuts down. I have yet to see a diablo2 character in wine. I think it might have something to do with the characters but i'm unsure. Can you help me out dude?

---

### Post by sb_ on 2007-06-26
I was having trouble installing so here is what I did. I made an ISO image of each disk and placed it in my home directory (this is done using the virtual desktop in winecfg).
I then proceeded to run the following command from my home directory
```

sudo mount -o loop -t iso9660 INSTALL.iso /media/cdrom1
wine /media/cdrom1/INSTALL.exe &

```
Whenever it asked me to insert a disk I would run each of these respectively.
```

sudo mount -o loop -t iso9660 INSTALL.iso /media/cdrom1
sudo mount -o loop -t iso9660 PLAYDISC.iso /media/cdrom1
sudo mount -o loop -t iso9660 CINEMATICS.iso /media/cdrom1

```

To "unmount" all the ISO's that you "mounted" run the following command until all "drives" are unmounted.
```

sudo umount /media/cdrom1/ -l

```

I will update this once I install LoD, otherwise assume the same thing.

In the end i ran this...

```

sudo mount -o loop -t iso9660 INSTALL.iso /media/cdrom1
wine /media/cdrom1/INSTALL.exe &
sudo umount /media/cdrom1/ -l
sudo losetup -d /dev/loop1

sudo mount -o loop -t iso9660 PLAYDISC.iso /media/cdrom1
sudo umount /media/cdrom1/ -l
sudo losetup -d /dev/loop1

sudo mount -o loop -t iso9660 CINEMATICS.iso /media/cdrom1
sudo umount /media/cdrom1/ -l
sudo losetup -d /dev/loop1

sudo mount -o loop -t iso9660 INSTALL.iso /media/cdrom1
sudo umount /media/cdrom1/ -l
sudo losetup -d /dev/loop1

sudo mount -o loop -t iso9660 Expansion.iso /media/cdrom1
wine /media/cdrom1/INSTALL.exe &
sudo umount /media/cdrom1/ -l
sudo losetup -d /dev/loop1

sudo mount -o loop -t iso9660 PLAYDISC.iso /media/cdrom1
sudo umount /media/cdrom1/ -l
sudo losetup -d /dev/loop1

sudo mount -o loop -t iso9660 Expansion.iso /media/cdrom1

```

Then to play LoD you can make a script from the above commands to mount it from the ISO for wine, then remove it when you are done.

---

### Post by havok1977 on 2007-07-04
Does anyone know how to make D2Loader-1.11b.exe work when running the game using Cedega? I have changed the Cedega main window shortcut so it should run it instead os the Diablo II.exe program, but when i try to run it, it just hangs.... any suggestions?

---

### Post by AZzKikR on 2007-07-05
> **cb951303 said:**
> 
**Problem 1: **A very common problem here is that the progress window blocks the CD swap dialog so you think that it doesn't install anything. A quick fix is to selecet "Emulate a virtual desktop" from winecfg.


Another fix  that worked for me, is simply dragging the main installation window out of the center screen. The CD swap dialog will then be displayed properly. 

I've been playing Diablo 2 LOD successfully for about 2 weeks now. Crashed only once in about 40 hours of playing time, and died 4 times in hardcore because of machine-lag.

About this machine-lag: I get really, REALLY poor performance in large parties and mobs. My framerate often drops from 80+ to ~10. When I go to Tyrael after I killed Duriel, I get ~1 fps (yes, ONE fps). This machine lag is really sucky because it prevents me to successfully participate in a party.

Any performance suggestions?

---

### Post by doh224 on 2007-07-05
> **cb951303 said:**
> UPDATE: With newer Wine versions running Diablo 2 + LoD on linux is much more simpler, here is how I do it...

_**Requirements**_
[LIST]
[*]Wine 0.9.39 ( [Website here]("http://www.winehq.com") )
[*]Working OpenGL drivers (Nvidia/Ati)
[*]Diablo 2 and/or LoD (I used a pirate copy, but hey I have my original cd keys)
[*]Latest LoD or Diablo 2 patch (1.11b)
[*]D2Loader for 1.11b ([Website here]("http://d2loader.blizzsector.net/"))
[/LIST]

**_Step 1_**
[LIST=1]
[*]Put the INSTALL cd and run the "INSTALL.EXE".  (It's a good idea to choose FULL INSTALL)
**Problem 1: **A very common problem here is that the progress window blocks the CD swap dialog so you think that it doesn't install anything. A quick fix is to selecet "Emulate a virtual desktop" from winecfg.
**Problem 2: **Here you may have an other little problem. If you run "INSTALL.EXE" form a bash command when the setup asks for you to change the disc, you won't be able to eject it because bash is making the cdrom busy. Here there is 2 solutions. Weather you type "wine eject" in the console or you just run "INSTALL.EXE" by double clicking it and choosing "wine" as the appropriate application.
[*](Optional) Now that the setup is over you put the expansion disc (LoD) and install it just like before.
[*]Copy all the missing *.mpq files from cds to your Diablo 2 directory.
[*]Apply the latest patches according to your install. (Use just one patch, Diablo 2 or LoD)
**Problem 3: **Patch should work flawlessly but if you're using a pirate copy, after upgrade, it will ask for the expansion cd no matter what you put in. Don't worry, just hit the cancel to complete the upgrade process. (It may say that patching is unsuccessful. It's not important)
[*]Unzip the D2Loader to the Diablo 2 directory.
[/LIST]

_**Step 2**_
[LIST=1]
[*]Run "D2VidTst.exe". It will find the  installed drivers. Choose Direct 3D.
[*]Run "winecfg" and create a new application profile.
[LIST]
[*]Add Application -> Choose "D2Loader-1.11b.exe"
[*]Windows Version -> Windows 2000 or Windows XP
[*]Audio -> Select just ALSA
[*]Graphics -> Unselect "Allow the window manager to control the windows"
We do that to be able to press Alt/Shift and mouse buttons at the same time while playing. It's a must-do for Diablo :)
[*]Leave anything else unchanged (I assume you already set the "Drives" properly)
[/LIST]
[*]Run "D2Loader-1.11b.exe" and enjoy :)
**Problem 4: ** You may get an error while connecting BNET saying that your exe is unrecognized. It's simply because you run it from outside of Diablo 2 directory directory.
Here is how my desktop entry looks...
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Diablo II - Lord of Destruction
Exec=env WINEPREFIX="/home/cosku/.wine" wine "C:\\Program Files\\Diablo II\\D2Loader-1.11b.exe" -sleepy -skiptobnet
Type=Application
Path=/home/cosku/.wine/dosdevices/c:/Program Files/Diablo II
Icon=/home/cosku/.wine/drive_c/Program Files/Diablo II/d2x.ico
GenericName[en_US]=

```
[/LIST]

mine still ask for the cd....?? and it won't run :S ?

---

### Post by AZzKikR on 2007-07-06
> **AZzKikR said:**
> Any performance suggestions?

I found a solution myself. After the installation of 1.11 patch, I got the option to select Direct**2D** instead of Direct**3D** after running DVidTest.exe. This really boosted the performance of the game.

---

### Post by cb951303 on 2007-07-08
> **doh224 said:**
> mine still ask for the cd....?? and it won't run :S ?
i beieve it has something to do with cd copy protection. (asssuming that you use pirate copies) Just download an other diablo/lod image and burn new cds...
Also you could try to prepare isos from your current cds and mount them whenever installer asks you...

---

### Post by cb951303 on 2007-07-08
> **AZzKikR said:**
> I found a solution myself. After the installation of 1.11 patch, I got the option to select Direct**2D** instead of Direct**3D** after running DVidTest.exe. This really boosted the performance of the game.
what's your graphics card?

---

### Post by AZzKikR on 2007-07-08
> **cb951303 said:**
> what's your graphics card?

I have an ATi Radeon X800/850. UT2K4 runs perfectly on it :P

---

### Post by Copter on 2007-07-09
> **AZzKikR said:**
> I found a solution myself. After the installation of 1.11 patch, I got the option to select Direct**2D** instead of Direct**3D** after running DVidTest.exe. This really boosted the performance of the game.
Hmm... in my case it was different. 3D mode (w/o perspective) gives me little better performance than 2D. Im using Xubuntu 6.10 with Intel 855 graphics chip, wine 0.9.40. As for my tips - it is safer to run **D2VidTst.exe** with **virutal desktop enabled** in my case at 1024x768. Other way it crashes.

Btw. running in windowed mode **wine Diablo\ II.exe -w** also saves me from some random crashes.

copter :]

---

### Post by cb951303 on 2007-07-09
> **AZzKikR said:**
> I have an ATi Radeon X800/850. UT2K4 runs perfectly on it :P
You might try the glide wrapper for Diablo II, it works perfectly with wine. Just do a google search for the diablo II glide wrapper then extract all the files (DLL files) to Daiblo II dir and rerun D2 video test. Then choose Glide (not D2D nor D3D).
D2D just dosn't feel right :lolflag:

---

### Post by AZzKikR on 2007-07-13
> **cb951303 said:**
> You might try the glide wrapper for Diablo II, it works perfectly with wine. Just do a google search for the diablo II glide wrapper then extract all the files (DLL files) to Daiblo II dir and rerun D2 video test. Then choose Glide (not D2D nor D3D).
D2D just dosn't feel right :lolflag:

Honestly, I've tried the Glide wrapper first before posting. Installation went all good and stuff, but the game just got locked up. Only survival was kill -9 or kill -HUP :P

D2D for me it is!

---

### Post by Gauss1777 on 2007-07-20
After some trouble I have this game working thanks this thread.

I decided to post here a problem, just if someone ran through something similar before.

I have tried an option to run the game adding: -opengl at the end, like:
$ wine Diablo\ II.exe -opengl

It happens that the game runs great! faster! and with better 3D quality! but!!!!  the floor always looks blocky, the render is not perfect, anyway to fix it?

I have tried the latest version of wine 0.9.41, gildewrapper for Diablo II, I have changed Direct3D options through winecfg, trying always swapping between Direct3D and Glide rendering with D2vidtst.exe, no success. I wish I can simple fix that blocky floor, the game is faster but  is not fun with such mess in the floor.

I haven't tried to change my video drivers, since I know it's just trouble to make direct rendering to work with my video chipset: Ati mobility IGP 320M. I have direct rendering active and Quake 3 runs fine.

BTW, the sound is choppy sometimes with some lag, that doesn't seem to be a problem of the game or the connection, in Windows everything is fine. I think is a problem with the audio support with wine, but is there something possible to do for a better performance in Wine?

I'm running Ubuntu Feisty.

---

### Post by don durito on 2007-07-25
hi,

have some serious problems installing diablo 2 cause it just won't install. 

i can start the diablo 2 setup selcet full intallation insert my cd key and then the installation taskbar freezes. And even worse is that the install shield is always shown on everyone of my 4 desktops. 

don't know what i am doing wrong so please help

heres my wine output (i am using wine 0.9.41)
```
peter@peter-think:~$ wine /media/cdrom/INSTALL.EXE 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1dc0020) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1b7178)->(0x10026,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32
fixme:dsalsa:SetFormat Your alsa dmix period size is 1024, try decreasing it to 512 if possible
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1b7178)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy



```

but the single player installation seems to work. don't know what the problem is

---

### Post by cb951303 on 2007-07-25
> **don durito said:**
> hi,

have some serious problems installing diablo 2 cause it just won't install. 

i can start the diablo 2 setup selcet full intallation insert my cd key and then the installation taskbar freezes. And even worse is that the install shield is always shown on everyone of my 4 desktops. 

don't know what i am doing wrong so please help
[/CODE]

but the single player installation seems to work. don't know what the problem is

It's been discussed too many times now, and it's included in the guide. Your "installation process dialog" blocks the "cd swap dialog" so you think the installation hangs. Just before starting to install, move the setup window out of the center of your screen...

---

### Post by spupy on 2007-08-18
I can't apply the patch. :( It says it can't find "d2char.mpq", but the file is right there! Is there any other way to patch it?

---

### Post by dsdexterds on 2007-09-07
hey guys, sorry if this has been asked already and I am just being a pain, I am new to this whole thing and I read or at least skim read all of the posts, I seen one that had a similar problem but no reply to him, so my problem is :

I put the install disc in my drive (using the original game which I bought), I then click on install.exe, it wuto runs in wine, but I just keep getting "insert install disc" pop-up nothing works, can anyone advise me please?

Thanks in advance

---

### Post by t2mg2003 on 2007-09-07
I have been using D2loader for many years. So has many of my friends, D2loader doesnt get you banned, its the illegit plugins that its able to load up for you that can get you banned.. (Maphack, injecting code into the game so it laggs or glitches, whatever...)  To the person saying they downloaded d2 loader since their CDrom died.. You wont be able to easily do it.  You will still need to copy the MPQ files from the disk to your d2 folder.

---

### Post by Amivit on 2007-10-08
> **cb951303 said:**
> 
[LIST]
[*]Diablo 2 and/or LoD (I used a pirate copy, but hey I have my original cd keys)
[/LIST]
A pirate copy? 
I got my diablo cd's in iso format on my windows drive. I'm not that good at taking care of my cd's :b. My LoD cd is broken.
Is there any software for ubuntu that works like daemontools?
Tried searching google and Synaptic Package Manager for virtual disk/drive software, but with no luck.

---

### Post by AZzKikR on 2007-10-08
Use the mount command to mount ISO's to a directory.
```
sudo mount -o loop -t iso9660 INSTALL.iso /media/cdrom1
```
This has been said in a post in this thread, by the way.

---

### Post by Amivit on 2007-10-08
Oops, my bad. I meant .mdf files. Can mount do that ?

---

### Post by lady_chance on 2007-10-19
Oh, wow. Brand new to Ubuntu (used SuSE until last week!), and got this up and running in about an hour today, including burning the CDs. Works absolutely -flawlessly-! I'd tried installing it previously, on SuSE, but wouldn't get it to work, so I'm very happy now. Wish I could play full screen, though, since it lowers the number of colors displayed when it's running in  Wine's virtual desktop, and it makes everything look -really- strange... But I am so not complaining, since the game looks and runs just fine, perfect audio, everything. Thanks muchly for the tut! 

Also, am using the newest version of Wine that Adept (using Kubuntu Gutsy) has, which probably contributes to this resounding success.

---

### Post by saltedfish on 2007-10-20
When I try to run D2Loader1.11.exe in wine, i get a 

"Failed to Create Game client Window"

 error. what gives?

---

### Post by lady_chance on 2007-10-20
> **saltedfish said:**
> When I try to run D2Loader1.11.exe in wine, i get a 

"Failed to Create Game client Window"

 error. what gives?

The same thing happened to me. Tell Wine to emulate a desktop, 800x600, and it ought to work just fine.

---

### Post by Falcorian on 2007-10-20
I'm having some problems getting D2 and LOD to work.

I installed them from CD fine, then I copied over all the mpqs (from all four disks, is this correct, I was confused here...).

Now I've downloaded the newest patch for LOD, and tried to install it, but I get an error:

```
Blizzard BNUpdate v2.72 compiled on Oct 16 2003
Log created at  6:45 pm on 10/20/2007

This patch upgrades Diablo II Lord of Destruction from version 1.07 or later to version 1.10.

ERROR: unable to load file 'Bnclient.dll' from archive
File not found

RESULT: Patch failed
```

Any advice? The appdb entry had a few posts on it, but no answers (and I didn't see anything on google or a search of this forum...).


Thanks.


EDIT: Ok, I patched it up on a windows partition then copied it over, followed the rest of the guide and it works great!

---

### Post by skadus on 2007-10-22
Question:

I've already installed D2+X the conventional way, with the actual game CDs, and now I'd like to run the game with a mounted iso file rather than the CD in the drive (mostly for battery life and less noise). Is there a way to do this (alternately, can I reinstall using the iso method mentioned above)?

I've tried using

```
dd if=/dev/cdrom of=d2x.iso
```
```
sudo mount -o loop -t iso9660 isos/d2x.iso /media/cdrom1
```

But it tells me that cdrom1 doesn't exist (do I need to create a cdrom1 folder under /media/?). Using cdrom0 instead (which is the actual mount point for my CD drive) I get an error from Diablo 2 saying to insert the Expansion disc. The mounted iso gives me a mount shortcut on my desktop saying 'cdrom0', rather than 'EXPANSION', which is what I get from putting the CD in the drive.

I'm relatively new to Linux and mounting drives, and so far trying to mount iso files yields just a means to view files from inside the iso, not an actual emulation of the disc I copied (or rather, Linux acts like it's just a spot on my hard drive rather than a virtual disc).

I hope I supplied enough details. Any help would be greatly appreciated. Thanks!

---

### Post by saltedfish on 2007-10-22
> **lady_chance said:**
> The same thing happened to me. Tell Wine to emulate a desktop, 800x600, and it ought to work just fine.

awesome, thanks worked perfectly.

---

### Post by saltedfish on 2007-10-25
now i have another problem

When I enter the Far Oasis in act 2, within a minute (sometimes as fast as 20 seconds) wine freezes. Im fairly certain it is the Far Oasis, because I went and killed Andy, and never had the same problem. Any ideas?

The game window simply freezes. I have to kill wine to exit.

Any help is appreciated

---

### Post by grey88 on 2007-10-31
I decided to try an experiment...  under windows (I know... BAD BOYS use Windows)..  I created a directory to make an install DVD for Diablo II and Expansion...  I found out that Diablo II will install from a backup DVD (simply copy all the files from each cd into the temp directory, overwriting files of the same size), but from INSTALL.EXE not SETUP.EXE (setup.exe will not recognize the disk.)

I installed D2 in Ubuntu Gutsy (7.10) with no problem (and no swapping of disks) from the temp directory, and then copied D2MUSIC.MPQ into the application directory.  After that, I inserted Expansion into my DVD drive and ran INSTALL.EXE (Since I already copied D2MUSIC.MPQ, it simply installed its own files and didn't ask for the D2 Play Disc.)

Now, when I run the game, I have the expansion disc mounted in my dvd drive (doesn't matter what drive) and play without any modifications!!

PS I never did make that DVD for D2 + LoD because LoD would not install from a directory...  may try that again later...  for now I simply want to play the game...

By the way, in case I forgot....  I upgraded Wine to the latest 9.48 version...  I had to change the audio settings to ALSA to hear sound, but other than that, it ran perfectly (but I might try that Virtual Desktop thing to be able to play without having to autohide the desktop bars)

---

### Post by saltedfish on 2007-10-31
no ideas why my problem is happening?

the problem has gotten worse, now wine freezes before I even enter a game.

---

### Post by saltedfish on 2007-11-02
no ideas? the problem has become really bad, the game is unplayable at this point. Anyone?

---

### Post by arron on 2007-11-04
> **saltedfish said:**
> no ideas? the problem has become really bad, the game is unplayable at this point. Anyone?

I just updated as well to feisty, and had crashing problems.  I ran the D2 video test, and took the first option, and bingo i can play again.  The second option used to work well with the wine with feisty (version 0.9.36 i think), but the new version 0.9.46 seems to be a bit different with gutsy.  Give it a try and let me know.

---

### Post by zephyrus17 on 2007-11-28
I am having trouble passing the Video Test. It keeps crashing on me for DirectDraw and Direct3D.

I have an Ati Integrated 1150 graphics card.

By the way, could it be due Compiz?

---

### Post by arron on 2007-11-28
> **zephyrus17 said:**
> I am having trouble passing the Video Test. It keeps crashing on me for DirectDraw and Direct3D.

I have an Ati Integrated 1150 graphics card.

By the way, could it be due Compiz?

Skip the video test, and take the first option.

---

### Post by zephyrus17 on 2007-11-29
First option? I was never offered any options in the first place.

I'll try reinstalling.

---

### Post by diediedieman on 2008-01-28
I neeed some help here cause im a ubuntu immmagrant,anyways when i ran the video test after installation it did the vid test and then it said that my system was not compatable with d2.I didn't get those open GL drivers cause I couldnt find them.if it is the openGL drivers that im missing please help me with detailed instructions.
 I'm running  an asus p4p800-vm onboard vid card

---

### Post by brundlelinux on 2008-02-07
Just wanted to chime in and offer some advice and tips.  Some have been covered before, some haven't.

One thing I've noticed that's a common theme among all posts with Diablo and some sort of problem is that many of you are trying to fix several problems simultaneously.  That's just NOT the best way to go about it.  I would highly recommend that everybody start with the basics and build from that.  Try installing the game from the actual commercial disks with your actual legit cd-keys before moving on to bootloaders and iso files and all the fancy stuff.  This will allow you to troubleshoot and resolve basic audio/graphics issues and get WINE set up properly and establish a control for your further modding.

Secondly, it can't be said enough.  You're going to have issues with that pesky pop-up telling you to insert the next disk.  Instead of tweaking the code for 'wine eject' or any of those overly complicated fixes, just do the common sense thing and move the main install window out of the way so that it's not covering the prompt for the next disk when it does pop up.  It's .5 seconds of work with only a click and drag vs, getting into code and modding script.

As far as bootloaders and no-cd hacks and whatnot.  Yes, they work, and if you feel comfortable using them based on your level of linux knowledge, jump in.  HOWEVER, if you  are new to linux or not the greatest when it comes to script and code, use Cedega.  If you aren't familiar with it, google it.  Some people swear by it, some people prefer using WINE.  It's personal preference and each of us will have a different opinion on it based on our unique experience with out unique hardware setup.  And I would never advocate doing this *cough cough*, but you can find Cedega for free on the internet with minimal searching.  Cedega is great for flawlessly integrating and automounting ISO files, which totally negates the need for a no-cd frontend or bootloader.

Lastly.... don't be discouraged if what worked yesterday doesn't work today.  I am relatively new to Ubuntu (about a year now), and I often geek out and do complete hard drive reformats to try other linux flavors.  Often, when I come back to Ubuntu and reinstall it, the changes in kernal and version of Wine will have changed the way I install Diablo and get it running again.  Don't be afraid to ditch that new version of Wine and go back to an earlier version.  Unlike most things in the world, with things involving Linux, newer DOES NOT necessarily mean better, just different.  If you used to have D2 and LoD running perfectly with Feisty but it seems to be a pain in your butt for Gutsy, don't be scared to just use Feisty.  Don't feel like you're being left behind or not "as cool" because you have an older version of Ubuntu or are using an older version of Wine.

One last thing... to the person using the Asus... Good luck and God speed.

---

### Post by jane123 on 2008-02-08
i have a problem,hopefully i can get some good answers for.
i have installed diablo 2,and i have diablo 2 lod expansion disc also.
but when i went to install the expansion,after i put the key in, i realized that i couldnt find my play disc for diablo 2
is there any way around this?

---

### Post by cb951303 on 2008-02-08
hehehe :) getting a new one maybe :P?

---

### Post by scizottm on 2008-03-01
You have to have the original play disc for the expansion to load 8(

---

### Post by OrbitWhite on 2008-03-08
:(:confused::(
Ok... here is is: I installed d2 no problem and then unzipped the d2loader, no problem there either! But patch... when i tried to run it, it gave me an error as if it doesn't see it being installed!

ok so i solved that problem by copying my old (updated) files from my windows to the ubuntu. i launch d2loader, it starts... then it crashes right away with that message that loader gives sometimes "Hey guys; we have a big error here"... it might be the graphic driver or something else... i dont know! i installed ENVY, but i dont know if i did it right... can someone please help me?

---

### Post by GSF1200S on 2008-03-09
> **diediedieman said:**
> I neeed some help here cause im a ubuntu immmagrant,anyways when i ran the video test after installation it did the vid test and then it said that my system was not compatable with d2.I didn't get those open GL drivers cause I couldnt find them.if it is the openGL drivers that im missing please help me with detailed instructions.
 I'm running  an asus p4p800-vm onboard vid card

Im guessing you have an nvidia card, right? Youre having issues with xrandr, as I did for a while. Theres a simple fix- for anyone with an Nvidia card that cant get the vid test to pass, add this to your etc/X11/xorg.conf:

Section "ServerFlags"
        Option     "RandR"     "on"
EndSection

right after the part that lists screen resolutions... Then, just restart X and all should be golden. Try typing xrandr before you do this: if you only get 1 resolution, then thats the problem. You should get a number of resolutions... attached is my output for xrandr and my xorg.conf...

```
Screen 0: minimum 320 x 240, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0*
   800x600        51.0     64.0     65.0
   640x480        52.0     69.0
   1600x1024      53.0
   1440x900       54.0
   1280x1024      55.0
   1280x960       56.0
   1280x800       57.0
   1280x768       58.0
   1152x768       59.0
   1024x768       60.0
   960x600        61.0
   896x672        62.0
   840x525        63.0
   800x512        66.0
   720x450        67.0
   640x512        68.0
   640x400        70.0
   640x384        71.0
   576x384        72.0
   512x384        73.0
   400x300        74.0     75.0
   320x240        76.0

```

**EDIT** Also, after fixing the xrandr, make sure that 800x600 is listed- if its not, the vid test will still fail. Youll need to add 800x600 as I did in my xorg.conf.

---

### Post by GSF1200S on 2008-03-09
> **OrbitWhite said:**
> :(:confused::(
Ok... here is is: I installed d2 no problem and then unzipped the d2loader, no problem there either! But patch... when i tried to run it, it gave me an error as if it doesn't see it being installed!

ok so i solved that problem by copying my old (updated) files from my windows to the ubuntu. i launch d2loader, it starts... then it crashes right away with that message that loader gives sometimes "Hey guys; we have a big error here"... it might be the graphic driver or something else... i dont know! i installed ENVY, but i dont know if i did it right... can someone please help me?

Youre going to have problems copying it from a windows partition.. i did the same thing and got the same error. Try installing D2, and then actually run the patch from the D2 directory itself. 

As for the drivers issue, what does:

> glxinfo

return when thrown in a terminal? If it says direct rendering: yes, you should be good. If not, than thats where errors for D2 are going to come from. Do you use compiz or anything? If so, than direct rendering should be working....

---

### Post by OrbitWhite on 2008-03-09
> **GSF1200S said:**
> Youre going to have problems copying it from a windows partition.. i did the same thing and got the same error. Try installing D2, and then actually run the patch from the D2 directory itself. 

As for the drivers issue, what does:



return when thrown in a terminal? If it says direct rendering: yes, you should be good. If not, than thats where errors for D2 are going to come from. Do you use compiz or anything? If so, than direct rendering should be working....

ok well, i checked the drivers, and they are saing "sirect rendering:yes"... i reinstalled d2, patched it successfully, put d2loader in the folder, launched it... and SAME error!

it like launches, goes to a black screen(makes you think that the cinematics are going to start playing) and then it shows the top and the bottom of my ubuntu desktop with the black screen in between, and then it gives me that error "Hey guys; We got a big error here"
crashed!

this computer worked with d2 beautifully in windows... and many other games... 

does anyone have any ideas?


maybe there is a way to run it in window mode, which of coarse makes things smoother?

---

### Post by GSF1200S on 2008-03-09
> **OrbitWhite said:**
> ok well, i checked the drivers, and they are saing "sirect rendering:yes"... i reinstalled d2, patched it successfully, put d2loader in the folder, launched it... and SAME error!

it like launches, goes to a black screen(makes you think that the cinematics are going to start playing) and then it shows the top and the bottom of my ubuntu desktop with the black screen in between, and then it gives me that error "Hey guys; We got a big error here"
crashed!

this computer worked with d2 beautifully in windows... and many other games... 

does anyone have any ideas?


maybe there is a way to run it in window mode, which of coarse makes things smoother?

Please open the d2loader from a terminal and see what output it gives you... it sounds exactly like an xrandr error... which video card do you have? Try typing xrandr in the terminal and see what it gives you... Also, try using the original exe and the expansion cdrom, just in case you got a bad loader...

---

### Post by OrbitWhite on 2008-03-09
WOW!!! I just launched it from the terminal and it worked!!!

Thanks so much everyone!

If i run into anymore problem, you will see me again :)!

---

### Post by GSF1200S on 2008-03-09
> **OrbitWhite said:**
> WOW!!! I just launched it from the terminal and it worked!!!

Thanks so much everyone!

If i run into anymore problem, you will see me again :)!

Heh.. Have fun doing Meph runs :)

---

### Post by lastelement0 on 2008-03-12
hey all,

just got d2 and lod installed in wine. however i have an issue were it messes with my screen resolution when i start it up.  it brings it in to about 680 x 400 or so when i have it set otherwise as 1280x800. where do i have to go so i keep this resolution?

---

### Post by GSF1200S on 2008-03-12
> **lastelement0 said:**
> hey all,

just got d2 and lod installed in wine. however i have an issue were it messes with my screen resolution when i start it up.  it brings it in to about 680 x 400 or so when i have it set otherwise as 1280x800. where do i have to go so i keep this resolution?

The games highest possible resolution is 800 x 600.. its native and lowest setting is 640 x 480. If youre monitor is 1280x800, then xrandr needs to resize the desktop to 800x600, hence making the game fullscreen even at such a low resolution...

Open a terminal and type:

xrandr

and if it prints out a bunch of resolutions, then you should be good. You can grab a program called grandr (sudo apt-get install grandr) that will give you a graphic interface to xrandr, change the desktop resolution, and then run the game and see how it works...

Check a few posts up for help on xrandr if youre using an Nvidia card and its not working..

**EDIT**- if youre saying that upon exiting the game your resolution is stuck at 640x480, then you could use grandr to switch back after game (could run the game with a script). This shouldnt happen though...

---

### Post by OrbitWhite on 2008-03-17
> **OrbitWhite said:**
> WOW!!! I just launched it from the terminal and it worked!!!

Thanks so much everyone!

If i run into anymore problem, you will see me again :)!

Yea now i know why it worked...

for some reason it doesnt launch with sound

it worked because i did -ns after the launch command (for no sound)

---

### Post by TristanXVX on 2008-04-06
I installed D2 + LoD and the 1.11b update. I'm also using the d2loader because when I try to use the cd it just keeps telling me to insert the cd. Now the problem is when I try to start up the game it flashes black then gives me the "hey guys, big error" message. After i close it every thing is really bright and looks like crap on my screen and I have to do ctrl+alt+backspace to fix it.  Anyone know whats up?

---

### Post by Tristan570 on 2008-04-07
Update: I reinstalled everything and it worked until I tried to change the resolution to 800x600. Then the same problem started again.

---

### Post by PseudoRasta on 2008-04-18
thanx same problem

---

### Post by dealen on 2008-04-28
i installed diablo 2 + lod ( orginal games ) without having problems and i patched v1.11. I try to play game intro and cinematics are okey but main menu isnt appear but main menü sounds and button sounds comming, i mean game is not locked. When i did winecfg virtual desktop there is no problem but i want to play full screen. I have latest nvidia driver and in use what should i do ?

---

### Post by cb951303 on 2008-04-28
> **dealen said:**
> i installed diablo 2 + lod ( orginal games ) without having problems and i patched v1.11. I try to play game intro and cinematics are okey but main menu isnt appear but main menü sounds and button sounds comming, i mean game is not locked. When i did winecfg virtual desktop there is no problem but i want to play full screen. I have latest nvidia driver and in use what should i do ?

which version of wine are you using?

---

### Post by MisterBill on 2008-04-28
Hi everyone, just wanted to add my own 2 cents worth to this discussion.

As background, I have been an obsessive ^H^H^H^H^H^H regular player of this frustratingly addictive game since around 2002 and have only recently (summer of 2007) switched to using it under Ubuntu Linux, up until that time I exclusively ran it under {gasp!} Micro$oft Window$ XP.

(Note: I have over 25 D2 accounts on the US East Realm, mostly mules but a large number of high level characters that I can't bear to part with; and I did not feel comfortable doing the deep dive into running D2 under Ubuntu until last summer, lest I lock myself out of being able to renew my characters periodically to stop Battle.Net from expiring them and deleting them. I'm happy to say however that as of approximately September 2007 I have finally and completely evicted Bill Gates and his virus and backdoor-infested bloatware from my home LAN, once and for all.)

The hardware configurations under which I have run this program, both under XP and Ubuntu (originally 7.10 but now 8.04, see below), are as follows:

PC #1: 2002 vintage desktop Intel P-4 1.6 GHz, 256 Mb RAM, AGP nVidia GeForce 200MX, 64 Mb VRAM (don't laugh -- I hate throwing out computers that are old, but still work). Using WINE under Xubuntu (because I figured that the XFCE environment would save me more RAM for Diablo as well as for other things).

PC #2: 2002 vintage desktop Intel P-4 1.6 GHz, 512 Mb RAM, AGP ATI All-In-Wonder Radeon original model, 64 Mb VRAM. Using WINE under "full", "real" Ubuntu.

PC #3: 2002 vintage desktop Intel Celeron 1.4 GHz, 256 Mb RAM, AGP nVidia GeForce 200MX, 64 Mb VRAM. (Boy, Celerons suck.) Using WINE under Xubuntu.

PC #4: 2005 vintage laptop Intel Mobility P-4 1.6 GHz, 512 Mb RAM, ATI Mobility Radeon 9000, (probably) about 128 Mb VRAM. Using WINE under Xubuntu.

PC #5: 2008 vintage laptop Acer Aspire 5920 Intel Mobility P-4 1.6 GHz, Intel Mobility x3100, (probably) about 128 Mb VRAM. Using WINE under Ubuntu.

(Note: Usually no more than 3 of these PCs are running D2 at any one time. As you may or may not be aware, Battle.Net seems not to like seeing more than 4 D2 sessions coming from the same IP address at the same time, even if there's a NAT enabled LAN behind that address, resulting in Temp Bans for the IP when the 5th PC tries to log on.)
[U]
Running the game[/U]

In general, my experiences with running D2 LoD under Ubuntu and Xubuntu have mostly been happy ones. And yes, I DO have legitimate CDs and license keys (no hacks, cheats, preloaders, nothing) for all the instances of Diablo II and LoD that I have loaded on all the above machines. (I don't use Maphack, TPPK, Chickenhack, Farcast or nonsense like that, nor do I buy "leet" items on-line. I don't cheat.)

Diablo runs fine on all of my PCs, but the frame rates vary tremendously, ranging from no more than about 20 or so (with up to 5 to 10 frames per second dropped in high-motion scenes) on the lower-end models, to over 90 on PC #6. The game is very slow in places (for example Uber Tristam, the animation after Shenk dies, anything with Necromancers with large numbers of Revives, etc.), but it's very important to point out that these results are not significantly worse than what I was experiencing when I was running the game "natively" using DirectX 8 under Window$ XP -- and note that when I was doing so, I was very careful to shut down Window$ background tasks, such as AV software and IM clients, that could adversely impact the performance of the game.

It's really an amazing testament to the ability of the Linux OS and the WINE emulator, when you consider how difficult it must have been to emulate Microsoft's highly proprietary, closed-source platform. (Or maybe it's an indictment of Microsoft? Is the glass half empty or half full?)

I can make the following comments about what I have experienced:

_Video Drivers:_

I don't really like fancy desktop effects, nor the huge overhead that they typically impose, so I have intentionally disabled things like Compiz. Also, I am using the generic (Open Source) nVidia, ATI and Intel drivers that come with Ubuntu, as opposed to the proprietary manufacturer drivers for ATI and nVidia. 

My experiences with both of the latter have not been happy, ranging from corrupted desktop images to total system freezes, and these problems had nothing to do with running D2 or other games. Maybe it's because I am using very old video cards, but I had much better luck with just the built-in, Ubuntu video drivers.

_WINE Setup:_

Originally, I tried to run D2 in full-screen mode, as I had done under Window$. While I still do this from time to time on PC #1, I found that the best overall compromise between (a) frame rate, (b) game responsiveness, (c) aggravation in having to reset (X)Ubuntu video resolution modes and so on, was to (c) force the overall (X)Ubuntu screen resolution down to "1024 x 768" and then tell WINE to run D2 in a 800 x 600 resolution window. If you set the underlying (X)Ubuntu screen resolution much higher, I noticed that the frame rate slows down considerably -- maybe it's redrawing the whole screen as opposed to just the WINE / D2 window?

In terms of audio support, I experimented with ALSA and with OSS and they both worked. I left audio hardware acceleration at "Standard".

_Installation:_

In all cases, I installed the game simply by inserting the "Install" CDs (both for Classic D2 and LoD), waiting for (X)Ubuntu to automount the CD and then double-clicking on the INSTALL.EXE file.

The only slight issue that I had, in any of these situations, was that you should eject the various CDs that the Blizzard installer program asks you for, by right-clicking on the relevant desktop image and selecting the "Eject" option (in other words do it via software, rather than by manually ejecting the CD with the button on the front of the CD or DVD drive itself). You do have to be patient, here, because there is sometimes a 2 to 3 second latency between when you tell (X)Ubuntu to eject a particular CD and when it actually pops out. If you try to rush the process along, the Blizzard installer can get confused as to what CD that it's waiting for... which can mean, "reinstall from CD #1".

Incidentally, I tried using dd to create an ISO image of the D2 key disk, but, due to deliberately created bad sectors on the CD (this is of course the stupid copy protection at work), the bit copying process stalled at about 65 per cent complete, with repeated "Disk I/O Error" messages from the terminal console. If I was really motivated, I suppose I'd find a way around this, but for a relatively cheap, 7 year old game I just can't be bothered.

_D2 Video Setup:_

The video setup in the Diablo program itself was interesting. On a couple of occasions, the D2 video tester told me "no valid graphics modes detected". My solution to this problem is, in order:

(a) Shut down the current instance of D2 under WINE, relaunch it under a new instance of WINE. If that doesn't work...

(b) Log out of your current (X)Ubuntu session and log in again. (I think this restarts X, or GNOME, or XFCE, or whatever). Then try step (a), again.

(c) Finally, failing all of that, try (oh no, shades of Window$ here) rebooting the computer. This worked for me once.

In terms of what to select, I found that the only video mode that really worked for me was "DirectX, 2D", and then I deliberately disabled fancy screen effects so that I'd get an acceptable frame rate on the lower-end machines. Attempts to experiment with other drivers (for example, DirectX 3D, OpenGL, etc.) usually resulted in either terrible frame rates (like, "3 frames per second"... ouch) or complete lockups at random times in the game. Since I almost exclusively play PVM Hardcore in Hell Difficulty Mode, stability is <ahem> quite an important issue for me, so I chose the safest route, which was 2D. Honestly, I don't miss the 3D perspective effects too much.

I was very surprised to discover that when I first logged on to Battle.Net with my instance of D2 under WINE, it invoked the 1.11b on-line patch, which happily went out and updated all my D2 executables in exactly the way in which it had under Window$. One word of warning, here: Don't try to just go and run D2, immediately after this patch is finished (and for God's sake don't "send a report to Blizzard" -- preserve your privacy!). Instead, exit D2 and the WINE emulator completely, then re-run the game.

A minor issue with installation was that under "real" Ubuntu, I got a correct-looking LoD icon (the blue one with the "face of Diablo" in it) on my desktop. Under Xubuntu, I did get a launcher icon which worked perfectly well, but it was the generic "blank document" picture on the icon, as opposed to the nice, gamesy Blizzard one. Oh well.

_Game Play:_

Since I am using D2 in the way in which Blizzard intended it to be used, I have the key CD in the drive while I'm playing. Let me say for the record that I don't particularly like doing this -- while I had the game under Window$, I was using the Hekko Virtual CD emulator ("CircleScan"), which worked reasonably well under XP, but which of course doesn't work under Linux -- but here again, I'm not sure that the effort that would be required to find a fool-proof, Warden-proof CD emulator for Linux would be worth the effort. (I don't want to get my CD-Key banned, doodz.)

One annoying thing about having to leave the CD in the drive is, I am using older CD-ROM drives that sound like a 747 taking off when they're spinning... which they do constantly, if you're outside a D2 playing session, because they always play that atmospheric D2 background music when you're just in the session creation or account / character manipulation screens. There doesn't seem to be any way of turning off this background music under WINE, even if you move the "Music" volume selector all the way to the left when in a D2 session.

I discovered that the "Alt" key didn't work properly, under windowed WINE sessions. This is, of course, also annoying because it's the key that you use to identify all the goodies that are lying on the ground after you trash Baal for the 34th time tonight... I mean, you just gotta know about that "cracked sash", right? The only solution that I could come up with, here, was to remap the "A" key to the "Show Items" setting in "Configure Controls"... it takes a bit of getting used to, but eventually using "A" instead of "Alt" became second nature to me.

For various reasons I have disabled the "Allow window manager to restrict mouse to screen" setting under WINE setup. You have to be aware of this during high-intensity game play, because it's not cool to mistakenly click outside the D2 window and have the XFCE or Gnome Desktop Manager take over from Diablo and try to get you to create a new folder, while you're running away from the pack of 18 Extra Strong, Extra Fast, Cursed Frenzytaurs with the Fanaticism aura. (Solution: Learn how to create a folder, or hit the "Esc" key, real fast.)

_Bugs / Crashes:_

Before I state what's below I should point out that I encountered random Diablo crashes under Windows, as well, at about the same frequency as I have under WINE and Linux, so in this respect running the game under Ubuntu is neither better nor worse than it is for running it in its "native" environment.

The most annoying bug, or near-bug, that I have encountered with D2 under WINE occurs exclusively under "real" Ubuntu (not Xubuntu) and it happens consistently under both Gutsy (7.10) and Hardy (8.04). The minute that I get a D2 session up and running, I see constant hard drive activity, the frame rate seems to stay at its normal speed (on PC #2 this is about 24 fps, no dropped frames), but the game is quite unresponsive... you wouldn't want to be fighting anything dangerous while this is going on.

The elevated hard drive thrashing persists for a minute or two then goes away by itself, after which the game is perfectly playable. And yes, I have tried to track down the offending process both through the built-in GNOME tools and the "htop" utility under the Terminal... there doesn't seem to be anything causing it, certainly nothing that's using a significant amount of CPU. (BTW, "GAME.EXE", which is the main D2 executable, seems to consistently use about 75% of my P-4's cycles, whether or not anything is in fact going on in the actual game session... my character can just be sitting in the Rogue Encampment and the CPU usage is the same as when she's fighting her way through the Pits.)

The second-most annoying bug is that D2 occasionally crashes when exiting from an online Battle.Net session, much more rarely when within a session, with an "Illegal Instruction 81000" error. This is usually preceded by the warning sign of characters, including NPCs in the town areas, moving at a snail's pace, as if the frame rate has crashed to zero. (For the record, it did something very similar under Window$, every so often.)

I suspect that this is some kind of DirectX or video emulation issue, because if I exit that instance of WINE, restart WINE and D2, I sometimes get exactly the same error, soon thereafter; but if I (see above) completely log out of XFCE / GNOME and then log back in, it invariably fixes the problem.

_Summary:_

Other than for those issues, the game basically works exactly as it does under Window$, so I'm a happy camper with (X)Ubuntu and WINE... now, if we could just get Mark Shuttleworth to eliminate all the TPPKers and other cheaters from Battle.Net. Do you think he has enough money to set up an Open Source version of BNet and survive the resulting onslaught from Blizzard's money-grubbing copyright lawyers? (I mean, if the EU can force Micro$oft to divulge its client-server communications protocols, who's to say that it can't force Blizzard to divulge how the D2 client talks to D2 servers, as well?)

Just a thought. On with Open Source... power to the people!

Mister Bill

---

### Post by Nobby on 2008-05-01
> **dealen said:**
> i installed diablo 2 + lod ( orginal games ) without having problems and i patched v1.11. I try to play game intro and cinematics are okey but main menu isnt appear but main menü sounds and button sounds comming, i mean game is not locked. When i did winecfg virtual desktop there is no problem but i want to play full screen. I have latest nvidia driver and in use what should i do ?

I'm having the same problem too.  It's like the game is coming up too big and the bottom is off the screen.  This happened since I installed a fresh Hardy & wine 0.9.60.  Before I was running Gutsy & 0.9.59 & everything was ok :(.

---

### Post by cb951303 on 2008-05-01
I didn't test it with 0.9.60 but this might be a regression

---

### Post by Envirotech on 2008-05-06
> **Nobby said:**
> I'm having the same problem too.  It's like the game is coming up too big and the bottom is off the screen.  This happened since I installed a fresh Hardy & wine 0.9.60.  Before I was running Gutsy & 0.9.59 & everything was ok :(.

I also get this and I am using Cedega. I did not have a problem with this in gutsy. I think it has something to do with the system not displaying the res of 800 x 600 properly.  I am using the 169.12 restricted driver. I had the problem after I did a upgrade from gutsy to hardy. So I reinstalled from scratch and the problem still exists. Is it xorg or the nvidia driver that is messing it up?  Any help would be appriciated. I have not tried the beta driver because I did not figure out how to purge the old ones. (i do now and I will try when I get home and see If I can fix this.)
:(

Also as to the cd mounting problem I am also having a problem with that.  I think that is a seperate issue with gnome-mount. 
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/203574](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/203574)

I hope the fix is pushed soon.

edit: the 173.08 also did not fix it. bummer

edit 2 : 96.43.05 nvidia drivers work without a proplem. Yaa I am posting this in the NV forums.

[http://www.nvnews.net/vbulletin/showthread.php?p=1649205#post1649205](http://www.nvnews.net/vbulletin/showthread.php?p=1649205#post1649205)

---

### Post by OpposingForce on 2008-06-01
I only have one problem so far, I start the game, and the intro scenes play and everything, but when the main menu comes up, I hear music and everything but it's not on screen.  I think it's a resolution bug, because, when I alt tab to some other program, then switch back to diablo, it works, and I have no issues from that point on (and can play online and everything).  But it happens every time you hit "save and quit" to go back to the main menu, I have to alt tab to get it correctly on the screen.  It's a bit dumb but at least it works.  I'm using a 1280x1024 resolution on the desktop.  Nvidia 6800 GT, latest drivers through Envy.  Wine 1.0 rc3.  I'm using the original REAL cd and NOT D2 loader.

Edit- and another bug.  On battle.net I can see servers, and can join one, but as soon as I leave, no servers appear in the list,  when I quit to the battle.net character select it says connecting for like forever.  The only way to get things back to normal is to completely exit battle.net, and log back in again.  It makes no sense.  Is this a game bug or a wine bug?  And how can I fix it?  Thanks.

---

### Post by FNDII on 2008-06-03
How would you make the game run in a window instead of full screen?

---

### Post by alzipan on 2008-06-05
By adding -w to the wine command.

I have no problems running it in a window, I just can't run it full screen. I get an Error 22 about failing while initializing DirectDraw.

---

### Post by Shadowmeph on 2008-06-16
New ladder starts tommorrow ( tuesday June 17th) now I used to play d2 all the time on windows and used to edit my registry "[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Diablo II]
"AllowHardcore"=dword:00000001 " so I could play hardcore. well I am new to wine and linux I had no problem installing D2LOD but am at a loss of how to get into the hard core ladder area anyone have any Ideas?

---

### Post by Swarms on 2008-06-16
> **Shadowmeph said:**
> New ladder starts tommorrow ( tuesday June 17th) now I used to play d2 all the time on windows and used to edit my registry "[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Diablo II]
"AllowHardcore"=dword:00000001 " so I could play hardcore. well I am new to wine and linux I had no problem installing D2LOD but am at a loss of how to get into the hard core ladder area anyone have any Ideas?

Just borrow a friends account with a character that has already completed hell, this enables you of creating hc chars on other users.

---

### Post by Shadowmeph on 2008-06-16
> **Swarms said:**
> Just borrow a friends account with a character that has already completed hell, this enables you of creating hc chars on other users.

I guess I could do that. How do I play in windows mode I see the -w command but I am not sure where to put it, is it possible to run multible d2s like I did when I had windows?

---

### Post by Swarms on 2008-06-16
About the windowed mode, I haven't tried it myself but the trick is to add -w to the launcher. I tried experiementing with it myself but couldn't figure it so all ears aswell. :)

Btw. if you need such a friend with a hc enabled account, just pm me.

---

### Post by LibertyShadow on 2008-06-16
Has anyone ever been banned from Battle.net for using wine in Diablo II?  I have been using Wine to play Diablo II Expansion for a month and a half now without any sign of problems.

I tried to Google an answer, and I saw that some WoW people were banned :confused:

---

### Post by Envirotech on 2008-06-16
> **LibertyShadow said:**
> Has anyone ever been banned from Battle.net for using wine in Diablo II?  I have been using Wine to play Diablo II Expansion for a month and a half now without any sign of problems.

I tried to Google an answer, and I saw that some WoW people were banned :confused:

I have been playing Diablo II for about 1 1/2 years with wine / winex and never got banned.

In my previous post I said I had a problem with Diablo II looking like it is zoomed in. I found a fix for it.  I put below in my xorg.conf. 

Option "ModeValidation" "NoXServerModes" 

I also can use the beta driver with this fix.  I got it from here.
[http://www.nvnews.net/vbulletin/showthread.php?t=106808](http://www.nvnews.net/vbulletin/showthread.php?t=106808)

---

### Post by LibertyShadow on 2008-06-17
Wow, we don't need the cd in 1.12a anymore!

I sure hope we don't get banned in this version either...

---

### Post by Shadowmeph on 2008-06-17
> **LibertyShadow said:**
> Wow, we don't need the cd in 1.12a anymore!

I sure hope we don't get banned in this version either...

I canoot connect after I installed the update is anyone else having this problem? I know they are online because othwers have been playing for a while today

---

### Post by LibertyShadow on 2008-06-18
I am not having problems connecting, but I also wined the blizzard updater because the first attempt through wine failed.
[http://us.blizzard.com/support/article.xml?articleId=20758]("http://us.blizzard.com/support/article.xml?articleId=20758")

So I guess they patched d2loader and as a result alot of hacks and bots are being banned.  Still no fix for anya bug, or patch for farcast.

---

### Post by Shadowmeph on 2008-06-19
> **LibertyShadow said:**
> I am not having problems connecting, but I also wined the blizzard updater because the first attempt through wine failed.
[http://us.blizzard.com/support/article.xml?articleId=20758]("http://us.blizzard.com/support/article.xml?articleId=20758")

So I guess they patched d2loader and as a result alot of hacks and bots are being banned.  Still no fix for anya bug, or patch for farcast.

I firgured it out I had to go to the folder and manually use the Link to BNUpdate.exe after it updated I had no problems connecting

---

### Post by alecz20 on 2008-06-24
The new patch really messed up the game for me.

I get plenty of random crashes. Sometimes when I click the portal in a game, or "Save and Exit" it causes Diablo to crash with an Access Violation Error.

Anyone else got this problem?


The second problem is that Alt+Tab restarts the session (Same effect as Ctrl+Alt+Backspace). - **This happened in 1.11 as well.**

1 - Enter game
2 - alt+tab to the Desktop
3 - Atl+tab back to the game
    Step 3 sometimes does nothing, so I have to switch workspaces.
4 - Notice the Session reset (all unsaved work lost).

I would be more than happy to provide any additional information on these two problems.

The Alt+Tab problem has been occurring over several wine versions.

Some system info:
7.10 all updates
Wine 1.0 (latest)
Default Wine configuration
No Desktop effects
Acer Laptop with Core duo, 2 GB ram, Intel GMA950 card (original drivers)

The info is of the top of my head, because I am at work.

Thanks

---

### Post by FNDII on 2008-07-01
D2 runs in a window for me when I run wine as a virtual desktop.

Wine<Settings<graphics<check the box run in virtual desktop

---

### Post by xdarkday on 2008-07-02
> **OpposingForce said:**
> I only have one problem so far, I start the game, and the intro scenes play and everything, but when the main menu comes up, I hear music and everything but it's not on screen.  I think it's a resolution bug, because, when I alt tab to some other program, then switch back to diablo, it works, and I have no issues from that point on (and can play online and everything).  But it happens every time you hit "save and quit" to go back to the main menu, I have to alt tab to get it correctly on the screen.  It's a bit dumb but at least it works.  I'm using a 1280x1024 resolution on the desktop.  Nvidia 6800 GT, latest drivers through Envy.  Wine 1.0 rc3.  I'm using the original REAL cd and NOT D2 loader.

I am having this same issue, only I cant get it to work by tabbing either. It seems like the screen for that tab freezes. Any fix for this yet?

---

### Post by brundlelinux on 2008-07-06
Just thought I'd chime back in and add a few insights since my last post.

Number 1)  I've now been running Diablo II LOD on Ubuntu/Wine for about 2 years.  I have NEVER had any issue with Blizzard thinking I was a hacker or min any other way violating the EULA and attempting to ban me.  Nor has this happened to any of my friends who use wine for Diablo.  Well, one friend... which brings us to...

Number 2)  One friend of mine was using MH to play.  He was detected and temp banned.  So, don't think that running Diablo on linux shields you from being detected with your MH / Pickit / bot prog.

Number 3)  The official release of Wine 1.+ has greatly reduced the number things I had to tweak to get the game to run.  I can honestly say that the game runs flawlessly and perfectly now without ANY tweaks.  Actually, it runs better than it did back on Windows.  The ONLY thing I ever have to do is re-assign the binding in-game for the ALT key to now be the space bar for showing items on the ground.

Number 4)  As most people know, Blizz has now given us the official option to play without a cd in the tray.  However, I mention it because there are still some people who don't realize that this was added in V 1.12.  Just copy over the .mpq files from the LOD disk to the diablo directory inside wine.  That's it.

I mention all of this because I used to be one of those people that HAD to use the Glide wrapper and HAD to use regression to an earlier version of wine to get the game to function properly.  I have nothing but kudos to the WINE team for their amazing advancements and code.

I wish everyone luck when D3 hits the shelves.  I must admit, I am NOT thrilled with what I've seen so far from D3 (AKA World of Diablocraft).  Total personal opinion.... I think taking this series to a 3D environment is a big mistake.  But, alas, I have been wrong before.  There was that one time back in the early 80's when I thought Beta was gonna blow VHS away.  Ha!

---

### Post by The Unmaker on 2008-07-06
I've been having an issue with installing LOD that I don't see (maybe I didn't look hard enough) addressed in this thread. I installed Diablo II with no problems but when I insert the LOD disc, it doesn't read it at all (in KDE. I already mounted the CD) and just gives the message:

Please insert the Diablo II CD labelled "Expansion Disc"

I was able to install Diablo II without any problems, so I don't think it's anything on part of the previous problems mentioned (such as not being able to access the hidden messages and ejecting the CD problem because it is tied up by bash). I've tried to access it using install.exe and setup.exe both and no avail:

wine /media/cdrom/install.exe

I have the virtual desktop emulation enabled (see above comment on the hidden ejection messages).

There are other unresponded threads on this. Any suggestions?

---

### Post by dserver on 2008-07-06
Has anyone tried getting a maphack to work? I've been playing around with EasyLoader (EPLite) but to no avail. See my thread on the topic: [http://ubuntuforums.org/showthread.php?t=850784](http://ubuntuforums.org/showthread.php?t=850784)

---

### Post by Cirno on 2008-07-09
Does anybody know how to install Diablo 2 + LoD using the Blizzard store installers? I lost my CDs quite some time ago but still had the keys written down, and when I found out I could get the games that way I was thrilled. I installed them on my Windows partition, but I figure if I can get them on my Ubuntu partition it'll be one less reason to boot up the other.

I've tried just running them with Wine and it doesn't work. Here are the results:

```
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```

Any help would be greatly appreciated!

---

### Post by brundlelinux on 2008-07-09
I'm not familiar with the Blizzard store.  What kind of downloads are they?  If it's ISO files, you can just create a mount point from your Windows partition to your Linux partition and run them with Wine.  

If it's another type of file, such as an actual executable .exe file(s), I'd create the mount point and copy them over to your linux partition and place them in your .wine folder and run them that way.

I'll help however I can if that doesn't work.

Edit:  To clarify... if you are dealing with ISO files, you will also need to mount them, so copying them over from partition to partion is probably the easiest way to go either way.

---

### Post by The Unmaker on 2008-07-10
> **The Unmaker said:**
> I've been having an issue with installing LOD that I don't see (maybe I didn't look hard enough) addressed in this thread. I installed Diablo II with no problems but when I insert the LOD disc, it doesn't read it at all (in KDE. I already mounted the CD) and just gives the message:

Please insert the Diablo II CD labelled "Expansion Disc"

I was able to install Diablo II without any problems, so I don't think it's anything on part of the previous problems mentioned (such as not being able to access the hidden messages and ejecting the CD problem because it is tied up by bash). I've tried to access it using install.exe and setup.exe both and no avail:

wine /media/cdrom/install.exe

I have the virtual desktop emulation enabled (see above comment on the hidden ejection messages).

There are other unresponded threads on this. Any suggestions?

I figured it out. There is an option under winecfg called Auto Detect that will detect all mounted drives. It was detecting the drive for the first Diablo II Install, but not for the LOD install, so I just had to press that button and it finally detected the CD. Game works great. This was cleared up in this thread:

[http://ubuntuforums.org/showthread.php?t=443821&highlight=diablo+2](http://ubuntuforums.org/showthread.php?t=443821&highlight=diablo+2)

If anyone is having any problems, I suggest checking that one out.

---

### Post by ForlornEgoist on 2008-07-23
So, I'm having problems installing D2: Xpansion.

Its start installing fine then freezes when it gets to D2XTalk.mpq. I've xfered all other files into the C://Diablo 2 folder manually as necessary (including the d2xtalk.mpq and D2music.mpw files) but I can't seem to get the damn thing to install.

The disc is in near-mint condition (with a negligble scuff and several scratches).

I don't get any error messages, it just simply stops xfering the file and then asks for the EXP. disc. I've tried this on several different computers (of varying types and efficiencies) which implies its a problem with the disc. Only, as forementioned, its in near-mint.

If you could help me to fix this problem, I'd appreciate it.

Note: I'm planning to buy a new Expansion pack if necessary. I'd prefer to find the problem with mine, however.

---

### Post by cetheriel on 2008-07-24
let me help with some issues that have already been solved:
*can't install: if it stops installing, try moving the window around. you might find out there is a window asking to change discs, but it is hidden behind the install window.
*no-cd patch: since patch 1.12a you don't need any. just install it and copy d2xmusic.mpq
*crashes on windowed mode: do not try running diablo with the -w option. instead, run on emulated desktop (wine config>graphics>emulate virtual desktop). i suggest a 800x600 emulated desktop. (do this only after install).
*alt+clicking fails: on wine config>graphics turn off "Allow the window manager control the windows"

ok so far?
my problem is that i can't mount the Expansion.iso i got, though running DameonTools on window$ mounts it pretty fine...

---

### Post by Lasperic on 2008-08-03
Hi 

I am now installing Diablo II on ubuntu 8.04. Had a bit of a problem with installing (always asking to put the cd in the drive although it was there) i was able to solve it by a symlink to a cd (easy through winecfg) but when i got to installing LOD it always pops up with a message that i need have diablo II installed before i want to install LOD . I have tried to only copy mpq files from lod cd but it doesent allow me to play druid nor assasin and if i try equip item like the head shield for a necromancer the game unexpectedly crashes . So i figured i need to get LOD to install the "normal way". So to get to the pont what i am asking is "does anybody know how to get the diablo II LOD to detect that i HAVE classic diablo II installed already?" any help or tips welcomed. 

Thanks ;)

Edit: NVM figured it out (just had to install diablo II from the beffining with diffrent approach hope it works better now (got to installing lod about now and it recognizes diablo II now :P )

---

### Post by Featherhead on 2008-08-04
I also have the digital downloads from the Blizzard store, and when I attempt to install them, I can't get passed the EULA because agree never becomes clickable. There is a solution over in the WineHQ AppDB, but being completely new to Ubuntu I'm having trouble following exactly what needs doing. Here's a link to the Wine page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=49](http://appdb.winehq.org/objectManager.php?sClass=version&iId=49)

Can anyone help clear things up for me? Thanks.

---

### Post by Lasperic on 2008-08-04
> **Featherhead said:**
> I also have the digital downloads from the Blizzard store, and when I attempt to install them, I can't get passed the EULA because agree never becomes clickable. There is a solution over in the WineHQ AppDB, but being completely new to Ubuntu I'm having trouble following exactly what needs doing. Here's a link to the Wine page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=49](http://appdb.winehq.org/objectManager.php?sClass=version&iId=49)

Can anyone help clear things up for me? Thanks.

Sure i had this problem too . ifound a guide somewhere on the internet . I forgot where so i will try to help you as best as i can on my owm.
Firstly install ies4linux ([http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation))
Install it then copy mshtml*.* from ~/.ies4linux/ie6/drive_c/windows/system32 to ~/.wine/drive_c/windows/system32 . Then run winecfg (in console).There find the library tab and add mshtml .Apply the changes and try now . That worked for me . Let us know if it helped ;)

---

### Post by Zyferian on 2008-08-20
Hey, guys... I did the install the old fashioned way with the isos, though to be honest, I'm wondering if doing it with the digital downloads might be better, since I have keys for that. 

Anyway... I got the program nicely installed and everything, but I ran into a little problem. Basically, when I go to play the game I can't see the bottom half of the screen. In other words, everything below the "Other Multiplayer" option is not visible. This has to do with running the game in 640x480 from what I've heard... but I have to run it in that res, since my computer won't support above that. 

Yep, you guessed it, I'm attempting to run this thing on an EEE PC 701. Any help would be awesome. 

That said, everything else on here is working like a dream.

---

### Post by Envirotech on 2008-08-20
I found the fix for Diablo 2 or any game that uses 800 x 600 resolution and it looks like it is zoomed in.

You need to put in the Device section of xorg.conf:

Option "ModeValidation" "NoXServerModes"

Thanks to the people in this thread. (dahveed3)

[http://www.nvnews.net/vbulletin/showthread.php?t=106808](http://www.nvnews.net/vbulletin/showthread.php?t=106808)

[http://www.nvnews.net/vbulletin/showthread.php?t=10730](http://www.nvnews.net/vbulletin/showthread.php?t=10730)

This Worked great for me. I had a hell of a time tring to fix it for my Ubuntu install.

> **Zyferian said:**
> Hey, guys... I did the install the old fashioned way with the isos, though to be honest, I'm wondering if doing it with the digital downloads might be better, since I have keys for that. 

Anyway... I got the program nicely installed and everything, but I ran into a little problem. Basically, when I go to play the game I can't see the bottom half of the screen. In other words, everything below the "Other Multiplayer" option is not visible. This has to do with running the game in 640x480 from what I've heard... but I have to run it in that res, since my computer won't support above that. 

Yep, you guessed it, I'm attempting to run this thing on an EEE PC 701. Any help would be awesome. 

That said, everything else on here is working like a dream.

---

### Post by NosLycn on 2008-08-21
I've got an odd little issue with Diablo 2.  When playing, occasionally, and without warning, the colors will go wonky.  No error is generated at the time of screen funk.

[[IMG]http://farm4.static.flickr.com/3033/2785952558_4f01b3b6cd_m.jpg[/IMG]]("http://farm4.static.flickr.com/3033/2785952558_e859346abd_o.png")

I have no idea what's going on.  Changing from 800x600 to 640x480 and back again temporarily fixes it, but there are still funky colors on things like the chat, and the boxes behind loot when pressing ALT.

Has anyone else experienced this issue?

---

### Post by Envirotech on 2008-08-22
@NosLycn, Does this also happen with your desktop? What about other games does it do the same thing? What about in windowed mode does it happen there?  Did you run the video test? Also did the ever run properly with this current setup? My first impression was maybe a loose video cable except this image was captured and so it could not be that.  Did you get a bad install of video drivers? If it does not do it in other games then I would check your wine config maybe something in there is messed up.

---

### Post by onclouds on 2008-11-25
Hi,

I'm a first time installer of Diablo 2 LOD on Ubuntu 8.10..

I have a few remarks.. 

1) I need to click Alt-Tab away from the game window then back again, click with the right mouse button and maximize/restore the window for the main screen to appear! (note that the 2 intro screens work fine)

2) After this I login to BN only to realise that I no longer have sound (Again, intros played sound without a problem)

Can anyone help me? I know sound isn't of much importance in Diablo but I still like to hear my sorceress' light cast! =)

thanks in advance

edit: I disabled Visual Effects (i believe it's Compiz) and solved the first issue! The sound problem remains though. =/

edit2: SOLVED!
I had only tried the game with ALSA for sound as most of the threads I've read recommend it.. But now I found one that said someone solved the issue by using OSS instead of ALSA and decided to try it.. It worked!!! Serves me right for not trying everything before asking questions! ;)

edit3: found the problem.. was using wine 1.0.1... updated and am now using ALSA driver. Sound works great!

PS: thanks for not replying to call me an idiot! xD

---

### Post by Symbolis on 2009-01-08
Decided to dig out my Diablo II+LoD  CDs and give it a spin under WINE.(Well, PlayOnLinux)

Install went smooth.
Running went smooth.

However, the first time I left click in game, I can no longer right click.

Any ideas?

Running 1.1.12 under Ubuntu 8.10(PlayOnLinux is 3.2.2)

EDIT:

Turns out I'm just an idiot and forgot that Raise Skeleton needs a corpse to function. Leaving this here to amuse others. ;)

---

### Post by arron on 2009-01-12
Nice......  Its happens to us all...  Now raise those skellies and kill!

I ant wait for D3 :-) Great excuse for a new pc too.

---

### Post by melzanis on 2009-01-31
Hi,
   I just installed D2 about 20 mins ago. It worked so well that I didn't need the loader. However, the window is a little smaller then I would like. I also changed the in-game resolution to 800x600 but even that is to small. 

I was hoping that there was a way to make it a little bigger?

---

### Post by cb951303 on 2009-01-31
> **melzanis said:**
> Hi,
   I just installed D2 about 20 mins ago. It worked so well that I didn't need the loader. However, the window is a little smaller then I would like. I also changed the in-game resolution to 800x600 but even that is to small. 

I was hoping that there was a way to make it a little bigger?

nope, thats how D2 is. 800x600 is the best you can get. If you have a higher resolution monitor it will look really tiny

---

### Post by Slakker on 2009-02-17
Hey all,  working on getting D2X to run on an old laptop, a Dell Inspiron 5000e.  I think my problem lies somewhere in the video drivers, as just getting my screen to display properly (was torn into three overlapping vertical bars, and still is at lower resolutions).

I was able to at least launch D2 earlier, but when I tried to copy over the *.mpq files and run it without the CD I started having some issues.  Neither the official *.exe nor D2Loader are having any luck getting it going, I'm running it in a Wine virtual desktop.  The window goes black as if it were about to start and I get an error message about an except or access violation or something.  Figuring that message would be pretty generic and not all that helpful (since it was the "Hey guys, we got a problem" message when i tried to run it fullscreen) I tried to run it from terminal, here's the output:

```

fixme:advapi:SetSecurityInfo stub
tmslak@ubuntu:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x33eae4,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
```

Anyone got any ideas?  It appears to be a graphics issue, but it at least launched before I tried doing it disc-less.  My graphics card is an ATI Rage 128.

---

### Post by cb951303 on 2009-02-18
> **Slakker said:**
> Hey all,  working on getting D2X to run on an old laptop, a Dell Inspiron 5000e.  I think my problem lies somewhere in the video drivers, as just getting my screen to display properly (was torn into three overlapping vertical bars, and still is at lower resolutions).

I was able to at least launch D2 earlier, but when I tried to copy over the *.mpq files and run it without the CD I started having some issues.  Neither the official *.exe nor D2Loader are having any luck getting it going, I'm running it in a Wine virtual desktop.  The window goes black as if it were about to start and I get an error message about an except or access violation or something.  Figuring that message would be pretty generic and not all that helpful (since it was the "Hey guys, we got a problem" message when i tried to run it fullscreen) I tried to run it from terminal, here's the output:

```

fixme:advapi:SetSecurityInfo stub
tmslak@ubuntu:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x33eae4,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
```

Anyone got any ideas?  It appears to be a graphics issue, but it at least launched before I tried doing it disc-less.  My graphics card is an ATI Rage 128.

could you post the output of **glxinfo | grep "direct rendering" **

---

### Post by Slakker on 2009-02-18
Thanks for the reply!  Any other info you need?

```
direct rendering: Yes
```

I've been thinking maybe a re-install would do it, but if there's a way to get it fixed without going through that whole song and dance it would be excellent.

---

### Post by soulbog on 2009-03-29
how do i install diablo 2 lod with the new wine ? i get insert the diablo 2 lod cd . and i realy got the original cd key but got a image.:confused::(

---

### Post by delog on 2009-04-27
Thank You :P

---

### Post by lpfan076 on 2009-06-07
Just a quick heads up to everyone, bnet currently bans for d2loader, and that was mentioned in the setup instructions. Everyone should use the original game.exe to run.

---

### Post by Saija on 2009-06-08
Hi all guys

This games installed just fine in my old Ubuntu install(a Hardy x86 i think...), due to some hard disk problems it was necessary to just bought and make a clean install, this time i installed a Hardy x64 version, everything seems fine, but when i try to install Diablo II this error appears:

> saija@hal-9000:/media/cdrom0$ wine SETUP.EXE
err:module:map_image Could not map section .text, file probably truncated
wine: could not load L"C:\\windows\\temp\\d2l_Install.exe": Bad EXE format for

Then i tried to run another executable in the cdrom and this its what i get:

> saija@hal-9000:/media/cdrom0$ wine Install.exe
wine: Unhandled page fault on write access to 0x00000000 at address 0x43c658 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x0043c658).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0043c658 ESP:0033ff0c EBP:0033ffe8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7b8b37f8 ECX:b8df2119 EDX:00000000
 ESI:7ffdf000 EDI:0043c658
Stack dump:
0x0033ff0c:  7b877689 7ffdf000 00000000 00000000
0x0033ff1c:  00000000 00000000 00000000 00000000
0x0033ff2c:  ffffffff 7b874cd0 7b843c60 7b8b37f8
0x0033ff3c:  ffbad370 00000014 0033ffe8 57cfafee
0x0033ff4c:  3edad919 00000000 00000000 00000000
0x0033ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x0043c658 EntryPoint() in install (0x0033ffe8)
0x0043c658 EntryPoint in install: addb  %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000- 1478000       Export          install
ELF     7b800000-7b94f000       Deferred        kernel32<elf>
  \-PE  7b820000-7b94f000       \               kernel32
ELF     7bc00000-7bcad000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bcad000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7efa3000-7efae000       Deferred        libnss_files.so.2
ELF     7efae000-7efc6000       Deferred        libnsl.so.1
ELF     7efc6000-7efeb000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     f7c55000-f7c59000       Deferred        libdl.so.2
ELF     f7c59000-f7da8000       Deferred        libc.so.6
ELF     f7da9000-f7dc1000       Deferred        libpthread.so.0
ELF     f7dd6000-f7f11000       Deferred        libwine.so.1
ELF     f7f13000-f7f32000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\Install.exe
        00000009    0 <==
0000000c
        00000016    0
        00000013    0
        00000012    0
        0000000e    0
        0000000d    0
0000000f
        00000015    0
        00000014    0
        00000011    0
        00000010    0
00000019
        0000001a    0
Backtrace:
=>0 0x0043c658 EntryPoint() in install (0x0033ffe8)


Any ideas what can i do or set just to install and play this game?

Thank you.

---

### Post by Lockheed on 2009-06-26
I am running D2 in wine using Glide wrapper and Emulated Virtual Desktop on 1280x800. The game works great in fullscreen. 

The problem is that if I switch to another ubuntu virtual desktop (say, to check an email) and then I swich back to Diablo, all I can see is an empty blue desktop with diablo icon in the bottom-left corner. I can still hear the game music/sound so the game is running, but I can see nothing.

I am using compiz.

Any guesses?

---

### Post by cb951303 on 2009-06-26
> **Lockheed said:**
> I am running D2 in wine using Glide wrapper and Emulated Virtual Desktop on 1280x800. The game works great in fullscreen. 

The problem is that if I switch to another ubuntu virtual desktop (say, to check an email) and then I swich back to Diablo, all I can see is an empty blue desktop with diablo icon in the bottom-left corner. I can still hear the game music/sound so the game is running, but I can see nothing.

I am using compiz.

Any guesses?

did you try alt+tab window switching?

---

### Post by Lockheed on 2009-06-26
> **cb951303 said:**
> did you try alt+tab window switching?

Yes but all it does is switching between ubuntu windows and blue wine desktop is one of them.

---

### Post by cb951303 on 2009-06-26
> **Lockheed said:**
> Yes but all it does is switching between ubuntu windows and blue wine desktop is one of them.

Did you try disabling compiz?

---

### Post by Lockheed on 2009-06-26
No, but that's not really an option for me. Can't live without the desktop wall.

---

### Post by TheBuzzSaw on 2009-06-26
I strongly recommend that any D2 players go to Battle.net, register your keys, obtain your "new" keys, and download the disc-free installer Blizzard now provides. It is far less tedious to install from files on your hard drive instead of from four swapping CDs.

---

### Post by Lockheed on 2009-06-26
> **TheBuzzSaw said:**
> I strongly recommend that any D2 players go to Battle.net, register your keys, obtain your "new" keys, and download the disc-free installer Blizzard now provides. It is far less tedious to install from files on your hard drive instead of from four swapping CDs.

Where exactly can I register my key? Can you provide direct link?

---

### Post by cb951303 on 2009-06-26
> **Lockheed said:**
> No, but that's not really an option for me. Can't live without the desktop wall.

in that case I'm pretty sure that diablo window is actually in a minimized status somewhere in the blue desktop window but I don't know how to revive it...

---

### Post by TheBuzzSaw on 2009-06-26
> **Lockheed said:**
> Where exactly can I register my key? Can you provide direct link?
[http://www.battle.net/](http://www.battle.net/)

Register an account. Once inside, it is a very easy process to register your games. Once a game is registered, a download link opens up for that game (and you are given a new key based on that new installer).

---

### Post by Lockheed on 2009-06-26
Thanks, **TheBuzzSaw**

> **cb951303 said:**
> in that case I'm pretty sure that diablo window is actually in a minimized status somewhere in the blue desktop window but I don't know how to revive it...

Anyone knows how to do it?

---

### Post by Lockheed on 2009-06-30
Well, it started to work just by itself. Now, by clicking on the Diablo icon on this blue desktop, I can restore the game to fullscreen.

I have another questions though. 

**1.** Sometimes by combining RMB and Alt within the game, a Gnome menu comes out (the one with windows Minimize, Maximize, etc.) and this is very dangerous cause until I click somewhere outside of it, I lose control over the game.
Can I disable this menu?

**2.**How can I enable 3d Sound in Diablo?

---

### Post by cb951303 on 2009-06-30
> **Lockheed said:**
> 
**1.** Sometimes by combining RMB and Alt within the game, a Gnome menu comes out (the one with windows Minimize, Maximize, etc.) and this is very dangerous cause until I click somewhere outside of it, I lose control over the game.
Can I disable this menu?


[quote=cb951303]
Graphics -> Unselect "Allow the window manager to control the windows"
We do that to be able to press Alt/Shift and mouse buttons at the same time while playing. It's a must-do for Diablo
[/quote]

have you seen this? first post of the thread :popcorn:

---

### Post by Lockheed on 2009-06-30
> **cb951303 said:**
> have you seen this? first post of the thread :popcorn:

I could swear I had that unselected. Thanks for pointing that out.
Any clues on the second question?

---

### Post by Lockheed on 2009-06-30
Scratch that. I have **"Allow the window manager to control the windows"** unselected but still getting that anoying RMB menu ingame.

---

### Post by cb951303 on 2009-06-30
> **Lockheed said:**
> Scratch that. I have **"Allow the window manager to control the windows"** unselected but still getting that anoying RMB menu ingame.

hmm, are you changing it globally or just for diablo exe?
try changing it globally maybe?

I never used 3d sound for diablo so I wouldn't know. But in a 2d game, what's the purpose of 3d sound one may ask :)

---

### Post by Lockheed on 2009-06-30
> **cb951303 said:**
> hmm, are you changing it globally or just for diablo exe?
try changing it globally maybe?
I tried both. Didn't help.

> I never used 3d sound for diablo so I wouldn't know. But in a 2d game, what's the purpose of 3d sound one may ask :)
It's not about the positioning but the quality. I actually meant Environmental but those two seem to be coming together.
When you set the sound to "Environmental" the sound effects are much more realistic and generally pleasant.

---

### Post by cb951303 on 2009-06-30
you can always install the exact same wine version from the tutorial. that should work

---

### Post by Lockheed on 2009-07-01
Why would newer Wine brake one of its basic functions?

---

### Post by cb951303 on 2009-07-01
> **Lockheed said:**
> Why would newer Wine brake one of its basic functions?

what do you mean by basic?

these are called regressions.

---

### Post by Lockheed on 2009-07-01
I'd suppose disabling this menu is a basic function.

Were you able to get D3D in D2VidTest? I am only getting D2D even though I installed DirectX 9c.

---

### Post by Lockheed on 2009-07-24
I've been running D2 with Glidewrapper and in fullscreen mode with no problem (emulated desktop 1280x800).

However, the game can get really slow if they is a lot of action on the screen, so as most people, I decided to go for DirectDraw.

When using DDraw, I have to disable emulated desktop because otherwise I have small diablo in the top/left corner and huge blue sheet everywhere else.

The problem is that now if I alt+tab from the game (or switch to another desktop), my desktops are in 800x600 resolution which, besides being ugly and unpractical, screws up all my desklets. 

On top of that, most of my active windows dissapear (although processes are still running) and I have to kill them with task manager. As a bonus, this also happens with Diablo, so I am unable to get back to the game.

As a desperation, I tried DDraw Diablo in VirtualBox XP. Fullscreen runs but the game is just a 800x600 box within pitch-black 1280x800 screen.

I will be grateful for any suggestions EXCEPT those telling me to play in windowed mode.

---

### Post by cb951303 on 2009-08-25
[http://www.moddb.com/games/diablo-2/news/d2multires](http://www.moddb.com/games/diablo-2/news/d2multires)

Good news, apparently you can run d2 in any resolution you want with the above modification.

---

### Post by fou-lu on 2009-10-20
hey i was wondering if anyone could help me with my D2 problem.
im using ubuntu 9.04 jaunty
wine 1.1.13
i have D2 installed (not LoD) and the latest patch
it will play the first two videos and then it will go black and i can only hear the music but see nothing. the only thing i can do is press escape to close the window.
if someone could please help me that would be great
thnks
*edit* i was using opengl and i found that it doesnt let diablo2 work. so i opened it with the cd adn now i dont see any video and still hear the sounds.
also theres a block in the top left corner that characters flash by

---

### Post by shnurui on 2009-12-22
> **fou-lu said:**
> hey i was wondering if anyone could help me with my D2 problem.
im using ubuntu 9.04 jaunty
wine 1.1.13

There's yer problem...Update wine...

The only thing not working is the No-CD patch, which I can't figure out the argument for.

---

### Post by beastrace91 on 2009-12-23
> **shnurui said:**
> The only thing not working is the No-CD patch, which I can't figure out the argument for.

Its kinda hit or miss. I have friends on Windows that still need to use a CD to load the game even with the 1.12 patch.

~Jeff

---

### Post by Raymond Lanphere on 2009-12-29
Hey I need help installing D2 and LOD i have the installer.exe set to open with wine but when i click it it doesn't start anything.  Furthermore, when I type wine /media/cdrom0/installer.exe into the terminal I get this message 

wine: could not load L"D:\\installer.exe": Module not found
raymond@Optimus-Prime:~$ err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r

any help would be amazing thanks all

---

### Post by Elviswind on 2010-01-14
> **shnurui said:**
> There's yer problem...Update wine...

The only thing not working is the No-CD patch, which I can't figure out the argument for.

> **beastrace91 said:**
> Its kinda hit or miss. I have friends on Windows that still need to use a CD to load the game even with the 1.12 patch.

~Jeff

I've got the no CD thing working . . . I came across some instructions on the Blizzard website saying that you have to copy all of the .MPQ files to your Diablo directory from the Diablo II Play CD and LoD CD.

> If all required Diablo 2 '.MPQ' files are installed on the
  hard drive, the game will no longer require the CD to play.

   For users that originally performed a 'Full Installation'
   and wish to run without the CD, all '.MPQ' files should
   be copied from the Diablo 2 CDs to the Diablo 2 directory. 
   Most users will only need to copy D2Music.mpq from the
   Diablo 2 Play CD and/or D2xMusic.mpq from the Lord of
   Destruction CD.  Mac users will need to copy these music
   files and rename them to 'Diablo II Music' and
   'Diablo II Expansion Music' respectively.

   Anyone who did not perform a 'Full Installation' will need
   to re-install from CD again to ultimately play without the CD. 
   In this case, a 'Full Installation' is required, followed by file
   copy step noted above.

---

### Post by Lockheed on 2010-02-03
I discovered how can you play Diablo 2 in a window of resolution higher than 800x600. You will need [Sven glide wrapper]("http://www.svenswrapper.de/english/index.html") for Diablo 2. 

1. Configure wine desktop to given resolution, let us say 1030x795.
2. Configure diablo to run in Glide mode.
3. Then, in the advanced options of the Glide wrapper, set windowed mode, force resolution to, say, 1024x768 and voila!

[[IMG]http://img717.imageshack.us/img717/473/diablo.th.jpg[/IMG]](http://img717.imageshack.us/i/diablo.jpg/)

---

### Post by onclouds on 2010-02-03
> **Lockheed said:**
> I discovered how can you play Diablo 2 in a window of resolution higher than 800x600. You will need [Sven glide wrapper]("http://www.svenswrapper.de/english/index.html") for Diablo 2. 

1. Configure wine desktop to given resolution, let us say 1030x795.
2. Configure diablo to run in Glide mode.
3. Then, in the advanced options of the Glide wrapper, set windowed mode, force resolution to, say, 1024x768 and voila!

[[IMG]http://img717.imageshack.us/img717/473/diablo.th.jpg[/IMG]](http://img717.imageshack.us/i/diablo.jpg/)


I would advice against using that for Battle.net games... 
I read on a forum that Blizzard considers that as a third-party program (which it is ;)) and bans accounts that use it =/

---

### Post by Lockheed on 2010-02-03
I highly doubt it is detectable in any way, as all it does is acting as a glide interpreter and hence is fully transparent. 
It has nothing to do with methods applied by hacks, as maphack.

---

### Post by hikaricore on 2010-02-03
Yep the glide wrapper is safe.  Don't be a FUD spreader.  :p

---

### Post by Sugi on 2010-02-04
I was actually thinking about trying that Glide mode thing out.  I wonder if it supports stretching for my wide monitor. XD I got use and prefer everyone being horizontally long-aged.

Sugi

---

### Post by Lockheed on 2010-02-04
> **Sugi said:**
> I was actually thinking about trying that Glide mode thing out.  I wonder if it supports stretching for my wide monitor. XD I got use and prefer everyone being horizontally long-aged.

Sugi


Let me know if it does, but I don't think so. It seems to be using only  predefined window resolutions.

---

### Post by jamesixgun on 2010-05-08
Hello! I'm very new to ubuntu and linux, so bear with me...

I've read through this thread and have not found workable solutions for my problem.

Here's the problem: sound in Diablo II LoD lags by a full second.

I'm using PlayOnLinux 3.7.6
I've tried Wine versions 1.1.43, 1.1.38, and 0.9.35
I've tried ALSA and OSS and JACK and the other two audio drivers (I don't remember their names...)
I've tried changing the ALSA Driver in the registry to UseDirectHW REG_SZ y
And I think I've tried some other stuff, all to no avail.

In all instances, the same problem. Sound lags by a full second. This wouldn't be a problem, but i like to hear the monsters coming so I can prepare for battle. 

I'm running Lucid Lynx 10.04 on a revA MacBook (MacBook 1,1), and Diablo  II LoD 1.13c, windowed. (If this even makes a difference.)

Thanks for your help and suggestions.

j6g

---

### Post by LasseNC on 2010-05-09
Hello

I want to play Diablo 2 LoD on my Asus EEE with Kubuntu 10.04 LTS.

I copied the Diablo folder from my Windows laptop.

However I am getting "Insert Expansion disc" I tried autodetection as per the guide, but I don't have any CD-rom in the EEE.

Tried manually updating to 1.13c, but it already was.

---

### Post by TheBuzzSaw on 2010-05-09
> **LasseNC said:**
> Hello

I want to play Diablo 2 LoD on my Asus EEE with Kubuntu 10.04 LTS.

I copied the Diablo folder from my Windows laptop.

However I am getting "Insert Expansion disc" I tried autodetection as per the guide, but I don't have any CD-rom in the EEE.

Tried manually updating to 1.13c, but it already was.

Register your key on Battle.net. Download the self-contained CD-free installer. Install it in WINE.

Just copying over your previous installation is not a good idea. It loses registry information among other things to where it no longer works. Install it fresh and just copy over your characters folder.

---

### Post by vel. on 2010-06-21
Hi, 
I've tried installing the game through whine from the disks.
Since I re-installed my OS and currently don't have access to the d2 and d2 LOD disks I was wondering if it is possible to install the game using only the .iso files I have ripped from them.
I have 4 .iso files being the 4 disks from the original game.
How can I install them through wine :) ?
-Still quite new to ubuntu so it would be helpful if I could get a detailed explanation.
Thank you!

---

### Post by ftmichael on 2010-06-21
I'm running 10.04 (Lucid) and using wine 1.2, obtained from [this PPA](https://launchpad.net/~neil-aldur/+archive/ppa) as recommended in [this thread](http://ubuntuforums.org/showthread.php?t=1448614).  Diablo 2 and LoD installed with no problem, and the video test ran without a hitch.  As soon as I tried to play the game, though, my entire screen turned green and I couldn't do anything - no keys or mouse clicks worked.  I had to hard reboot.  I tried turning off Compiz; all that did was give me a grey screen instead of a green one when I next tried to run LoD.

I had previously tried obtaining wine through Synaptic, which gave me 1.1.42 and is what I used to install, but the game froze when I reached the menu screen and I had to force-quit, so I googled and found the recommendation to use wine 1.2.

I have no idea what the issue is.  LoD worked perfectly for me with 9.04 (Karmic), with the same graphics hardware (onboard Intel graphics chip).  I'm using a different monitor but I don't see why that would contribute to the problem.

Thoughts?

---

### Post by Breambutt on 2010-06-22
> **vel. said:**
> Since I re-installed my OS and currently don't have access to the d2 and d2 LOD disks I was wondering if it is possible to install the game using only the .iso files I have ripped from them.
I have 4 .iso files being the 4 disks from the original game.
How can I install them through wine :) ?
Well, I still use Gmount-ISO since the built-in archive mounter in Lucid seems a little shaky with multi-CD/image installers - it's much like what you'd do with Daemon Tools to mount images in Windows. You can download it with
```
sudo apt-get install gmountiso
```
after which you might want to run
```
sudo mkdir /media/Gmount
```
to create a mount point for the images that will appear as a CD drive alongside your actual drives. The original CDs need to be installed from the terminal since you aren't the owner of the CD drive, but with mounted images you can just start clicking away.

Should be pretty trivial. Mount and unmount when it asks for a new disk.

> I have no idea what the issue is. LoD worked perfectly for me with 9.04 (Karmic), with the same graphics hardware (onboard Intel graphics chip). I'm using a different monitor but I don't see why that would contribute to the problem.

Thoughts?
Probably "something" to do with the drivers but I'm afraid I don't know jack about those Intel chips. I'm curious, what happens when you try running it in a window?

Don't forget to try [http://www.svenswrapper.de/english/index.html](http://www.svenswrapper.de/english/index.html) in case it wasn't mentioned already. A funny way of scaling the window to your preferred size if nothing else, could also save lives if it's just X going bonkers when you try running the game in fullscreen.

P.S. Play classic, LoD is for wussies.

---

### Post by ftmichael on 2010-06-23
I switched back to wine 1.1.42 and reinstalled, and now it seems to be working, although there's no sound.  I'm afraid of switching to wine 1.2 again in case it screws everything up again.  Is wine 1.2 necessary to get the sound to work?

---

### Post by Siljrath on 2010-08-09
yeah, sound is a bit intermittent on mine.

fora while there i was running

		<item label="d2">
			<action name="Execute">
				<execute>
					wine /home/g/.wine/drive_c/d2/Diablo\ II.exe -w
				</execute>
			</action>
		</item>


(oops, thougt i had just the command in the clipboard, n not the whole openbox menu.xml entry, oh well, i'll leave it there for now)

with the -w, only because it wasnt working without it... but after several updates without checking, it now works for me without the -w, and i can once again enjoy edge to edge fullscreen without the blue win default desktop background colour, which i also had to have just in order to get it to work.   someone out there musta been sprucing up some code...  if i knew who, i'd flattr u.  ;)

dunno if i actually got anything from the tutorial again this time around... but searches brought me back around here for the inspiration to try grandr and sans -w.   ;)

---

### Post by greyscale42 on 2010-10-09
I just got Diablo II working in Wine (very easy after the update to the newest version) but whenever I play it and then exit the games all of the colors on my laptop look washed out. Sort of like someone airbrushed the hell out of my screen and then turned up the brightness and contrast. If I reboot my laptop all of the colors go back to normal but its still somewhat annoying. Any idea why this happens? Is there a simple way to reset the colors scheme on my laptop to go back to normal? I'm running Ubuntu 10.04.

---

### Post by mulliganl on 2010-12-06
> **fou-lu said:**
> hey i was wondering if anyone could help me with my D2 problem.
im using ubuntu 9.04 jaunty
wine 1.1.13
i have D2 installed (not LoD) and the latest patch
it will play the first two videos and then it will go black and i can only hear the music but see nothing. the only thing i can do is press escape to close the window.
if someone could please help me that would be great
thnks



I have a similar problem but with ubuntu 10.04 and wine 1.2.  Someone replied to this post to say that he should update wine, but my wine is the latest version.

Basically, I try to run Diablo 2 and the two Blizzard opening videos run fine, but the main menu won't load. There's just a black screen with a hint of the ubuntu tool bars around and I can only hit esc to close everything and go back to the ubuntu desktop.

I've run the video test and it suggested the 3d mode. I've tried both the 3d and 2d video and both have the same result.

Any help would be greatly appreciated.

---

### Post by GSF1200S on 2010-12-08
I had the same issue; disable compiz (or disable desktop effects) before launching the game. I do this in my script for launching diablo 2. A script like below would work:
```
#!/bin/bash
metacity --replace &
sleep 1
wine "/home/username/.wine/drive_c/Program Files/Diablo II/Game.exe"
sleep 1
compiz --replace
```

Haha, anyone in here know the viability of a pure bonemancer with a level 40 bonespear and full synergies in Hell difficulty Act V in singleplayer?

---

### Post by sudden0utburst on 2011-01-27
hey im having a problem... i installed diablo through wine...  when i put in the LOD disc... the whole cd rom device disappears.....  i also cant open the iso for some reason nor the mdf (i downloaded 2 to make sure it wasnt the image...)    

like i said the other cds work but when i insert the expansion one the disk drive itself disappears n it doesnt seem to recognize the cd.... Also i cant seem to no-cd patch it without having the lod installed (wrong version, error, etc...)   
 
any help?

---

### Post by Tripwire32 on 2011-06-12
d2 installs fine but get an error when trying to run game. unknown exception (80000101). i'm using wine 1.2 and installed diablo 2 using winetricks. can anyone please help?

---

### Post by UnderPantGn0mes on 2012-10-13
All righty then. i got it perfect running with digital copys (which u dont need cds n makes it UNBELIEVABLY easy to install n run) n even a mod (chaos empire) my only issue is dark clouds and auras having werid shadows n burning souls spitting out grey lol

idk wut the issue is, its a lil creepy actually lol but not hard to deal with. any ideas???

i run full screen, n have sound all threw acts (well that ive been threw havnt realized any other problems other then lil coloring difference)

Ubuntu 10.04
wine 1.4
Diablo 2 + lod + CE(chaos empire)

any help or information need just reply and let me know 
Thx ^_^ ):P

---

### Post by overdrank on 2012-10-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

