---
title: "[SOLVED] WINE:  Counter Strike Portable AKA Counter Strike Decayed Lite"
date: 2008-10-14
forum: Wine
---

### Post by s.fox on 2008-10-14
Hi,

I was wondering if anybody has been able to get this program to work in Wine.  I had a go but it won't go past the second extraction process in the installer.  I did check to see if it is the installer by running it in Windows XP without any problems.

Any thoughts/ suggestions would be great.

-Ash R

---

### Post by asdfoo on 2008-10-14
> **Ash R said:**
> Hi,

I was wondering if anybody has been able to get this program to work in Wine.  I had a go but it won't go past the second extraction process in the installer.  I did check to see if it is the installer by running it in Windows XP without any problems.

Any thoughts/ suggestions would be great.

-Ash R


Which version of Wine did you try? Wine 1.1.6 is the latest development release.

Can you show us the terminal output?

---

### Post by Gcentrex on 2008-10-14
Extract it on a windows system then copy the files over since its a portable version it would be using a steam emulator and reg entries should not even be required to run.

---

### Post by s.fox on 2008-10-14
> **Gcentrex said:**
> Extract it on a windows system then copy the files over since its a portable version it would be using a steam emulator and reg entries should not even be required to run.

I did that but its still not working.  I believe all that needs to be running is hl.exe for the game to work.  Executing the .exe file from terminal gives me this error in a pop up window:

DELTA_Load:  Couldn't load file delta.lst

I checked that this file exists and is in the same location as it would be in windows and it all looks ok.

Thanks for all the help

-Ash R

---

### Post by s.fox on 2008-10-14
Things are getting weird.

I have managed to get the program to run on another ubuntu machine. The only difference is that the machines use differnt versions of wine.

The machine that works has wine 1.0
The machine that doesn't work has wine 1.1.5

After doing a little research I have found that the most recent version is 1.1.6.  Can I roll back the version of wine to 1.0?

-Ash R

---

### Post by Gcentrex on 2008-10-14
No you can't just load hl.exe and have it load most lightly the string used to launch the game from memory would be this

-nosteam -game cs

That's all it should need to run the game in nosteam mode as most unpacked Half-Life engine games are run using that switch.

Also I am able to run Counter Strike on 1.1.5 and also on 1.1.6 using steam and even a steam emulator even condition zero works even thought its listed as not working.

---

### Post by s.fox on 2008-10-14
aha!  i think we are  getting somewhere.  Thank you Gcentrex for all you advice/help.

```
$ wine -nosteam -game cs
wine: could not load L"C:\\windows\\system32\\-nosteam.exe": Module not found
```

Would i be right in thinking that all i have to do is copy this module from the XP computer that has this program installed?

Once again massive thank you.

---

### Post by Gcentrex on 2008-10-15
> **Ash R said:**
> aha!  i think we are  getting somewhere.  Thank you Gcentrex for all you advice/help.

```
$ wine -nosteam -game cs
wine: could not load L"C:\\windows\\system32\\-nosteam.exe": Module not found
```

Would i be right in thinking that all i have to do is copy this module from the XP computer that has this program installed?

Once again massive thank you.

No I did mean like this

```
hl.exe -nosteam -game cs
```

You need to copy the entire folder were it was installed to on the windows xp pc, you will properly have to use a script to change to the correct folder then run that command to launch the game, it should not require the steam id as from memory running in nosteam mode removes that requirement.

I still don't understand why the installer does not work from wine but then again I never have tested the half-life 2 offline installer before but I have tested multiple steam emulators and have gotten them to work.

---

### Post by s.fox on 2008-10-15
I tried ```
hl.exe -nosteam -game cs
```
but got a bash command error,  so i then tried

```
wine hl.exe -nosteam -game cs

```

This gave me the pop up error message 

"DELTA_Load: Couldn't load file delta.lst"

Does anybody have any ideas what i am doing wrong?

Thanks for all the help and support!

-Ash R

P.S everytime i get the delta.lst error my screen resolution does change.  It may or not be important but I thought you guys might like to know

---

### Post by Gcentrex on 2008-10-15
> **Ash R said:**
> I tried ```
hl.exe -nosteam -game cs
```
but got a bash command error,  so i then tried

```
wine hl.exe -nosteam -game cs

```

This gave me the pop up error message 

"DELTA_Load: Couldn't load file delta.lst"

Does anybody have any ideas what i am doing wrong?

Thanks for all the help and support!

-Ash R

P.S everytime i get the delta.lst error my screen resolution does change.  It may or not be important but I thought you guys might like to know

Sounds to me that it is missing that file a .lst in the half-life engine it contains a list of files in a basic explanation. 

Did you change to the folder containing hl.exe and launch it from their or it might have loading errors as it will not be able to find files.

---

### Post by s.fox on 2008-10-15
Dumb question - where is the half-life engine in terms of folder names?

