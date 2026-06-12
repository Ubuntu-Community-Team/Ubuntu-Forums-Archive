---
title: "Carmageddon 2 Glide on Wine (Guide of sort)"
date: 2008-07-08
forum: Wine
---

### Post by TheCoach on 2008-07-08
Carmageddon 2 is a great game that I still love to this day. I managed to get a re-release of original cd too!
So now that I have installed my Hardy I decided to give the game a go.

Ofcourse it was a failure at first as this game refuses to detect any kind of rendering mode that wine offers it.

Then i thought oh why not just try zeckensack's glide wrapper.
[http://www.zeckensack.de/glide/](http://www.zeckensack.de/glide/)
After installing the wrapper on Wine, Carma 2 finds glide mode and runs VERY VERY smoothly. Actualy even smoother than it did on W******! And it runs in high resolution mode too.(you have to set it trough glide config)
This might also help other guys who have troubles runing old games that have glide rendering option as zecken wrapper seems to be 100% compatible with wine.

Now for you people who still have this game i'd recommend reinstalling it and getting some of the many many addon cars and tracks made for it on these sites:

[Best of Mac Carpocalypse]("http://coffey.polygonized.com/")
[C.R.U.D.]("http://crud.toshiba-3.com/")
[Wasted]("http://carma.jjunkies.com/")
[TTR's Garage]("http://ttr.toshiba-3.com/")

Have fun!

I'm using Wine 1.1.0 and i have Ati driver version 8.6 installed.

---

### Post by sledgeas on 2009-03-02
Hi,

Did you try the multiplayer?

Cheers!
-- 
sledge

---

### Post by juamez. on 2009-03-15
I just tested it, and while Carmageddon 2 is fluent while in lowres software modus, it is hardly playable in Direct3D modus (5 to 10fps).

But now with that Glide Wrapper I get the software framerate combined with the D3D graphic beauty (even better I'd say), woop!

Conclusion: with zeckensack's glide wrapper fully playable with no penalties at all.

---

### Post by Dieter@be on 2009-04-12
Good to hear you got it working.
When I start the game, I pick settings and then click 'launch' I get "Carmageddon Fatal Error: Couldn't open General Settings file"

I tried installing the glidewrapper, I tried direct3d, glide and software, all give the same problem.  (but I don't think it's somewhere with the settings/graphics, it seems like it cannot access some file it needs).  I installed wine and carmageddon 2 "fresh".

Anyone an idea?

Edit: woohoo got it working too. apparently I needed a no-cd patch..
It doesn't save the game though :(

---

### Post by juamez. on 2009-04-17
I use the no-cd patch, but that was not enough to keep me from getting the same problem as yours.

To solve the problem, I first change my working dir in the shell to the carmageddon dir, and in that dir I launch the game with the wine carma2.exe command. To not have to go into the shell everytime I want to play carmageddon 2, I made a bash script that does all that. This scripts is called when I click the shortcut I made myself in the Applications - Games menu of Ubuntu.

---

### Post by Arcnsparc on 2009-05-26
I can get it to install (the game, directx, but not quicktime) but it crashes before anything happens when I try and run it...  Does anyone know where a guide or trouble shoot for installing is for this game?

---

### Post by asdfoo on 2009-05-26
> **Arcnsparc said:**
> I can get it to install (the game, directx, but not quicktime) but it crashes before anything happens when I try and run it...  Does anyone know where a guide or trouble shoot for installing is for this game?

don't install directx, read the guide in the original post which says to install the glide wrapper.

---

### Post by redwaldmcmanus on 2009-07-07
Where did you get the no-cd patch? I'm struggling to find it.
Cheers

---

### Post by Th3_uN1Qu3 on 2009-07-07
Uh, is it THAT hard to GOOGLE? First hit was the right file. "carmageddon 2 no cd"

---

### Post by afrodeity on 2010-07-10
No sound, sound server keeps quitting if I open volume control. Oh dear.

---

### Post by afrodeity on 2010-07-10
Crikey now the sound is working fabulously. Must be gremlins from the future realising abandonware is all we have left in Africa. Yay for Ubuntu. Must be I turned on NAS in the WINE settings.

PS: Is there a trick to getting it to play the right size in a window? I have a virtual desktop set at 1200 x 800 but it still very small. If I set it to full desktop I get monitor weirdness and my mouse not getting grabbed properly.

UPDATE: Okay, here's the problem. I have sound in the intro but not during the game. Also I can only use my mouse in DirectD but not Glide.

---

### Post by JonasDK on 2010-11-14
Hello everyone

I am trying to make Carmageddon 2 work on Wine. I installed the game and the Glidewrapper. The launcher complained about the 3DFX Glide not being OK but it is OK now! So the Glidewrapper works. But I get an error message saying that 'Windows NT is not supported'. How do I fix this?

Thanks!
A nostalgic gamer.


EDIT: I got it working, but no sound either!

---

### Post by Ranko Kohime on 2010-11-15
I'm running here, but no sound at any point.  Frame rate is kinda bad all around, but then I'm running on my EeePC, with a 900MHz (in theory) Celeron...  But then, it ran faster on the 400MHz Celeron I used to run it on.  :confused:

---

### Post by JonasDK on 2010-11-16
> **Ranko Kohime said:**
> I'm running here, but no sound at any point.  Frame rate is kinda bad all around, but then I'm running on my EeePC, with a 900MHz (in theory) Celeron...  But then, it ran faster on the 400MHz Celeron I used to run it on.  :confused:
I fixed my sound by selecting the OSS driver in the Wine preferences.
Everything works now.
Enjoy!

---

### Post by Ranko Kohime on 2010-11-16
> **JonasDK said:**
> I fixed my sound by selecting the OSS driver in the Wine preferences.
Everything works now.
Enjoy!
Cool, I'm getting sound now.  Was it really that horrible?  :lolflag:

I just noticed, though, that it isn't saving my game, bummer.  :confused:

---

### Post by JonasDK on 2010-11-17
> **Ranko Kohime said:**
> Cool, I'm getting sound now.  Was it really that horrible?  :lolflag:

I just noticed, though, that it isn't saving my game, bummer.  :confused:

Seems like you are having all the same problems as I have had! 
Saving works! You just aren't loading the saves. Go to menu and click on Load game, your saves will be there. You can go to settings and select 'Auto Load ON' and everything will be ok.
The only sad thing is that the resolution is quite low. I just change my Ubuntu-resolution to something like 1024x768 and the Carmageddon window will be a bit larger.

This game is too awesome. :cool:

---

### Post by Ranko Kohime on 2010-11-18
> **JonasDK said:**
> Seems like you are having all the same problems as I have had! 
Saving works! You just aren't loading the saves. Go to menu and click on Load game, your saves will be there. You can go to settings and select 'Auto Load ON' and everything will be ok.
The only sad thing is that the resolution is quite low. I just change my Ubuntu-resolution to something like 1024x768 and the Carmageddon window will be a bit larger.

This game is too awesome. :cool:
Now I feel stupid.  :mrgreen:

Anyway, Carmageddon is forcing my 800x480 display into 640x480, which actually works.  Just widescreen enough to look good, without it looking too stretched.

It also works the same on my Mac (slowly, framerate around 15fps or so)

---

### Post by handy on 2010-11-19
Apparently there is a Windows program called dgVoodoo which you can use to change the resolution of Carma2.

I don't know if it works under Wine, but it does do the job on Windows.


Here is the dgVoodoo site:

[http://dege.freeweb.hu/](http://dege.freeweb.hu/)

[I][B]
[edit:][/B] I just had a look on the WineHQ database & I see that dgVoodoo is recommended for a number of games, so at least I now know that it works with Wine. 

Perhaps there is a slim chance that it may possibly allow you to have higher screen res' than the Glide wrapper you are currently using?[/I]

---

### Post by handy on 2010-11-21
Firstly, I have to own up to using the FOSS Radeon driver stack for my HD2600Pro GPU; so I have any additional problems that, that lot may bring...

I got hold of a copy of Carma2 & I just installed it, added the NoCD patch & then played around firstly with the dgVoodoo package. I could get the first screen & then the 2nd, where my mouse movement was severely limited (I'm using a 24" mon' with 1920x1600 pixels) I could choose the Viper (from memory) & then I got the next screen where the mouse limitations stopped me. I tried different Wine window sizes but it was no help.

So I removed dvVoodoo & installed the GlideWrapper, told it I was using Carma2, & gave it a whirl. No go. After the launcher window it tries to load the next screen for a 3-4 seconds & then closes itself. 

I tried a range of window sizes in Wine, but still nothing. I blame this on the driver stack I'm using. The errors in the terminal & the little error window that comes up to tell me *"BRender error detected. Failure: Unable to allocate Main Front Screen."*

This is the error message printed to the terminal, there is one of the last line for each of a range of screen resolutions & colour depths:

```
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1739f0,0x173338): stub
err:winediag:X11DRV_WineGL_InitOpenglInfo The Mesa OpenGL driver is using software rendering, most likely your OpenGL drivers haven't been installed correctly
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 320x200x16 @59! (XRandR)
```


I'm using -git packages & a Radeon patched kernel .37, on Arch, so I guess I'll give Carma another whirl after each update until the glorious day when I can get back on the roads of mayhem & go splat! :)

---

### Post by afrodeity on 2010-12-05
Still small box with no sound. Have OSS box clicked, have tried nGlide and dgVoodoo

---

### Post by kabrita on 2011-06-22
I just registered with the brand name from my goats yoghurt in a desperate attempt to get some more info or feedback or ideas or whatever on how to get this running.

Let's start at the beginning and go from there..

* running puppy linux 4.3.1, wine 1.1.29, screen resolution at 1280x1024
* got carma2 unpacked in /path/carma2/
* same for nocd
* got GlideWrapper in its own folder in carma2 folder
* used the configurator.exe found in the GlideWrapper folder to tell her that I want to play Carmageddon2, and tinkered with different settings that seemed logical to me at different times
* cd to /path/carma2
* then wine carma2.exe
* got the BRender error described on page 2 of this thread. carma2 looking for screen resolutions no higher than 400x300x24
* carma2_SW.exe crashes after it gives me false hope by showing me the menu with sound and full mouse control. *'Unable to setup DirectDraw - please check that DirectX is enabled'*
* carma2_HW.exe does the same as carma2.exe
* got dgvoodoo unpacked in the carma2 folder, not its own
* run dgvoodoosetup.exe, get to the box that says: settings are valid from dgvoodoo: select glide2x.dll from the carma2 folder, leave the glide- and global settings as they are
* again cd to /path/carma2, and wine carma2.exe
* this changes my resolution to something BIG, presumably 400x300 and I have to ctrl-alt-backspace out and restart x
* carma2_HW does the same,
* carma2_SW does the same as before (DirectX error)

Any suggestions on what I'm missing? :confused:

---

### Post by handy on 2011-06-22
> **kabrita said:**
> 
...
Any suggestions on what I'm missing? :confused:

Probably just Windows/DOS.

Sorry I couldn't resist. :)

I couldn't get it to work on my machine either, unfortunately.

Welcome to the forum by the way.

---

### Post by chib on 2011-07-18
I'm also having issues getting this game working correctly.  Here is my findings so far;

I had the bug where my mouse is restricted to the resolution of the original game (640x480?), I also had no sound excluding the animation when started.

Tinkering with Zeckensack's glide wrapper (.84c) I could get up to half my screen working but that was it.

I then managed to find a different glide wrapper called 'nGlide 0.96' (from 2010),  this version has fewer settings but if I set the resolution to 1920*1200 (along with setting my monitor to that res) then I can get the game to run with full mouse movement.  However this bring with it new issues,  1) The upper and lower panels are visible over the game.  2) Running at such a high resolution drastically reduces the framerate.  3) Trying any other resolution and the game fails to start or runs but the mouse issue is back.

