---
title: "HOWTO: Get Grim Fandango Working with Wine"
date: 2008-02-07
forum: Wine
---

### Post by Kimm on 2008-02-07
This is a game I had trubble getting to work. It will function somewhat good without these steps, but it might cause wine to crash (something that never happened to med after I did this).

I could not find any good tutorial for this on the forum (or on the net), so I decided to compile one myself :)

[SIZE="5"]**Step 1: Getting Wine**[/SIZE]
For this you need the official build of Wine (not the ubuntu build), in case you haven't already added this repository, this is how you do it:

Open up a terminal and type these commands (for gutsy, if you use a different version of ubuntu, follow the instructions here: [URL="http://www.winehq.org/site/download-deb"]Wine Download
[/URL]):

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```

This build **works on both x86 and amd64!**

[SIZE="5"]**Step 2: Configuring Wine**[/SIZE]
Grim Fandango will not run in full screen (or windowed, as is made possible by the launcher you will get later), but rather, you need to configure wine to emulate a virtual desktop, and run the game in full screen inside that (which will work best).

Type in your terminal:

```

winecfg
```

Click on the "Graphics" Tab and check "Emulate a virtual desktop", now you need to define the size for this desktop. I prefer 1024x768 since I think it gives me enough room to actually do something, but that is up to you (and the game will scale it anyway).

Now, click "Apply" and close the configuration window

[SIZE="5"]**Step 3: Installing Grim Fandango**[/SIZE]
Now, simply pop the Grim Fandango CD1 into your drive and launch the installation program. Install the game to wherever you like.
Do not install the patch yet! (released by LucasArts to fix some bugs and add Windows XP compability), that comes later!


[SIZE="5"]**Step 4: Getting a Custom Launcher**[/SIZE]
Download and unzip [URL="http://www.grimfandango.net/files/launcher/GrimLauncher1.2.zip"]**this file**
[/URL]

Create the folder .grimfandango in your home directory ("mkdir .grimfandango" in your console), and move "Grim Launcher.exe" to this directory.

[SIZE="5"]**Step 5: Setting It Up As a Menu Item**[/SIZE]

Download **[this icon]("http://www.good-tutorials.com/images/icons/15895.jpg")** to the .grimfandango directory.

Now, type in terminal:

(if you are using Kubuntu, replace gedit with kwrite, if you are using Xubuntu replace it with mousepad)

```

sudo gedit /usr/bin/grimfandango

```

Now, copy paste this into the file (make sure to replace: **<yourusername>** with your username)

```

#!/bin/bash

cd /home/**<yourusername>**/.grimfandango/
wine Grim\ Launcher.exe

```

Save and close.
Now, type in terminal:

```
sudo chmod +x /usr/bin/grimfandango
```

Now, type this in your terminal:

```

sudo gedit /usr/share/applications/grimfandango.desktop

```

And copy & paste this into the newly opened file (Again: make sure to replace: **<yourusername>** with your username):

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Grim Fandango
Comment=Classic adventure game
Exec=grimfandango
Icon=/home/**<yourusername>**/.grimfandango/15895.jpg
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;Game;Adventure;

```

Save and close.
You should now be able to find "Grim Fandango" in your games menu.

[SIZE="5"]**Step 6: Starting the Launcher for The First Time**[/SIZE]
There are still some things to be done for the game to run well. Start the launcher from the menu (notice the emulated desktop around the launcher window).
The Launcher should comment on that you have not installed the patch for the game, and if you would like to do so now. Let it install the  patch (this is the only way I got the path installation program to work). Follow the instructions for the installer.

When the patch is installed, click "Options" and then "Run Grim From Hard Drive"
The Launcher will ask you to place CD1 in the drive, do that and let it continue. It may seem to freeze, but it is simply working. After a while it will ask for CD2, pop it in the drive and continue.

The game may crash if you use the CDs while playing.

[SIZE="5"]**Step 7: Starting the Game**[/SIZE]

The Game is now ready for play. Make sure to always start it with the "Play Fullscreen" button.


[SIZE="5"]**Known Problems**[/SIZE]
The game will run fine, but with some flaws.
Your character will leave black tracks where he moves (this isn't to bad though, it will not obstruct the game).

Also, the sound may become funky at times, the only workaround for this that I can find, is to save the game, and restart (the sound should be fine again). This does not happen very often, so it shouldn't be a big problem.

You may sometime find that all keys don't work, just click the game window and it should start working again.


[SIZE="5"]**Enjoy the game!!**[/SIZE]
:popcorn:

---

### Post by mael on 2008-08-24
thanks! :)

