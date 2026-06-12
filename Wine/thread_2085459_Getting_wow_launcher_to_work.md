---
title: "Getting wow launcher to work"
date: 2012-11-18
forum: Wine
---

### Post by Markvangarde on 2012-11-18
Good Day I am brand new to Ubuntu, and looking forward to work on this OS for a long time, but I don't know how to get World of warcraft's launcher to work, I have my wow installation in a windows partition and hope to leave it there, and I have seen I can lauch the wow.exe game and go to the logon menu of wow, but the launcher doesn't work, in a terminal I can see activity but I end up with wow error code blzpts00007, does anyone know what I should do to get this one to work? please...

---

### Post by rudeboyskunk on 2012-11-18
You are using wine, right?  What are you typing into the terminal to get it to run?  Copy and paste what you typed and what came out so we can see just what the problem is.

---

### Post by Markvangarde on 2012-11-18
Yes, I don't know how to use it correctly, double clicking on the wow.exe file opens the program(game), I have downloaded a new wow installer from battle.net, and copied that file to, the windows partition in "program files\world of Warcraft\World-of-Warcraft-Setup-enUS.exe" and run this code is a terminal: 

"wine "d:\program files\world of Warcraft\World-of-Warcraft-Setup-enUS.exe" -opengl"

I mounted d:\ as my windows partition with the game and other files, c:\ is where my windows lies.

I thought the wow launcher should install the latest updates and stuff

---

### Post by wildmanne39 on 2012-11-18
*Thread moved to **Wine**.*

---

### Post by rudeboyskunk on 2012-11-19
I googled that error code and it says it means the Blizzard Agent is missing.

If you go to the terminal, instead of typing in the Windows path (Linux uses different ways to make paths than Windows), just navigate to folder where WoW.exe is located.

Either that, or just do a complete re-install of WoW onto your Linux partition.  That's what I always did when I played WoW.  Trust me, it makes the whole situation a lot easier.

---

### Post by Tweak42 on 2012-11-19
The wow launcher should be the game directory and named "World of Warcraft Launcher.exe".  If you copied the game straight from a windows install and into a wine prefix you need to run the launcher first so it can download/install/update the "Blizzard Agent/Client" whatever into the wine prefix.

For me the Agent is installed to:  > /home/<username>/.wine/drive_c/users/Public/Application Data/Battle.net/
I have had to delete it a few times when some patch messed up and it would not let any Blizzard games update, (WoW, Diablo3 and Starcraft2).  Just running the launcher would re-download the Agent and the launcher could run it's updates.

When in doubt 1) rename your old wine prefix (just in case need to roll back), 2) run winecfg to create a new prefix, 3) Link or copy your wow directory to the wine prefix. 4) Run wow launcher to install the Agent and check the game files.  5) Run wow.exe

Note: starting the game from the launcher play button has had problems in the past, so I normally run the game directly i.e. "wine Wow.exe -opengl"

---

