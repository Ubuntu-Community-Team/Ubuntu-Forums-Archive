---
title: "idea"
date: 2008-02-13
forum: Wine
---

### Post by Choad on 2008-02-13
had this thought a while back

what would be super slick, is if when you click on an exe file it queries an online database of known apps and tells you how well it is likely to run, and also tells you about any work arounds for issues that can be solved.

i've been happily playing poker with the windows version of full tilt poker under wine and it's flawless (minus some embedded html stuff that fails when i try and install gecko) and i expect in fact the *vast* majority of apps will run fine under wine... it'd just be good to have a system in place to let us know straight up how well it'll work.

would save a lot of people a lot of hassle.

thoughts?

also, clicking an exe for the first time should prompt you to install wine, and you shouldnt have to right click-> open with. *also* for some reason running an exe from the command line as "wine bla.exe" works when right click->open with->wine fails. colour me confused.

---

### Post by Ferrat on 2008-02-13
could work but a core system based version would be very unsafe and resource grabbing since it would check every exe every time and so on. 

but creating a wine integration only for that purpose should work, you could rate different .exe / programs / apps and just tie it to a very simple database with the parameters
- App name
- App version
- WINE version
- Any patches
- patch name if possible (if one was used)
- rating
- small comment 

and the program could return upon search 
- The results ppl has had with your verions of the app and wine
- The best results ppl has had with that version of the app
- The best resluts ppl has had with that version of wine
- The best results regardless of versions
and if anyone used patches ect 

and last 5 comments on the one of the results you click on

Only draw back is that you would need an active server 24/7 with a SQL or likewise but data flow should be minimal, then you would have to write a integration that can preferably register when wine installs something and if it was a true integration of wine then maybe just maybe the wine devs would like to have a look at it for the appdb :) 

would be useful in lowering bandwidth usage for them I think and giving ppl a more up to date check since some apps never get registered with wine appdb or hasn't been updated in a long while even tho there are ppl that are activly trying to get them to work and some make them work and just doesn't tell anyone and ppl are asking over and over again on forums like these if anyone has gotten it to work.

---

### Post by Choad on 2008-02-14
well i'm sure that canonical would host it if they thought it was a good idea and would make ubuntu the best.

it could be community maintained as well, in the spirit of ubuntu. the details you described would work well, and maybe it could even use the same login credentials as ubuntuforums (for submitting info regarding an exe). that way you could even have it so that people with the highest number of "thanks" (ie, people who are likely to know what they're talking about) get their ratings and comments more highly regarded.. or something... as well as a way of meta-moderating the comments so anyone can rate up a useful comment.... i'm sure in no time at all it would become an extremely useful feature.

i don't know what a "core based system is" but the way i envisage it it would not be resource intensive. it would just be a single sql query to a remote server per click on an exe.

---

### Post by Ferrat on 2008-02-14
well with corebased I meant a ubuntu function that checked every exe that you used, a bit diffused way of putting it I know :) 

yeah but if your system checks every exe when you click them you got something taking resources everytime ect but if you instead have a more manual approach with like a system just picking up the app names ect that wine installs then needs an active query before it starts doing things.

---

### Post by Choad on 2008-02-14
i'm still not following you. what resources is it taking? 

for example you have some program called "wineloader" or something that is the prefered app for exe files

wineloader comes up, using whatever minimal resources it needs to create a gtk dialog and connect to an online database. it queries the database with the details of your system and the app you're trying to run, tells you what you need to know and has a nice "launch" button that kills the wineloader process and executes the actual exe. the wineloader process is now gone... no overhead... only a slight inconvenience to people who wanted the exe to run instantly.... but that can be gotten around with a checkbox that says "do not show this dialog next time i run My_Random_Program.exe" 


we could even have it so patches and fixes can be automatically applied using "wineloader"

---

### Post by Ferrat on 2008-02-14
I'm a litlle of a minimalist when it comes to that I guess, just don't like things running in the background when you just as well could make them just a app that you use no more than you need to when you need it and so on :)

---

