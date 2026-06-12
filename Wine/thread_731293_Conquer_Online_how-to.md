---
title: "Conquer Online how-to"
date: 2008-03-21
forum: Wine
---

### Post by h4mx0r on 2008-03-21
Done with wine 0.9.58
Requirements:
**pristine install of conquer** (from windows and never ran, blank game settings)
**mfc42.dll** (version found in Win XP SP2 4602907535fd682195dfff9117365826)
**msvcp60.dll** (1f57eb5b92b2ac7f9d71a77d184d8c13 or 6050bcc1b23f3df7a1876cbdcbac8232)
**quartz.dll** (version found in Win XP SP2)
**simsun.ttf** (from microsoft word or chinese language pack for it)
**arial.ttf **
**cour.ttf** (cour.ttf and arial.ttf from most windows installs I think)
**animated cursor patches** ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7440))
**custom game settings** (found in /ini of conquer directory can move the gui buttons and text to proper locations, everything is editable heck my class name is Supreme Overlord)

The .dll go into .wine/drive_c/windows/system
The .ttf go into .wine/drive_c/windows/fonts

run winecfg and add msvcp60.dll , mfc42.dll , and quartz.dll to libraries and mark them as native.

run regedit then go to HKEY_LOCAL_MACHINE/Microsoft/Windows/CurrentVersion/Fonts
and
HKEY_LOCAL_MACHINE/Microsoft/Windows NT/CurrentVersion/Fonts
Add the fonts to the registry in those locations (Ex. right click and choose string enter Courier New then for its value put cour.ttf) Oh and simsun.ttf for its string name there is a space "Sim Sun"