---

### Post by nickgaydos on 2008-08-24
Good guide and fun game :-)

---

### Post by mhedges48 on 2008-08-27
very good guide, thank you. The game works but only in a small window... any ideas on how to get it full screen? I setup winecfg as stated in the guide but doesn't seem to have an effect, always goes to a 800x600 window....


thanks!

---

### Post by mhedges48 on 2008-08-29
I used an ugly fix and just lowered my screen resolution so the game took up more of the screen... not clean but works

---

### Post by Kevbert on 2008-08-30
Excellent post, thanks Kimm. I'll now try and get some more windows games going with wine.

---

### Post by Siekomonki on 2009-01-09
So let me preface this with the statement that I'm a total Linux newb.  I started playing with Ubuntu 8.10 about three days ago, and I'm starting to earn the ropes.  The other day I decided to try and use Wine to get Grim Fandango to run (on my own, mind you, it never even occured to me that someone else would want to as well >.<).  It was a spot of fun, since I have an Eee PC (no cdrom), but I eventually got it working.  Almost.  Upon game load, it pops up with an error: "Grim Fandango could not initialize your hardware.  Please make sure your not running any DirectX apps that take exclusive control of your hardware."

After I found this tutorial I tried following it to the letter, and still get the same error. My theory is simply that my hardware isn't quite up to spec, but if so that would be lame, since it passed all the render tests that the game's Troubleshooter offers.  Any thoughts?

---

### Post by steve04 on 2009-01-24
Thank you for the tutorial!  I got the game set up and running but unfortunately it is in a small window.  I followed every step in the tutorial too, any clue how to fix this?

---

### Post by Weevil on 2009-02-03
Just a side note; anyone having problems installing the patch should probably read this:

[http://bugs.winehq.org/show_bug.cgi?id=5224](http://bugs.winehq.org/show_bug.cgi?id=5224)

---

### Post by Porrhandske on 2009-11-03
thank you very much:D, now I have something to do for the weekend

---

### Post by zazolo on 2009-11-19
I tryed installing grim fandango on my samsung nc10 running ubuntu 9.10
 
I configured everything like the guide says, but after the installation process, after copied every file from cd1-cd2 into the hard drive in order to run without cd.... how can I play?
 
I launched Grim Fandango from the menu games, and shows up a window called "Default - Wine desktop", where it is the Grim Fandango Launcher inside
 
If I click on Play Fullscreen, nothing appens, the same if I click on Play windowed
 
how can I start the game?
 
PS I haven's installed the patch, it is something I have to do?

---

### Post by Kimm on 2009-11-21
> **zazolo said:**
> 
PS I haven's installed the patch, it is something I have to do?

Yes, you have to install the patch (as I noted in the original post ;) ), you can do that from the Grim Fandango launcher.

---

### Post by Mark76 on 2009-11-21
Last time I played one of my LucasArts games it worked perfectly well with scummvm.

Has that been removed from the repos?

---

### Post by zazolo on 2009-11-22
Nothing

still doesn't work

I also reinstalled everything from the beginning, but still when I click on the Play Fullscreen button, after a while it shows a popup with "no disk is inserted"

Is that anyone which has installed properly grim fandango on an nc10?

---

### Post by Mark76 on 2009-11-22
Just tried it again and for some reason it didn't work at all.

I'm sure I used scummvm to play it last time

---

### Post by Digital Magi on 2009-11-27
I got it installed, then patched and copied the required files to play from the HD using the Grim Launcher 1.5 utility.

I'm having some odd graphical glitches if I try to run in fullscreen mode, hoping somebody can help. In fullscreen mode, the intro, menu and cutscenes all display beautifully. However, when it switches to gameplay the background images are all inverted... it looks like Manny is walking on the ceiling. Controls all work, and sound is fine. The other interactive characters are the same way as Manny - they display properly but their background is upside down. 

If I hit F1 to bring up the ingame menu the menu overlay is upright and works normally (but in the game Manny is upside down while the background scene is upright - the opposite of while playing - weird).

I attached a couple of screenshots.

In windowed mode the game runs normally but the window is quite small no matter what size I set the emulated desktop as so I am hoping to get fullscreen working.

Running 9.10 with wine version 1.1.33 using an Intel 845GM mobile chipset (laptop)

Edit: I tried to play again on a desktop machine running an nvidia card, no problems. So I'm thinking it is a problem with the intel drivers. Any thoughts ?

---

