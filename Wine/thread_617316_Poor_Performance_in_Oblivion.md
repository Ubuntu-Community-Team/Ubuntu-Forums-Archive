---
title: "Poor Performance in Oblivion"
date: 2007-11-19
forum: Wine
---

### Post by colsanders on 2007-11-19
i switched to ubuntu yesterday, installed oblivion with cedega, and it ran unspeakably slow like 2 fps, i usually run this all maxed 1280x1024 with 30 fps, please help me :D

---

### Post by aoanla on 2007-11-19
> **colsanders said:**
> i switched to ubuntu yesterday, installed oblivion with cedega, and it ran unspeakably slow like 2 fps, i usually run this all maxed 1280x1024 with 30 fps, please help me :D

Presumably, you switched to Ubuntu from Windows? Have you been able to run any other 3d applications since installing Ubuntu?
Did you turn on the Restricted Drivers for your 3d card after installing Ubuntu (System Menu -> Administration -> Restricted Drivers Manager)?
What's your hardware configuration?

If you had enabled your restricted drivers, can you tell us what the result of typing 

glxinfo | grep render

in a terminal window is?

---

### Post by KhaaL on 2007-11-19
Oblivion runs with worse performance under wine / cedega than in windows - that's a known issue. You're going to have to lower the graphics since you can't run it maxed - preferably by only using bloom outdoors and HDLR (sp?) indoors.

---

### Post by hikaricore on 2007-11-19
_CAPS REMOVED FROM TITLE_

Don't do this again.  ^_^

---

### Post by colsanders on 2007-11-19
well ive had the nv accelerated drivers enabled, no hdr is enabled, bloom is. ill try not using bloom, but i got call of duty 1 working and it runs perfect at 1600x1200 with only one framerate boggle at the mg(beacause of advanced particles)

my system:

475 watt psu sli ready
intel celeron D 2.4ghz 553 fsb
Winfast A7600GT TDH
1GB DDR400
320GB HDD

yes i know celeron sucks also :)

---

### Post by Melhisedek on 2007-11-20
IIRC CoD is OpenGL game, based on Quake III engine and those run better on Linux.

---

### Post by DarkSim on 2007-11-20
I don't know if it will work but when I played Oblivion on Windows I used a few mods that reduced default textures or took refraction animations out of oblivion gates and the like. There was also a project to make meshes more optimized. Maybe someone with a lower end system will find it useful. Make sure you read the details each download comes with.

Here I found them:
[http://www.tesnexus.com/downloads/file.php?id=2411](http://www.tesnexus.com/downloads/file.php?id=2411)
[http://www.tesnexus.com/downloads/file.php?id=3726](http://www.tesnexus.com/downloads/file.php?id=3726)
[http://www.tesnexus.com/downloads/file.php?id=6948](http://www.tesnexus.com/downloads/file.php?id=6948)
[http://www.tesnexus.com/downloads/file.php?id=6446](http://www.tesnexus.com/downloads/file.php?id=6446)
[http://www.tesnexus.com/downloads/file.php?id=6447](http://www.tesnexus.com/downloads/file.php?id=6447)
[http://www.tesnexus.com/downloads/file.php?id=6448](http://www.tesnexus.com/downloads/file.php?id=6448)
[http://www.tesnexus.com/downloads/file.php?id=6550](http://www.tesnexus.com/downloads/file.php?id=6550)
[http://www.tesnexus.com/downloads/file.php?id=7099](http://www.tesnexus.com/downloads/file.php?id=7099)

(Must have Shivering Isles for these):
[http://planetelderscrolls.gamespy.com/View.php?view=OblivionMods.Detail&id=3572](http://planetelderscrolls.gamespy.com/View.php?view=OblivionMods.Detail&id=3572)
[http://planetelderscrolls.gamespy.com/View.php?view=OblivionMods.Detail&id=2731](http://planetelderscrolls.gamespy.com/View.php?view=OblivionMods.Detail&id=2731)

---

### Post by hikaricore on 2007-11-20
There's actually a thread around here about some of these mods and which to use for best performance under WINE if you search for it.  ^_^

---

### Post by DeadSuperHero on 2007-11-20
Well, first off he's new to Ubuntu and Linux in general. How do I know this?
Gents, colsanders is my younger brother. So, I can help him with setting this stuff up, but we need to look into how to do these patches. Would one install the patches through Cedega as well? Hm...
EDIT: Oooh...they seem to be .zip files...hmmm....

---

### Post by hikaricore on 2007-11-20
uggg you kids are lazy ^_^

[http://ubuntuforums.org/showthread.php?t=349764&highlight=oblivion](http://ubuntuforums.org/showthread.php?t=349764&highlight=oblivion)

Here's a kinda dated howto.  Should work with the latest version of WINE I believe though, I don't play the game.

You also may want to check the WINE Application Database page: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3150)

The best info can probably be found there.

---

### Post by DeadSuperHero on 2007-11-20
No mate, he's just inexperienced. 

:)

---

### Post by DarkSim on 2007-11-20
I glanced  through that howto briefly before I posted and I only saw the operation optimization one mentioned. Didn't mean to step on any toes just trying to help someone get their game fix on. 

I quit playing Oblivion about a month after Shivering Isles came out so I really haven't been up to date with the recent tweaks. After you're done checking out that walkthrough check out here for some more tips :
[http://www.bethsoft.com/bgsforums/index.php?showforum=23](http://www.bethsoft.com/bgsforums/index.php?showforum=23)

---