I then found a site that claims patching the game to version 2 solves the mouse bug.  Once patched however I get the error "couldn't open general settings file".

As for the audio issue, I tried using the OSS Driver as suggested to no prevail.  Using the EsounD driver gives me full sound... that lags.

I've been trying to get this working for over 2 hours now,  I'm gonna leave it here hoping someone with a better understanding of Glide and Carma (and linux on a whole :P) will be able to help out.

I found all the patches as well as 'nGlide' here: [http://rr2000.toshiba-3.com/R4/PC.htm#c2]("http://rr2000.toshiba-3.com/R4/PC.htm#c2")

---

### Post by ThatGrrl on 2012-05-05
I love Carmageddon. I still have my original CD for 2000 and the version that came out next but never played very well. 

I've got Windows back for a short time. Bought  a new computer and had trouble getting Ubuntu installed on it. But, for now Carmageddon works - no sound once the game starts and it randomly crashes. Suddenly the game starts to give me close ups and then far away shots and then it freezes on a long, long pull away. It may be a QuickTime thing because that's the only thing missing when I reninstalled it. 

I haven't tried Wine for anything yet. I will load it up once I get Ubuntu figured out on this PC. I never had a problem installing Ubuntu before. I hope Carmageddon runs smoothly for me. I've missed that game more than any others.

---

