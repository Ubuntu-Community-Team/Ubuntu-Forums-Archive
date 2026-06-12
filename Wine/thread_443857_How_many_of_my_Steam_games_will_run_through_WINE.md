---
title: "How many of my Steam games will run through WINE?"
date: 2007-05-14
forum: Wine
---

### Post by Hobo Joe on 2007-05-14
Ok, so I looked it up, and it says, "Half-Life, Half-Life 2, Counter-Strike 1.6, Source", then it says, any games that run on the Half-Life or Source engine.
Does that include Garry's Mod, HL2 Deathmatch, HL Source, Episode 1, DM:MM, and SiN: Emergence?
Also, will I be able to run any mods?

Thanks in advance!

---

### Post by crispy_420 on 2007-05-14
Sounds like anything originally based Half-Life series. After all they are just mods of the original game and use the same technology. So it looks like all should apply. But I don't know if SiN will, not to familiar with it or it's engine. Life would be easier if Steam came out with a linux version but I don't think that will ever happen.

I suggest looking at the gaming forums here to get a hands on experience opinion.

---

### Post by zPacKRat on 2007-05-14
FYI if your running an ATI card you will have a much harder time getting source based games to run. On 7.04 with WINE 9.33 installed via the WINE apt repository I could only get source games to run in a 1024 x 768 window on a 1680 x 1050 widescreen monitor and it was not stable. This was on a AN8-SLi with a opteron 165 and 2 gigs of memory and an x1800xt video card with 512 megs of ram. Also alot of the advanced video settings were unavailable. I'm not sure if this gets better with a Nvida based video card or not. 

Good luck and please post your results if you don't get it to run.
z:guitar:

---

### Post by Hobo Joe on 2007-05-14
Ok, I got it running, and the first thing I downloaded was half life, becuase it was smallest.

First impressions: It works, but there are definitely problems.
1. I can't change my resolution.
2. Even when it's in fullscreen mode, it's not fullscreen, it's in a 'window' but it doesn't have borders.
3. When I start a game, I can look around, but once a press a key, it locks up, and I can't move or look around or anything. But I CAN press esc and get back to the menu.

I'll keep trying to get it running though.

EDIT:

I tried manually changing the resolution from the launch option to 1152X864 but it still remains at it's unknown but small resolution...

---

### Post by B. Gates on 2007-05-14
I suppose the obvious question is ask whether your drivers are all up to date.

My experiences when running HL with Wine were reasonable, except for the fact there was a half-second delay between a sound event and hearing the actual sound. You'd fire a gun, see the muzzle flash and recoil, but the gunshot would be played a short moment later. It wasn't a critical thing, but it works perfectly in Windows, so...

---

### Post by paparappa on 2007-05-15
Well how does Counter Strike 1.6 work through wine? Anyone tried it or is it the same problems as it is with half.life?

**Edit:** Now i tried Counter Strike 1.6 thorugh steam on my ubuntu. Works perfectly to me :)

---

### Post by ebichu on 2007-05-15
I just tried CS 1.6, and i got like average 40 or so fps in windowed mode.
CPU 2.6Ghz, 256 MB of Ram and ATI Radeon 9200 SE (haha). Using opensource drivers or smthing, runs well. ^^

---

### Post by paparappa on 2007-05-15
Ok this is quite embarrassing. I started steam when it was installed but then i shut down.. Now i want to start it again and i dont know how :P What should i write in the terminal?

---

### Post by ebichu on 2007-05-15
cd to steam dir, and then wine steam.exe

---

### Post by paparappa on 2007-05-15
**Edit:** Sorry, missed the Sudo part :P

However i still get an error though it looks like this now:
```
fixme:msi:MSI_OpenDatabaseW open failed r = 80030050!
```

**Edit:** Sorry, again!

I just wrote the thing totally wrong, it works perfectly now :)

---

### Post by Hobo Joe on 2007-05-15
Ok, I finally got HL to work. I actually have no idea what I did....

But I'm still unable to change the resolution though. I've already tried changing it through the launch options, but it didn't work. The only thing I can think of is going to the .cfg file to change it. But I don't know the directory that WINE saves it to. Can anyone tell me that?

