---
title: "How to: Starcraft on Ubuntu with Wine"
date: 2008-06-21
forum: Wine
---

### Post by Crovaax on 2008-06-21
So I'm new to Ubuntu and I had a little trouble getting Starcraft setup when I switched over.  
I thought I would post in the off chance that I save someone else time.

First install Wine, a common windows emulation program.
Install directions can be found [**_here_**]("http://www.winehq.org/site/download-deb")

Then in a terminal (Applications->Accessories->Terminal) type:
> winecfg
Go to the Graphics tab. I have the following two options checked.
'Allow DirectX apps to stop the mouse leaving their window' &
'Allow Pixel Shader'

I'm not sure if this is necessary but I also went to the Graphics tab and clicked autodetect 
and to the Audio tab and let it pick default audio drivers for me.

Insert Starcraft CD

(icon should appear on desktop, right click on it and go to Properties and then the Volume tab.  
If your Mount Point is not "/media/cdrom0" replace "/media/cdrom0" in the following commands with your mount point)

Open a *new* terminal and then type:

> cd ../../media/cdrom0
> wine install.exe

Insert BroodWar CD and repeat StarCraft CD directions

Go **_[here]("http://us.blizzard.com/support/article.xml?articleId=21149&rhtml=true")_** and download latest starcraft patch to your desktop

Then open *new* terminal and then type:
> cd Desktop
> wine BW-1152.exe

*Note if the patch you dled is a later patch it will have a different name, use that name instead of BW-1152.exe

Now with your BroodWar cd still in the cd-rom type the following commands in a *new* terminal (if you only have original starcraft use that cd):
> cp ../../media/cdrom0/install.exe Desktop/BroodWar.mpq
> chmod 777 Desktop/BroodWar.mpq
> cp Desktop/BroodWar.mpq .wine/drive_c/"Program Files"/Starcraft/BroodWar.mpq
The above commands will allow you to play starcraft without a cd

Now to play the game open a terminal and type:
> wine .wine/drive_c/"Program Files"/Starcraft/StarCraft.exe

A couple of notes for you:
1) When you go to battle.net your screen will be black, but just move the mouse around and you will find that it's just a rendering problem, in game play will be fine though.  The menus will be messed up too, but it's still workable.  Like I said, in game no issues.

2) You won't be able to connect to battle net unless you go to System->Preferences->Appearence visual effects tab and select none
Else you will get a warning that your version of starcraft is out of date

---

### Post by Dark Coz on 2008-06-21
This is the wrong forum here.  I know any Wine-related forums go here.

[http://ubuntuforums.org/forumdisplay.php?f=313]("http://ubuntuforums.org/forumdisplay.php?f=313")

---

