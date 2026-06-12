---
title: "Guild Wars: Music Plays, No Game Window"
date: 2007-07-10
forum: Wine
---

### Post by dorath on 2007-07-10
Here's an odd one for y'all.  And first things first: *GW was running fine up until around a week or so ago* (with or without CompizFusion on).

I've been watching for a few days hoping that somebody else would post about it, and that it wasn't just me. ;)

Here's the problem: when I start up GW all I get is the music in the background.  No game window opens.  The process will run merrily along until I kill it.

I've tried a number of different flags (-dx8, etc) in lots of different combinations, but the result is always the same:  sound but no window.  Tweaked stuff in winecfg, same story.  Compiz stuff on or off, and even the same result with Compiz completely removed.  Removed WINE 0.9.39, installed 0.9.40, same thing (I haven't tried going backto 0.9.38, but it *was* working in 0.9.39).  I can't for the life of me think of anything I installed around that time that would have mucked things up.  I've been keeping an eye on the appdb to see if anyone has posted there, but so far nothing.

Thoughts?
Suggestions?
Solutions?  ;-)

Any and all would be appriciated!

EDIT:
If you'd like to know any configuration type questions, please don't hesitate to ask.  Might take me a bit to figure out how to get the info, but I'll do my best.

---

### Post by Seraed on 2007-07-10
I haven't played for about a week, and today I saw that it was updating. Ta-da! It broke. It tells me that my Video Card is unsupported and the game freezes when I try to continue. The option to turn sound off worked for me though as that has been the only way I could play (it would freeze with sound on).

I'm definitely thinking it was the update to GW.

---

### Post by dorath on 2007-07-10
Hmm.   I'm not getting any error messages.  It just patches, the patch window goes away, and a second later I hear the background music.

Based on your experience though, I tried running with the -nosound flag and unfortunately got the same result (just without sound).

Tried using regedit to get rid of the registry keys, but sadly that didn't help either.  Same result.

---

### Post by Seraed on 2007-07-10
Funny, I tried *enabling* sound to see if that would make a change with mine :P

No luck though, still freezing.

---

### Post by dorath on 2007-07-14
At wits end, I finally removed Gw.dat, Gw.exe, and Gw.tmp from the \Guild Wars\ directory and reinstalled.  I'm short a whole lot of files, but I've got my graphics back again.

Definately better than nuthin'  :)

---

### Post by RuB3N on 2007-10-09
Does no one know how to fix it??

because it would be greatly appriciated if they did!!

---

### Post by aznanimedude on 2008-05-27
interesting
i just installed ubuntu hardy heron on this new computer
installed wine, then installed Guild Wars.
same thing, music comes on, but i can't see a game window, so apparently i'm not the only one who got this problem
but seeing as how noone has posted here in ahwile, can i assume you guys figured it out? what did you do then, since i can't for the life of me think of what's going wrong

---

### Post by Verily on 2008-06-12
Well I dunno if it'll help anyone, but I did the same thing dorath did (deleted the stuff in the Guild Wars folder on drive_c in wine and then reinstalled) and ... my graphics seem to be back as well.  Though I'm not really sure what fixed it.

I did also start running it in a virtual desktop instead of fullscreening, since I prefer to have it not-fullscreened anyway, but I don't know if that made a difference or not.

---

### Post by Ignotser on 2008-07-02
Bump

---

### Post by gamgee911 on 2008-10-13
bump

I'm getting the same issue

---

### Post by greatwolf on 2008-11-03
See, this is exactly why linux will never be mainstream. Because crap like this springs up and there's never really a satisfactory resolution.

Anyway, I just encountered this same exact problem. It happened for me when I put it into window mode alt-enter. Following it I switched from desktop 1 to desktop 2 and then back again, the guild wars window would disappear. Following attempts to start gw yields the same results as you guys have already described.

I think it has something to do with wine not liking gw in window mode and just losing its focus. I suspect gw saves what window size to start with somewhere in gw.dat. So I'm going to boot back into windows, start gw from there, make it fullscreen and see if that fixes it in ubuntu.

---

