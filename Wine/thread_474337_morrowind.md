---
title: "morrowind"
date: 2007-06-15
forum: Wine
---

### Post by k33bz on 2007-06-15
ive looked all over the forums, and i saw loki use to have the installers for it, but no longer carries it on his site. does anyone know where i can get the installer for it?

---

### Post by The Noble on 2007-06-15
You can install and run morrowind in wine; it should be working very well now. I have no clue about the loki installer though.

---

### Post by hikaricore on 2007-06-15
Morrowind @ WINE Application Database: [http://appdb.winehq.org/appview.php?iAppId=1015](http://appdb.winehq.org/appview.php?iAppId=1015)
Community WINE info page: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Thread on ubuntuforums.org about Morrowind: [http://ubuntuforums.org/showthread.php?t=360728&highlight=morrowind](http://ubuntuforums.org/showthread.php?t=360728&highlight=morrowind) (pretty much defunct method, the site it links appears to be down)

---

### Post by cogadh on 2007-06-15
AFAIK, Morrowind can only be run with Wine, but it doesn't work very well (rated bronze on AppDB [http://appdb.winehq.org/appview.php?iAppId=1015](http://appdb.winehq.org/appview.php?iAppId=1015)). You don't need the Loki installer, it should install fine through Wine.

EDIT - Well that's what I get for taking a break while typing, two other people already answer the question. :)

---

### Post by k33bz on 2007-06-15
> **cogadh said:**
> AFAIK, Morrowind can only be run with Wine, but it doesn't work very well (rated bronze on AppDB [http://appdb.winehq.org/appview.php?iAppId=1015](http://appdb.winehq.org/appview.php?iAppId=1015)). You don't need the Loki installer, it should install fine through Wine.

EDIT - Well that's what I get for taking a break while typing, two other people already answer the question. :)

ya i was just reading on that. didnt realize peeps had answered my question yet.  and i have wine installed, but i dont use it since i had problems with it in the past.does mrrowind work ell with virtual box

---

### Post by hikaricore on 2007-06-15
> **k33bz said:**
> does mrrowind work ell with virtual box

No.

Games that use 3D acceleration do not work on virtual machines as they do not have physical access
to video hardware.  There has been some progress in making this happen, but it's a long way off.

Your best bet is WINE.  So if it's important to ya, buckle down and go for it.

---

### Post by lordhebe on 2007-06-15
Morrowind does run quite well with wine with a bit of tweaking. Once you've installed the game, apply a no-cd crack for your version, and copy the video file from your cd to the folder that the cd-crack tells you to. Be sure to disable music by renaming the music folder (you might be able to do it by tweaking the config file I'm not sure)  because while the music will play as of wine 0.9.37, it causes the game to crash very early on. (You may have better luck than me) The game also has trouble going fullscreen, so I recommend activating window mode in the launcher, or using a wine desktop, and zooming in by pressing CTRL ALT +

This made Morrowind work near perfect for me, with the only problem being the mini map being black, and my character portrait being black. I made a appdb report, I gave it gold.

---

### Post by AguilaFenris on 2008-05-18
I was able to install Morrowind without a hitch, but the frame rate is really slow, and it's really not worth playing. Is there a way too configure Wine to remedy this problem? (I don't think it's my machine; 2.4 ghz, 512 ram. standard video card, played fine on XP)

---

### Post by chritianpettet on 2008-05-18
if playing morrowind is really important you could use cedega, i use it and it is worth paying the money for it

games work very well under cedega, i highly recommend it

[http://www.transgaming.com/products/cedega/](http://www.transgaming.com/products/cedega/)

---

### Post by cogadh on 2008-05-19
If you are going to pay extra money just to play games on Linux, check out CrossOver Games ([www.codeweavers.com](www.codeweavers.com)). Unlike Cedega, it actually supports the Wine project fully and has a far better track record when it comes to customer support. Additionally, CX Games is a straightforward single purchase ($40 US), not a subscription-based drain on your wallet like Cedega.

---

### Post by regor210 on 2008-12-01
[http://www.uesp.net/wiki/Morrowind:Linux](http://www.uesp.net/wiki/Morrowind:Linux)

This site may be of some help.

---

### Post by Rymer on 2009-11-10
Hi all!
I have a problem: I'm trying to run Morrowind using Wine-1.1.31 on my Ububntu-9.10, but nothing happens. It've been installed, but now, when I'm clicking "start game" nothing changes, as if i had not clicked it at all. at the same time, uninstalling button works good (lol). I've tried CrossOver Games demo. It gave the same effect. I've tried to config wine for Morr with [this]("http://www.uesp.net/wiki/Morrowind:Linux") manual (without changing ini file), but it did not help me.
What is wrong? :confused::confused::confused:

[SIZE="1"]PS: sorry for my English, it's not my native language.[/SIZE]

---

### Post by beastrace91 on 2009-11-10
Try upgrading to the latest Wine version - 1.1.32 - but as you said it is also not working with CXGames this may not be the issue. What is your graphics card & driver version?

Also can you post the out put from trying to run the Morrowind.exe from console with Wine?

Regards,
~Jeff

---

### Post by Rymer on 2009-11-10
Hm. It says:
> could not load L"C:\\windows\\system32\\Morrowind.exe": Module not found
How can i make WINE load Morr not from sys32, but from c:\\Program Files\\Bethesda Softworks\\Morrowind (where this file is located)?

---

### Post by beastrace91 on 2009-11-10
Try running this in terminal: ```
cd ~/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Morrowind && wine Morrowind.exe
```

~Jeff

---

### Post by Rymer on 2009-11-10
> err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Morrowind\\Morrowind.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Morrowind\\Morrowind.exe" failed, status c0000135

:(

---

### Post by Progressive on 2009-11-10
EDIT: Nevermind

---

### Post by Progressive on 2009-11-10
Actually, you need to place MSCVP60.dll in your system32 folder.

You can find it on your windows partition or if you don't have one I can't help you... but Google might be able to help ;)

---

### Post by Rymer on 2009-11-11
Thanks! It  works! 
The only trouble now is that the game is full of lags. (And i don't think my notebook is too weak for Morrowind as i was playing Assassin's Creed, Prince of Persia and so on under Vista without any problems.) While starting, there are a lot messages _*"failed allocate memory"*_ and such ones: > fixme:quartz:TransformFilter_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!


---

### Post by beastrace91 on 2009-11-11
What are your system specs? Also have you seen [this](http://bugs.winehq.org/show_bug.cgi?id=14186)?

~Jeff

---

### Post by Progressive on 2009-11-11
It could also be an issue with the game itself.

Try these mods and patches in the following order... most of these install to your Morrowind folder or Morrowind Data Files folder, and it should be pretty clear which ones go where (and it should tell you).

(Most of this information can be found, albeit in windows-specific form, here: [http://morrowind2009.wordpress.com/](http://morrowind2009.wordpress.com/) )


1) The official patch:
[http://static.bethsoft.com/downloads/patches/Morrowind_v1.2.0722.exe](http://static.bethsoft.com/downloads/patches/Morrowind_v1.2.0722.exe)

2) [http://planetelderscrolls.gamespy.com/View.php?view=Mods.Detail&id=7347](http://planetelderscrolls.gamespy.com/View.php?view=Mods.Detail&id=7347)

3) [http://www.tesnexus.com/downloads/file.php?id=19510](http://www.tesnexus.com/downloads/file.php?id=19510)

4) At this point you should run the Morrowind Launcher, click Data Files, and make sure all the mods are checked.

5) [http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=34](http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=34) After installing, press the "Just Fix It!" button

6) [http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=22](http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=22) This will allow you to set extra settings to prevent drops in FPS and generally tweak the game, and this will become your new launcher program instead of Morrowind Launcher.

(by the way, I recommend using lots of Texture Packs and other mods to improve the visual quality of Morrowind, and many are listed in that first link to the Morrowind2009 blog.

---

### Post by Rymer on 2009-11-12
beastrace91, **_THANKS a lot!_** It works for me!

---

### Post by braithwa on 2009-11-22
The "Tamriel Rebuilt" project renewed my interest in Morrowind.  Tamriel Rebuilt is a massive community contributed extension of Morrowind, not on Vardenfaal, but on the Morrowind mainland across the sea.  The project is well underway and so huge that it dwarfs the original work.

I followed advice on this forum and others to install Morrowind on Linux.  I made 4 or 5 attempts at Morrowind installation.  

My two attempts on hardy heron did not succeed, ie. I did not get to play the actual game, it just crashed before getting there.  These were done using wine and Play on Linux. 

My second two were on Karmic Koala.  These ran, but the game was jerky and slow to the point where I would not have enjoyed playing it.  It was essentially unplayable for me.   None of the tweaks would work.  

But I persisted.  My successful attempt was using Cedega.  I finally payed my fee and used their software engine 7.3.3.  I have to say, that following the instructions the whole thing just worked pretty well.  I have only played the introduction and walked around Sayda Neen, but it is looking good.

---

### Post by beastrace91 on 2009-11-22
I'm glad you got it working but just so you know odds are you could have gotten it working under Wine with a few tweaks ;)

At any rate would you care to link me to that 3rd party mod you mentioned? It sounds like good fun :D

~Jeff

---

