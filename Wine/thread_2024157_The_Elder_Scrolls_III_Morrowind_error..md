---
title: "The Elder Scrolls III: Morrowind error."
date: 2012-07-13
forum: Wine
---

### Post by SerFaren on 2012-07-13
So, I installed Morrowind and got it to load up, but whenever it's about to go to the title screen, it says "Music error: Cannot create filter graph".

I opened it up with Wine Windows Program Loader.

Is there a fix to this problem?


Tried it with Steam: Same problem.

---

### Post by Dlambert on 2012-07-13
Try installing in playonlinux. Or updating your WINE.

---

### Post by SerFaren on 2012-07-13
> **Dlambert said:**
> Try installing in playonlinux. Or updating your WINE.

I'll see if I can't get that working...

---

### Post by Dlambert on 2012-07-13
Let us know

---

### Post by shaggy2dope on 2012-07-13
hello all, i registered here real quick because i know for certian if i ask on gentoo i wont get a response for days probably, than i was going to make a thread on morrowind in wine.

but then i saw this so i said it must be a sign.


does anyone know if in wine you can install the morrowind graphic overhaul mod/MSGO?

would you need 7zip for windows to run the extractfile that initiates the scripts so you dont have to run the .exes one at a time? or is that exactly what you have to do, just run the exes one at a time,

also because you cannot the morrowind launcher at all would the modded data files be automatically loaded to the list of things to run.


also i'd like to say o.p i'm using wine-1.5.7, install/play of everything is fine, no winetrickery needed, so yea an easy solution for you is find an upgrade probably in deb testing areas or something.

thank you all, and sorry for derailing the thread sordof, go ahead and delete this if nessicary and i'll start a brand new one.

---

### Post by Toz on 2012-07-13
Moved to the Wine sub-forum.

---

### Post by Dlambert on 2012-07-13
The only way to know about the mods it to try it and post results. Have either of you trip OpenMW? Google it for more info.

---

### Post by shaggy2dope on 2012-07-15
> **Dlambert said:**
> The only way to know about the mods it to try it and post results. Have either of you trip OpenMW? Google it for more info.

yeah i have use'd openMW, i think i got my resources wrong or something though, like in /etc/openmw/openmw.cfg you have to direct it to the data/resources.

well i directed the data just to my /media/cdrom and it works fine for that, but resources i was confused. i dont know if they were talking about the gpl resources from the actual openmw install, or resources from a legitimate install, either way i didnt change the resources and left it at default.

 it runs flawlessly, but your stuck in TCL mode flying around, and cant really open any doors, and i spawned inside some cavern really couldn't find my way out of it even with flying through the walls, all the characters say he same thing etc etc, like a early early beta test version of morrowind, i use'd a different ebuild for openmw from someone named edmundo who has an over lay for openmw-overlay on git, but it's not availible in gentoo's layman list, they have 2 ebuilds for it in paddymac and l29ah i believe but they dont work, you have to make a cloned git repo of edmundo/openmw-overlay and use those sources/ebuilds. (well in my case i had to)

it's as smooth as butter but i dont really think there is any actual playability to it, unless i did it wrong.

either it's still just that much of a work in progress, or i used the wrong ebuilds(but that was the only solution i could find to get the actual compiling going)

i haven't looked at the source for the openmw.org actual openmw.9999 compaired to this openmw.9999 but now that i've mentioned it, i will when i feel like it later 


and the way morrowind runs in wine it's pretty unnecessary if you only want to play the game, cause it's easy as pie to install and runs just the same as a windows computer/xbox.

but yea i dont like using wine for anything either and would eventually love to get complete openmw clone of morrowind installed.

on a nother note i'll answer my previous question of yes you can install the mods with the 7zip extractor, but during the extracting process it'll notify you need a version of vcredist.exe which i got and installed fine, but at the last second it'll also tell you you need netframework 2.0,  so i went and downloaded the said file. but  the install will fail aswell at the last second


there are also versions of it in winetricks, but all of them fail aswell but for a different reason (there for x86 only). but the one the overhaul mod tells you to install is 64bit, netfx64.exe i believe, but either way they all fail, so now all the overhaul mods are crammed into my morrowind directory but some work good and some dont especially with outbeing able to configure any of them due to not having netfx64.exe


sorry i would've posted my results of me trying this out anyway,

i just figured for how long this stuff has been out someone somewhere has bound to have tried it:confused:

---

### Post by shaggy2dope on 2012-07-15
also to the op

if you can never end up getting it to work.

i'd suggest removing wine and deleting .wine directory from your home folder, install playonlinux and install it in there.


it' makes a simple job, that much simpiler.

i even was able to install oblivion (still crashes when you click new game though) and couldn't even get passed 5 seconds in the installer in a stock wine install with dx9 and yada yada yada.

but i dont know there's some issues, i'll think i'll keep it around just for things like Call of cthulu dark corners of the earth, on wine it's beautiful, but with playonlinux it crashes at start up and the debugging thing doesn't really tell me much ;(

---

### Post by shaggy2dope on 2012-07-15
> **shaggy2dope said:**
> also to the op

if you can never end up getting it to work.

i'd suggest removing wine and deleting .wine directory from your home folder, install playonlinux and install it in there.


it' makes a simple job, that much simpiler.

i even was able to install oblivion (still crashes when you click new game though) and couldn't even get passed 5 seconds in the installer in a stock wine install with dx9 and yada yada yada.

but i dont know there's some issues, i'll think i'll keep it around just for things like Call of cthulu dark corners of the earth, on wine it's beautiful, but with playonlinux it crashes at start up and the debugging thing doesn't really tell me much ;(


dont follow that advice, none of the things i've installed with playonlinux works, i thought they would just by asuming making it all the way to the main menu counted as working, everything crashes ;( wine + winetricks way eaiser, less mess in your home folder with just one simple .wine, instead of .playonlinux/.wineprefixes ugh, sorry sir i hope you get it working 100% with wine

---

### Post by shaggy2dope on 2012-07-15
> **shaggy2dope said:**
> dont follow that advice, none of the things i've installed with playonlinux works, i thought they would just by asuming making it all the way to the main menu counted as working, everything crashes ;( wine + winetricks way eaiser, less mess in your home folder with just one simple .wine, instead of .playonlinux/.wineprefixes ugh, sorry sir i hope you get it working 100% with wine


i'm an idiot and forgot to optirun playonlinux for morrowind, for what ever reason that's the only way i can get it to run, i've even had it running on the intel gpu with wine also with no problems so it's strange it, hopefully that was the cause for oblivion to fail too, but i doubt it.

sorry for the confusion

---

### Post by shaggy2dope on 2012-07-16
i dont know anymore, after careful consideration i'd suggest using both regular wine/q4wine + playonlinux for little scripts that can be used to install things easy + create the "proper" wine version environment that best suits the game/app.

and for games you cant seem to install using playonlinux, just wine to do it.

i'm thinking theres a way to point the regular /home/.wine to write to /home/playonlinux/.wine by default instead somewhere but i haven't came across it yet

---

### Post by Dlambert on 2012-07-17
Stop bashing playonlinux, it works great and you must have done something wrong/had a compatibility issue. Have a nice day. :D

---