After everything is setup you cd to the Conquer directory and run /home/user/customwine/lib/wine play.exe and it should work or run autopatch until it is fully updated, repeat as neccessary. You have to hold alt to login to the game and the user/pass is underneath where it should be ([http://bugs.winehq.org/attachment.cgi?id=5190](http://bugs.winehq.org/attachment.cgi?id=5190)). The game will lag slightly from error message output, you should disable wine fixme messages through which ever method you prefer.

tips- game may crash if certain special effects happen so I disable them (more info on that later). Don't change resolution else your settings might be trashed permanently (no clue why??). You have to use a 1024x768 virtual desktop, else your system might halt and die.

If there are any questions/opinions or volunteering of help with the /ini settings or info about dinput.dll possibly fixing the unicode problem with having to hold alt to enter login info I would be very grateful.

ps- also working on custom gui theme for the game perhaps an ubuntu or tux theme with really eyecandy quality graphics

---

### Post by chain2k on 2008-05-21
Hi,
Have to tell you that for now there is only one trouble - with direct input and ALT key. All other problems solved)
You can check my POL installation script for Conquer Online here
[http://www.playonlinux.com/en/topic-1552-Conquer_Online_20.html](http://www.playonlinux.com/en/topic-1552-Conquer_Online_20.html)

The Most easy problem was lost focus on logon window) The problem was in fonts DPI, so a little registry fix can heal it (you can see it in my script)

bye

---

### Post by h4mx0r on 2008-07-17
The latest 1.1 wine works far better because the new conquer client has a small cinema then a 3d login. However the alt key login issue has progressed in significance. I think I can type the username but the password keeps switching focus to the login button and not working or erasing asterisks. Like there is a Remember option for username I think there is a remember option for password but I have not played around with conquer that much. You might want to include some sort of kill statement in the conquer launcher because they have this trojan checker program that could possibly linger running afterwards and spike system resources.

I tried your method of running conquer and I am concerned because of how you must use a pristine copy of conquer from windows. How did you compensate for that by having an installer method of install? When I try your installer method I get a white screen. You also might want to have it install gecko engine when its installing conquer just to speed things along. I sometimes use .net installed with winetricks so I can use some user created apps for changing special effects settings and adding custom themes to the game.

I look forward to working with you to maintain this game. I lack some experience working with playonlinux, doesn't look all that hard by your example. I do have a few apps I might try to get going with it such as doukutsu, mushclient, and deicide just to get some experience with how it handles its scripts.

---

### Post by h4mx0r on 2008-07-17
That tip about having to use a virtual desktop though, you really don't need to if you have it working properly. At one point I was missing something and the game would run for like a minute working fine then crash and I didn't want it to mess with my desktop all broken like that. I just favor it as a precaution and the game only goes up to 1024x768 anyway so it looks a bit obscured on higher resolutions.

---

### Post by realsaiko on 2008-07-21
Thank you for your info, but i still got problems... the conquer installed fine and updated also without problems... i`ve launched the conquer, can select the server, login with alt (or without alt but it`s more difficult) but the game stuck`s when loading in about 15-20% of all load and thats all... and i don`t know why... i`m using Linux Mint and Wine 1.1.1

---

### Post by bren21 on 2008-07-21
When I tried I got to the screen where you choose high or low def, and I choosed low. After that the trojan scanner came up, once it was done the game never loaded.

---

### Post by DivineJustice on 2008-07-23
> **bren21 said:**
> When I tried I got to the screen where you choose high or low def, and I choosed low. After that the trojan scanner came up, once it was done the game never loaded.
I am having the same problem as you, I even removed the trojan scanner



removing the trojan scanner-

Video on what to do
[http://youtube.com/watch?v=_QprtMhDBN4](http://youtube.com/watch?v=_QprtMhDBN4)

Directions from video if you don't want to waste time watching
1. go into your Conquer2.0 directory 
2. delete the zftqat folder
3. go into ini folder
4. open Startgame.ini
5. delete everything after the '='
should say

[ZFTqat]
Filename=

6. save it

At original poster, I put the msvcp60.dll and mfc42.dll into my folder, but it doesn't appear in Wine's libraries list, i've tried both the system and system32(where all my .dll are found) folders

---

### Post by DivineJustice on 2008-07-24
forgot to restart my computer after enabling a restricted driver:p

right now i enter my username and pass, but it get stuck at about 1/5 way on loading screen

> **h4mx0r said:**
> The game will lag slightly from error message output, you should disable wine fixme messages through which ever method you prefer.

this might be my problem, how would i do this?

---

### Post by h4mx0r on 2008-07-24
***IMPORTANT***
I need everyone to cd to the conquer directory and run conquer with "wine play.exe > log.txt 2>&1" then post log.txt please so we can see what is the matter. That will show the new error messages. And please follow DivineJustice's tip linked to here [http://youtube.com/watch?v=_QprtMhDBN4](http://youtube.com/watch?v=_QprtMhDBN4)
***

Also what I meant by preventing lag from fixme messages is to completely disable the debugging system by running it with "WINEDEBUG=-all wine play.exe"

DivineJustice: You have to run winecfg and mark those dll as native,builtin. Or if that doesn't work try marking them just native. native,builtin tries using the specially modded wine dlls in conjuction with the native ones you supplied so usually gives better results.

realsaiko: yes the login problem is really urking my nerves here, any ideas for a permanent fix for it? I'll try searching the wine patches database and looking over some more font fixes to try to get it working right. Wine 1.1.1 might have all the things required to play conquer out of the box if we can just get around the login.

Sidenote- can anyone provide debugging information for what dlls and fonts conquer usually runs with in a native windows environment? I know how to work with wine well but with windows I'm not so good with, I'll perhaps try using virtualbox or something for testing.

---

### Post by h4mx0r on 2008-07-24
Quote from winehq - "2.9. My application won't run, and says it needs MFC42.DLL or MSVCP60.DLL

See "How can I get a copy of some runtime library?" above. You can install MFC42.DLL, MSVCP60.DLL, and friends by running winetricks and selecting vcrun6."
------------
I think it might be better if we use winetricks to install vcrun6 because there might be more than just those 2 dlls missing and I think it gives the right ones needed, could someone double check that?

I also think the newer conquer might have started using .net because I heard of some plans for that so also using winetricks to install dotnet20 might help.

"sh winetricks corefonts vcrun6 dotnet20"

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by Yoinazek on 2008-10-16
Hi I was trying to log in and the loading bar gets stucked just like what DivineJustice said so I ran wine play.exe and here is the log...thanks for the help

---

### Post by Yoinazek on 2008-10-23
No one has answered but I'm going to tell whats happening anyways.  I got to pass the loggin bar and I got into the game . I know I got into the game because I can hear the game, problem is I can't see anything, screen is black.  Any ideas?!


-Edit-
I disabled desktop effects and the only thing that changed is instead of black screen i get random colors >_<

---

### Post by GrantsV on 2008-11-15
Ok, we are past the first login, creating a new character.  But it says invalid character for character name regardless of what we put in!  Anyone else seen this??

---

### Post by GrantsV on 2008-11-16
The exact message, when creating a new character is always:

"Sorry, the name you specified contains invalid characters."

Everything else appears to be working fine.

---

### Post by sunshine1 on 2009-09-18
> **Yoinazek said:**
> Hi I was trying to log in and the loading bar gets stucked just like what DivineJustice said so I ran wine play.exe and here is the log...thanks for the help

i have the same any ideas

---

### Post by sunshine1 on 2009-09-18
help please i want to play this game

---

### Post by sunshine1 on 2009-09-24
why there is no helping

---

### Post by Orfintain on 2009-12-23
is this worth trying ?

---

