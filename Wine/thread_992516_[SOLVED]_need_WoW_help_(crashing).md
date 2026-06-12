---
title: "[SOLVED] need WoW help (crashing)"
date: 2008-11-24
forum: Wine
---

### Post by Ixonal on 2008-11-24
OK, so I have WoTLK installed and the sound now working correctly. I'm running it in OpenGL mode (D3D crashes immediately after execution begins). The issue is that after a random interval upon entering the game world, WoW crashes. When run on the command line, it spews out something about being unable to allocate memory. This seems to be accelerated in proportion to the value for the draw distance setting.

I'm running a custom system, dual core Pentium processor, 2 gigs of RAM, GeForce 9800 GT card, using Intrepid Ibex, beta nvidia drivers (same issue happened with drivers from envy), and wine 1.1.9

These crashes are driving me nuts and I really don't want to go back to Windows. Can somebody please help me??

---

### Post by gangadjinn on 2008-11-24
I had alot of problems with WoW crashing on my *** too... 

I started by going through my addons and using the elimination process on them... seems lighyheaded and mobmap vreated alot of issues for me... 

nowdays I rarely get any crashes...

---

### Post by Ixonal on 2008-11-24
now, I could see that being an issue if the crashes happened when I use a particular addon, but this seems to be tied to the draw distance.

---

### Post by Zorthanis on 2008-11-24
Lucky my wow won't even start right it gets to the start screen were the dragon is with OPen GL mode setup and its like all dark and I can't see anything.

---

### Post by Ixonal on 2008-11-25
bump

any ideas yet anyone?

---

### Post by Ixonal on 2008-11-25
anyone looking at this? need more info? nething?

---

### Post by Eviljim on 2008-11-26
Well going back to the addon thing, I used to have my WoW install crash at random intervals after entering the game world, and it turned out to be Cartographer addon. Dont forget that all addons are loaded before entering the world, even if you dont use them in game.

Have you tried disabling all addons and trying again?

Failing that, I suggest rolling back to whatever drivers were in the repo when 8.04 was released (I use ATI so dont know what version that would be) and possibly rolling back to Wine 1.01.

---

### Post by Ixonal on 2008-11-28
hmmm, cartographer.... thought there wasn't a working version currently, lemme see if I have that on...

update: cartographer was on, turned it off, but still having issues. turned draw distance up to half and all of the polygons became garbled (though the game didn't freeze). when I set it a lil bit lower, the polygons went back to normal, but I looked around a lil and it just crashed. This is still sayin to me that it's a rendering issue rather than a mod issue since the polygons go all wonky

update 2: ok, after that crash I logged back in and tried again, and now I'm not crashing anymore, so it appears it WAS cartographer after all. I went through a few stress tests that would've crashed it before and everything remained stable, so I'm happy to say that everything is well! ty for the suggestion!

---

### Post by Mayfairy on 2008-11-30
Interesting. I've had lots of crashes too recently. They started appearing after WOLTK installation and most of the time happen in Dragonblight area. 

Sometimes I can go on hours without a single crash but in Dragonblight it happens roughly every 5 minutes. Especially the crashes seem to be centered around the plains with the dragon sanctuary. Lots of things happening there with flying dragons and everything so I'd imagine the problem being something with the display drivers / card. 
Few days ago I manage to tone the problem down a lot by decreasing the detail level but after shutting down the client for a while and starting again the problems appeared again, worse than ever, even with the decreased details. 

Then again I do have Cartographer installed, or at least I should have unless I didn't manage to make it work with WOTLK. If Cartographer indeed is the problem then the bad coding or something with WOTLK might be the issue. Cartographer worked nicely for me before WOTLK.

EDIT: 2 days later; not a single crash after disabling Cartographer.

---

### Post by Eviljim on 2008-12-08
> **Ixonal said:**
> hmmm, cartographer.... thought there wasn't a working version currently, lemme see if I have that on...

update: cartographer was on, turned it off, but still having issues. turned draw distance up to half and all of the polygons became garbled (though the game didn't freeze). when I set it a lil bit lower, the polygons went back to normal, but I looked around a lil and it just crashed. This is still sayin to me that it's a rendering issue rather than a mod issue since the polygons go all wonky

update 2: ok, after that crash I logged back in and tried again, and now I'm not crashing anymore, so it appears it WAS cartographer after all. I went through a few stress tests that would've crashed it before and everything remained stable, so I'm happy to say that everything is well! ty for the suggestion!

your welcome :)

---

### Post by btallas on 2008-12-08
I believe carbonite is also a culprit for crashing.  With carbonite enabled, I can play until I open the map which then takes my framerate down to like 1-3 frames per 5 seconds.  When I disable carbonite, everything seems to work (although still about 10 fps slower than vista).  Looks like any map addons might be issues.

---

### Post by xarte on 2008-12-09
Does Questhelper rely on Cartographer?  If not, are you running Questhelper ok?

After the patch I was  having problems with crashing and DCing on this machine on XP, and turning off pixelshading fixed it. Not pretty, but functional.

there's a handy list of in-game commands here
[http://www.pooh.cz/pooh/a.asp?a=2014990](http://www.pooh.cz/pooh/a.asp?a=2014990)

---

### Post by Eviljim on 2008-12-09
> **xarte said:**
> Does Questhelper rely on Cartographer?  If not, are you running Questhelper ok?

After the patch I was  having problems with crashing and DCing on this machine on XP, and turning off pixelshading fixed it. Not pretty, but functional.

there's a handy list of in-game commands here
[http://www.pooh.cz/pooh/a.asp?a=2014990](http://www.pooh.cz/pooh/a.asp?a=2014990)

Questhelper can use Cartographer to provide Tomtom like enhancements, but it is not dependant on it, as I only use QHelper.

---