### Post by Crinos512 on 2008-02-14
How about a little standalone app you could run in a terminal:

```

> **winecheck Oblivion.exe**
Currently Installed Wine version 0.9.55

Name		The Elder Scrolls IV: Oblivion
Version	1.2.x
License 	Retail 
URL		http://www.elderscrolls.com/home/home.htm
Votes 		19 
Rating		Gold
Wine Version	0.9.52.

What works: Game Runs, no visual problems with spells 
What does not: Much slower than native 
What was not tested: entire game 
Additional Comments: nVidia 6600GT, latest drivers

HOWTO
To start the game you MUST delete or rename the Video folder in the Data directory else the game will fail to start (from 0.9.45 Videos work).
 Alternatively you can enter the Video directory and remove some specific files that could cause a crash. my Video folder currently contains these files: 'bethesda softworks HD720p.bik', ' Map loop.bik', 'OblivionOutro.bik' ,'CreditsMenu.bik' and 'Oblivion iv logo.bik'; and works fine with an unaltered main menu screen. 
Currently it's needed to enter at least two registry entries into Wine manually prior running the game. Enable GLSL and set VideoMemorysize to the memory size Your video card has. Optional key is OffscreenRenderingMode, where value 'fbo' is recommended and value 'pbuffer' has best results. See the example .reg file below:

REGEDIT4 
[HKEY_CURRENT_USER\Software\Wine\Direct3D] 
"OffscreenRenderingMode"="fbo" 
"UseGLSL"="enabled" 
"VideoMemorySize"="256"

Shall You rather use pbuffer instead of fbo, You'll have to switch off refraction shader in game's Oblivion.ini file: bUseRefractionShader=0 to get rid of bug 8184.
 As of Wine 0.9.51, and possibly earlier, it is no longer needed to create the UseGLSL entry. Also, pbuffer is only recommended if you are using 0.9.38. In all later versions up to the current 0.9.51, pbuffer can cause frequent crashes.
If you are having problems, or would like more info on running The Elder Scrolls IV: Oblivion more smoothly, please see the Oblivion Linux Wiki.

```

(*pulled from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506))

Which you could set as a shortcut in Nautilus's right click menu so that it opened a terminal window and displayed the results.

---

### Post by Ferrat on 2008-02-14
yeah that was something alone the thoughts I had :)

---

### Post by Choad on 2008-02-15
> **Crinos512 said:**
> How about a little standalone app you could run in a terminal:

```

> **winecheck Oblivion.exe**
Currently Installed Wine version 0.9.55

Name		The Elder Scrolls IV: Oblivion
Version	1.2.x
License 	Retail 
URL		http://www.elderscrolls.com/home/home.htm
Votes 		19 
Rating		Gold
Wine Version	0.9.52.

What works: Game Runs, no visual problems with spells 
What does not: Much slower than native 
What was not tested: entire game 
Additional Comments: nVidia 6600GT, latest drivers

HOWTO
To start the game you MUST delete or rename the Video folder in the Data directory else the game will fail to start (from 0.9.45 Videos work).
 Alternatively you can enter the Video directory and remove some specific files that could cause a crash. my Video folder currently contains these files: 'bethesda softworks HD720p.bik', ' Map loop.bik', 'OblivionOutro.bik' ,'CreditsMenu.bik' and 'Oblivion iv logo.bik'; and works fine with an unaltered main menu screen. 
Currently it's needed to enter at least two registry entries into Wine manually prior running the game. Enable GLSL and set VideoMemorysize to the memory size Your video card has. Optional key is OffscreenRenderingMode, where value 'fbo' is recommended and value 'pbuffer' has best results. See the example .reg file below:

REGEDIT4 
[HKEY_CURRENT_USER\Software\Wine\Direct3D] 
"OffscreenRenderingMode"="fbo" 
"UseGLSL"="enabled" 
"VideoMemorySize"="256"

Shall You rather use pbuffer instead of fbo, You'll have to switch off refraction shader in game's Oblivion.ini file: bUseRefractionShader=0 to get rid of bug 8184.
 As of Wine 0.9.51, and possibly earlier, it is no longer needed to create the UseGLSL entry. Also, pbuffer is only recommended if you are using 0.9.38. In all later versions up to the current 0.9.51, pbuffer can cause frequent crashes.
If you are having problems, or would like more info on running The Elder Scrolls IV: Oblivion more smoothly, please see the Oblivion Linux Wiki.

```