### Post by Trap3d on 2008-11-03
cant u ppl read heres ur solution read trough all the posts and then paste that you need a frigiin solution :mad:
> **dorath said:**
> At wits end, I finally removed Gw.dat, Gw.exe, and Gw.tmp from the \Guild Wars\ directory and reinstalled.  I'm short a whole lot of files, but I've got my graphics back again.

Definately better than nuthin'  :)

---

### Post by greatwolf on 2008-11-03
> **Trap3d said:**
> cant u ppl read heres ur solution read trough all the posts and then paste that you need a frigiin solution :mad:

> **greatwolf said:**
> See, this is exactly why linux will never be mainstream. Because crap like this springs up and there's never really a satisfactory resolution.


Reinstalling 3-4gigs worth of files just because ubuntu & wine doesn't know how to get back a minimized window is not what I would call a satisfactory resolution. That's like reinstalling the whole operating system just to reset firefox back to its default settings.

Anyway, for those that are still looking for a solution to this problem read on. There IS a much simpler way to fix this. Boot into Windows XP and start gw.exe from there. Once the client is running just maximize with alt-enter or right-click->maximize from the taskbar. Once maximized close the client; you don't even need to login. Reboot back into linux and start it up. It should work normally now.

So everyone has a choice, you can either just delete everything and start from scratch -- redownloading all 3-4gigs worth of it (not really a solution at all if you ask me) or you can fix it by booting into windows. See? windows is good for something.

---

### Post by Trap3d on 2008-11-04
> **greatwolf said:**
> Reinstalling 3-4gigs worth of files just because ubuntu & wine doesn't know how to get back a minimized window is not what I would call a satisfactory resolution. That's like reinstalling the whole operating system just to reset firefox back to its default settings.

Anyway, for those that are still looking for a solution to this problem read on. There IS a much simpler way to fix this. Boot into Windows XP and start gw.exe from there. Once the client is running just maximize with alt-enter or right-click->maximize from the taskbar. Once maximized close the client; you don't even need to login. Reboot back into linux and start it up. It should work normally now.

So everyone has a choice, you can either just delete everything and start from scratch -- redownloading all 3-4gigs worth of it (not really a solution at all if you ask me) or you can fix it by booting into windows. See? windows is good for something.
firstly now every 1 has xp or any other dual boot second if 3-4 gigs reinstall wich takes up about max 10 mins is like reinstalling whole system i sugest you upgrade your pc... and yes its max 10 mins i know i installed wow tbc + patches up to 2.4.2 in 5 mins that was about 8 gig so stfu plus not everyone need to redownload it plus redownloading wow isnt much for me it took me 3 hrs to do it and if thats much i dont know... i just left it on trought the night

---

### Post by greatwolf on 2008-11-04
No point arguing with a troll. Those of you who need a solution here it is. Hope you find it useful.

---

### Post by ironstorm on 2008-11-09
This has recently happened to me...  

I've been trying to figure out what happened that caused it, so far I'm thinking it may have to do with having two copies of GW.exe both messing with GW.dat at the same time...   I'll play around a bit, and if that turns out to be the reason why I'll do a script to stop double starts.

---

### Post by ironstorm on 2009-02-14
I think I have found a potential solution to prevent this problem from occurring.  It doesn't work if your copy is already messed up (in that case you'll have to either replace Gw.dat with a working backup or delete it and re-download).

Working with copy of Guild Wars that isn't messed up yet:
[LIST=1]
[*]Go into winecfg (Wine -> Configure Wine)
[*]Click "Add Application"
[*]choose Gw.exe from where ever it is installed. 
[*]Next go into the "Graphics" tab, check "Emulate Virtual Desktop", and put 800x600 as the resolution.
[/LIST]

This will cause Guild Wars to run inside a Wine Desktop window, minimizing and spinning the compiz desktop cube will not cause this window to disappear.  You can change the resolution by using the graphics options menu inside Guild Wars.   

I only run Guild Wars as a window, so this may not work for fullscreen.

Cheers,

-G

---

### Post by uns3r on 2009-03-03
my guild wars is messed up
it loads and everything but very slowly and the worst problem of them is that it is upside down

---

