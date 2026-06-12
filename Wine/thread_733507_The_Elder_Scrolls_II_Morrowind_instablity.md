---
title: "The Elder Scrolls II: Morrowind instablity"
date: 2008-03-23
forum: Wine
---

### Post by Majin Zero on 2008-03-23
I'm just seeing it running very sluggishly, I check my system monitor; I'm using only half my RAM, and my CPU isn't super taxed, only around 60% with spikes up to 70%.

However, I'm seeing it freeze, as I move between areas, when a name of a area appears in the lower right, it lags, then eventually goes forward, as if it were loading in a disk based game.

The music also does that, as it moves from track to track, there is a long pause.

During combat, if status affects are applied, the game my lag then.

Some times the game will lag during NPC conversations, and I'll have to click a topic/action twice for it to register.

also, just looking around isn't smooth, it isn't halting when I spin and look around, it's just....it's jerky, not a smooth "I'm moving around" type of feel to it.

My computer has a 2.8 HT Pentium 4 CPU, 1 gig of RAM, and a 9600 GT Gfx Card.

I think I'm well above minimum requirements for the game.

I have a bunch of mods, but most are just "bug fixes"

I do have 3 mods that I'm suspecting are bogging things down

Morrowind comes alive

Children of morrowind

better bodies

Could those 3 be the cause of the sluggish performance?

---

### Post by Majin Zero on 2008-03-24
it seems pidgin becomes unresponsive when I have morrowind open, and if I alt-tab out of morrowind to do something else, morrowind will lock up.

Is this some known issue with Wine/morrowind?

---

### Post by Sugi on 2008-03-24
It seems like you are talking about Elder Scrolls 3 Morrowwind, but in your titled you called it Elder Scrolls 2.  Elder Scrolls 2 was Daggerfall, not Morrowind.  But I think you might Morrowind, because the mods you talk about is only for Morrowind.  Which Elder Scrolls are you talking about?

Sugi

---

### Post by Majin Zero on 2008-03-24
ooops, it's III, morrowind.

I don't even know where to grab daggerfall....

---

### Post by DarkSim on 2008-03-24
Children of Morrowind and MCA are very script intensive. Also the engine Morrowind is built on isn't that optimized. You could have a top notch rig and Morrowind will still chug along. You can look at your Morrowind.ini file and make some tweaks that might help a little.

Here is an archived thread from the official forums about tweaking the .ini
[http://www.yacoby.net/es/forum/9/6027921165763400.html](http://www.yacoby.net/es/forum/9/6027921165763400.html)

One note about using mods. Sometimes even when a mod is installed correctly you will run into people missing heads or clothes aren't showing up. The way to fix this is to: (It takes a good bit)

1.)In game open the console up with the ~ key and click on the person/item causing the problem. Type ori. This usually gives the mod that person/item is from unless it is on a levelled list.

2.)There is a name at the top of the console box. That will be the item you're looking for in the mod so write it down.

3.) Open up the mod in the Construction Set and find the item name from the top of the console box. Look to see what the name of the part that is not showing up is called. Now find that in the appropriate tab and double click on it. There will be a box that has a mesh name. Write it down.

4.)There are 2 ways possibly to do this.:
-A.Find the mesh manually and make a copy that has the same name but all in lower case. Do the same for the texture. It will have the same name but be in Textures folder.
-B. I haven't tried this but you could get a windows version of nifskope, make a copy of the offending mesh with lowercase name and then link the corresponding texture and save.

Sorry for the long winded rambling but you said you were using MCA and I had to do that with a few of the meshes and textures added by that mod for it to show up in game. It took me a while to sort most of it out but I still run across a headless person now and again.

---

### Post by Sugi on 2008-03-24
I figured that you were refering to Elder Scrolls 3 Morrowind, but sometimes you can never know.  I think you might be able to find Daggerfalls within stores, but then again, maybe not.  It's fricken old.  I know it's aviable online.  The usally Ebay and amazon (for the long price of $37.00 and aviable for DOS only :)).  Now, I can tell you right now, that you will not be able to find Arena in stores or probably not online either for sale for that matter.  The Elder Scrolls 1: Arena, that it is.  But, the good news is, it's aviable for download.  FREE.  Bring out your old copy of DOS and your floppy drive. :)

Sugi

---

