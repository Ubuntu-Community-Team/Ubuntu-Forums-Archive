---
title: "world of warcraft lag"
date: 2013-05-15
forum: Wine
---

### Post by mysteron75 on 2013-05-15
I am running Wow and I am experiencing a lot of lag when i am running dungeons. My system is running ubuntu 13.04 with the latest wine and playonlinux and my hardware is an intel i7 3820 with 16gigs of ram and gtx560 ti. I have already set my wow to run with opengl. Everything runs fine everywhere until i get in a fight in a dungeon. Then i am unable to do anything it so slow. I even set my graphics to the lowest settings. Are there anymore tweaks I can do?

---

### Post by Lightning Dragon on 2013-05-15
Hi,

I have one thing you could try via winetricks > regedit, if you are willing to try it. I have used it a few times to speed up games, so maybe it will work for you. If you are willing, here is the instructions;

Open regedit > HKEY_CURRENT_USER > software > wine > Direct3D > disable UseGLSL. 

Careful with it though. If you don't want to risk your install, then don't do it. Other than that, have you tried the official response to this? It has been given to players a lot and I've seen that unchecking the "Optimize Networkf or Speed" works for them.

> 

The first thing to try is to uncheck "Optimize Network for Speed" from the Options>Network menu. If you're in an instance when you do this, make sure to exit and then re-enter after unchecking the box to test.

Next, move on to resetting your UI. Navigate to the World of Warcraft folder on your computer. Make sure the game is not running while you are doing this. Once in the folder, delete the Cache, Interface, and WTF folders.

After doing that, please double-click on the icon labeled 'Repair' and run the Repair Tool. Then test your instance lag and see if it has improved.


Lastly, addons can cause lag, which I hear a mod called Healbot does a lot. Do you have any installed?

---

### Post by mysteron75 on 2013-05-15
I opened the registry editor in playon and i followed 
[COLOR=#000000]Open regedit > HKEY_CURRENT_USER > software > wine > Direct3D > disable UseGLSL. 

and i didnt have that key. I did uncheck network optimization



[/COLOR]

---

### Post by Lightning Dragon on 2013-05-15
Hi,

Hmm, that's strange. Maybe my directions are off. Here, try this site;

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

If you still can't find it, open up winecfg and then add it to the library and then disable it. If it doesn't work, return back to where you had it.

---