(*pulled from [http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506))

Which you could set as a shortcut in Nautilus's right click menu so that it opened a terminal window and displayed the results.
ok so that is exactly what i had in mind, except your version runs in a terminal and you have to right click to get to it

terminal is just no. i don't mind it, but it scares a lot of people. you must be really REALLY anal if you can't spare the resources to present that information in a simple gtk dialog 

as for the right click thing.... why bother? what's wrong with setting it as the default app for exe's? this point is not so important, a right click -> check compatability would suffice

aside from the semantics, are we in agreeance that this would in fact be a good idea?

edit: actually... this is not beyond my abilities.... i may have a go at making it :D

---

### Post by aoanla on 2008-02-15
> **Choad said:**
> had this thought a while back

what would be super slick, is if when you click on an exe file it queries an online database of known apps and tells you how well it is likely to run, and also tells you about any work arounds for issues that can be solved.

Not to rain on your parade, because I can see why people might like this... but how is this significantly different to someone visiting the Wine AppDB to check on the status of an application? It's not like it's hard to bookmark it and then search for a given app...
Essentially what you're asking for is to complicate AppDB by including a client-side mapping between application executable names and application entries in the AppDB. 
Frankly, wouldn't it be easier just to add something to the Wine install that prompts you to go to AppDB to check on the compatibility of programs?

---

### Post by Choad on 2008-02-15
> **aoanla said:**
> Not to rain on your parade, because I can see why people might like this... but how is this significantly different to someone visiting the Wine AppDB to check on the status of an application? It's not like it's hard to bookmark it and then search for a given app...
Essentially what you're asking for is to complicate AppDB by including a client-side mapping between application executable names and application entries in the AppDB. 
Frankly, wouldn't it be easier just to add something to the Wine install that prompts you to go to AppDB to check on the compatibility of programs?
yeah... i know about this and you know about this but my dad, for example, doesn't have a clue.

advantages of this over say showing a popup saying "check appdb for info" would be integration and ease of use. it's also a lot nicer... i mean... computers are supposed to do the grunt work for us, right? not tell us to go off searching a random website we've never heard of and then not understand anything we read anyway. a lot of people really are truly clueless. my dad for sure would struggle to search appdb even with me telling him exactly what to do, and then understanding what's said would be nigh on impossible

i have my pythons playing nicely with my mysqls now... let's see what i can come up with

---

### Post by Ferrat on 2008-02-16
> **aoanla said:**
> Not to rain on your parade, because I can see why people might like this... but how is this significantly different to someone visiting the Wine AppDB to check on the status of an application? It's not like it's hard to bookmark it and then search for a given app...
Essentially what you're asking for is to complicate AppDB by including a client-side mapping between application executable names and application entries in the AppDB. 
Frankly, wouldn't it be easier just to add something to the Wine install that prompts you to go to AppDB to check on the compatibility of programs?

Well it really doesn't have to be the wine appdb, just a db where ratings are stored, could be a totally self sufficient system but as to why, well the appdb is flawed in a major way, many doesn't use it. 

A lot of apps still have data only from versions that have a date release name instead of a 0.9.xx ect and some apps doesn't get updated within the 0.9.xx versions either. 

For ex. some programs that are rated gold or platinum are broken (sometimes without the maintainer knowing or caring) or the way to fix them has changed but no updates, other apps that are rated garbage actually work OTB platinum and so on. 
A simple, active and easy to use rating system would help a lot since you would get more up to date information, maintainers can't always keep up and some has moved on to other apps ect. and users doesn't always create the test data. This would give an more accurate rating and give you hints as to which version of wine to use other than just what version the maintainer used last time he updated.

---