I'm dowloading HL2 now, I'll post the results once it's done.

---

### Post by bastiegast on 2007-05-15
In theory half life, half life2, CS 1.6, CS source should work pretty close to perfectly. 

For me they work perfectly most of the time. Including resolution changing although I don't test that much since I usually play at 1280 * 1024.

HL episode one works fine just like HL2 but HDR(which makes the game look REALLY shiny) has some glitches. If I enable it the lightning is usually too dark and it seems to periodically get brighter and darker sometimes, like a cloud moves pas the sun.

Still I played the entire first two chapters with HDR enabled, I started suspecting the game was too dark in the third chapter were I almost constantly had to use my flashlight. 
So in HDR makes the game still look very nice but has some glitches which eventually made me turn it off.

---

### Post by Hobo Joe on 2007-05-15
> **bastiegast said:**
> 
If I enable it the lightning is usually too dark and it seems to periodically get brighter and darker sometimes, like a cloud moves pas the sun.

Well, that's what HDR does. :popcorn: 


It's supposed to simulate how your eyes would normally adjust to change in how bright things are.

---

### Post by Hobo Joe on 2007-05-15
Ok, I downloaded HL2 and tried it out.

First impressions: meh.

Well, first, it tried to give me a widescreen resolution becuase i'm running dual monitors. I tried out a few things, but in the end, I had to just turn off one of the monitors in my settings.
When I finally DID get it to run at a normal (4:3 AR) resolution, the highest it would let me go is 1152X864. I suppose this is ok... At the resolution, on all full settings, I was getting 25-70 FPS. I was really hoping to get more with my 8800 GTS...
Another thing is that the intro vid is all messed up, like it runs really slow. I mean REALLY slow, it takes about 2 minutes for it to play.
And the last thing is, when I tried to close the game the whole computer froze, and I couldn't even alt+ctrl+backspace out of it. I had to do a hard reboot.

---

### Post by scotty2hott2k on 2007-05-15
you have have aa or ansitropic filtering on (or hdr) turn it off and you should get much better frame rates.

---

### Post by Hobo Joe on 2007-05-15
Yeah, I know that, I'm just dissapointed that WINE doesn't get more out of my card, becuase I know my card is really good.

I tried it again, this time it didn't freeze when I shut it down.

---

### Post by bastiegast on 2007-05-15
> **Hobo Joe said:**
> Well, that's what HDR does. :popcorn: 


It's supposed to simulate how your eyes would normally adjust to change in how bright things are.

Yeah I know what HDR does ;) but I compared it too screenshots of HL2 epp 1 running in windows. And the brightness changes are very large ranging from almost complete darkness to overbright and also just when looking steadily at a light source it seems like someone is turning a dimmer.

Intro video plays sometimes very slow and sometimes at full speed for me (I use to tinker my settings a lot and upgrade as  soon as a new update is available so it might be related to that). Just add -novid to launch options.
About your fps, I feel your pain but 25 fps is about all your eyes can see so that shouldn't matter too much.

---

### Post by Hobo Joe on 2007-05-15
Tried Lost Coast.

It didn't go all that well. There was no HDR option(the menu was greyed-out), the reflections were all goofed up. The water wasn't 'rippling', it was just a reflection 'map' that was slowly moving in one direction. There was no walkbob, and it froze up when I tried to quit.

---

### Post by Hobo Joe on 2007-05-15
Ok, I have a stupid question about WINE:

How do I install separate apps through wine? For example, if I were to install another game, would I just put the CD in and then say 'wine /media/cdrom0/install.exe'? Or do I have to make a separate install for every app? Becuase I tried to install WC3 and it went really badly...

---

### Post by bastiegast on 2007-05-15
> **Hobo Joe said:**
> Tried Lost Coast.

It didn't go all that well. There was no HDR option(the menu was greyed-out), the reflections were all goofed up. The water wasn't 'rippling', it was just a reflection 'map' that was slowly moving in one direction. There was no walkbob, and it froze up when I tried to quit.

That shouldn't happen and makes me wonder if you even have the latest wine version which is 0.9.37 (issue wine --version).

