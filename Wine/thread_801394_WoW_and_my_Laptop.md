---
title: "WoW and my Laptop"
date: 2008-05-20
forum: Wine
---

### Post by OZFive on 2008-05-20
I am not a gamer really.

My Nephew is.

He REALLY REALLY wants me to play WoW with him sometimes online and I agreed. So I installed WoW as per instructions and got the game to load and I got video and menus, but no sound. Then I remembered I still had to do some more to the installation about OpenGl and the regedit. So I did that. Now I run it and I get sound but no video. Black screen :S

What can I do....

System : Hardy 8.04
Laptop : Sony Vaio VGN-N325E
Processor : Pentium Dual Core 1.73
RAM : 1 Gb
Processor : Intel® Graphics Media Accelerator 950
Video RAM : 224MB12 Total Available Graphics Memory
Chipset : Intel® 943GML


He is a Level 57 Druid something or other, I am sure he just wants me on there to kick my butt somehow, as he cannot do it in real life

---

### Post by CubicleInmate on 2008-05-20
OZFive:

I actually just finished dealing with this same issue myself.  My wife and I have been playing WoW together for years, and it was the only reason I have suffered a Windows installation to exist on my machine.

The short version of the steps I took:
Copied a fully patched installation of WoW from my wife's computer to my own.  (For me, into ~/wow/)
Disable all of the additional effects in the Settings / Preferences / Appearance panel.
Disable Beryl / Compiz if either are in use.

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
 wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine
```
Run Wine from the menu once to create a default configuration file, or type "winecfg" in the terminal to accomplish the same thing.

Apply the [Registry fix]("https://help.ubuntu.com/community/WorldofWarcraft#head-4b2ddfc20b64caffa3c5fbfad67a0480440ccad2").

Follow the directions [here]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b") to install some additional DLL files.

Run WoW once using:
```
wine <WoW Directory>Wow.exe -d3d &
```

This will create the default configuration for WoW.

Make sure these lines exist in newly created <WoW Directory>/WTF/Config.wtf
Add them if they do not exist.
```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET UIFaster "2"
SET M2UseShaders "0" 
```

Install [this mod]("http://files.wowace.com/ApplyToForehead/no-ext/") to enable you to change video settings from within the game under OpenGL.

Using the links below I was able to get WoW running under 8.04 at a level acceptable enough to raid with.  Hope they help you out.  Some of them are specific to ATI video cards, which is what I unfortunately have - but there may be some useful information there if you encounter problems.

[http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine")
^^ This is by far the most complete resource.

[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting")
[http://www.wowwiki.com/Linux]("http://www.wowwiki.com/Linux")
[http://www.wowwiki.com/Linux/Wine]("http://www.wowwiki.com/Linux/Wine")

[http://ubuntuforums.org/showthread.php?t=770939]("http://ubuntuforums.org/showthread.php?t=770939")
[http://ubuntuforums.org/showpost.php?p=2119432&postcount=123]("http://ubuntuforums.org/showpost.php?p=2119432&postcount=123")
[http://ubuntuforums.org/showpost.php?p=2148980&postcount=157]("http://ubuntuforums.org/showpost.php?p=2148980&postcount=157")
[http://ubuntuforums.org/showpost.php?p=2183925&postcount=185]("http://ubuntuforums.org/showpost.php?p=2183925&postcount=185")

Mouse side-buttons in WoW: [click here]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-0753324f056db5202af629578d53c9e433da0b66")

Slow Mouse issues: [http://ubuntuforums.org/showthread.php?t=340193]("http://ubuntuforums.org/showthread.php?t=340193")

---

### Post by twist2b on 2008-05-20
wow thats really good news. I always used XP through Virtual Box. this is really interesting.

---

### Post by konungursvia on 2008-05-20
Yes, me too, WoW and Kyodai Mahjong, as well as WordPerfect 12 and Adobe Acrobat Pro, are the *only* 4 little reasons I still have Windows xp. I couldn't get all of them running in wine 0.59, so I'll keep xp for now.

---

### Post by Sammi on 2008-05-21
You might want to try both d3d and opengl in config.wtf, because you have an Intel graphics card. Sometimes they won't work in opengl.

---

### Post by OZFive on 2008-05-21
Well I got it to work.

The graphics are pretty bad, I had to turn down all the settings to thier bare minimum to get it to work and of course it is still a bit slow in responses.  BUT it works (I did not expect much performance form a laptop with my specs).  Thanks all for the help, and if there are further tricks and tips to get it to work better, please let me know.

---

### Post by CubicleInmate on 2008-05-21
Good to hear you are up and running OZ5.  As Sammi mentioned, with an intel card you may want to try running in d3d instead of opengl.  It is possible that you could see better performance that way.  From what I have read opengl appears to be the backup plan for most people, unless you have an ATI card - then it becomes the only plan in most cases.

The available video memory on your card is pretty low, but if it works that's a great starting point!  There may not be a lot more you can do with it if you have already reduced all video settings to the minimum.

For comparison:
I'm sitting on a dual core 3.2ghz processor with 2gb of ram and a 512mb video card - and last night running Firefox and WoW in a 1440x900 window I was using 80% of one core, 20% of the other, and 1gb of ram.  I have reduced my visible terrain distance to the mid-range and turned multisampling down to 4x from 6x.  Everything else was left at full.

This resulted in performance to match what I had in WinXP in a raid setting, giving me a range of 25-33 FPS in Hyjal Summit last night.  Approximately the same framerates while standing around Shattrath also.

---

### Post by OZFive on 2008-05-22
> **Sammi said:**
> You might want to try both d3d and opengl in config.wtf, because you have an Intel graphics card. Sometimes they won't work in opengl.

How do I try this out in d3d?

---

### Post by CubicleInmate on 2008-05-22
You can remove the line:

SET gxApi "opengl"

from your config.wtf file and it will default to d3d (unless you have also specified opengl in your launcher, or on the CLI.  Alternatively, just try it out from a terminal with:
```
wine <WoW Directory>/Wow.exe -d3d &
```

---

### Post by OZFive on 2008-05-22
So I tried the open from terminal with this...

wine /home/matthew/.wine/drive_c/Program Files/World of Warcraft/Wow.exe -d3d &

and got this...

> matthew@matthew-laptop:~$ wine /home/matthew/.wine/drive_c/Program Files/World of Warcraft/Wow.exe -d3d &
[1] 7764
matthew@matthew-laptop:~$ wine: cannot find '/home/matthew/.wine/drive_c/Program'


What am I doing wrong here?

---

### Post by Faud on 2008-05-22
Just delete the line -opengl in your config.wtf folder. It will do the same thing.

---

### Post by Sammi on 2008-05-22
> **OZFive said:**
> wine /home/matthew/.wine/drive_c/Program Files/World of Warcraft/Wow.exe

What am I doing wrong here?
The problem is the empty space between "Program" and "Files". "World of Warcraft" will also be a problem. The terminal stops reading a path when it reaches an empty space. Just put " signs around the parth and the terminal will know to read the paths as a whole. Like this:

```
 wine "/home/matthew/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"
```But you shouldn't do it like this anyway. Use this instead:

```
wine "C:\Program Files\World of Warcraft\WoW.exe"
```This way Wine sets the working directory right.

Putting -d3d at the end should be redundant if there's nothing else specified in config.wtf, because WoW defaults to DirectX (which the -d3d tag specifies).

Anyway I like putting the line into config.wtf over using the tag, as it's a one time fix, that you don't have to keep doing every time you start WoW.

Use either:
SET gxApi "opengl"
SET gxApi "d3d" (or nothing as WoW defaults to DirectX)

---