### Post by angelcleff on 2011-02-04
Thanks a lot broo!!!! :p 
it works just perfect and without those black marks that you mentioned 
again thank you so much [-o<

---

### Post by Chelidze on 2011-07-08
[SIZE="5"]**Step 5: Setting It Up As a Menu Item**[/SIZE]

Download **[this icon]("http://www.good-tutorials.com/images/icons/15895.jpg")** to the .grimfandango directory.

Now, type in terminal:

(if you are using Kubuntu, replace gedit with kwrite, if you are using Xubuntu replace it with mousepad)

```

sudo gedit /usr/bin/grimfandango

```

Now, copy paste this into the file (make sure to replace: **<yourusername>** with your username)

```

#!/bin/bash

cd /home/**<yourusername>**/.grimfandango/
wine Grim\ Launcher.exe

```

Save and close.
Now, type in terminal:

```
sudo chmod +x /usr/bin/grimfandango
```

Now, type this in your terminal:

```

sudo gedit /usr/share/applications/grimfandango.desktop

```

And copy & paste this into the newly opened file (Again: make sure to replace: **<yourusername>** with your username):

```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Grim Fandango
Comment=Classic adventure game
Exec=grimfandango
Icon=/home/**<yourusername>**/.grimfandango/15895.jpg
Terminal=false
X-MultipleArgs=false
Type=Application
Categories=Application;Game;Adventure;

```

Save and close.
You should now be able to find "Grim Fandango" in your games menu.

 Great tutorial easy to follow even for me but this file is deleted is there a way to reupload it ????

---

### Post by Kudagra on 2011-12-19
Its only 6 months later.

It doesnt matter what the .jpg picture is of. I just googled Grim Fandango and saved an icon sized picture to my .grimfandango file and renamed it 15895.jpg


One problem Im getting is once I shut down my computer I lose GF in my Games. Not a problem because I dont have much on here ( I dont like clutter)so its easy to find. Also I suspect its just resized for by the program but I just have a small window even when opening it with Full Screen.

Also when I use the F1 my save screens are inverted and backwards. Not a problem..just annoying.

On a side note...I cant imagine how I solved this more then 10 years ago without the internet walkthroughs/

---

### Post by Neo@NHNG on 2012-02-16
For me letting the Launcher install the patch did not work (Ubuntu 11.10, Wine 1.2.3). It downloaded just fine but when the patch process should have been started it gave an error ("Unhandled page fault on read access").

This command, I got from [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=553") did work however:
```

cd ~/.wine/dosdevices/c:/Programme/LucasArts/Grim
wine start /unix gfupd101.exe

```

Have fun.

---

### Post by madscientist on 2012-09-24
Found my son watching a youtube video of Grim Fandango yesterday and surprised him by plunging into my archives and bringing out the original CDs: loved that game.

After struggling with this to get it running for a while yesterday with Wine, I found ResidualVM: [http://residualvm.org/](http://residualvm.org/)

This is a native, open source rewrite of the underlying game engine for Grim Fandango that runs on Linux, Windows (newer versions), and Mac in both 32bit and 64bit.  You just copy the data files (don't need any .exe's etc.) from the CD's to your system, then run the ResidualVM program instead of the Windows programs.

I played well into Year 2 and it worked perfectly for me: all music, dialog, sound effects, video (with 3d enabled), save/restore.  Not one single glitch, restart, or futzing around.  It will manage the 1.01 patch, too, just drop it into the same directory as your data files.

:guitar:

---

### Post by marbertone on 2013-04-17
Hello,
I apologise if the question has already been answered.
I did installation then I patched it.
Nevertheless I try to run and it says "no disc inserted".
What should I do?
Thanks,
MA

---

### Post by madscientist on 2013-04-17
Don't bother with the patch.  Just use residualvm as in my post directly above yours.  It doesn't use any of the EXE from GF, only the data files, so no bugs in the EXE need to be patched.  I played halfway through Year 3 without a hitch, before I got sidetracked.  Need to get back to that!!

---

### Post by marbertone on 2013-04-18
Thank you very much, madscientist!
Works like a charm!
:popcorn:

---

### Post by marbertone on 2013-04-19
Just another question, please.
Fullscreen doesn't work at all.
Were you able to make it work?
Thanks.

---

### Post by marbertone on 2013-04-29
I have solved it!

You must edit .residualvmrc and go to [Grim Fandango] section, in which you have to put "fullscreen=true" (default is "false").

Thank you guys for having let me discovered Residualvm.

MA

---