I have a folder called strike and it contains the .lst file

```
[user@localhost cstrike]$ ls
addons                 de_aztec.wad          motd.txt
ajawad.wad             decals.wad            n0th1ng.wad
autobuy.txt            [COLOR="Red"]**delta.lst** [/COLOR]            overviews
BotCampaignProfile.db  de_vegas.wad          rebuy.txt
BotChatter.db          de_vertigo.wad        resource
BotProfile.db          dlls                  SAVE
buffer.dat             events                sbgui
cached.wad             game.ico              server.cfg
classes                GameServerConfig.vdf  settings.scr
cl_dlls                gfx                   sound
commandmenu.txt        halflife-cs.fgd       spectatormenu.txt
config.cfg             itsitaly.wad          spectcammenu.txt
cs_assault.wad         liblist.gam           sprites
cs_bdog.wad            liquids.wad           steam.inf
cs_cbble.wad           listenserver.cfg      tempdecal.wad
cs_dust.wad            logos                 titles.txt
cs_office.wad          manual                tswad.wad
cstrike.ico            mapcycle.txt          user.scr
cstrike.wad            maps                  xeno.wad
custom.hpk             models

```

Am i even in the right folder? 

Thank you for your help and patience with me.

---

### Post by Gcentrex on 2008-10-15
> **Ash R said:**
> Dumb question - where is the half-life engine in terms of folder names?

I have a folder called strike and it contains the .lst file

```
[user@localhost cstrike]$ ls
addons                 de_aztec.wad          motd.txt
ajawad.wad             decals.wad            n0th1ng.wad
autobuy.txt            [COLOR="Red"]**delta.lst** [/COLOR]            overviews
BotCampaignProfile.db  de_vegas.wad          rebuy.txt
BotChatter.db          de_vertigo.wad        resource
BotProfile.db          dlls                  SAVE
buffer.dat             events                sbgui
cached.wad             game.ico              server.cfg
classes                GameServerConfig.vdf  settings.scr
cl_dlls                gfx                   sound
commandmenu.txt        halflife-cs.fgd       spectatormenu.txt
config.cfg             itsitaly.wad          spectcammenu.txt
cs_assault.wad         liblist.gam           sprites
cs_bdog.wad            liquids.wad           steam.inf
cs_cbble.wad           listenserver.cfg      tempdecal.wad
cs_dust.wad            logos                 titles.txt
cs_office.wad          manual                tswad.wad
cstrike.ico            mapcycle.txt          user.scr
cstrike.wad            maps                  xeno.wad
custom.hpk             models

```

Am i even in the right folder? 

Thank you for your help and patience with me.

You inside the cstrike folder game folder (Counter-Strike folder game data folder), their should be a folder before that with a file called hl.exe and some other folders too, that is the exe you need to run from wine so you load it like this  

```
wine hl.exe. -nosteam -game cstrike
```

The one before saying to load -game cs was an error on my part that was me looking at my own old unpacked version for use in collage so I did mod it a lot so it would not show up in a system search.

I looked through my gcf files and noticed my error :popcorn:

Let me know if it loads ok for you after that, also as long as your able to play any native games in OpenGL you should how almost no issues now.

Just make sure to have the gecko engine installed even thought you cant read the server messages yet with it may be in a new version it will work, but without it the game will not work.

---

### Post by s.fox on 2008-10-15
Thank you,  it loaded actually up :)

However- I don't actually know what the gecko engine is or where to get it. Where can i get it?  I know its not installed because when i try to run a game it crashes and i can see something about gecko not installed.  I can see an option to install but the desktop is unresponsive.  

Once again thank you so much for all your help,  it looks like we are winning :)

-Ash R

---

### Post by Gcentrex on 2008-10-15
> **Ash R said:**
> Thank you,  it loaded actually up :)

However- I don't actually know what the gecko engine is or where to get it. Where can i get it?  I know its not installed because when i try to run a game it crashes and i can see something about gecko not installed.  I can see an option to install but the desktop is unresponsive.  

Once again thank you so much for all your help,  it looks like we are winning :)

-Ash R

That's good to know now this is easy compared to another thread I'm posting on :( , as for gecko engine this is what you can do.

Open a terminal then type this into it

```
wget http://www.kegel.com/wine/winetricks
```

After it is downloaded then do this

```
sh winetricks
```

Look in the list and I recommend you install gecko and also install allfonts that will install all windows core fonts plus some commonly used ones too.

Then you should be able to run the game then let me know how you get on with that.

---

### Post by s.fox on 2008-10-15
I can't thank you enough!  Its finally working :)

You have been a great help with this problem

-Ash R

---

### Post by Robbol on 2011-12-01
Okay first I know this is a very old post but I need some help with counter strike lite by decayed

the game runs but when I get to the start up screen I get a box asking for a registration code o_O

any ideas how to get past it ?

---

