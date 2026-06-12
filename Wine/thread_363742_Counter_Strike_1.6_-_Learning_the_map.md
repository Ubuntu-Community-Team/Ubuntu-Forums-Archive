---
title: "Counter Strike 1.6 - Learning the map"
date: 2007-02-17
forum: Wine
---

### Post by ashmew2 on 2007-02-17
Hello every1 , I was wanting to know something about playing Counter Strike 1.6 under wine/cedega.I installed the game using wine (I have the setup as a single .exe). I dont use steam and i use cedega to run the game in opengl mode. Everything is working just PERFECT! but there is this lil thingy , Whenever i try to play a game with bots on any map (such as de_minidust2) , it keeps saying "Learning the map" then "Analyzing hidden spots" , and then when its done , it restarts the round....but instead of starting this time  , it again says "Learning the map" and restarts and goes on and on and on. What i think is that whenever the game "learns" the maps , it creates a .nav and a .txt of the map( which contain the info) in the directory of the maps.(And frankly i think there is where the problem lies!)
Please help!! The game is running perfectly !! Just this bug!! Help!!!!!!!!!!

Thanks

---

### Post by bichopro on 2007-02-17
excuse me i speak so bad English

the bot need learn the map before play and, be patience and wait the necessarily time for this, after this you can play in this map with bots and you never see this message ever more ( in this map)

this process crate a .nav (not so sure of the extension of the file :) ) file in the map folder.
that all...

i hope was usefully, and sorry again for my English

pd: more long map..more time to process

---

### Post by ashmew2 on 2007-02-17
I dont think u got my question...
Please visit the link : [http://www.youtube.com/watch?v=bPU66uGqmrk](http://www.youtube.com/watch?v=bPU66uGqmrk)
I created a 1 minute video so u can see what is happening..

---

### Post by ashmew2 on 2007-02-19
BUMP!!
i'm using windows XP to export the .nav files !!:cry: 
Some1 help!!

---

### Post by ashmew2 on 2007-02-21
Bump

---

### Post by Brynster on 2007-02-21
enough of the bumping already.

Having played around with this a little myself the way i got around it was to hunt the internet for .nav files for the maps. (not very successful though.)

Somebody also suggested it was a permissions issue, If you right click on the .wine folder (its hidden so you'll need to uncover it) and in the permissions tab make it writable by ticking all the write permission boxes this may "fix" the issue for you. I didn't have much joy with that either.

---

### Post by ashmew2 on 2007-02-21
I already tried that!!!!!! and man , do u also have a non-steam copy of CS 1.6 ? and are u having the same problem concerning LEARNING THE MAP?!

---

### Post by ashmew2 on 2007-02-22
OK i found a solution....I got this COunter Strike - R3LOADED edition from somewhere and when i learn maps in that , it works fine (but the graphics are horribly screwed up) , so i just copy paste the nav files from reloaded to original cs directory :D

---

### Post by Brynster on 2007-02-22
Sorry i couldn't help further. But i am glad you got it sorted.

---

### Post by ADeCe on 2008-05-17
This problem is resolved if you remove the cs_amd64.so and cs_i386.so from your /cstrike/dlls folder.

---

### Post by airon1986 on 2009-04-20
1: install zbot

2: go to C:\Program files\Steam\steamapps\(username)\counter-strike\cstrike and **create a new folder** called "maps"

3: start cs 1.6 and create a game with your new map.

4: in console you write "bot_nav_save"

(this command creates a .nav file in the "maps" directory you created earlier. First I thought that the .nav file would be saved in C:\Program files\Steam\steamapps\(username)\counter-strike\cstrike_norwegian\maps, but for some reason it did not)

5: type "h" and "quick add bot"

6: now it should work! :)

---

### Post by alex.rayu on 2009-04-21
Have checked if the read/write permissions are set for the .wine folder and all folders in it? (.wine folder is a hidden folder residing in your home folder). Sometimes permissions are set to read-only, and that prevents the system from saving nav files. Right click on the folder (.wine) and set the permissions, and apply them to the internal folders and files as well.

---

### Post by Found on 2009-10-05
It's a problem with a back slashes instead of forward for the .nav files directory.
```
ERROR: Cannot save navigation map 'cstrike\maps\cs_militia.nav'
```
I didn't manage to find the solution.

---

### Post by AGsPlm on 2012-09-01
Hi all, idk if u guys resolved this problembut i had it too, my CS 1.6 was installed in C:\Program Files\Counter Strike 1.6\ , and the bot to save the analyse need premicion (cuz its in C:\Program Fil...)  what u need to do is **cut ur counter strike folder to desktop and create a new shortcut**, fo rme its result, sorry guys if i got bad english, im portuguese, only made this account to try help on this. cyya :)

---

### Post by AGsPlm on 2012-09-01
* and plz, say me if it work with you*:D

---

