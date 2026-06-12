---
title: "Dreamfall on cedega"
date: 2006-07-17
forum: Wine
---

### Post by oedipuss on 2006-07-17
Has anyone tried to play Dreamfall : the Longest Journey on cedega?

With the latest cedega version the game runs, but there are some glitches that can be annoying..

First of all, there's a ~1cm border on the top and left of the screen where the 3d graphics get bugged. The cursor and menus however are rendered correctly. 
Also, shader effects (such as distortion over a flame, to emulate heat) are displayed even when they should be obstructed by walls etc, so random places on the screen get distorted for no apparent reason.

[IMG]http://i31.photobucket.com/albums/c384/ydralisk/09320bb0.jpg[/IMG]
The distortion in the two circles is caused by two torches behind the wall.

 I was wondering if anyone has found a way to correct these glitches. 
 I've already tried various settings, with no results.

PS: they don't look that bad in the screenshot, but animated they can be rather distracting.

---

### Post by oedipuss on 2006-07-19
No one has tried this game on cedega? 

Oh I forgot to mention that in order for it to run I had to copy d3dx9_27.dll and dbghelp.dll from winxp to cedega's fake windows directory. Also, all this was on a NVIDIA card, with the latest drivers installed.

Its a pity, the game would be perfect if not for these problems whith the shaders.

---

### Post by doomstone on 2006-07-25
I'm trying to get it to run on the newest Cedega. but it jsut won't start. i do not get any error messages at all

---

### Post by doomstone on 2006-07-25
i copyed the 2 files "d3dx9_27.dll and dbghelp.dll" and now can i get the protecter to start, but how did you get past the protecter? mine keeps saying that my system do not meed the req

---

### Post by kahping on 2006-07-26
I tried with Wine 0.9.17 but only copied 'd3dx9_27.dll'. The game just spews out a whole bunch of error messages to console. There wasn't any clues to suggest copying 'dbghelp.dll' as well (at least i didn't notice any).

I guess i'll give it another go when i have time. Hopefully, it works. I'm a fan of the original game :)

---

### Post by doomstone on 2006-07-26
Dam i have been looking for a way to get it to worke on linux for 2 days now :(
I hace come so far that a crack must be the way forward, but i can not get any of them to worke. do any of you know a crack there workes?

---

### Post by kahping on 2006-07-27
> **doomstone said:**
> Dam i have been looking for a way to get it to worke on linux for 2 days now :(
I hace come so far that a crack must be the way forward, but i can not get any of them to worke. do any of you know a crack there workes?

Search MegaGames if you haven't already...

I too haven't managed to get Dreamfall to run. I guess Cedega's the only way to go with this game for now :-(

---

### Post by kahping on 2006-08-12
*bump*

Just an update on the situation. Dreamfall can be made to run with Wine 0.9.19 and a cracked .exe (to remove StarForce) :) 

But it's running very slow, has lots of graphical glitches and tends to lock up within minutes of running (at least on my machine) ](*,)

---

### Post by patrick295767 on 2006-08-12
> **kahping said:**
> *bump*

Just an update on the situation. Dreamfall can be made to run with Wine 0.9.19 and a cracked .exe (to remove StarForce) :) 

But it's running very slow, has lots of graphical glitches and tends to lock up within minutes of running (at least on my machine) ](*,)

I am using wine for gaming... And I have the impression that cedega is the only way for gaming wiht recent games. 

Pitty that you'd have to pay monthly
 
 Wine is okay for oldies.

---

### Post by Roasted on 2006-08-12
What do you mean wine is okay for oldies? Is Wine's support for growing games coming to a halt or something?

---

### Post by kahping on 2006-08-12
Sorry about my previous post. There's a mistake in there. I had the highly experimental UseGLSL registry key enabled so that got in the way of my tests.

I'm happy to report that Dreamfall runs fine and smooth on Dapper with Wine 0.9.19 =D> 

There's only some minor glitches:
[LIST=1]
[*]white box @ top left corner whenever there's subtitles or menus on-screen
[*]occasional game stutters (including sound stutters)
[*]horizontal black band in main menu (this disappears in seconds and isn't present when playing :wink: )
[/LIST]

> **Roasted said:**
> What do you mean wine is okay for oldies? Is Wine's support for growing games coming to a halt or something?

Not that i'm aware of. But Wine is more general purpose than Cedega. Cedega mainly focuses on getting games to run, so it gives you a better chance of playing that new game now.

Wine isn't focused on games only. It tries to support (almost) every Windows software (games, Office, Lotus Notes, etc...). Because of this, it tends to not be able to run that new game but don't jump to conclusions before trying. 

[QUOTE=patrick295767]I am using wine for gaming... And I have the impression that cedega is the only way for gaming wiht recent games.

Pitty that you'd have to pay monthly

Wine is okay for oldies.[/QUOTE]

How true :( 

And the fact that i have trouble with compiling Cedega means more woe for me. It's not true that Cedega's the only way to go.

Wine will never improve in their gaming support if nobody tried to get it running and reported their findings to the Wine developers. Reporting to Cedega improves Cedega. Some of that gets send upstream back to Wine, but that means Wine's seriously gonna be lagging in the game support department.

As an example, take Dreamfall. I reported the bug to the Wine devs and they fixed it in 1 or 2 days. I'm a newbie to compiling from source, so i had to wait for 0.9.19 before testing and now Dreamfall works. All it took was a trivial addition of a few stubs into Wine before it worked.

I bet many new games are like that. They just have 1 or 2 stumbling blocks that prevent Wine from running them.

I think i'll shut up now. I'm starting to get whiny :p

---

### Post by longest_journey on 2006-12-31
Sorry to bump this thread.

I googled on this and I found out that there is the USA 6CD version and the European DVD version.

Which version is the person who got it running under Wine running?

Where is the crack which I need to download for the Starforce version?

Both gamecopyworld and megagames give me:

Failed to initialize Direct3D: Aborting

thanks

Edit: Further googling it appears that my video card is not good enough :(

---

### Post by thetictacaddict on 2008-01-05
I've got the Game of the Year Edition, which comes with both a Longest Journey DVD and a Dreamfall DVD.  I have been trying to get Dreamfall working with both wine and Cedega and I just can't get it to start!  I added d3dx9_27.dll and dbghelp.dll, and I've tried several different exe fixes.  Cedega doesn't do anything visible, and under Wine, the game crashes with a message to send the debug information to Funcom.  I wonder if the Game of the Year Edition needs a different fix, but I can't find any information about it.

---

### Post by kahping on 2008-01-07
Might be a regression. I finished the game long ago when I managed to get it running on Ubuntu. I used Wine 0.9.19 at the time. 

0.9.21 had problems so it's possible that nobody noticed the regression since Longest Journey isn't really the type of game to appeal to an audience as broad as other games like Half Life 2, Supreme Commander, C&C3, etc..

You could refer to [my post]("http://onubuntu.blogspot.com/2006/08/dreamfall-on-ubuntu.html"). I recorded the steps I took along with problems I encountered in case I ever wanted to play again :-D 

No guarantees they'd still work though :-(

---

