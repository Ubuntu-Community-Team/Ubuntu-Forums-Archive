---
title: "Xubuntu 14.04:  Do not know what commands to use WINE properly like making a prefix"
date: 2014-04-29
forum: Wine
---

### Post by queazy03 on 2014-04-29
Hi,

The instructions say: '*Create a fresh Wildstar prefix with WINEARCH=win32 by typing  "WINEPREFIX=~/prefix/wildstar/ WINEARCH=win32 winecfg". Please edit to  suit your own folder structure.'*
...but what is my folder structure?  I don't know what to write.



I'm am using Xubuntu 14.04 with these parts at "[http://pcpartpicker.com/p/3weiH](http://pcpartpicker.com/p/3weiH)".  I'm trying to install WINE so I can play the mmorpg game WildStar, but I am such a beginner at Xubuntu I can't properly understand the written directions to do so.  After a few days, I was able to 
* get WINE, 
* add the WINEHQ PPA Repository, 
* software update, 
* do that "sudo apt-get update" then "sudo apt-get upgrade",  
* and also 'sudo apt-get update' then 'sudo apt-get install wine1.7".  
but now I'm stuck at adding this prefix thing.

Please see "[http://appdb.winehq.org/objectManager.php?sClass=version&iId=30246](http://appdb.winehq.org/objectManager.php?sClass=version&iId=30246)" and take note about the 'Additional Contents' section.  The first step in additional contents is

* 1) Create a fresh Wildstar prefix with WINEARCH=win32 by typing "WINEPREFIX=~/prefix/wildstar/ WINEARCH=win32 winecfg". Please edit to suit your own folder structure.*
...As simple as that sounds, I completely screw it up.  I think the thing is that I do not know my own folder structure, therefore I do not know what to write down to suit it to my own folder structure.  I imagine I have to write that down where the " ~ " (tilda) is, but I'm not really sure.  I've asked in a few place but have not gotten a clear response that I can comprehend.  

How do I create a prefix and what is my folder structure?  Do you think there would be anything else I would get lost at following those directions?  Thank you.

---

### Post by Toz on 2014-04-29
The default wine prefix is ~/.wine (its simply a folder structure, in this case a hidden .wine folder in your home folder). To create another prefix, just specify another folder name. "~/prefix/wildstar" will only work if the folder prefix exists on your system. I would suggest using this command:
```
WINEPREFIX=~/.wildstar WINEARCH=win32 winecfg
```
...which will create the prefix (folder) as .wildstar in your home directory.

For the instructions from that wineappdb page that you linked to, simply replace "~/prefix/wildstar" with "~/.wildstar" in each instance.

---