If you have the latest version and the problems are still there, type regedit in a command line, go to HKEY_CURRENT_USER\Software\Wine\Direct3D and add a new string value: UseGLSL and give it the value "enabled"*(you need to add the key Direct3D if it's not there already). See if that helps.

Also are you using an ATI card? If so that might be the source of your problems, I have no experience with ATI cards in linux but I hear lots of people are having problems with them.

---

### Post by bastiegast on 2007-05-15
In theory you don't need a separate install for every app, you can just install them on the same fake C drive like you wuld in windows. If you want a clean install you can remove the .wine directory. Warning: this will remove all your wine programs. You can also have different fake c drives for wine at the same time if you want to isolate apps and settings, you can specify another location for the wine directory by setting the WINEPREFIX enviroment variable: export WINEPREFIX=/path/to/wine then create the directory by executing wineprefixcreate

---

### Post by Hobo Joe on 2007-05-15
> **bastiegast said:**
> That shouldn't happen and makes me wonder if you even have the latest wine version which is 0.9.37 (issue wine --version).

If you have the latest version and the problems are still there, type regedit in a command line, go to HKEY_CURRENT_USER\Software\Wine\Direct3D and add a new string value: UseGLSL and give it the value "enabled"*(you need to add the key Direct3D if it's not there already). See if that helps.

Also are you using an ATI card? If so that might be the source of your problems, I have no experience with ATI cards in linux but I hear lots of people are having problems with them.

Yes, I have 0.9.37.

I have basically no experience editing registry though, so if you could perhaps walk me through it....
Under wine there is no Direct3D folder.

I have an nVidia 8800 GTS.

---

### Post by bastiegast on 2007-05-15
Ok editing the registry is pretty easy, I assume you already navigated to HKEY_CURRENT_USER\Software\Wine\, If the Direct3D key isn't there, create it by right clicking the wine folder icon and clicking "add key", now type Direct3d and hit enter. Click on your fresh key and right click in the empty field on the right, in the popup menu go to new > String value (I think it's called string value, my install is dutch so im not sure look for something similair, a string is an array of characters). Call the string value UseGLSL hit enter right click your new String value and click edit, type "enabled" (without quotes) and hit enter and exit the registry. Fire up steam :) 
I go to sleep now so I hope you get it right.

Edit: rereading your post, maybe you misunderstood me,  HKEY_CURRENT_USER\Software\Wine\ is not a folder. You have to run regedit: Open a command line type regedit and hit enter, from there you will see what I mean.

---

### Post by Hobo Joe on 2007-05-15
Well, I didn't really notice any difference...

But the issue I want to fix the most is how I can get it to just run in one of my monitors without having to turn the other one off... Because otherwise it wants to run it at a widescreenres.

---

### Post by Jovec on 2007-05-15
> **Hobo Joe said:**
> Well, I didn't really notice any difference...

But the issue I want to fix the most is how I can get it to just run in one of my monitors without having to turn the other one off... Because otherwise it wants to run it at a widescreenres.

What make is your video card and what method are you using for dual monitor display?

Nvidia's twinview, for example, treats both monitors as a single display and there is no way to display a fullscreen app on just on monitor while have the second monitor in use.  You need to use a windowed mode, or implement a metamode in your xorg.conf with an entry like "1280x1024, NULL" to disable the second monitor when the game is running.  Dual X screens will work too, but those have other issues.

---

### Post by topsites on 2007-05-16
Forget it, I switched to Linux to get away from the script kiddies and all the rest of the punks who think they own the Internet.
Wine is for people who want a little cheese with it.

Leave windows alone, don't look back, there be dragons.
It hurts one time, and you're done.

---

### Post by Macca86 on 2007-12-19
steam just fully locks up and freezes on me. All my drivers are up to date. I installed "Gecko" but im not sure if it's on properly, if not that may be the problem. Is there anyway I can check?

---

### Post by Beren Camlost on 2007-12-19
> **Macca86 said:**
> steam just fully locks up and freezes on me. All my drivers are up to date. I installed "Gecko" but im not sure if it's on properly, if not that may be the problem. Is there anyway I can check?

Do this in a terminal:

```
wine iexplore http://www.winehq.org
```If Gecko is not properly installed it will prompt you with the steps needed to do so.

---

