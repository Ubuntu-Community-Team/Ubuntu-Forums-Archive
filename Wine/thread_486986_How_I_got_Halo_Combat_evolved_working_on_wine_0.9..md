---
title: "How I got Halo: Combat evolved working on wine 0.9.39"
date: 2007-06-28
forum: Wine
---

### Post by lordhebe on 2007-06-28
In order to help those getting it working, here are the exact steps I followed to get Halo working.

**This guide will also work for Crossover. Halo works following this guide for 6.1 and 6.2. 6.2 sees better performance and the lack of the "window" bug, meaning until the crash on startup regression is fixed Crossover 6.2 is the best way to play Halo.**

**NOTE: Regressions in Wine 0.9.43 prevent Halo from working, use wine 0.9.42, or if all else fails, fall back to 0.9.39. The regression has yet to be fixed. I will do a regression test when I'm able to next, with hoping that this will eventually be fixed.**

**Update: This appears to be fixed with 0.9.52, however there does appear to be an abnormally high amount of memory usage.**


== Step 1: Install wine ==
[LIST=1]
[*]Install wine, following instructions on winehq: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) Remember to run winecfg, and configure your sound drivers. It doesn't matter whether you're set to OSS or ALSA, performance is the same.
[/LIST]

== Step 2: Preparation ==

[LIST=1]
[*](Optional, ignore if installed with add/remove program) FInd a .exe file, for example the setup.exe on your halo cd, right-click it and click properties. Click on Open with, and click add. Click custom command, and type wine. Click add and then close.
[*]Go to [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) , download the file and open it. Then copy the file to your system32 folder in your fake c drive
[/LIST]

== Step 2: Install Halo ==

[LIST=1]
[*]Double click setup.Exe in your halo cd, or run ```
wine /path/to/cdrom/Setup.Exe
``` in a terminal
[*]Follow the install through, it will generate a few errors that can be safely ignored.
[*]At the end of the install do not press Play now, it will not work.
[/LIST]

== Step 3: Necessary settings ==

[LIST=1]
[*]In your Halo folder, run haloupdate.exe to update to the latest version OR download this file and run it: [http://www.softwarepatch.com/games/halo.html]("http://www.softwarepatch.com/games/halo.html")
[*]Copy protection does not work, in order to get the game working, a no-cd crack must be used.
[*]Then right click on the Halo icon on your desktop and click properties. (If it isn't there, make one, using ```
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe"
``` as the command, assuming that's where you installed the game)
[*]Click Launcher, and in the Command box, after the speech marks (at the end) add -novideo. For example ```
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" -novideo
```
[/LIST]

== Step 4: Playing! ==


You should now be able to run the game simply by clicking on the desktop shortcut. But there are some full screen issues. I recommend you run the game in a virtual desktop (configure that by running winecfg). Also make sure that if you run it like that then make sure Halo is set to run in the same resolution as wine's virtual desktop, or vice versa. To force Halo to run at your preferred resolution, add ```
-vidmode w,h,r
``` on the end of your command, the same way as we added the -novideo line. (make sure the -novideo line remains), changing it for you proffered resolution, for example : ```
-vidmode 1024,768,60
```


There are some known issues, these are explained on the appdb. I filed the Gold report that is linked, and another member (The noble) filed the bronze one underneath it. They are with Nvidia and ATI cards respectively. 

Here are a few screenshots of me playing the game:

[http://ubuntuforums.org/attachment.php?attachmentid=35555&d=1182011098](http://ubuntuforums.org/attachment.php?attachmentid=35555&d=1182011098)
[http://ubuntuforums.org/attachment.php?attachmentid=35556&d=1182011098](http://ubuntuforums.org/attachment.php?attachmentid=35556&d=1182011098)
[http://ubuntuforums.org/attachment.php?attachmentid=35557&d=1182011098](http://ubuntuforums.org/attachment.php?attachmentid=35557&d=1182011098)

You can notice a slight visual glitch on the third picture, that is very minor and I personally didn't notice it until after I had taken the picture.

Please note that I do not guarantee that the game will work for you. These are these exact steps that I followed to get the game working in the state that I gave the Gold rating. Please do not sue me if you go out and buy the game and can't get it working, ask here for help and make sure you followed the guide correctly.

It should also be noted that I am only able to run the game by doubleclicking on the desktop icon, running the game via a terminal causes a file missing error.




**TIP:** Well when it comes to a laggy mouse, unfortunately there's no known way to solve it. I do experience the issue, but not enough for me to make a big deal of it, but since other people seem to be having worse cases of the issue I've done some experimenting and found a way to lessen the issue (for me anyway)

First disable Specular in Halo's options, then run regedit and change or create ```
HKEY_CURRENT_USER\Software\Wine\Direct3D\RenderTargetLockMode
```with  the content ```
enabled
```

This improved things, but the problem was still there, but it made the game more playable. Some people may have to lower settings in game to improve this issues. (It seems to be worse when more is on screen, which suggests that people with higher graphics cards would probably have a smoother ride.)



**TIP:** offscreenrenderingmode:

backbuffer (default) Best, no visual glitches, good performance.

pbuffer: Good performance but many visual glitches pictured in an attachment.

fbo: No visual glitches, but bad performance.


I hope this helps those of you who are having problems.

---

### Post by xelnaga666 on 2007-06-28
Wow nice one ;), hows online play? Does the no-cd .exe allow for it?

Ive got halo sitting there on my shelf which hasnt been played for about 2 years hehe. Looking forward to trying it out again on a kubuntu box.

Thanks

---

### Post by The Noble on 2007-06-28
As I have posted in other threads, I am the one who made the bronze report on appdb. I was using an x700 pro from ATI and noticed some problems, which may or may not be related to using the .9.38 release. If anyone happens to use an ATI card and gets halo to work with no visual glitches, please post. I should be able to test 
the latest .9.39 this next week, so I'll report my finding then. 

xelnaga666 asked the valid question on online play. When I used .9.38, I could connect to several servers and scroll through the server pages. I couldn't actually *see* what was happening, but it should work now.

If all is in working order, this will make me really happy to see that Wine has gotten to such a high directx 9 level of compatibility that even an in house game runs great.

---

### Post by lordhebe on 2007-06-29
Yeah sorry noble I credited you in the post. 

Yes I have been able to play online, th game works well, but very few servers show up, although I think this is because of the no-cd crack, not because of a wine issue.

Oh and while the how-to was written for Ubuntu, the process should be very similar for kubuntu and xubuntu. (I'm sorry I have never used xubuntu and have had very little experience of kubuntu)

---

### Post by hikaricore on 2007-06-29
Hopefully this will end the massive wave of halo threads.... lol.

Mad props lordhebe.

---

### Post by Alucard_Duskmoon on 2007-06-29
Installing it right now :D
I'm going to also test it in LAN (With another windows computer) and in online multiplayer modes.

---

### Post by Doug52392 on 2007-07-02
I tried installing Halo, and it installed OK, but I cant play it. :( The installation worked, but when I tried running it with the downloaded Halo.exe program, the computer just freezes. When I restarted the computer and ran it again, I got a dialog that said the program didnt exit correctly and I should run Halo in safe mode. When I clicked safe mode, it still froze. Again i can see the computer at least switches the display resolution to load the game, but nothing comes up. I just see my desktop, which is bigger than normal because the display resolution at least changes. I have a Toshiba Satellite 1905 laptop with 16mb ATI Radeon Mobility M6 graphics card (I know 16mb is low, but the game worked fine in Windows despite the old graphics card) and 256mb RAM. I tried changing some settings using winecfg, and tried several other patches, but none work. Why wont it work for me?

---

### Post by lordhebe on 2007-07-02
Downloaded Halo.exe? Do you mean the no-cd crack or an illegitimate version of the game? Plus try running the game in a terminal and see if you can catch the output. Plus make sure that you have the -novideo flag active. Oh and I have yet to try the game on wine 0.9.40, so there could be some regressions preventing it from working. Try installing 0.9.39.


EDIT: Whoops yes sorry I forgot about the card, yes The noble is right you will not be able to run this game on linux, sorry

---

### Post by Doug52392 on 2007-07-02
I downloaded the NOCD crack, which had the halo.exe program in it (I bought the game legally from a local game store, and used the CD to install it).  In addition to an actual exe program, I saw a Halo mini-image for a NOCD crack. Its an IMG file, but I did not download it. Would that work? I will try to get the output of running Halo via a terminal window (I know alot shows up, but the game freezes before I can do anything)

---

### Post by The Noble on 2007-07-03
> **lordhebe said:**
> Yeah sorry noble I credited you in the post. 

Yes I have been able to play online, th game works well, but very few servers show up, although I think this is because of the no-cd crack, not because of a wine issue.

Oh and while the how-to was written for Ubuntu, the process should be very similar for kubuntu and xubuntu. (I'm sorry I have never used xubuntu and have had very little experience of kubuntu)

There is no need to apologize, I was merely explaining my experience in the matter (thanks for the credit anyhow!). 

Anyways, as I said before, online worked flawlessly for me (sadly the graphics didn't). There we 20 to 30 servers up and running, although I only tried one. And Doug52392, your system is not going to be able to play halo under linux; even though you were able to get it running under windows, the combination of bad drivers from ATI and the added overhead of wine will cripple your system. I suggest at least a 64 MB dedicated graphics card.

Also, I am going to test both .9.39. and .9.40 tomorrow when I get home (in about 16 hours for those of you in a different time zone). I'll report my finding here.

---

### Post by GMU_DodgyHodgy on 2007-07-05
I followed your instructions below for installing Wine.


Step 1: Install wine ==

   1. Install wine, following instructions on winehq: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) Remember to run winecfg, and configure your sound drivers. It doesn't matter whether you're set to OSS or ALSA, performance is the same.


However- when I tried to run winecfg - the terminal window would say it could not create the paths c:\setup or c:\win32, etc.  It appears it did not have authority to install these directories.  Hence I could not install the updated .dll file later on in your tutorial.

How did I screw up mu installation of wine and how can I reverse it and start over??

:(

---

### Post by burt_57 on 2007-07-05
Hey if you ever get Wine working let me know.
I never could get it to play my favorite games.

---

### Post by hikaricore on 2007-07-05
Merged threads.

If you are responding with questions on an recent **EXISTING** guide what purpose does it serve making a new thread?

---

### Post by marq on 2007-07-05
alright, i followed the guide exactly, but i cant seem to get it working, 
if i remove the novideo flag, the videos do run but then when it comes time for the menu, i have a black screen, with choppy sound in the back.

when i run  wine halo.exe i get the following error message

> err:module:import_dll Library ogg.dll (which is needed by L"C:\\windows\\system32\\vorbisfile.dll") not found
err:module:import_dll Library vorbis.dll (which is needed by L"C:\\windows\\system32\\vorbisfile.dll") not found
err:module:import_dll Library vorbisfile.dll (which is needed by L"Z:\\home\\marq\\halo.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\marq\\halo.exe" failed, status c0000135

i tryed installing those libraries to my system32 folder on the fake c drive wine makes, and i still get them

i have a 1.7 ghz processor, 640 megs of ram and i though i had a 16 meg video card (i know the halo says it needs 32 but i tryed anyways....and wine tells me it's 64 meg so it might be) it's an old nvidia card so i shouldent have those ati problems i've been hearing about

it installed wthout any problems and used the nocd patch,  im using the -novideo --vidmode 640,480,60  

i read the appdb and can recognize my problem as bug#7264 but do not understand how to fix it

i dont know what to do, id install windows in dual boot but i dont have a big enough harddrive

anything helps, thanks in advance

---

### Post by lordhebe on 2007-07-05
Hmmm, a 16mb card? I'm guessing that your black screen at the menu is because of insufficient memory available. Oh and I thought wine doesn't detect how much memory your card has, it you have to specify it in regedit, and 64mb was the default. Oh and I getting this right? It ran if you don't have the -novideo command it runs? Try running with -use11

---

### Post by marq on 2007-07-05
it runs the videos without it, but the menu stays the same, i currently have 2  choises, watch the pretty videos then watch a black screen, or watch a black screen lol 
thanks for the tip ill try it

---

### Post by marq on 2007-07-05
i tryed using -use11
suprisingly it still runs with the black screen, but the audio has changed to completely spectacular

im not sure if it matters but my  card is agp, and pretty old, chances are it's a 16 though

edit: would it help to run it from a terminal without gnome and everything?

---

### Post by lordhebe on 2007-07-05
What is the actual card? If it's only got 16 there's a high chance that you won't be able to run Halo, no make that next to zero chance. As a last resort try using the -useff flag. It caused severe graphical glitches for me, but from what I can tell it is for running Halo on pre-pixel shader cards. It might get the game running in a barely playable state.

---

### Post by GMU_DodgyHodgy on 2007-07-05
> **lordhebe said:**
> What is the actual card? If it's only got 16 there's a high chance that you won't be able to run Halo, no make that next to zero chance. As a last resort try using the -useff flag. It caused severe graphical glitches for me, but from what I can tell it is for running Halo on pre-pixel shader cards. It might get the game running in a barely playable state.

Lord Hebe - Can I get your assistance on my problem with WINE installation.  It doesn't install the fake c:\ drive on my machine - complains about permission.

---

### Post by GMU_DodgyHodgy on 2007-07-05
I tried to install Halo in Wine and got the following message:

XXXX@grendel:~$ sudo wine /path/to/cdrom/Setup.Exe
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/XXXXXX', starting in the Windows directory.
wine: cannot find '/path/to/cdrom/Setup.Exe'
XXXX@XXXXX:~$ 

Any ideas on I am doing wrong??

---

### Post by hikaricore on 2007-07-05
This line is not supposed to be taken literally:

```
sudo wine **/path/to/cdrom/Setup.Exe**
```

Also there is no reason to run wine as root with sudo.  This is NOT part of the guide.

**/path/to/cdrom/** need to actually be the PATH to your cdrom drive.. and then **setup.exe**

---

### Post by marq on 2007-07-05
my video card would be 

nVidia Corporation
NVIDIA Vanta/Vanta LT 16 MB 4x AGP
i have a pci video card i can take from another computer (shhh they wont notice =P)
but i have to give up my sound for it

---

### Post by GMU_DodgyHodgy on 2007-07-06
> **hikaricore said:**
> This line is not supposed to be taken literally:

```
sudo wine **/path/to/cdrom/Setup.Exe**
```

Also there is no reason to run wine as root with sudo.  This is NOT part of the guide.

**/path/to/cdrom/** need to actually be the PATH to your cdrom drive.. and then **setup.exe**

Hikarecore - You are right - I actually figured that out last evening on my own.  When I installed WINE I accidentally changed the c:\ drive reference in the winecfg to a root location.  When I took a closer look at the error messages I was getting in the terminal window - I tried to install as root and it worked - then I realized my problem.  I deleted the .wine folder and reinstalled wine.  then it worked.  I actually was able to install Halo.exe and run the updates. 

However, when I click on the icon nothing happens.  I will review the directions again and retrace my steps. 

Overall - progress made and I learned something new.  Not too bad!

---

### Post by ketzerei on 2007-07-08
I would like to know how well WOW and Neverwinter Nights runs on wine for you.

---

### Post by ketzerei on 2007-07-08
YES! It works. It freezes my comp in 1024X768, it has no sound, only works in safe mode, and doesnt always render. BUT IT WORKS! ) :P

Here's some screens.
[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-1.png[/IMG]

---

### Post by lordhebe on 2007-07-09
Are you using an ATI card by any chance? It seems that ATi cards have problems like that running Halo, bt we can't be sure.

---

### Post by beeldings on 2007-07-14
I followed your guide and was able to install Halo with Wine 0.9.39 (for some reason the installer would hang at "Creating game folders" when I used Wine Wine 0.9.40 or Wine 0.9.41). Anyway, my question is how can I improve in-game performance? I have the virtual desktop set to 1280x1024 and I launch the game with "-vidmode 1280,1024,60", all video settings are maxed out. The game runs horribly, even if I decrease the resolution and with particles disabled and the textures set to low. I don't run any another applications when using Halo, so I'm not quite sure what to make of it. I tried upgrading to Wine 0.9.40 and 0.9.41 but the performance is still sub-par. I checked the system requirements for Halo and my computer definitely exceeds the minimum requirements: AMD Athlon 64 3200+, 2 GB DDR 400 memory, BFG Technologies GeForce 7800GS AGP 8x (with the Nvidia drivers installed via Envy), on Feisty Fawn. I searched for some information on the Wine AppDB and didn't find anything useful. Are there any launch options or registry tweaks that I may have overlooked?

---

### Post by The Noble on 2007-07-14
Ah, sorry for being late guys, I had some things come up. Anyways, I tried using wine .9.41, but it seems to freeze my entire system for some reason (aka powerbutton to reset). I'm redownloading .9.39 and I'll see if that makes a difference.

EDIT: Well, it looks like I am going to have to wait for my halo fix. .9.39 does not kill my system, but I have the black menu problem still. I guess I am going to have to wait for my halo fix in linux. 

Lordhebe, if you get the time, would you mind trying .9.41 to see if there is a regression? It may be good to alert the wine devs to any problems now rather than later.

---

### Post by beeldings on 2007-07-16
I was finally able to get Halo to install with Wine 0.9.41. There was a problem with Wine 0.9.41 and the Halo installer that prevented the installer from copying a file, "msxmlenu.msi", to the Halo folder on the Wine virtual drive. So, by copying msxmlenu.msi from the Redist directory on the Halo CD to the Halo folder on drive_c, the installer was then able to proceed without further complications.

edit:
Ok, I just played through most of the first level, and everything appears to work properly in Wine 0.9.41. The flashlight was functioning and there was no noticeable mouse lag. I ran the game at 800x600, I am going to up the resolution to see if I experience any performance degradation similar to when I ran Halo with Wine 0.9.39.

update:
I managed to bump the resolution up to 1280x1024. Halo appears to run pretty smooth.

---

### Post by Dark Aspect on 2007-07-16
> **marq said:**
> my video card would be 

nVidia Corporation
NVIDIA Vanta/Vanta LT 16 MB 4x AGP
i have a pci video card i can take from another computer (shhh they wont notice =P)
but i have to give up my sound for it

[Your Problem is You don't meant the Minimum system requirements]("http://support.microsoft.com/kb/829479")

Anyway I got Halo to play finally here's a pic

[IMG]http://i183.photobucket.com/albums/x72/Dark_Aspect/Screenshot.png[/IMG]

Game runs great on my Geforce 6800 GS video card,I am using Wine 0.9.41.Full screen has a few problems on my computer but I can fix this by zooming in with CTRL +.

---

### Post by lordhebe on 2007-07-18
Great that you got the game working guys, and I will update to version 0.9.41 soon to see if there is a regression, though it would seem like there isn't. (Sorry about my absence for the last week, been very busy)

---

### Post by El Flavio on 2007-07-18
Hi! I installed the game without any flaws (using wine 0.9.41) and updated the game sucesfully also. I followed all the steps and they all came out good except the last step (playing). My problem is when I try to run the desktop icon launcher, i get a "Fatal error" message or a message that says another copy of halo is running on this machine (see pic). What did i do wrong  and how can I fix? FYI: I have a AMD 64 Processor 3500+ and a NVIDIA GeForce 6200 TurboCache video card and 2gigs of RAM.

[IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/problem.png[/IMG]

---

### Post by lordhebe on 2007-07-19
Hmm I've never seen that problem before, try doing a ```
wineserver -k
``` or a system restart, then running the game again. Or you could try running the game in a terminal by typing ```
wine "C:/Program Files/Microsoft Games/Halo/halo.exe"  -novideo
```

---

### Post by El Flavio on 2007-07-19
> **lordhebe said:**
> Hmm I've never seen that problem before, try doing a ```
wineserver -k
``` or a system restart, then running the game again. Or you could try running the game in a terminal by typing ```
wine "C:/Program Files/Microsoft Games/Halo/halo.exe"  -novideo
```

tried both, still getting the same message. Also, i forgot to mention that I also get a "Gathering exception data..." message before the fatal error message.

---

### Post by lordhebe on 2007-07-23
Sorry for the delay, I've been very busy, but anyway. I tested wine 0.9.40, and experienced no problems, in fact I noticed a slight increase in framerate. I will test 0.9.41 and see if anything's changed.

Update:

Tried wine 0.9.41, and Halo still works, although I don't know whether this was with .40 as well but I have noticed some major improvements to sound since .39, for example the menu was crackly for me and now it's perfect.

Fantastic. Great work wine devs!

---

### Post by lordhebe on 2007-08-03
Wine 0.9.42 released, Halo still works, no noticeable improvements or regressions.

---

### Post by arvinkebob on 2007-08-06
Well I got around to installing this yesterday and it works except for one thing. It doesn't play in fullscreen but in a window and part of the screen is cut off so I have to run the game in a virtual desktop. I assume gnome is in the way as I ran this in Kubuntu and it ran perfectly (as well as SuSE 10.2). 

Does anyone know a way to run this in fullscreen? I assume you, lordhebe, got it to work as I didn't see a post saying otherwise. Also as with many other people the mouse was laggy so I just bumped the sensitivity from 3 to 7 and the frame limiter to NO VSYNC and it runs smooth but not as smooth as in fullscreen (like i Kubuntu).

Thanks and glad to be a member of the forum.

---

### Post by lordhebe on 2007-08-06
Sorry my sincere apologies, I should have made note of this, but I use a workaround to get it fullscreen. I use XVID mode for changing resolutions, because it zooms in the picture rather than changing the resolution, and then move the mouse to hide the window borders. You do this by running regedit, and changing The string value ```
UseXRandR
``` to ```
N
``` and ```
UseXVidMode
``` to ```
Y
```

Sorry I should have mentioned this before.

---

### Post by arvinkebob on 2007-08-06
Where are these strings located at? I tried searching but I found nothing. Thanks.

---

### Post by lordhebe on 2007-08-07
Press ALT+F2 and type ```
regedit
``` You may have to create new string values. The string values I am referring should be in ```
HKEY_CURRENT_USER/Software/Wine/X11 Driver/
```

Sorry just realized that I didn't tell you the directory of the string values. Look at the wineHQ page for registry keys for more information. [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by arvinkebob on 2007-08-07
Sorry if I'm being a bother but I'm still not able to get it to run in fullscreen. I created the strings and set the values but when I start Halo it's the same thing. Could you show screenshots of it running in fullscreen and how you used xvidmode to work this out. Thanks.

---

### Post by lordhebe on 2007-08-07
It doesn't run fullscreen. I use a workaround.

Using Xvidmode I run Halo and It appears like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40108&d=1186518633[/IMG]

I then press Alt+tab and move the move to the edge of the screen (which gets it to move) and line it up so it looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40109&stc=1&d=1186518783[/IMG]

So a faked fullscreen then. I'm sorry I didn't make this point clear. It's also possible to get "true" fullscreen by disabling the ability for the window manager to manage windows, but for me this means it doesn't have keyboard focus, and a can't move, which is obviously not practical.

To get xvidmode to work make sure your regedit looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=40106&stc=1&d=1186518398[/IMG]

Oh and don't worry, you're not being a bother. This is the place to get help and I enjoy giving help.

---

### Post by arvinkebob on 2007-08-07
Ok about the "Managed" option, how come the keyboard doesn't focus on the application running? I tried the xvidmode which worked but now I have a huge black border that almost cuts half way through the screen.

Also why is it that gnome and only gnome interferes with this. KDE works perfectly but gnome seems to hate it. Is it possible they may fix it in a future release? Thanks again.

EDIT: Ok scratch the border problem, it now works. I was being ignorant. But I'm still wondering why gnome causes this.

---

### Post by ketzerei on 2007-08-12
Ok, I had tried your tutorial with wine shortly after you published your how-to. I had gotten it to work-sorta-and could see the menu and start a campaign game or a multi-player game, but-even in safe mode-only the top 8th of the screen would render. I have an ATI card so this could have been the problem seeing as how the ATI drivers stink. Today, however, I re-installed halo and tried your tutorial again, but every time I run it with any number of configurations, it freezes my computer and I have to push the reboot button. Any idea if this is just a bug in the new release, or something else. Suggestions appreciated. -Ketz

---

### Post by lordhebe on 2007-08-12
Okay I just tried 0.9.43, and the same thing happens for me, so it's probably a regression. I'll update my main post and file a bug report when I get the chance.

---

### Post by Dark Aspect on 2007-08-12
> **lordhebe said:**
> Okay I just tried 0.9.43, and the same thing happens for me, so it's probably a regression. I'll update my main post and file a bug report when I get the chance.
Good I was about to see if there is a way to file a bug report myself as Halo does not work with wine 0.9.43 for me either and the worse of it is I get a error when I tried to downgrade wine with an older .deb file I had backed up.......it looks like I'll have to wait for a new release:(

Of course on a side note a new version of wine comes out like every 20 days or so.

---

### Post by hikaricore on 2007-08-12
> **Dark Aspect said:**
> Of course on a side note a new version of wine comes out like every 20 days or so.

More like every 2 weeks on a Friday, but who's counting.  ^_^ :guitar:

---

### Post by ketzerei on 2007-08-14
After many lockups and crashes I was finally able to get a terminal output. Here's what happens when I run it with the -use11, -nosound, -novideo, and -width640 commands:

ketzerei@ketzerei-desktop:~$ wine '/home/ketzerei/.wine/drive_c/Program Filecrosoft Games/Halo/halo.exe' -novideo -nosound -use11 -width640
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:winedevice:ServiceMain driver L"SecDrv" failed to load

Any ideas?

---

### Post by ketzerei on 2007-08-15
Ok, now I cant even run halo update. Heres the output:

```
ketzerei@ketzerei-desktop:~/.wine/drive_c/ProgramFiles/MicrosoftGames/Halo$ wine haloupdate.exe
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
wine: Call from 0x7b843f20 to unimplemented function winhttp.dll.WinHttpOpen, aborting
wine: Unimplemented function winhttp.dll.WinHttpOpen called at address 0x7b843f20 (thread 0009), starting debugger...
Unhandled exception: unimplemented function winhttp.dll.WinHttpOpen called in 32-bit code (0x7b843f98).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b843f98 ESP:0033eb38 EBP:0033eb9c EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82ee9d EBX:7b8b0888 ECX:00000000 EDX:7c6bf038
 ESI:7c6bf038 EDI:7c6bf0fc
Stack dump:
0x0033eb38:  0033ebc0 00000008 00427d10 00000414
0x0033eb48:  80000100 00000001 00000000 7b843f20
0x0033eb58:  00000002 7c6bf860 7c6bf95d 7bc8553c
0x0033eb68:  0033eba8 7bc440cd 7bc8d6e4 ffffffff
0x0033eb78:  00000000 0033eb98 7c04c8b8 00000016
0x0033eb88:  7bc8d6e4 7bc58cfc 00427d10 00427d48
Backtrace:
=>1 0x7b843f98 RaiseException+0x78() in kernel32 (0x0033eb9c)
  2 0x7c6bf801 in winhttp (+0xf801) (0x0033ebcc)
  3 0x7c6bf133 in winhttp (+0xf133) (0x0033f438)
  4 0x00401bf9 in haloupdate (+0x1bf9) (0x006544e8)
  5 0x00000002 (0x00650001)
  6 0xf0000100 (0x00001100)
  7 0x00000000 (0x00000000)
0x7b843f98 RaiseException+0x78 in kernel32: movl        0xfffffffc(%ebp),%ebx
Modules:
Module  Address                 Debug info      Name (89 modules)
PE        400000-  439000       Export          haloupdate
PE      10000000-1003a000       Deferred        patchw32
PE      3f800000-3f912000       Deferred        strings
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c6ad000-7c6c1000       Export          winhttp<elf>
  \-PE  7c6b0000-7c6c1000       \               winhttp
ELF     7c6fa000-7c72c000       Deferred        uxtheme<elf>
  \-PE  7c700000-7c72c000       \               uxtheme
ELF     7c72c000-7c741000       Deferred        midimap<elf>
  \-PE  7c730000-7c741000       \               midimap
ELF     7c741000-7c767000       Deferred        msacm32<elf>
  \-PE  7c750000-7c767000       \               msacm32
ELF     7c767000-7c82c000       Deferred        libasound.so.2
ELF     7c82c000-7c85e000       Deferred        winealsa<elf>
  \-PE  7c840000-7c85e000       \               winealsa
ELF     7c9d2000-7c9ea000       Deferred        msacm32<elf>
  \-PE  7c9e0000-7c9ea000       \               msacm32
ELF     7c9ea000-7c9ef000       Deferred        libxfixes.so.3
ELF     7c9ef000-7c9f8000       Deferred        libxcursor.so.1
ELF     7c9f8000-7ca15000       Deferred        imm32<elf>
  \-PE  7ca00000-7ca15000       \               imm32
ELF     7d03d000-7d043000       Deferred        libxrandr.so.2
ELF     7d893000-7d89c000       Deferred        librt.so.1
ELF     7d89d000-7d8a5000       Deferred        libxrender.so.1
ELF     7d966000-7e297000       Deferred        fglrx_dri.so
ELF     7e297000-7e337000       Deferred        libgl.so.1
ELF     7e337000-7e33c000       Deferred        libxdmcp.so.6
ELF     7e33c000-7e33f000       Deferred        libxau.so.6
ELF     7e33f000-7e430000       Deferred        libx11.so.6
ELF     7e430000-7e43e000       Deferred        libxext.so.6
ELF     7e43e000-7e443000       Deferred        libxxf86vm.so.1
ELF     7e443000-7e45b000       Deferred        libice.so.6
ELF     7e45b000-7e464000       Deferred        libsm.so.6
ELF     7e464000-7e4ee000       Deferred        winex11<elf>
  \-PE  7e470000-7e4ee000       \               winex11
ELF     7e568000-7e588000       Deferred        libexpat.so.1
ELF     7e588000-7e5b3000       Deferred        libfontconfig.so.1
ELF     7e5b3000-7e5c7000       Deferred        libz.so.1
ELF     7e5c7000-7e632000       Deferred        libfreetype.so.6
ELF     7e632000-7e65f000       Deferred        ws2_32<elf>
  \-PE  7e640000-7e65f000       \               ws2_32
ELF     7e65f000-7e679000       Deferred        wsock32<elf>
  \-PE  7e670000-7e679000       \               wsock32
ELF     7e679000-7e736000       Deferred        comctl32<elf>
  \-PE  7e680000-7e736000       \               comctl32
ELF     7e736000-7e839000       Deferred        shell32<elf>
  \-PE  7e750000-7e839000       \               shell32
ELF     7e839000-7e892000       Deferred        shlwapi<elf>
  \-PE  7e850000-7e892000       \               shlwapi
ELF     7e892000-7e8b2000       Deferred        mpr<elf>
  \-PE  7e8a0000-7e8b2000       \               mpr
ELF     7e8b2000-7e8fc000       Deferred        wininet<elf>
  \-PE  7e8c0000-7e8fc000       \               wininet
ELF     7e8fc000-7e95a000       Deferred        setupapi<elf>
  \-PE  7e910000-7e95a000       \               setupapi
ELF     7e95a000-7e96e000       Deferred        lz32<elf>
  \-PE  7e960000-7e96e000       \               lz32
ELF     7e96e000-7e988000       Deferred        version<elf>
  \-PE  7e970000-7e988000       \               version
ELF     7e988000-7e99b000       Deferred        libresolv.so.2
ELF     7e99b000-7e9b9000       Deferred        iphlpapi<elf>
  \-PE  7e9a0000-7e9b9000       \               iphlpapi
ELF     7e9b9000-7ea12000       Deferred        rpcrt4<elf>
  \-PE  7e9d0000-7ea12000       \               rpcrt4
ELF     7ea12000-7eab1000       Deferred        ole32<elf>
  \-PE  7ea20000-7eab1000       \               ole32
ELF     7eab1000-7eaf9000       Deferred        advapi32<elf>
  \-PE  7eac0000-7eaf9000       \               advapi32
ELF     7eaf9000-7eb05000       Deferred        libgcc_s.so.1
ELF     7ebff000-7ecbf000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecbf000       \               gdi32
ELF     7ecbf000-7edfd000       Deferred        user32<elf>
  \-PE  7ece0000-7edfd000       \               user32
ELF     7edfd000-7ee8b000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8b000       \               winmm
ELF     7ef9d000-7efa8000       Deferred        libnss_files.so.2
ELF     7efa8000-7efb2000       Deferred        libnss_nis.so.2
ELF     7efb2000-7efc9000       Deferred        libnsl.so.1
ELF     7efc9000-7eff0000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7ca6000-b7caa000       Deferred        libdl.so.2
ELF     b7caa000-b7deb000       Deferred        libc.so.6
ELF     b7dec000-b7e03000       Deferred        libpthread.so.0
ELF     b7e13000-b7f27000       Deferred        libwine.so.1
ELF     b7f29000-b7f44000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\ProgramFiles\MicrosoftGames\Halo\haloupdate.exe
        00000009    0 <==
```

---

### Post by arvinkebob on 2007-08-15
The game is leaking memory with wine 0.9.43 so it just loads and loads until your RAM's been used up at which point the computer froze. I can't do anything to figure out what's wrong either since it also uss 100% CPU.

---

### Post by ketzerei on 2007-08-15
This is the only error message I get now:

err:winedevice:ServiceMain driver L"SecDrv" failed to load

any ideas?

---

### Post by ketzerei on 2007-08-15
FYI for everyone, you need winhttp.dll to run halo update with the new release of wine. :)

---

### Post by lordhebe on 2007-08-16
Thanks for that information, sorry about my delayed response, but I'm afraid there is not much I can do with your problem. I highly suggest you just revert to a previous version of wine, preferably 0.9.42.

---

### Post by ketzerei on 2007-08-16
Thanks. But may I so bold to ask HOW?

---

### Post by lordhebe on 2007-08-16
Of course you may. First uninstall the version of wine you currently have installed, then go here: [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html") and download a deb file for a previous version and install that instead. If it asks you to update wine, remove the wine repository from your software sources.

---

### Post by ketzerei on 2007-08-16
Update: Dont know how exactly, but halo "runs" now. I keep getting a shaders .vsh file missing or corrupt like error. Any ideas?

Edit: heres the other part of the error I get in the terminal

### FAILED TO OPEN DATA-CACHE FILE.

### FAILED TO OPEN DATA-CACHE FILE.

err:dialog:EndDialog got invalid window handle (0x1002a); buggy app !?
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  144 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x3200084
  Serial number of failed request:  1385
  Current serial number in output stream:  1385

---

### Post by lordhebe on 2007-08-17
I get that very odd problem as well if I run it through a terminal. Oddly it runs without problems when I run it by double clicking on the desktop shortcut.


AWAY: I am going to be away for 2 weeks as of Sunday.

---

### Post by ketzerei on 2007-08-19
Well, I removed wine and installed 9.39 and got it working again. However, thanks to ATI's crap drivers, it just barely renders. :( Other than the fact that it has no sound ( I had it before dont know why it dont work now ) and the mouse doesnt get grabbed very well it runs perfectly.

Edit: I should also point out that its Halo CE, not the original.

---

### Post by arvinkebob on 2007-08-20
I just switched back to 0.9.42 and everything's all well. Too bad I had to change because GTA: SA has quite a big performance boost in 0.9.43 :(

---

### Post by ketzerei on 2007-08-27
So, anyone tried 9.44 yet?

---

### Post by Dark Aspect on 2007-08-28
> **ketzerei said:**
> So, anyone tried 9.44 yet?
Um yeah its still broken for me and I said the H*ll with it so now I am running Halo though the new version of Crossover with sound issues and some speed lost.I played around with crossover and I got it working ok.

Thats the only thing I hate about wine is crossover just seems more stable in the fact that once some thing works it does not break again in a newer version.Having said that I know crossover is not designed for games.

---

### Post by Gentooer on 2007-08-30
I have Halo running with wine .9.42.  I have the same problems with fullscreen, but I also can't run it windowed in any resolution other than 800x600 or else most of the screen is black. :(  Did you guys have problems changing the resolution?

I also have  the same memory leak with .9.43 and .944.  Has anyone filed a bug report about this yet?

EDIT: After downloading the correct no-cd (I had been using a different one before i saw this guide), windowed mode works great at any resolution.  Fullscreen mode works perfectly expect it doesn't have keyboard focus.  Is there any way to give it focus without putting the border around it?

EDIT2: I got keyboard focus in fullscreen by running it in its own X server.  NOW everyhting is perfect!! :D

---

### Post by lordhebe on 2007-09-02
: Back :

Great to hear about your success, I will try 0.9.44 today and update the main post.

---

### Post by ketzerei on 2007-09-04
I was curious, is there a previous version of wine that anyone has tried that works better with ATI drivers? Or better yet, can anyone recommend some tweaks for ati cards so I dont have to run halo in 640x480 and have an 1/8 of the screen missing?

Edit: also, does the no cd exe have anything to do with performance as well?

---

### Post by lordhebe on 2007-09-05
The no-cd has no affect on performance, and the game won't run without it due to copy protection issues. And I doubt there is an earlier version which removes ATI issues, it's 99% likely to be the dodgy drivers.

---

### Post by ketzerei on 2007-09-05
That still doesnt answer my last question though. Are there any ways I can improve performance? I dont mean to sound, well, mean, but I REALLY dont want to dual boot. Its annoying.

---

### Post by lordhebe on 2007-09-07
Well I have tried playing around with different game settings and wine settings and have been unable to find any setting whch improve performance, so I'm afraid I can't help you. All I can suggest are lowering game settings to improve performance (as you would on Windows)

---

### Post by fakie_flip on 2007-09-08
Halo begins to install, but during the installation, it says "Creating game folders ..." and is stuck there. In the console, wine gives me this output.

```
fixme:imm:ImmReleaseContext (0x10026, 0x154458): stub
fixme:exec:SHELL_execute flags ignored: 0x00000400
err:msi:copy_package_to_temp failed to copy package L"C:\\Program Files\\Microsoft Games\\Halo\\msxmlenu.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!
fixme:imm:ImmGetDefaultIMEWnd (0x20048 - 0x10028 0x154458 ): semi-stub
```

I am using wine version 0.9.42 and 64 bit ubuntu 7.04.

---

### Post by lordhebe on 2007-09-09
Are you running the installer under quick mode? Don't use it, it can cause problems.

---

### Post by El Flavio on 2007-09-09
I finally got mine working! I got it running in Linux Mint (98% Ubuntu). Just followed your instructions again, installed it and had an error that told me to reinstall it, so i did and it worked fine! I am running wine 0.9.41.

I am having trouble getting it into full screen mode. I tried the -vidmode 1024,768,60 thing and it works, but the audio is screwy and my mouse movements lag. i tried changing it in the Halo settings also, but that does not work. What else could I do???

[IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/halol1.png[/IMG]

---

### Post by Sockerdrickan on 2007-09-10
Yeah I had that problem too a while back

---

### Post by Sockerdrickan on 2007-09-10
Can I smooth mouse movements in windowed mode (virtual desktop)

---

### Post by lordhebe on 2007-09-11
Well when it comes to a laggy mouse, unfortunately there's no known way to solve it. I do experience the issue, but not enough for me to make a big deal of it, but since other people seem to be having worse cases of the issue I've done some experimenting and found a way to lessen the issue (for me anyway)

First disable Specular in Halo's options, then run regedit and change or create ```
HKEY_CURRENT_USER\Software\Wine\Direct3D\RenderTargetLockMode
```with  the content ```
enabled
```

This improved things, but the problem was still there, but it made the game more playable. Some people may have to lower settings in game to improve this issues. (It seems to be worse when more is on screen, which suggests that people with higher graphics cards would probably have a smoother ride.)

I'm adding this post to my first.

---

### Post by Sockerdrickan on 2007-09-11
Lol look at my graphics card (However it is mouse lag W A S D feels like 60 fps)

---

### Post by lordhebe on 2007-09-11
That's strange but you're probably having a smoother ride than I am with my Geforce 7300 256MB.

The rooms that the mouse lag happens in suggests that it's not actually mouse lag, it could be a sudden hit of slowdown caused by some unknown problem.

---

### Post by Sockerdrickan on 2007-09-11
Ok

---

### Post by lordhebe on 2007-09-11
UPDATE:

USE BACKBUFFER. I change to it from fbo and noticed a MASSIVE IMPROVEMENT.

offscreenrenderingmode:

backbuffer (default) Best, no visual glitches, good performance.

pbuffer: Good performance but many visual glitches pictured in an attachment.

fbo: No visual glitches, but bad performance.




Using backbuffer all but removed the issue for me. Use regedit (type in a terminal) and this guide to help you: [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys").

HKEY_CURRENT_USER\Software\Wine\Direct3D\OffscreenRenderingMode

---

### Post by Sockerdrickan on 2007-09-11
Still mouse lag I'm afraid

---

### Post by ketzerei on 2007-09-15
So, anyone tried halo on the new version of wine yet?

---

### Post by Sockerdrickan on 2007-09-15
I was just about to ask that myself!

---

### Post by lordhebe on 2007-09-16
Yes I've tried, it still crashes :mad:

---

### Post by Sockerdrickan on 2007-09-16
Will it ever be fixed :'(

---

### Post by ketzerei on 2007-09-16
It seems not.

---

### Post by lordhebe on 2007-09-29
The trend continues with 0.9.46.

When I have time I'll run a regression test, but I'm busy at the moment, so if someone else has time please go ahead and try if you want.

---

### Post by gwoodard on 2007-10-01
How do u "copy" the file to the system32 folder?

mfc42.dll file I hit right click on the dll file select copy but it wont paste in the system32 folder in my fake c: drive

---

### Post by lordhebe on 2007-10-05
What happens? Does it give you an error message? Does nothing happen?

What I do is open the .rar with file-roller and extract it directly to the system32 folder.



UPDATE: 

While Halo continues not to work with core wine, it works with the new version of Crossover (6.2) near flawlessly (still follow the guide)

It no-longer has the gnome "window" bug, and the framerate is higher. I suggest running Halo with crossover.

There is only one minor problem, and that haloupdate.exe does not work. You instead have to get the patch off the internet and run that instead. It will probably freeze at the end, but it should have finished. Run it again to make sure.

---

### Post by gwoodard on 2007-10-07
Nothing happens it dose not want to paste to the system32 file...
thought it was bad (i deleted the it) i try again to see what happens

---

### Post by beeldings on 2007-10-10
> **lordhebe said:**
> 
UPDATE: 

While Halo continues not to work with core wine, it works with the new version of Crossover (6.2) near flawlessly (still follow the guide)

It no-longer has the gnome "window" bug, and the framerate is higher. I suggest running Halo with crossover.

There is only one minor problem, and that haloupdate.exe does not work. You instead have to get the patch off the internet and run that instead. It will probably freeze at the end, but it should have finished. Run it again to make sure.

Confirmed. I originally installed and updated Halo using Wine 0.9.39 and then proceeded to upgrade Wine to the latest version. As there appears to be several errors running Halo on Wine, I noted Lordhebe's post and gave it a shot with CrossOver. The game is able to run in full-screen without the Gnome menubar problem, and there is a noticeable improvment in sound quality and framerates. If you absolutely must play Halo on Linux, I would advise you to download and install the CrossOver 6.2 demo. But, since Halo is not offically supported by Codeweavers (the developers of CrossOver) don't expect much tech support, your best bet is to stick with this message board and the Wine AppDB. YMMV.

If you like it, support the good people behind CrossOver and purchase a copy for yourself. Codeweavers simply "get it" and their technical support is top-notch. I've been a customer for abour a year now (since they offically supported WoW) and I highly recommend their services. And unlike Transgaming/Cedega, Codeweavers contributes code to the Wine project (I know of at least one Codeweavers dev that actively works on Wine).

---

### Post by seanj on 2007-10-13
I tried this with WINE version 0.9.39, but while entering my CD key, I get something about "Cannot load PidGen.DLL", and it sends me back to the CD key entry screen.

---

### Post by Dark Aspect on 2007-10-13
> **lordhebe said:**
> While Halo continues not to work with core wine, it works with the new version of Crossover (6.2) near flawlessly (still follow the guide)

It no-longer has the gnome "window" bug, and the framerate is higher. I suggest running Halo with crossover.

There is only one minor problem, and that haloupdate.exe does not work. You instead have to get the patch off the internet and run that instead. It will probably freeze at the end, but it should have finished. Run it again to make sure.

Okay this is really weird haloupdate.exe worked for me in crossover 6.2........that and I still have the window problem to a degree.When I use a res under 1024x768 then its fine but the window problem reappears when I go higher then that.

I have 64-bit Ubuntu.

---

### Post by ketzerei on 2007-11-03
So, any progress in any of the other wine releases? This thread hasnt seen much action lately so I was just wondering.

---

### Post by lordhebe on 2007-11-04
Well I trief 0.9.48, and had no luck, but I'm gonna try again soon, I don't think I gave it a proper test. In order to bring an end to this I will attempt to do a regression test when I get the chance. (If anyone can't be bothered to wait, feel free to do one yourself, it will be much appreciated)

The thing I since nothing has happened Halo wise for a while now, I thought I wouldn't bother posting an update with every new version, then this thread would become bloody tedious. I will post the second Halo works again however.

P.S. Did further testing: still broken but there have been some improvement: When using an offline patch it doesn't freeze at the end anymore, it gives you a completion message.

---

### Post by ketzerei on 2007-11-04
So.. can you tell me what im doing wrong? I've installed halo trial as a test... but when I run it, it eats all my memory and goes awry. I have an ATI card, so that may be the issue. But do you have any specific config options you did? I should also point out this is in crossover.

---

### Post by lordhebe on 2007-11-05
I don't fully understand your problem sorry. You said you're using crossover? Which version? I've never heard of that problem before, with crossover anyway.

---

### Post by ketzerei on 2007-11-05
Yeah, I should be more specific. I'm running Gutsy, I have crossover 6.2 (trial), an ATI Radeon X1600 card, and I'm trying to install halo trial. I installed the .deb of crossover 6.2, ran the config thingy, and went through the halo trial installer. No hiccups, no nothing. So, I thought "sweet, all is well and I can finally play!" But when I click on the link on my desktop (or any other method of starting it) it pops up fullscreen like it should, but it doesnt completely fill the window, which I assumed was just a glitch, but sure enough, it eats up all my memory and just sits there. So, I have no idea what im doing wrong.

---

### Post by lordhebe on 2007-11-06
I'm sorry I have no idea. It may be just the trial, or mabye it's something else. Have you set you graphics card memory settings in regedit? (Or does crossover detect it automatically? I forget) Do you have enough ram to run the game (although I'm guessing you do) other than that I don't know what to suggest sorry.

---

### Post by gwoodard on 2007-11-07
I use wine 0.9.48...do the same directions apply or do I have to uninstall 0.9.48 and install 0.9.38? and reinstall Halo?

Here are my problems...1. the "Halo" screen (with ring in back ground) pops up in a 1024x768 box... then the green or wine desktop pops up exiting halo and giving an exception but no details

---

### Post by lordhebe on 2007-11-13
Halo does not work with wine 0.9.42 <  You just have to install a previous version of wine, and then Halo should run without you having to uninstall it. I have been unable to test 0.9.49 because for some reason the .deb won't install. I do apologise that I haven't been working on this, I've been very busy recently.

---

### Post by Ferrat on 2007-11-13
> **lordhebe said:**
> Halo does not work with wine 0.9.42 <  You just have to install a previous version of wine, and then Halo should run without you having to uninstall it. I have been unable to test 0.9.49 because for some reason the .deb won't install. I do apologise that I haven't been working on this, I've been very busy recently.

According to bug data you should be able to run Halo with later versions if you disabled OSS and ALSA sound, anyone tried this??

Edit tried it, well I get as far as the logo movies with sound, but as soon as the menu is about to load X crashes sort of and I need to do a hard reboot

also tried
-novideo 
-nosound

fullscreen and windowed (both wine and halo)

---

### Post by gwoodard on 2007-11-13
I got tired of messing with wine 0.9.49...So I uninstalled it and got the deb files for 0.9.39 (I use 7.10 but the 7.04 files work fine and so does Halo!)

---

### Post by Ferrat on 2007-11-13
Seems the ATi driver is really messed up still get the same errors more or less and hard lock, tried crossover, well got to menu but no control in the window and the menu was 4-5times bigger than the resolution set aswell as sound jumping over and over before shutting down. 

So a no go :(

---

### Post by ketzerei on 2007-11-21
Well, since I've last posted, I've had NO luck or improvement. Halo, on wine or crossover and on ATI, is TOTALLY and UTTERLY unplayable. :'(

---

### Post by caffienefree on 2007-12-04
Not having much luck with 09.50. Normal mode of entering halo results in the virtual desktop suddenly shutting down. Going in by safe mode starts the game, but gives weird graphics (text lines are white boxes, instead of the Halo moving in the background there is just a gray shape).

Then again, I wasn't exactly getting anywhere with 09.39 either... =P

---

### Post by painejake on 2007-12-06
Brilliant Thanks for that!!:guitar:

---

### Post by Sockerdrickan on 2007-12-29
Something tells me it will work with this new 0.9.52

---

### Post by Sockerdrickan on 2007-12-29
It works!!!!!!!

BUT

It takes 1.3GB memory (wtf)
Still no true full screen

---

### Post by lordhebe on 2008-01-02
Hmm, the fact it works is good news, need to try it myself at some point. Apologies for my long absense, due to work I have been forced to convert to windows, going to set up a dual-boot system at some point.

---

### Post by indianballer24 on 2008-01-14
OK, the fact that it works on Wine.52 is great news. But what are the exact steps to get it to run. Also has anyone tried wine.53.

---

### Post by indianballer24 on 2008-01-16
So, I guess no one has tried it yet?

---

### Post by aaabbb on 2008-01-27
Hello! I play Halo 1/CE and Halo alot (on XP)and I followed this article to get it to work in ubuntu. Well, when i start the game, (this happens with the trial and the full version) I get this error message from my monitor, and NOT the game: OUT OF RANGE Hf: 30khz-70khz Vf:50hz-160hz, 75.2hz 60hz. 

So-it seems that the game is set to a horizontal frequency that my monitor can't handle-i need to know how to set it lower, or what to do. I have multiple computer parts and monitors, maybe i should try another monitor...? 

I would really appreciate some help!

---

### Post by aaabbb on 2008-01-27
oh, and apparently someone did try it! =)

---

### Post by aaabbb on 2008-01-27
the only exception is that i am using a newer version of wine, but i don't think that matters

---

### Post by aaabbb on 2008-01-27
i am using a different monitor at this very moment, and the game started up (the full version) but it is not working. The halo logo screen dimmed itself to be black and white after a moment and the mouse is lagged. right after that, some tiny window came up for a split second and the game exited.

I tried the Halo PC Trial, (without installing it) and got an error that said the vsh.bin shader was corrupted or missing. (???) it was not either, so i am going to try to install the program instead of running it off a folder moved from anither pc.

---

### Post by Sockerdrickan on 2008-01-27
It works and the mouse doesn't lag, true fullscreen
still 1.3GiB memory usage (hmm)

this is with WINE 0.9.54

---

### Post by aaabbb on 2008-01-27
Ok! The Halo Trial only works right after installation, and even then, it doesn't work right. I won't even botherto list the load of problems there are with my box. Oh well...I guess i will have to move on to bigger and better things.

---

### Post by aaabbb on 2008-01-27
> **Tux0r said:**
> It works and the mouse doesn't lag, true fullscreen
still 1.3GiB memory usage (hmm)

this is with WINE 0.9.54

Lucky You...:)

---

### Post by indianballer24 on 2008-01-30
I tried to install halo trial on wine. It didnt even start. I guess its because I only have 1GB of Ram?

---

### Post by diddler on 2008-02-14
Lordhebe, you are a Wine God (or God of Wine, whichever trips your trigger).  I followed the steps you posted and this is the FIRST Windows game I have managed to get to work in Linux!

A few comments, but doesn't alter my joy:

a)  I too suffer from mouse lag, but insufficient to affect the game.
b)  Oddly, the sound works better than on my previous Windows machine.
c) The game refuses to shut down on its own, but sends the hard drive racing until I force quit - not a real problem since the game is the thing.
d)  One of the files in the crackCD archive came with a little Trojan attached.  I found it because I had to go to my Windows machine to unarchive the download and my antivirus picked it up.

Thanks again for your most illuminating "how-to".  It was the most useful and easy to follow help I have found in this forum.

---

### Post by spacefreak86 on 2008-02-14
Question. I am currently using Wine 0.9.54 and was able to install Halo, but when I start the program, I hear the background music, but the screen loads and the top portion and where the four buttons (Campaign, Multiplayer, Settings and Quit) are, there are white boxes that cannot be accessed. Has anyone else experienced this or know how to work around it?

---

### Post by diddler on 2008-02-14
Well, my HALO has a few new twists that add to the excitement.

Since I am playing in the WINE desktop, any time I move the mouse too fast it jumps out the WINE desktop onto the LINUX desktop and I end up opening a few other LINUX applications (which really interrupts a battle with the Covenant).

The flashlight only lights up the back of my pistol, but I think that is a bug in the original game that was solved by a patch, but apparently the bug is still in the cracked .exe file.

The game still refuses to shut down.  I guess it is making up for all the time I could not play it.

Anyway, now can I get Halo2 to work?

---

### Post by cameronol on 2008-02-15
how high should you graphics card be.... i have the  Halo CE version (i also have the Halo CD too!) but i don't know how to install it, properly.

My computer is kind of crappy: Ubuntu 7.10, on board graphics card, 256MB ram,80G hard disk,  logitech subwoffer. What do i need to do and   am i eligible to even try this on my comp??

---

### Post by ashmew2 on 2008-02-17
```
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe"
``` 

Dont know if I should be pointing this out , but shouldnt it be ~/.wine instead of /home/***chris***/.wine ?

---

### Post by hooplah on 2008-02-17
Sorry for bumping this thread, but I require assistance from either the creator of this thread, or anyone who may pass by.

Well, I got the game installed, but when I run it I have some issues. I am running wine 0.9.39 by the way, in latest versions, the game locks up for no apparent reason.

Anyway, my problems are: when I look around, the mouse is very jerky , I followed the steps you provided in the initial post, no change at all. Also, when I get to the 'action' part of the game where I have a firearm, there's no sound when the gun is shot, actually, there is some sound, but it's extremely dim. 

Anyway, if anyone knows how to fix the problems I'm having, I'd LOVE to know.

Cheers,
Max

---

### Post by Joseph_Schafer on 2008-02-25
Um, I cant get it to work with sound. Works fine w/out but I would really like sound. It has someting to do with DSD being a stub or something. If you have any thing that would help, i woud appreciate it.

---

### Post by indianballer24 on 2008-02-29
Whenever I try to launch it I get white boxes on the main menu where it says campaign, multilayer, options, quit. Does anyone know how to fix this?

---

### Post by lordhebe on 2008-03-01
Hi guys sorry for the long delay since my long post (I'm posting this on **WINDOWS VISTA** :mad: )

Great to hear that it seems Halo is working again, to a certain extent. True fullscreen is always great (I've yet to try it to see if it works for me) but memory usage that high is a big problem.

> My computer is kind of crappy: Ubuntu 7.10, on board graphics card, 256MB ram,80G hard disk, logitech subwoffer. What do i need to do and am i eligible to even try this on my comp?? 

It depends on what you onboard graphics card is, if it's a low-end intel I would say there's very little chance. If it's a Geforce 6200 or something better, you may be able to squeeze something out of it.

> Hello! I play Halo 1/CE and Halo alot (on XP)and I followed this article to get it to work in ubuntu. Well, when i start the game, (this happens with the trial and the full version) I get this error message from my monitor, and NOT the game: OUT OF RANGE Hf: 30khz-70khz Vf:50hz-160hz, 75.2hz 60hz. 

So-it seems that the game is set to a horizontal frequency that my monitor can't handle-i need to know how to set it lower, or what to do. I have multiple computer parts and monitors, maybe i should try another monitor...? 

I would really appreciate some help!

Sorry for lack of replay, try manually changing the refresh rate to one supported by your monitor, using a flag on the end of your command or desktop shortcut. (See my original post for more information)

> Dont know if I should be pointing this out , but shouldnt it be ~/.wine instead of /home/chris/.wine ? 

It works either way, and obviously the "chris" part would depend on your username (mine being chris)

> Lordhebe, you are a Wine God (or God of Wine, whichever trips your trigger). 

Erm... thank you. Glad to hear you found my how-to useful, however I do not think I am a wine god, or a god of wine. Those ranks should be held by the developers.

> One of the files in the crackCD archive came with a little Trojan attached. I found it because I had to go to my Windows machine to unarchive the download and my antivirus picked it up.

Hmm that's worrying, I never had a case like that, are you sure your antivirus isn't on the fritz? (Mine used to go beserk with every .exe extension)

---

### Post by Nico0020 on 2008-04-02
very nice, just installed the demo last night.  Simple install, very clean.  Had to disable the sound, but everything else works fine.  Ran a little sluggish at times.  Hopefully this will get worked on a bit more. Let us know if there are any changes!

---

### Post by domi84 on 2008-04-14
Hi
I am following this guide ( [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720&iTestingId=21585](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720&iTestingId=21585) ), but I can not install Halo. The terminal gives this:
```
mimmo@mimmo-laptop:~$ wine /media/cdrom0/Setup.Exe
mimmo@mimmo-laptop:~$ wine: Unhandled page fault on write access to 0x00000060 at address 0x7eaccd97 (thread 0018), starting debugger...
Unhandled exception: page fault on write access to 0x00000060 in 32-bit code (0x7eaccd97).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eaccd97 ESP:0033e584 EBP:0033e5ac EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000010 EBX:7ead4980 ECX:0033e5b8 EDX:00000000
 ESI:00132398 EDI:00010026
Stack dump:
0x0033e584:  00000100 00010026 00010026 0033e658
0x0033e594:  00423d76 00010026 00000000 7eaccd70
0x0033e5a4:  7ed91704 00000000 0033e658 00423ebf
0x0033e5b4:  00132398 00132398 0044d078 00010026
0x0033e5c4:  00000100 00000000 00010026 0033e658
0x0033e5d4:  7ed91704 00000000 00000000 00000000
Backtrace:
=>1 0x7eaccd97 ImmDestroyContext+0x31() in imm32 (0x0033e5ac)
  2 0x00423ebf in mgs13f1 (+0x23ebf) (0x0033e658)
  3 0x7ed6d010 WINPROC_wrapper+0x4b0() in user32 (0x0033e698)
  4 0x7ed6f706 in user32 (+0xaf706) (0x0033f798)
  5 0x7ed72c9a in user32 (+0xb2c9a) (0x0033f7c8)
  6 0x7ecfe595 DefDlgProcW+0x88() in user32 (0x0033f7f8)
  7 0x7ed6cb7a WINPROC_wrapper+0x1a() in user32 (0x0033f828)
  8 0x7ed6ceae WINPROC_wrapper+0x34e() in user32 (0x0033f868)
  9 0x7ed7258c in user32 (+0xb258c) (0x0033f8a8)
  10 0x7ed35aee in user32 (+0x75aee) (0x0033f918)
  11 0x7ed3911e in user32 (+0x7911e) (0x0033f978)
  12 0x7ed395d9 SendMessageW+0x4c() in user32 (0x0033f9d8)
  13 0x7ed038a6 in user32 (+0x438a6) (0x0033fb48)
  14 0x7ed04acf CreateDialogIndirectParamAorW+0x3a() in user32 (0x0033fb68)
  15 0x7ed04bdd CreateDialogIndirectParamA+0x41() in user32 (0x0033fb98)
  16 0x0044d27a in mgs13f1 (+0x4d27a) (0x00000001)
  17 0x00000000 (0x00000000)
0x7eaccd97 ImmDestroyContext+0x31 in imm32: subl        $1,0x50(%eax)
Modules:
Module  Address                 Debug info      Name (74 modules)
PE        400000-  49b000       Export          mgs13f1
PE      10000000-10712000       Deferred        mgs3023
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e38d000-7e3bf000       Deferred        uxtheme<elf>
  \-PE  7e390000-7e3bf000       \               uxtheme
ELF     7e3bf000-7e3d3000       Deferred        midimap<elf>
  \-PE  7e3c0000-7e3d3000       \               midimap
ELF     7e3d3000-7e3f9000       Deferred        msacm32<elf>
  \-PE  7e3e0000-7e3f9000       \               msacm32
ELF     7e3f9000-7e410000       Deferred        msacm32<elf>
  \-PE  7e400000-7e410000       \               msacm32
ELF     7e410000-7e4d5000       Deferred        libasound.so.2
ELF     7e4e7000-7e51c000       Deferred        winealsa<elf>
  \-PE  7e4f0000-7e51c000       \               winealsa
ELF     7e51c000-7e525000       Deferred        libxcursor.so.1
ELF     7e525000-7e52a000       Deferred        libxfixes.so.3
ELF     7e52a000-7e52d000       Deferred        libxcomposite.so.1
ELF     7e52d000-7e533000       Deferred        libxrandr.so.2
ELF     7e533000-7e53b000       Deferred        libxrender.so.1
ELF     7e53b000-7e540000       Deferred        libxdmcp.so.6
ELF     7e540000-7e543000       Deferred        libxau.so.6
ELF     7e543000-7e634000       Deferred        libx11.so.6
ELF     7e634000-7e642000       Deferred        libxext.so.6
ELF     7e642000-7e647000       Deferred        libxxf86vm.so.1
ELF     7e647000-7e65f000       Deferred        libice.so.6
ELF     7e65f000-7e667000       Deferred        libsm.so.6
ELF     7e66e000-7e677000       Deferred        librt.so.1
ELF     7e679000-7e707000       Deferred        winex11<elf>
  \-PE  7e690000-7e707000       \               winex11
ELF     7e748000-7e768000       Deferred        libexpat.so.1
ELF     7e768000-7e793000       Deferred        libfontconfig.so.1
ELF     7e7a5000-7e7ba000       Deferred        libz.so.1
ELF     7e7ba000-7e82a000       Deferred        libfreetype.so.6
ELF     7e82a000-7e83d000       Deferred        libresolv.so.2
ELF     7e83d000-7e85b000       Deferred        iphlpapi<elf>
  \-PE  7e840000-7e85b000       \               iphlpapi
ELF     7e85b000-7e8b9000       Deferred        rpcrt4<elf>
  \-PE  7e870000-7e8b9000       \               rpcrt4
ELF     7e8b9000-7e959000       Deferred        ole32<elf>
  \-PE  7e8d0000-7e959000       \               ole32
ELF     7e959000-7e9b0000       Deferred        shlwapi<elf>
  \-PE  7e970000-7e9b0000       \               shlwapi
ELF     7e9b0000-7eab8000       Deferred        shell32<elf>
  \-PE  7e9c0000-7eab8000       \               shell32
ELF     7eab8000-7ead7000       Export          imm32<elf>
  \-PE  7eac0000-7ead7000       \               imm32
ELF     7ead7000-7eaeb000       Deferred        lz32<elf>
  \-PE  7eae0000-7eaeb000       \               lz32
ELF     7eaeb000-7eb04000       Deferred        version<elf>
  \-PE  7eaf0000-7eb04000       \               version
ELF     7eb04000-7ebc3000       Deferred        comctl32<elf>
  \-PE  7eb10000-7ebc3000       \               comctl32
ELF     7ebc3000-7ec12000       Deferred        advapi32<elf>
  \-PE  7ebd0000-7ec12000       \               advapi32
ELF     7ec12000-7ecab000       Deferred        gdi32<elf>
  \-PE  7ec20000-7ecab000       \               gdi32
ELF     7ecab000-7edeb000       Export          user32<elf>
  \-PE  7ecc0000-7edeb000       \               user32
ELF     7edeb000-7ee77000       Deferred        winmm<elf>
  \-PE  7ee00000-7ee77000       \               winmm
ELF     7ee77000-7ee8f000       Deferred        libnsl.so.1
ELF     7ee8f000-7ee98000       Deferred        libnss_compat.so.2
ELF     7efc9000-7efee000       Deferred        libm.so.6
ELF     7eff5000-7f000000       Deferred        libnss_files.so.2
ELF     b7ca5000-b7caf000       Deferred        libnss_nis.so.2
ELF     b7cb0000-b7cb4000       Deferred        libdl.so.2
ELF     b7cb4000-b7dfe000       Deferred        libc.so.6
ELF     b7dff000-b7e17000       Deferred        libpthread.so.0
ELF     b7e29000-b7f3d000       Deferred        libwine.so.1
ELF     b7f3f000-b7f5b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        00000016    0
        00000011    0
        00000010    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
00000017 (D) C:\windows\temp\MGS13f1.Exe
        00000018    0 <==
00000019 
        0000001b    0
        0000001a    0
Backtrace:
=>1 0x7eaccd97 ImmDestroyContext+0x31() in imm32 (0x0033e5ac)
  2 0x00423ebf in mgs13f1 (+0x23ebf) (0x0033e658)
  3 0x7ed6d010 WINPROC_wrapper+0x4b0() in user32 (0x0033e698)
  4 0x7ed6f706 in user32 (+0xaf706) (0x0033f798)
  5 0x7ed72c9a in user32 (+0xb2c9a) (0x0033f7c8)
  6 0x7ecfe595 DefDlgProcW+0x88() in user32 (0x0033f7f8)
  7 0x7ed6cb7a WINPROC_wrapper+0x1a() in user32 (0x0033f828)
  8 0x7ed6ceae WINPROC_wrapper+0x34e() in user32 (0x0033f868)
  9 0x7ed7258c in user32 (+0xb258c) (0x0033f8a8)
  10 0x7ed35aee in user32 (+0x75aee) (0x0033f918)
  11 0x7ed3911e in user32 (+0x7911e) (0x0033f978)
  12 0x7ed395d9 SendMessageW+0x4c() in user32 (0x0033f9d8)
  13 0x7ed038a6 in user32 (+0x438a6) (0x0033fb48)
  14 0x7ed04acf CreateDialogIndirectParamAorW+0x3a() in user32 (0x0033fb68)
  15 0x7ed04bdd CreateDialogIndirectParamA+0x41() in user32 (0x0033fb98)
  16 0x0044d27a in mgs13f1 (+0x4d27a) (0x00000001)
  17 0x00000000 (0x00000000)


```

---

### Post by Darknessboi on 2008-04-27
Help....Every time I click the launcher in the desktop it just goes to the virtual desktop and exits like in a second. Please why is it doing this?

---

### Post by Wessel on 2008-05-01
Thanks for your tutorial! I've got halo installed, I've replaced haloce.exe with the no-cd crack, then i updated ed it. En i added a starter on the desktop with your code:

```
env WINEPREFIX="/home/wessel/.wine" wine "C:\Programma Bestanden\Microsoft Games\Halo Custom Edition\haloce.exe"
```

(I have a dutch pc, so ¨Programma Bestanden¨ means Program Files)

But i still get this error:

```
preloader: Warning: failed to reserve range 00000000-00010000
fixme:win:GetWindowPlacement not supported on other process window 0x10026

```

What am I doing wrong?

[edit]The error preloader: Warning: failed to reserve range 00000000-00010000 have i solved thanks to anderbrait ([http://ubuntuforums.org/showthread.php?t=770262](http://ubuntuforums.org/showthread.php?t=770262))[/edit]

---

### Post by Darknessboi on 2008-05-04
Help! I did everything u said and when I run the exe it goes to the second Halo sign and freezes my whole entire computer, I cant even log out with CTRL Backspace when dat happens. SOMEONE PLEASE HELP

---

### Post by lordhebe on 2008-05-05
> **Darknessboi said:**
> Help! I did everything u said and when I run the exe it goes to the second Halo sign and freezes my whole entire computer, I cant even log out with CTRL Backspace when dat happens. SOMEONE PLEASE HELP

Which version of wine are you using? What version of windows is  is wine set to?

---

### Post by Darknessboi on 2008-05-05
my wine windows version is windows 2000 and im using the newest version of wine.

---

### Post by SteveZettler on 2008-05-12
I have a friend whose kids keep killing XP with malware and viruses. So I set him up with Ubuntu instead. Now he is happy but the kids are bummed because they cannot play Halo. If this work I a big thank you goes out to for your work in figuring it out.
Thanks SteveZ

---

### Post by SuperNatendo on 2008-05-20
When I run the installer, Wine opens the virtual desktop, then closes it promptly.  When I attempt installing in terminal I get this:


nathan@NDRubuntu:~/mountedimage$ wine setup.exe
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
nathan@NDRubuntu:~/mountedimage$ wine: Unhandled page fault on write access to 0x7bc337cf at address 0x7eac52a1 (thread 0021), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on write access to 0x7bc337cf in 32-bit code (0x7eac52a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eac52a1 ESP:7f22f164 EBP:7f22f18c EFLAGS:00210202(   - 00      - -RI1)
 EAX:7bc3377f EBX:7eac9ec8 ECX:7f22f198 EDX:00000000
 ESI:7f02ba08 EDI:00010052
Stack dump:
0x7f22f164:  00000100 00010052 00010052 7f22f238
0x7f22f174:  00423d76 00010052 00000000 7eac527a
0x7f22f184:  7ed9070c 00000000 7f22f238 00423ebf
0x7f22f194:  7f02ba08 7f02ba08 0044d078 00010052
0x7f22f1a4:  00000100 00010052 00000000 7f22f238
0x7f22f1b4:  7ed9070c 7f22f1f8 7b88e4e6 7edb0520
Backtrace:
=>1 0x7eac52a1 ImmDestroyContext+0x31() in imm32 (0x7f22f18c)
  2 0x00423ebf in mgs60b7 (+0x23ebf) (0x7f22f238)
  3 0x7ed6d4d8 in user32 (+0xad4d8) (0x7f22f278)
  4 0x7ed70615 in user32 (+0xb0615) (0x7f22f748)
  5 0x7ed70f40 in user32 (+0xb0f40) (0x7f22f788)
  6 0x7ecfab87 DefDlgProcW+0x87() in user32 (0x7f22f7b8)
  7 0x7ed6b69a WINPROC_wrapper+0x1a() in user32 (0x7f22f7e8)
  8 0x7ed6bd7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f828)
  9 0x7ed71151 in user32 (+0xb1151) (0x7f22f868)
  10 0x7ed3487a in user32 (+0x7487a) (0x7f22f8d8)
  11 0x7ed37afd in user32 (+0x77afd) (0x7f22f938)
  12 0x7ed37f6a SendMessageW+0x4a() in user32 (0x7f22f978)
  13 0x7ed0043c in user32 (+0x4043c) (0x7f22fb48)
  14 0x7ed01666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fb68)
  15 0x7ed01791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fb98)
0x7eac52a1 ImmDestroyContext+0x31 in imm32: subl	$1,0x50(%eax)
Modules:
Module	Address			Debug info	Name (76 modules)
PE	  400000-  49b000	Export          mgs60b7
PE	10000000-10711000	Deferred        mgs644b
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e389000-7e3bb000	Deferred        uxtheme<elf>
  \-PE	7e390000-7e3bb000	\               uxtheme
ELF	7e3bb000-7e3cf000	Deferred        midimap<elf>
  \-PE	7e3c0000-7e3cf000	\               midimap
ELF	7e3cf000-7e3f5000	Deferred        msacm32<elf>
  \-PE	7e3e0000-7e3f5000	\               msacm32
ELF	7e3f5000-7e40c000	Deferred        msacm32<elf>
  \-PE	7e400000-7e40c000	\               msacm32
ELF	7e40c000-7e4cf000	Deferred        libasound.so.2
ELF	7e4e0000-7e516000	Deferred        winealsa<elf>
  \-PE	7e4f0000-7e516000	\               winealsa
ELF	7e516000-7e51f000	Deferred        libxcursor.so.1
ELF	7e51f000-7e524000	Deferred        libxfixes.so.3
ELF	7e524000-7e527000	Deferred        libxcomposite.so.1
ELF	7e527000-7e52d000	Deferred        libxrandr.so.2
ELF	7e52d000-7e535000	Deferred        libxrender.so.1
ELF	7e535000-7e538000	Deferred        libxinerama.so.1
ELF	7e538000-7e53d000	Deferred        libxdmcp.so.6
ELF	7e53d000-7e555000	Deferred        libxcb.so.1
ELF	7e555000-7e557000	Deferred        libxcb-xlib.so.0
ELF	7e557000-7e55a000	Deferred        libxau.so.6
ELF	7e55a000-7e641000	Deferred        libx11.so.6
ELF	7e641000-7e64f000	Deferred        libxext.so.6
ELF	7e64f000-7e654000	Deferred        libxxf86vm.so.1
ELF	7e654000-7e66c000	Deferred        libice.so.6
ELF	7e66c000-7e674000	Deferred        libsm.so.6
ELF	7e685000-7e716000	Deferred        winex11<elf>
  \-PE	7e690000-7e716000	\               winex11
ELF	7e734000-7e755000	Deferred        libexpat.so.1
ELF	7e755000-7e77f000	Deferred        libfontconfig.so.1
ELF	7e790000-7e7a5000	Deferred        libz.so.1
ELF	7e7a5000-7e815000	Deferred        libfreetype.so.6
ELF	7e815000-7e828000	Deferred        libresolv.so.2
ELF	7e828000-7e846000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e846000	\               iphlpapi
ELF	7e846000-7e8a6000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a6000	\               rpcrt4
ELF	7e8a6000-7e94a000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e94a000	\               ole32
ELF	7e94a000-7e9a3000	Deferred        shlwapi<elf>
  \-PE	7e960000-7e9a3000	\               shlwapi
ELF	7e9a3000-7eaad000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eaad000	\               shell32
ELF	7eaad000-7eacc000	Export          imm32<elf>
  \-PE	7eab0000-7eacc000	\               imm32
ELF	7eacc000-7eae0000	Deferred        lz32<elf>
  \-PE	7ead0000-7eae0000	\               lz32
ELF	7eae0000-7eaf9000	Deferred        version<elf>
  \-PE	7eaf0000-7eaf9000	\               version
ELF	7eaf9000-7ebb8000	Deferred        comctl32<elf>
  \-PE	7eb00000-7ebb8000	\               comctl32
ELF	7ebb8000-7ec09000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec09000	\               advapi32
ELF	7ec09000-7eca4000	Deferred        gdi32<elf>
  \-PE	7ec20000-7eca4000	\               gdi32
ELF	7eca4000-7edea000	Export          user32<elf>
  \-PE	7ecc0000-7edea000	\               user32
ELF	7edea000-7ee78000	Deferred        winmm<elf>
  \-PE	7ee00000-7ee78000	\               winmm
ELF	7ee78000-7ee90000	Deferred        libnsl.so.1
ELF	7ee90000-7ee99000	Deferred        libnss_compat.so.2
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7d01000-b7d0b000	Deferred        libnss_nis.so.2
ELF	b7d0c000-b7d10000	Deferred        libdl.so.2
ELF	b7d10000-b7e5f000	Deferred        libc.so.6
ELF	b7e60000-b7e78000	Deferred        libpthread.so.0
ELF	b7e89000-b7f9e000	Deferred        libwine.so.1
ELF	b7fa0000-b7fbc000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000016    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000013    0
	00000012    0
00000017 
	00000019    0
	00000018    0
00000020 (D) C:\windows\temp\MGS60b7.exe
	00000021    0 <==
Backtrace:
=>1 0x7eac52a1 ImmDestroyContext+0x31() in imm32 (0x7f22f18c)
  2 0x00423ebf in mgs60b7 (+0x23ebf) (0x7f22f238)
  3 0x7ed6d4d8 in user32 (+0xad4d8) (0x7f22f278)
  4 0x7ed70615 in user32 (+0xb0615) (0x7f22f748)
  5 0x7ed70f40 in user32 (+0xb0f40) (0x7f22f788)
  6 0x7ecfab87 DefDlgProcW+0x87() in user32 (0x7f22f7b8)
  7 0x7ed6b69a WINPROC_wrapper+0x1a() in user32 (0x7f22f7e8)
  8 0x7ed6bd7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f828)
  9 0x7ed71151 in user32 (+0xb1151) (0x7f22f868)
  10 0x7ed3487a in user32 (+0x7487a) (0x7f22f8d8)
  11 0x7ed37afd in user32 (+0x77afd) (0x7f22f938)
  12 0x7ed37f6a SendMessageW+0x4a() in user32 (0x7f22f978)
  13 0x7ed0043c in user32 (+0x4043c) (0x7f22fb48)
  14 0x7ed01666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fb68)
  15 0x7ed01791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fb98)
nathan@NDRubuntu:~/mountedimage$ 

Anyone Know what I need to do?

---

### Post by Vrekk on 2008-05-21
i cant install it :( i ran the exe in the Terminal and got this

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
brett@Bretts:~$ wine: Unhandled page fault on read access to 0x00000048 at address 0x7e69963c (thread 003c), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00000048 in 32-bit code (0x7e69963c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7e69963c ESP:7f22f6b8 EBP:7f22f730 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7e702914 ECX:00000020 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x7f22f6b8:  00000000 00000000 00000000 00000000
0x7f22f6c8:  00000020 00000020 ffffffff 00000002
0x7f22f6d8:  000010a0 00001117 7f22f740 00000020
0x7f22f6e8:  00000000 7f272cd4 7f272cd4 00000000
0x7f22f6f8:  00000000 00004f4b 7f22f730 7ec5bf2f
0x7f22f708:  7ec8cc00 00000000 00000020 00000020
Backtrace:
=>1 0x7e69963c X11DRV_GetBitmapBits+0x29c() in winex11 (0x7f22f730)
  2 0x7ec2ed36 GetBitmapBits+0x196() in gdi32 (0x7f22f7a0)
  3 0x7ece72fe CreateIconFromResourceEx+0x8de() in user32 (0x7f22f840)
  4 0x7ece790a in user32 (+0x2790a) (0x7f22f8c0)
  5 0x7ece8a20 LoadImageW+0x2d0() in user32 (0x7f22f970)
  6 0x7ece90d6 LoadImageA+0x56() in user32 (0x7f22fa50)
  7 0x7ece9677 LoadIconA+0x97() in user32 (0x7f22fa80)
0x7e69963c X11DRV_GetBitmapBits+0x29c in winex11: call	*0x48(%edx)
Modules:
Module	Address			Debug info	Name (76 modules)
PE	  400000-  49b000	Deferred        mgsda85
PE	10000000-10711000	Deferred        mgsdbea
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e390000-7e3c2000	Deferred        uxtheme<elf>
  \-PE	7e3a0000-7e3c2000	\               uxtheme
ELF	7e3c2000-7e3d6000	Deferred        midimap<elf>
  \-PE	7e3d0000-7e3d6000	\               midimap
ELF	7e3d6000-7e3fc000	Deferred        msacm32<elf>
  \-PE	7e3e0000-7e3fc000	\               msacm32
ELF	7e3fc000-7e413000	Deferred        msacm32<elf>
  \-PE	7e400000-7e413000	\               msacm32
ELF	7e413000-7e4d6000	Deferred        libasound.so.2
ELF	7e4e5000-7e51b000	Deferred        winealsa<elf>
  \-PE	7e4f0000-7e51b000	\               winealsa
ELF	7e51b000-7e524000	Deferred        libxcursor.so.1
ELF	7e524000-7e529000	Deferred        libxfixes.so.3
ELF	7e529000-7e52c000	Deferred        libxcomposite.so.1
ELF	7e52c000-7e532000	Deferred        libxrandr.so.2
ELF	7e532000-7e53a000	Deferred        libxrender.so.1
ELF	7e53a000-7e53d000	Deferred        libxinerama.so.1
ELF	7e53d000-7e555000	Deferred        libxcb.so.1
ELF	7e555000-7e63c000	Deferred        libx11.so.6
ELF	7e63c000-7e64a000	Deferred        libxext.so.6
ELF	7e64a000-7e662000	Deferred        libice.so.6
ELF	7e662000-7e66a000	Deferred        libsm.so.6
ELF	7e679000-7e70a000	Export          winex11<elf>
  \-PE	7e690000-7e70a000	\               winex11
ELF	7e72f000-7e750000	Deferred        libexpat.so.1
ELF	7e750000-7e77a000	Deferred        libfontconfig.so.1
ELF	7e789000-7e79e000	Deferred        libz.so.1
ELF	7e79e000-7e80e000	Deferred        libfreetype.so.6
ELF	7e80e000-7e821000	Deferred        libresolv.so.2
ELF	7e821000-7e83f000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e83f000	\               iphlpapi
ELF	7e83f000-7e89f000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e89f000	\               rpcrt4
ELF	7e89f000-7e943000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e943000	\               ole32
ELF	7e943000-7e99c000	Deferred        shlwapi<elf>
  \-PE	7e950000-7e99c000	\               shlwapi
ELF	7e99c000-7eaa6000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eaa6000	\               shell32
ELF	7eaa6000-7eac5000	Deferred        imm32<elf>
  \-PE	7eab0000-7eac5000	\               imm32
ELF	7eac5000-7ead9000	Deferred        lz32<elf>
  \-PE	7ead0000-7ead9000	\               lz32
ELF	7ead9000-7eaf2000	Deferred        version<elf>
  \-PE	7eae0000-7eaf2000	\               version
ELF	7eaf2000-7ebb1000	Deferred        comctl32<elf>
  \-PE	7eb00000-7ebb1000	\               comctl32
ELF	7ebb1000-7ec02000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec02000	\               advapi32
ELF	7ec02000-7ec9d000	Export          gdi32<elf>
  \-PE	7ec10000-7ec9d000	\               gdi32
ELF	7ec9d000-7ede3000	Export          user32<elf>
  \-PE	7ecc0000-7ede3000	\               user32
ELF	7ede3000-7ee71000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee71000	\               winmm
ELF	7ee71000-7ee7c000	Deferred        libnss_files.so.2
ELF	7ee7c000-7ee94000	Deferred        libnsl.so.1
ELF	7ee94000-7ee9d000	Deferred        libnss_compat.so.2
ELF	7ee9d000-7eea2000	Deferred        libxdmcp.so.6
ELF	7eea2000-7eea4000	Deferred        libxcb-xlib.so.0
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff1000-7eff6000	Deferred        libxxf86vm.so.1
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d31000-b7d34000	Deferred        libxau.so.6
ELF	b7d3b000-b7d3f000	Deferred        libdl.so.2
ELF	b7d3f000-b7e8e000	Deferred        libc.so.6
ELF	b7e8f000-b7ea7000	Deferred        libpthread.so.0
ELF	b7eb6000-b7fcb000	Deferred        libwine.so.1
ELF	b7fcd000-b7fe9000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000027    0
	00000023    0
	00000022    0
	00000021    0
	00000020    0
	0000001f    0
	00000009    0
0000000c 
	00000016    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000014    0
	00000012    0
0000003b (D) C:\windows\temp\MGSda85.exe
	0000003c    0 <==
Backtrace:
=>1 0x7e69963c X11DRV_GetBitmapBits+0x29c() in winex11 (0x7f22f730)
  2 0x7ec2ed36 GetBitmapBits+0x196() in gdi32 (0x7f22f7a0)
  3 0x7ece72fe CreateIconFromResourceEx+0x8de() in user32 (0x7f22f840)
  4 0x7ece790a in user32 (+0x2790a) (0x7f22f8c0)
  5 0x7ece8a20 LoadImageW+0x2d0() in user32 (0x7f22f970)
  6 0x7ece90d6 LoadImageA+0x56() in user32 (0x7f22fa50)
  7 0x7ece9677 LoadIconA+0x97() in user32 (0x7f22fa80)
err:syslevel:_CheckNotSysLevel Holding lock 0x7ec8cc00 level 3
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7eda9520, level 2): Holding 0x7ec8cc00, level 3. Expect deadlock!

Any ideas anyone?

---

### Post by Half-Left on 2008-05-21
Make sure you run the updater in the directory and update Halo, should work after that. Also if you getting really slow menu then just change the resolution to higher, I got it working with only a few graphical glitches, 0.9.59.

---

### Post by Vrekk on 2008-05-21
Hey i got mine working pretty well. i Uninstalled wine and then resinatalled with 9.60 and it can be played now. But i do have a graphic error that kinda bugs me (as shown below) but it sometimes dosent happen  and i my mouse will occanisly leave the screen witch bugs me in battle.

---

### Post by aliayaz on 2008-05-29
the way to fix the flash light go to properties then the launcher tab and just add this at the end -use14 it should fix it that's what i heard and to fix the mouse thing just go to configure wine and allow direct x to keep mouse inside the box

---

### Post by Dark Ares on 2008-05-30
has anyone found out a way to solve the problems that me and SuperNatendo & VreKK have?? i have wine v9.59. Any help?

---

### Post by EnergySamus on 2008-05-30
See that area in my sig where it says "Soon to be Ubuntu 8.04"... Well soon to be now means today! Thank you so much! I can't wait to pwn those Covenant frooblets. I need something to play on my laptop, since I can't take my Xbox 360 with me!


EnergySamus

---

### Post by brodiepearce on 2008-06-02
I can't get the installer to start, and I've inserted mfc42.dll into System32 etc. etc..  This is everything I'm getting from starting Setup.Exe with wine to when it dies, hard:

```

user@host:/media/mnt$ wine Setup.Exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
brodiepearce@brodsta:/media/mnt$ preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
wine: Unhandled page fault on write access to 0x7bc337cf at address 0x7eabe2a1 (thread 001d), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on write access to 0x7bc337cf in 32-bit code (0x7eabe2a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eabe2a1 ESP:7f22f164 EBP:7f22f18c EFLAGS:00210206(   - 00      - RIP1)
 EAX:7bc3377f EBX:7eac2ec8 ECX:7f22f198 EDX:00000000
 ESI:7f026750 EDI:00010026
Stack dump:
0x7f22f164:  00000100 00010026 00010026 7f22f238
0x7f22f174:  00423d76 00010026 00000000 7eabe27a
0x7f22f184:  7ed8970c 00000000 7f22f238 00423ebf
0x7f22f194:  7f026750 7f026750 0044d078 00010026
0x7f22f1a4:  00000100 00010026 00000000 7f22f238
0x7f22f1b4:  7ed8970c 7f22f1f8 7b88e4e6 7eda9520
Backtrace:
=>1 0x7eabe2a1 ImmDestroyContext+0x31() in imm32 (0x7f22f18c)
  2 0x00423ebf in mgs200 (+0x23ebf) (0x7f22f238)
  3 0x7ed664d8 in user32 (+0xa64d8) (0x7f22f278)
  4 0x7ed69615 in user32 (+0xa9615) (0x7f22f748)
  5 0x7ed69f40 in user32 (+0xa9f40) (0x7f22f788)
  6 0x7ecf3b87 DefDlgProcW+0x87() in user32 (0x7f22f7b8)
  7 0x7ed6469a WINPROC_wrapper+0x1a() in user32 (0x7f22f7e8)
  8 0x7ed64d7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f828)
  9 0x7ed6a151 in user32 (+0xaa151) (0x7f22f868)
  10 0x7ed2d87a in user32 (+0x6d87a) (0x7f22f8d8)
  11 0x7ed30afd in user32 (+0x70afd) (0x7f22f938)
  12 0x7ed30f6a SendMessageW+0x4a() in user32 (0x7f22f978)
  13 0x7ecf943c in user32 (+0x3943c) (0x7f22fb48)
  14 0x7ecfa666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fb68)
  15 0x7ecfa791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fb98)
0x7eabe2a1 ImmDestroyContext+0x31 in imm32: subl	$1,0x50(%eax)
Modules:
Module	Address			Debug info	Name (76 modules)
PE	  400000-  49b000	Export          mgs200
PE	10000000-10711000	Deferred        mgs3d3
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e395000-7e3c7000	Deferred        uxtheme<elf>
  \-PE	7e3a0000-7e3c7000	\               uxtheme
ELF	7e3c7000-7e3db000	Deferred        midimap<elf>
  \-PE	7e3d0000-7e3db000	\               midimap
ELF	7e3db000-7e401000	Deferred        msacm32<elf>
  \-PE	7e3e0000-7e401000	\               msacm32
ELF	7e401000-7e418000	Deferred        msacm32<elf>
  \-PE	7e410000-7e418000	\               msacm32
ELF	7e418000-7e4db000	Deferred        libasound.so.2
ELF	7e4ea000-7e520000	Deferred        winealsa<elf>
  \-PE	7e4f0000-7e520000	\               winealsa
ELF	7e520000-7e529000	Deferred        libxcursor.so.1
ELF	7e529000-7e52e000	Deferred        libxfixes.so.3
ELF	7e52e000-7e531000	Deferred        libxcomposite.so.1
ELF	7e531000-7e537000	Deferred        libxrandr.so.2
ELF	7e537000-7e53f000	Deferred        libxrender.so.1
ELF	7e53f000-7e542000	Deferred        libxinerama.so.1
ELF	7e542000-7e55a000	Deferred        libxcb.so.1
ELF	7e55a000-7e641000	Deferred        libx11.so.6
ELF	7e641000-7e64f000	Deferred        libxext.so.6
ELF	7e64f000-7e667000	Deferred        libice.so.6
ELF	7e667000-7e66f000	Deferred        libsm.so.6
ELF	7e67e000-7e70f000	Deferred        winex11<elf>
  \-PE	7e690000-7e70f000	\               winex11
ELF	7e72f000-7e750000	Deferred        libexpat.so.1
ELF	7e750000-7e77a000	Deferred        libfontconfig.so.1
ELF	7e789000-7e79e000	Deferred        libz.so.1
ELF	7e79e000-7e80e000	Deferred        libfreetype.so.6
ELF	7e80e000-7e821000	Deferred        libresolv.so.2
ELF	7e821000-7e83f000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e83f000	\               iphlpapi
ELF	7e83f000-7e89f000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e89f000	\               rpcrt4
ELF	7e89f000-7e943000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e943000	\               ole32
ELF	7e943000-7e99c000	Deferred        shlwapi<elf>
  \-PE	7e950000-7e99c000	\               shlwapi
ELF	7e99c000-7eaa6000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eaa6000	\               shell32
ELF	7eaa6000-7eac5000	Export          imm32<elf>
  \-PE	7eab0000-7eac5000	\               imm32
ELF	7eac5000-7ead9000	Deferred        lz32<elf>
  \-PE	7ead0000-7ead9000	\               lz32
ELF	7ead9000-7eaf2000	Deferred        version<elf>
  \-PE	7eae0000-7eaf2000	\               version
ELF	7eaf2000-7ebb1000	Deferred        comctl32<elf>
  \-PE	7eb00000-7ebb1000	\               comctl32
ELF	7ebb1000-7ec02000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec02000	\               advapi32
ELF	7ec02000-7ec9d000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec9d000	\               gdi32
ELF	7ec9d000-7ede3000	Export          user32<elf>
  \-PE	7ecc0000-7ede3000	\               user32
ELF	7ede3000-7ee71000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee71000	\               winmm
ELF	7ee71000-7ee7c000	Deferred        libnss_files.so.2
ELF	7ee7c000-7ee94000	Deferred        libnsl.so.1
ELF	7ee94000-7ee9d000	Deferred        libnss_compat.so.2
ELF	7ee9d000-7eea2000	Deferred        libxdmcp.so.6
ELF	7eea2000-7eea4000	Deferred        libxcb-xlib.so.0
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff1000-7eff6000	Deferred        libxxf86vm.so.1
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7ca0000-b7ca3000	Deferred        libxau.so.6
ELF	b7caa000-b7cae000	Deferred        libdl.so.2
ELF	b7cae000-b7dfd000	Deferred        libc.so.6
ELF	b7dfe000-b7e16000	Deferred        libpthread.so.0
ELF	b7e25000-b7f3a000	Deferred        libwine.so.1
ELF	b7f3c000-b7f58000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000001b    0
	00000016    0
	00000014    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000013    0
	00000012    0
00000017 
	0000001a    0
	00000019    0
	00000018    0
0000001c (D) C:\windows\temp\MGS200.Exe
	0000001d    0 <==
0000001e 
	00000020    0
	0000001f    0
Backtrace:
=>1 0x7eabe2a1 ImmDestroyContext+0x31() in imm32 (0x7f22f18c)
  2 0x00423ebf in mgs200 (+0x23ebf) (0x7f22f238)
  3 0x7ed664d8 in user32 (+0xa64d8) (0x7f22f278)
  4 0x7ed69615 in user32 (+0xa9615) (0x7f22f748)
  5 0x7ed69f40 in user32 (+0xa9f40) (0x7f22f788)
  6 0x7ecf3b87 DefDlgProcW+0x87() in user32 (0x7f22f7b8)
  7 0x7ed6469a WINPROC_wrapper+0x1a() in user32 (0x7f22f7e8)
  8 0x7ed64d7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f828)
  9 0x7ed6a151 in user32 (+0xaa151) (0x7f22f868)
  10 0x7ed2d87a in user32 (+0x6d87a) (0x7f22f8d8)
  11 0x7ed30afd in user32 (+0x70afd) (0x7f22f938)
  12 0x7ed30f6a SendMessageW+0x4a() in user32 (0x7f22f978)
  13 0x7ecf943c in user32 (+0x3943c) (0x7f22fb48)
  14 0x7ecfa666 CreateDialogIndirectParamAorW+0x36() in user32 (0x7f22fb68)
  15 0x7ecfa791 CreateDialogIndirectParamA+0x41() in user32 (0x7f22fb98)

```

Any help would be much appreciated.  :)

*edit*
A few posters earlier in this thread seem to have received the same problem and had success by installing the latest version of wine (9.6?), I might give that a shot.

---

### Post by Half-Left on 2008-06-02
It is recommended that you modify your winecfg for ALSA and Windows XP/2K.

1) Download mfc42.dll from: [http://www.dll-files.com/dllindex/download.php?mfc42download0UKiRIdLjP](http://www.dll-files.com/dllindex/download.php?mfc42download0UKiRIdLjP)

2) Unzip mfc42.dll and place it into Wine's system32 folder.

3) Mount your Halo CD and run setup.exe.

4) Go through Setup as normal.

5) Go to Halo's folder on your HardDisk, and run haloupdate.exe and wait for it to update.

6) Download the version 1.07 no-cd patch here: [http://www.gameburnworld.com/dl/dl.php?file=HaloCombatEvolvedv1.07NoCDFixedexeEng.rar](http://www.gameburnworld.com/dl/dl.php?file=HaloCombatEvolvedv1.07NoCDFixedexeEng.rar)

^^^ Kudos to GameBurnWorld for the patch. =]

7) Extract and place it in your Halo folder (replace the older one).

8) Run halo.exe as is or with the arguments below, depending on your preference and system, then enjoy!


 
Command Line Arguments

If you feel adventurous, you can try these other arguments, as they may affect your gameplay to the better or the worse.
-?

Displays a list of all arguments.

-nosound
Disables all sound.

-novideo
Disables video playback.

-nojoystick 
Disables joystick/gamepads.

-nogamma
Disables adjustment of gamma.

-useff
Forces the game to run as a fixed function card.

-use11
Forces the game to run as a shader 1.1 card.

-use20
Forces the game to run as a shader 2.0 card.

-safemode
Disables as much as possible from the game.

-window
Runs the game in a window.

-width640
Forces the game to run at 640x480.

-vidmode w,h,r 
Forces the game to run at width, height, refresh rate.

-adapter x
Forces the game to run fullscreen on a multimon adaptor.

-port x
Server port address used when hosting games.

-cport x
Client port address used when joining games.

-ip x.x.x.x
Server IP address used when you have multiple IP addresses.

-screenshot
Enables the "Print Screen" key to generate screenshots

-timedemo
Runs four movies and writes out timedemo.txt.

-console
Enables the debugging console.

---

### Post by Judo on 2008-06-03
I'm just here to confirm Half-Left's method works.  I was looking for a good no-CD crack.  And yes, I bought the game.

There's a little mouse skipping, if that's understandable.  The frame rate is smooth but the mouse appears to cause some effect similar to a low frame rate.  Hopefully, that's just a bug in WINE-rc3 that will be fixed in 1.0.

---

### Post by Vrekk on 2008-06-03
to fix brodiepearce's problem. the FAILED TO RESERVER... needs fixed, this should do it. [http://ubuntuforums.org/showthread.php?p=4852878](http://ubuntuforums.org/showthread.php?p=4852878) it is a prolem that appers in Hardy

---

### Post by Vrekk on 2008-06-04
Hey it works pretty well with Crossover 7.0 the mouse is a little jumpy.  But it keeps leaving the windows on me still.  I have it set to Allow Direct X apps to stop the mouse from leaving the window, but i still can if i turn it enoufg, which is offten in combat.  Also the game wount fully close i have to force it too

---

### Post by servvs on 2008-06-07
I am getting something similar to what brodie is getting. 

```
 Unhandled page fault on write access to 0x7bc337cf at address 0x7eac02a1 (thread 0018), starting debugger...
Unhandled exception: page fault on write access to 0x7bc337cf in 32-bit code (0x7eac02a1).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eac02a1 ESP:0033f164 EBP:0033f18c EFLAGS:00010202(   - 00      - -RI1)
 EAX:7bc3377f EBX:7eac4ec8 ECX:0033f198 EDX:00000000
 ESI:001340d0 EDI:00010026
Stack dump:
0x0033f164:  00000100 00010026 00010026 0033f238
0x0033f174:  00423d76 00010026 00000000 7eac027a
0x0033f184:  7ed8b70c 00000000 0033f238 00423ebf
0x0033f194:  001340d0 001340d0 0044d078 00010026
0x0033f1a4:  00000100 00010026 00000000 0033f238
0x0033f1b4:  7ed8b70c 0033f1f8 7b88e4e6 7edab520
Backtrace:
=>1 0x7eac02a1 ImmDestroyContext+0x31() in imm32 (0x0033f18c)
  2 0x00423ebf in mgs2dd (+0x23ebf) (0x0033f238)
  3 0x7ed684d8 in user32 (+0xa84d8) (0x0033f278)
  4 0x7ed6b615 in user32 (+0xab615) (0x0033f748)
  5 0x7ed6bf40 in user32 (+0xabf40) (0x0033f788)
  6 0x7ecf5b87 DefDlgProcW+0x87() in user32 (0x0033f7b8)
  7 0x7ed6669a WINPROC_wrapper+0x1a() in user32 (0x0033f7e8)
  8 0x7ed66d7e WINPROC_wrapper+0x6fe() in user32 (0x0033f828)
  9 0x7ed6c151 in user32 (+0xac151) (0x0033f868)
  10 0x7ed2f87a in user32 (+0x6f87a) (0x0033f8d8)
  11 0x7ed32afd in user32 (+0x72afd) (0x0033f938)
  12 0x7ed32f6a SendMessageW+0x4a() in user32 (0x0033f978)
  13 0x7ecfb43c in user32 (+0x3b43c) (0x0033fb48)
  14 0x7ecfc666 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033fb68)
  15 0x7ecfc791 CreateDialogIndirectParamA+0x41() in user32 (0x0033fb98)
  16 0x0044d27a in mgs2dd (+0x4d27a) (0x00000001)
  17 0x00000000 (0x00000000)
0x7eac02a1 ImmDestroyContext+0x31 in imm32: subl	$1,0x50(%eax)
Modules:
Module	Address			Debug info	Name (76 modules)
PE	  400000-  49b000	Export          mgs2dd
PE	10000000-10711000	Deferred        mgs577
ELF	7b800000-7b92c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca5000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca5000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e39e000-7e3d0000	Deferred        uxtheme<elf>
  \-PE	7e3a0000-7e3d0000	\               uxtheme
ELF	7e3d0000-7e3e4000	Deferred        midimap<elf>
  \-PE	7e3e0000-7e3e4000	\               midimap
ELF	7e3e4000-7e40a000	Deferred        msacm32<elf>
  \-PE	7e3f0000-7e40a000	\               msacm32
ELF	7e40a000-7e421000	Deferred        msacm32<elf>
  \-PE	7e410000-7e421000	\               msacm32
ELF	7e421000-7e4e4000	Deferred        libasound.so.2
ELF	7e4e4000-7e51a000	Deferred        winealsa<elf>
  \-PE	7e4f0000-7e51a000	\               winealsa
ELF	7e51a000-7e523000	Deferred        libxcursor.so.1
ELF	7e523000-7e528000	Deferred        libxfixes.so.3
ELF	7e528000-7e52b000	Deferred        libxcomposite.so.1
ELF	7e52b000-7e531000	Deferred        libxrandr.so.2
ELF	7e531000-7e539000	Deferred        libxrender.so.1
ELF	7e539000-7e53e000	Deferred        libxdmcp.so.6
ELF	7e53e000-7e556000	Deferred        libxcb.so.1
ELF	7e556000-7e63d000	Deferred        libx11.so.6
ELF	7e63d000-7e64b000	Deferred        libxext.so.6
ELF	7e64b000-7e663000	Deferred        libice.so.6
ELF	7e663000-7e66b000	Deferred        libsm.so.6
ELF	7e679000-7e70a000	Deferred        winex11<elf>
  \-PE	7e690000-7e70a000	\               winex11
ELF	7e732000-7e753000	Deferred        libexpat.so.1
ELF	7e753000-7e77d000	Deferred        libfontconfig.so.1
ELF	7e77d000-7e782000	Deferred        libxxf86vm.so.1
ELF	7e78b000-7e7a0000	Deferred        libz.so.1
ELF	7e7a0000-7e810000	Deferred        libfreetype.so.6
ELF	7e810000-7e823000	Deferred        libresolv.so.2
ELF	7e823000-7e841000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e841000	\               iphlpapi
ELF	7e841000-7e8a1000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8a1000	\               rpcrt4
ELF	7e8a1000-7e945000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e945000	\               ole32
ELF	7e945000-7e99e000	Deferred        shlwapi<elf>
  \-PE	7e950000-7e99e000	\               shlwapi
ELF	7e99e000-7eaa8000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eaa8000	\               shell32
ELF	7eaa8000-7eac7000	Export          imm32<elf>
  \-PE	7eab0000-7eac7000	\               imm32
ELF	7eac7000-7eadb000	Deferred        lz32<elf>
  \-PE	7ead0000-7eadb000	\               lz32
ELF	7eadb000-7eaf4000	Deferred        version<elf>
  \-PE	7eae0000-7eaf4000	\               version
ELF	7eaf4000-7ebb3000	Deferred        comctl32<elf>
  \-PE	7eb00000-7ebb3000	\               comctl32
ELF	7ebb3000-7ec04000	Deferred        advapi32<elf>
  \-PE	7ebc0000-7ec04000	\               advapi32
ELF	7ec04000-7ec9f000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec9f000	\               gdi32
ELF	7ec9f000-7ede5000	Export          user32<elf>
  \-PE	7ecc0000-7ede5000	\               user32
ELF	7ede5000-7ee73000	Deferred        winmm<elf>
  \-PE	7edf0000-7ee73000	\               winmm
ELF	7ee73000-7ee7e000	Deferred        libnss_files.so.2
ELF	7ee7e000-7ee96000	Deferred        libnsl.so.1
ELF	7ee96000-7ee9f000	Deferred        libnss_compat.so.2
ELF	7ee9f000-7eea2000	Deferred        libxinerama.so.1
ELF	7efcd000-7eff2000	Deferred        libm.so.6
ELF	7eff4000-7eff6000	Deferred        libxcb-xlib.so.0
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d21000-b7d24000	Deferred        libxau.so.6
ELF	b7d28000-b7d2c000	Deferred        libdl.so.2
ELF	b7d2c000-b7e7b000	Deferred        libc.so.6
ELF	b7e7c000-b7e94000	Deferred        libpthread.so.0
ELF	b7ea2000-b7fb7000	Deferred        libwine.so.1
ELF	b7fb9000-b7fd5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000016    0
	00000013    0
	00000010    0
	0000000e    0
	0000000d    0
00000011 
	00000015    0
	00000014    0
	00000012    0
00000017 (D) C:\windows\temp\MGS2dd.Exe
	00000018    0 <==
00000019 
	0000001b    0
	0000001a    0
Backtrace:
=>1 0x7eac02a1 ImmDestroyContext+0x31() in imm32 (0x0033f18c)
  2 0x00423ebf in mgs2dd (+0x23ebf) (0x0033f238)
  3 0x7ed684d8 in user32 (+0xa84d8) (0x0033f278)
  4 0x7ed6b615 in user32 (+0xab615) (0x0033f748)
  5 0x7ed6bf40 in user32 (+0xabf40) (0x0033f788)
  6 0x7ecf5b87 DefDlgProcW+0x87() in user32 (0x0033f7b8)
  7 0x7ed6669a WINPROC_wrapper+0x1a() in user32 (0x0033f7e8)
  8 0x7ed66d7e WINPROC_wrapper+0x6fe() in user32 (0x0033f828)
  9 0x7ed6c151 in user32 (+0xac151) (0x0033f868)
  10 0x7ed2f87a in user32 (+0x6f87a) (0x0033f8d8)
  11 0x7ed32afd in user32 (+0x72afd) (0x0033f938)
  12 0x7ed32f6a SendMessageW+0x4a() in user32 (0x0033f978)
  13 0x7ecfb43c in user32 (+0x3b43c) (0x0033fb48)
  14 0x7ecfc666 CreateDialogIndirectParamAorW+0x36() in user32 (0x0033fb68)
  15 0x7ecfc791 CreateDialogIndirectParamA+0x41() in user32 (0x0033fb98)
  16 0x0044d27a in mgs2dd (+0x4d27a) (0x00000001)
  17 0x00000000 (0x00000000)

```

It just doesn't have the stuff at the beggining, and it won't launch the installer at all, any help would be awesome, using hardy btw.

---

### Post by Vrekk on 2008-06-07
I am not sure but i think that is a bug with wine 1 rc3, downgrade to v9.6 or something then upgrade back up

EDIT: This should help brodies problem too, even if you arent running wine 1 rc3

---

### Post by servvs on 2008-06-07
TY Vrekk, I didn't even realize but I had version 9.59, updated to 9.6 and at least the installer works now, so now I can test it out.

---

### Post by Vrekk on 2008-06-07
Your welcome servvs tell us if it works for ya

---

### Post by EnergySamus on 2008-06-08
Thanks for this excellent post! I have a question: When you get to the install part there are little check boxes on the screen. They say: install for all users, install game spy arcade, and Create desktop icon. Should I uncheck all of these? 

Thanks
EnergySamus

Update: I now have the game installed. I told it to create a desktop icon, but it didn't. After installing the no-cd crack, I used the line env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" (with cris becoming my name, of course). It tells me: Cannot find Z: home/myname/config.text

Does anyone know?

EnergySamus

---

### Post by Vrekk on 2008-06-09
> **EnergySamus said:**
> Thanks for this excellent post! I have a question: When you get to the install part there are little check boxes on the screen. They say: install for all users, install game spy arcade, and Create desktop icon. Should I uncheck all of these? 

Thanks
EnergySamus

Update: I now have the game installed. I told it to create a desktop icon, but it didn't. After installing the no-cd crack, I used the line env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" (with cris becoming my name, of course). It tells me: Cannot find Z: home/myname/config.text

Does anyone know?

EnergySamus
Ok EnergySamus, what i would do it go to Applications -> Wine -> Programs -> Microsoft Games -> Halo -> the click and drag the lanuch in the start menu onto the desktop that will make one for you.  Add the -novideo line and you would be running fine

On a differnt note, i am not sure if my game is updating or not.  When i run the patching program it says updating the game and then just closes.  If i try to press multiplayer it says i am not fully upto date.  Is there a way to fix this, becuase it may help my stupid mouse leaving the screen problem

---

### Post by EnergySamus on 2008-06-10
> **Vrekk said:**
> Ok EnergySamus, what i would do it go to Applications -> Wine -> Wine Apps -> Microsoft Games -> Halo -> the click and drag the lanuch in the start menu onto the desktop that will make one for you.  Add the -novideo line and you would be running fine

On a differnt note, i am not sure if my game is updating or not.  When i run the patching program it says updating the game and then just closes.  If i try to press multiplayer it says i am not fully upto date.  Is there a way to fix this, becuase it may help my stupid mouse leaving the screen problem

Thanks!!! For me the updater is working. I am not sure what your issue is. But I do have a fix for the mouse: Use Wine RC1. This is supposed to be the best for Halo, and I am currently having no issues (or mouse issues) with Halo!

EnergySamus

Edit: I am running mine on my laptop, if that matters.

---

### Post by Vrekk on 2008-06-10
Found a fix for my mouse problem FULLSCREEN.  i found a nice way to do it.  Set you vitrual desktop to fullscreen (for me 1024*768) then set it so that the window manager dose not manager or decorate the virtual desktop.  The i just added the -vidmode 1024,768,60 thing in and BOOM fullscree.  And thanks engerysaumus, the mouse movement is more steady with wine rcl1

---

### Post by bronco 2010 on 2008-06-20
Any idea if Phears Halo Hack would work?  Or any other mods for Halo on Wine?

---

### Post by knight666 on 2008-06-24
Hi,

I installed Halo on a Windows box on my external harddrive.
I used a nocd crack to get the game running at all, but when I try to run it, using the following:
> env WINEPREFIX="/home/knight666/.wine" wine "/media/disk-5/Program Files/Microsoft Games/Halo/Halo.eXe" -novideo
it says:
> Halo - Fatal Error
Problem: Cannot find 'Z:\windows\config.txt'
Alright, so I go into winecfg and I change C:\ to /media/disk-5 and try again.
Now it says:
> Halo - Fatal Error
Problem: Cannot find 'N:\\config.txt'

I do not have enough space on / to install Halo there, how can I go around this problem? :(

---

### Post by Vrekk on 2008-06-24
knight, do you have wine set up to see your external drive? Try opening winecfg ,drives (i think i cant access my computer right now), and add in you external hd.

---

### Post by knight666 on 2008-06-25
Well, yeah. :\
I add it as N:\, it complains it can't find it as Z:\.
I add it as Z:\ TOO, it complains it can't find it as S:\.
Etcetera ad infinitum!

---

### Post by knavarathna92 on 2008-06-29
Hey guys I have a small problem.  I've followed this guide.  I updated and replaced halo.exe. with the 1.07 no-cd crack but when I click the launcher all I get is a black screen encompassing my entire monitor.  My command is as follows: 

env WINEPREFIX="/home/kasun/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" -novideo -vidmode 1024,768,60

BTW, I had problems on XP since my graphics card was too new to be supported on first setup but I remember that some updates fixed this on windows but wasn't sure if it was the game update.  My card is an ATI radeon X1350 pro.

Also if it means anything, I keep on downloading & installing the same updates over and over again when I run the update file.

---

### Post by ToaStOmGi on 2008-06-30
Where is the "fake c drive"?

---

### Post by ToaStOmGi on 2008-06-30
Ok so i cant get halo to run with wine. The setup.exe. I click open with Wine Windows Simulator, but nothing happens.

---

### Post by Vrekk on 2008-06-30
did you try running it in the termail?

```
wine '*path to cd/[I]setup.exe*[/I]
``` if you still get an error post the results

---

### Post by ToaStOmGi on 2008-06-30
I dont get an error at all when i try to run it. Just, nothing happens. When i run it in the terminal it says command not found.

---

### Post by filip102 on 2008-07-05
I have some interesting bug.... can somebody tell me wtf is that? :confused:

[IMG]http://img393.imageshack.us/img393/1296/wtfxu2.jpg[/IMG]

ToaStOmGi: I hade some problem like you, just install new wine.

---

### Post by ytrium on 2008-07-19
I had this problem, but fixed it by starting it using a bash script (my first ever script, so go easy on me ;) )  I thought that maybe Halo was having a hard time finding itself.

Halo.sh
```

#!/bin/bash

cd /home/ytrium/.wine/drive_c/Halo
./halo.exe -novideo -useff

```

cd points to my directory
./halo.exe starts the program

My script runs really slow if I run in terminal, due to some other fixme: problem constantly reporting, so I've been just using Run.

Now, if I could just get all the graphics to display.  Having shader issues.

> **knight666 said:**
> Hi,

I installed Halo on a Windows box on my external harddrive.
I used a nocd crack to get the game running at all, but when I try to run it, using the following:

it says:

Alright, so I go into winecfg and I change C:\ to /media/disk-5 and try again.
Now it says:


I do not have enough space on / to install Halo there, how can I go around this problem? :(

---

### Post by arvinkebob on 2008-08-10
Yaharrr! Halo 1.08 update came out a few days ago! NO disc check!!! Online anybody?

---

### Post by PLAY3ER on 2008-08-20
hey all, sorry to bring up an old post, but didn't wanna make a new one, i have halo installed and all, but it will not update, and, i never updated it, the auto installer always had, i say has, because windows xp has ticked me off for the last time, and im going Ubuntu for my Destop/Gamming.

Thanks for any and all help

btw: im not new to Ubuntu, just new to trying to get halo to work :P

---

### Post by DavidFromCanada on 2008-08-25
Hey I need help, I can't get halo to update to 1.08. It just runs the installer and quits.

---

### Post by hac13 on 2008-09-07
Hey thanks for the instructions. When I try to run Halo it goes through some videos then says that it has "encountered a problem." I don't know how to make sense of any of the output but it would be great if somebody could decipher it:
> 
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x136978) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x57602c8) : stub
fixme:imm:ImmReleaseContext (0x10026, 0x136ca8): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x136ca8): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-4,-23)-(644,484)
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1506
fixme:d3d:state_psizemin WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
fixme:d3d:state_multisampmask (WINED3DRS_MULTISAMPLEMASK,0) not yet implemented
fixme:d3d:state_psizemax WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 0.000000
fixme:d3d:handleStreams Tangent and binormal bump mapping is only valid with vertex shaders
fixme:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1506
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0x8bdfaa0
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Halo"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000048,0x7e2e280c,0x7e2e23c4): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x00000048,0x12afa8,0x7e2e23c4): stub
err:eventlog:ReportEventW L"halo.exe"
err:eventlog:ReportEventW L"1.0.1.580"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"0.0.0.0"
err:eventlog:ReportEventW L"00000000"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.


---

### Post by Vrekk on 2008-09-08
did you add int the -novideo to the lancher like the instrustions say?

---

### Post by jack frost on 2008-09-20
> **lordhebe said:**
> In order to help those getting it working, here are the exact steps I followed to get Halo working.

**This guide will also work for Crossover. Halo works following this guide for 6.1 and 6.2. 6.2 sees better performance and the lack of the "window" bug, meaning until the crash on startup regression is fixed Crossover 6.2 is the best way to play Halo.**

**NOTE: Regressions in Wine 0.9.43 prevent Halo from working, use wine 0.9.42, or if all else fails, fall back to 0.9.39. The regression has yet to be fixed. I will do a regression test when I'm able to next, with hoping that this will eventually be fixed.**

**Update: This appears to be fixed with 0.9.52, however there does appear to be an abnormally high amount of memory usage.**


== Step 1: Install wine ==
[LIST=1]
[*]Install wine, following instructions on winehq: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) Remember to run winecfg, and configure your sound drivers. It doesn't matter whether you're set to OSS or ALSA, performance is the same.
[/LIST]

== Step 2: Preparation ==

[LIST=1]
[*](Optional, ignore if installed with add/remove program) FInd a .exe file, for example the setup.exe on your halo cd, right-click it and click properties. Click on Open with, and click add. Click custom command, and type wine. Click add and then close.
[*]Go to [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42) , download the file and open it. Then copy the file to your system32 folder in your fake c drive
[/LIST]

== Step 2: Install Halo ==

[LIST=1]
[*]Double click setup.Exe in your halo cd, or run ```
wine /path/to/cdrom/Setup.Exe
``` in a terminal
[*]Follow the install through, it will generate a few errors that can be safely ignored.
[*]At the end of the install do not press Play now, it will not work.
[/LIST]

== Step 3: Necessary settings ==

[LIST=1]
[*]In your Halo folder, run haloupdate.exe to update to the latest version OR download this file and run it: [http://www.softwarepatch.com/games/halo.html]("http://www.softwarepatch.com/games/halo.html")
[*]Copy protection does not work, in order to get the game working, a no-cd crack must be used.
[*]Then right click on the Halo icon on your desktop and click properties. (If it isn't there, make one, using ```
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe"
``` as the command, assuming that's where you installed the game)
[*]Click Launcher, and in the Command box, after the speech marks (at the end) add -novideo. For example ```
env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe" -novideo
```
[/LIST]

== Step 4: Playing! ==


You should now be able to run the game simply by clicking on the desktop shortcut. But there are some full screen issues. I recommend you run the game in a virtual desktop (configure that by running winecfg). Also make sure that if you run it like that then make sure Halo is set to run in the same resolution as wine's virtual desktop, or vice versa. To force Halo to run at your preferred resolution, add ```
-vidmode w,h,r
``` on the end of your command, the same way as we added the -novideo line. (make sure the -novideo line remains), changing it for you proffered resolution, for example : ```
-vidmode 1024,768,60
```


There are some known issues, these are explained on the appdb. I filed the Gold report that is linked, and another member (The noble) filed the bronze one underneath it. They are with Nvidia and ATI cards respectively. 

Here are a few screenshots of me playing the game:

[http://ubuntuforums.org/attachment.php?attachmentid=35555&d=1182011098](http://ubuntuforums.org/attachment.php?attachmentid=35555&d=1182011098)
[http://ubuntuforums.org/attachment.php?attachmentid=35556&d=1182011098](http://ubuntuforums.org/attachment.php?attachmentid=35556&d=1182011098)
[http://ubuntuforums.org/attachment.php?attachmentid=35557&d=1182011098](http://ubuntuforums.org/attachment.php?attachmentid=35557&d=1182011098)

You can notice a slight visual glitch on the third picture, that is very minor and I personally didn't notice it until after I had taken the picture.

Please note that I do not guarantee that the game will work for you. These are these exact steps that I followed to get the game working in the state that I gave the Gold rating. Please do not sue me if you go out and buy the game and can't get it working, ask here for help and make sure you followed the guide correctly.

It should also be noted that I am only able to run the game by doubleclicking on the desktop icon, running the game via a terminal causes a file missing error.




**TIP:** Well when it comes to a laggy mouse, unfortunately there's no known way to solve it. I do experience the issue, but not enough for me to make a big deal of it, but since other people seem to be having worse cases of the issue I've done some experimenting and found a way to lessen the issue (for me anyway)

First disable Specular in Halo's options, then run regedit and change or create ```
HKEY_CURRENT_USER\Software\Wine\Direct3D\RenderTargetLockMode
```with  the content ```
enabled
```

This improved things, but the problem was still there, but it made the game more playable. Some people may have to lower settings in game to improve this issues. (It seems to be worse when more is on screen, which suggests that people with higher graphics cards would probably have a smoother ride.)



**TIP:** offscreenrenderingmode:

backbuffer (default) Best, no visual glitches, good performance.

pbuffer: Good performance but many visual glitches pictured in an attachment.

fbo: No visual glitches, but bad performance.


I hope this helps those of you who are having problems.
It works for campaign but not for multiplayer.. Once I click on that it goes to blue screen.. I actually have the copy I purchased.. shouldn't it work

---

### Post by jamesrfla on 2008-10-12
I did all the instructions and Halo still wouldn't work. When I got rid of -novideo I got farther then when I had -novideo added. When I have -novideo added I get the Halo screen you get before the short clips and the entire computer locks up and I have to pull the plug on the computer. Without -novideo I get Halo then the videos. After that is locks up and have to pull the plug again. I also tried installing Halo trial but got the same results. I am currently running Ubuntu 8.04.1 with the latest Wine version. I run compiz if that means anything. Any help will be much appreciated!!

---

### Post by Mr. Man on 2008-10-17
what file do i copy it to and where do i find this?

---

### Post by Ferrat on 2008-10-17
> **jamesrfla said:**
> I did all the instructions and Halo still wouldn't work. When I got rid of -novideo I got farther then when I had -novideo added. When I have -novideo added I get the Halo screen you get before the short clips and the entire computer locks up and I have to pull the plug on the computer. Without -novideo I get Halo then the videos. After that is locks up and have to pull the plug again. I also tried installing Halo trial but got the same results. I am currently running Ubuntu 8.04.1 with the latest Wine version. I run compiz if that means anything. Any help will be much appreciated!!

Have you tried turning of Compiz since that affects 3D performance?

---

### Post by jamesrfla on 2008-10-17
> **Ferrat said:**
> Have you tried turning of Compiz since that affects 3D performance?

How do you turn off compiz and later turn it back on?

---

### Post by boe-bots on 2008-10-20
I tried to install it but I clicked next after I put the cd key in, and it said "cannot load PidGen.dll". Has anyone had this problem and do you know how to fix it.? 


Thanks!

---

### Post by Shaythong on 2008-10-20
Go to Step 2.2 (mfc42.dll) and put that in your WINE system32 folder.

---

### Post by jamesrfla on 2008-10-31
> **jamesrfla said:**
> I did all the instructions and Halo still wouldn't work. When I got rid of -novideo I got farther then when I had -novideo added. When I have -novideo added I get the Halo screen you get before the short clips and the entire computer locks up and I have to pull the plug on the computer. Without -novideo I get Halo then the videos. After that is locks up and have to pull the plug again. I also tried installing Halo trial but got the same results. I am currently running Ubuntu 8.04.1 with the latest Wine version. I run compiz if that means anything. Any help will be much appreciated!!

I disabled Compiz ```
metacity --replace
``` After that I ran Halo with -novideo I got a blank screen and I couldn't do anything. I tried ctrl+alt+backspace and ctrl+alt+F1 and nothing seemed to work. I tried running without -novideo and it showed the three commercials in the begging then when it came to show the menu it did the same thing as last time with the blank screen. Then I tried running it with -novideo -vidmode 1024,768,60 -use11 I got the same results. Any ideas?:confused:

---

### Post by Dask8r on 2009-01-12
> **jamesrfla said:**
> I disabled Compiz ```
metacity --replace
``` After that I ran Halo with -novideo I got a blank screen and I couldn't do anything. I tried ctrl+alt+backspace and ctrl+alt+F1 and nothing seemed to work. I tried running without -novideo and it showed the three commercials in the begging then when it came to show the menu it did the same thing as last time with the blank screen. Then I tried running it with -novideo -vidmode 1024,768,60 -use11 I got the same results. Any ideas?:confused:

Same problem, some help on this would be nice :popcorn:

---

### Post by Nickhamm on 2009-01-30
Has anyone got the game to work with GMA950 graphics?

Laptop Specs:
1.66Ghz Intel Core Duo
2GB Memory
GMA950 Graphics
120GB hard drive
Ubuntu 8.10
Wine 1.1.13

I have tried installing Halo: CE and Halo Custom Edition, using the NoCD Patch and using the latest 1.08 update, -novideo, virtual desktop on and off, -safemode and -useff on and off and it either freezes after the initial Halo logo or complains about a shader file. Any help to get it running would be great because it's driving me nuts!

---

### Post by Gp. on 2009-03-10
Hi, just wondering how I enable the net?

Can't seem to get multiplayer (internet) working?

---

### Post by Ascendaeus on 2009-03-25
Online Won't work at all for me just like that other guy was saying it says it's checking for updates until i exit if i try to run the update (in either Halo ce or Halo)it Says i installed it  in-correctly or something but the Campaign Works fine! How does the Campaign work if i don't have the game properly installed????? ???? ????? ??? ? ?? ? ?? ?? ?? ? ???? ??? ??? ? ?

---

### Post by Vrekk on 2009-03-25
I don't know why is says that the game isnt installed right, but I do know there is an issue with update working.  I dont think the only solution for right now is not to play online. Sorry

The updater dose work on the new crossover games 7.2, but there is an issue with the mouse that prevents you looking to the left, for me at least

---

### Post by Darkside44 on 2009-04-06
ummm ok i have the most recent version of wine and i have halo installed and working just fine. I only have one problem... its terribly slow! its not my PC either:

AMD Athlon 3200+ 2.4Ghz Processor 
nVidia GeForce 5500MX 256VRAM PCI 
1Gb of DDR RAM
80Gb HDD 
Realtek Audio card

i need to know how to get it running properly... PLEASE help me!

if you have any advice please also comment here: [http://www.linuxforums.org/forum/ubuntu-help/144158-new-linux-plz-help-me.html](http://www.linuxforums.org/forum/ubuntu-help/144158-new-linux-plz-help-me.html)

Thanks

---

### Post by AllRadioisDead on 2009-04-07
I just installed Halo Custom Edition (Same thing, without campaign), and I get a crash error just before the menu screen. If someone could help me out, that would be great, I really want to play.

---

### Post by AllRadioisDead on 2009-04-08
Here's my terminal output:
```
crisis@crisis-core:~/.wine/drive_c/Program Files/Microsoft Games/Halo Custom Edition$ wine haloce -novideo -vidmode 1280,1024,75
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33d4f4,0x00000000), stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x33805c) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {1aeaa606-35f0-11d1-b161-00c04fc28aca}
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1374c0,0x13a080): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33d734,0x00000000), stub!
Using profile path .
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1280x1024x32 @75! (desktop)
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetSoftwareVertexProcessing (0x1787a8) : stub
fixme:imm:ImmReleaseContext (0x1002a, 0x136398): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x136398): semi-stub
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x1
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-4,-23)-(1284,1028)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x6b3caa0,0x6b3c9e8): stub
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1454
fixme:d3d:state_multisampmask (WINED3DRS_MULTISAMPLEMASK,0) not yet implemented
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
fixme:d3d_surface:surface_upload_data Using DXT1/3/5 without advertized support
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x33ec94) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33e9b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33ed00,0x00000000), stub!
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {1aeaa606-35f0-11d1-b161-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x33f108,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33edf0,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1364a8,0x13b820): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:adpcm:ADPCM_StreamOpen We don't support encoding yet
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {da4e3da0-d07d-11d0-bd50-00a0c911ce86} could be created for context 0x1
err:ole:CoGetClassObject class {0a4252a0-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {0a4252a0-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {2721ae20-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {2721ae20-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {2eb07ea0-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {2eb07ea0-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {65e8773d-8f56-11d0-a3b9-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {65e8773d-8f56-11d0-a3b9-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {65e8773e-8f56-11d0-a3b9-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {65e8773e-8f56-11d0-a3b9-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {ad809c00-7b88-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {ad809c00-7b88-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {cc7bfb41-f175-11d1-a392-00e0291f3959} not registered
err:ole:CoGetClassObject no class object {cc7bfb41-f175-11d1-a392-00e0291f3959} could be created for context 0x1
err:ole:CoGetClassObject class {cc7bfb46-f175-11d1-a392-00e0291f3959} not registered
err:ole:CoGetClassObject no class object {cc7bfb46-f175-11d1-a392-00e0291f3959} could be created for context 0x1
err:ole:CoGetClassObject class {cf1dda2c-9743-11d0-a3ee-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {cf1dda2c-9743-11d0-a3ee-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {cf1dda2d-9743-11d0-a3ee-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {cf1dda2d-9743-11d0-a3ee-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {fbf6f530-07b9-11d2-a71e-0000f8004788} not registered
err:ole:CoGetClassObject no class object {fbf6f530-07b9-11d2-a71e-0000f8004788} could be created for context 0x1
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Halo"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x0000004a,0x6cd7fc,0x6cd3b4): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x0000004a,0x134f58,0x6cd3b4): stub
err:eventlog:ReportEventW L"haloce.exe"
err:eventlog:ReportEventW L"1.0.8.616"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"0.0.0.0"
err:eventlog:ReportEventW L"00000000"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


```
Can anyone please help?

---

### Post by Gp. on 2009-04-11
My setup looks like this...

---

### Post by thebrian on 2009-04-22
I get it to install successfully, but after the intro movies, it minimizes and gives me a window that says "gathering exception data..." then another error that tells me to quit.

Even when I add -novideo, it does the same thing, but just skips the vidoes.

I'm running the latest version of WINE on Ubuntu Hardy 8.04.1

thanks if anybody can help me!

---

### Post by jamesrfla on 2009-04-22
> **thebrian said:**
> I get it to install successfully, but after the intro movies, it minimizes and gives me a window that says "gathering exception data..." then another error that tells me to quit.

Even when I add -novideo, it does the same thing, but just skips the vidoes.

I'm running the latest version of WINE on Ubuntu Hardy 8.04.1

thanks if anybody can help me!

A lot of people seem to be having the same issue and I am too. I kind of just gave up on it and built a gamer and put XP, Vista (for halo 2 only), and Ubuntu.

---

### Post by Tailgate1981 on 2009-05-06
when i try to install halo i make it all the way to the screen to install the game but i can't click on install, i tryed alt+i like i did on all the other steps but nothing happens

---

### Post by Gothamite on 2009-05-07
Hello, when I run halo I get a black screen when it is supposed to show the  main menu, I hear the music so I know that the game is running, so I push the enter key several times to start playing in the single player mode, I hear stuff happening but I can only see lights and some weird stuff in the middle of the screen. When I start halo in safe mode the menu is still black, but when I'm playing the single player in safe mode I can actually see, the problem is that even though I can see all objects, the HUD, my hands and AI are invisible it is also extremely choppy and very visually glitchy.

I have an ATI 2400 pro 256 mb with the xorg drivers Pentium 4 and 2 GB ram with ubuntu 8.04 and the latest wine.

Any Ideas would be great thanks :o

---

### Post by garrett94 on 2009-05-13
hey i got halo installed fine and then updated it and replaced the original halo.exe with a no CD crack but whenever i try to open it i get a window saying "Halo has encountered a problem and needs to close.  We are sorry for the inconvenience." and yes i have tried running it in a verual desktop and it still doesn't work. PLEASE HELP i love halo and i really need it to work

---

### Post by Vrekk on 2009-05-13
> **garrett94 said:**
> hey i got halo installed fine and then updated it and replaced the original halo.exe with a no CD crack but whenever i try to open it i get a window saying "Halo has encountered a problem and needs to close.  We are sorry for the inconvenience." and yes i have tried running it in a verual desktop and it still doesn't work. PLEASE HELP i love halo and i really need it to work

If you updated Halo with the newest patch, then you cant need to use the no cd crack, the update takes away the need to have the cd in the drive.  Run the updater again and it should help.  Btw dose the update finish or dose it crash? I've never gotten the update to work right in wine

---

### Post by garrett94 on 2009-05-13
> **Vrekk said:**
> If you updated Halo with the newest patch, then you cant need to use the no cd crack, the update takes away the need to have the cd in the drive.  Run the updater again and it should help.  Btw dose the update finish or dose it crash? I've never gotten the update to work right in wine
the updater runs fine it updated the first time and now just says game up to date... i tried to run the game in terminal and i got the same problem but it showed this error message
 fixme:win:EnumDisplayDevicesW ((null),0,0x32d3dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32cd54,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32c754,0x00000000), stub!
oft Games/Halo/halo.exe: main/renderbuffer.c:2153: _mesa_reference_renderbuffer: Assertion `oldRb->Magic == 0xaabbccdd' failed.
fixme:faultrep:ReportFault 0x32be10 0x0 stub

---

### Post by Nevart on 2009-07-15
Awesome post.  If there is an award for Post of the Year, I hope you win!

---

### Post by bloodyroard on 2009-08-01
hii I'm new......a have a trouble when run halo, no shou menu and the screm is black.... please.... helpme. I have wine 1.0.1

---

### Post by Joe Awsome on 2010-08-27
I'n in the same boat as bloodyroard, I've got a black screen with no menus to be seen anywhere. I get sound at the main menu but no vid, and what's weird enough is that the bungie, gearbox, and microsoft games intro vids all work fine. any help with this problem is greatly apreciated, thanx.

---

### Post by Joe Awsome on 2010-08-27
the updater crashes for me, and I think I'm running wine 1.2.

---

### Post by Kyomaru on 2010-09-12
okay, i got the program to launch, but when it starts, it says, Halo did not shut down right. start in safemode or not. if i start normaly, it dosnt make it past the microsoft games logo. but if i start in safe mode, it starts, and it makes it to the title screen, i just cant see it. stuck on halo logo with backround music playing. whats going on?!

---

### Post by treyk4 on 2010-10-21
> stuck on halo logo with backround music playing. whats going on?! 
I'm having this same issue. Running 10.04
Also, haloupdate.exe always crashes, around the time the text "Updating the game..." appears in the top-left.

---

### Post by sona1111 on 2012-12-03
sorry to revive this thread but i can not seem to find answers anywhere:

Hello, i have been using ubuntu on my laptop for a long while, and i really like it better then windows besides the fact theirs a few games i cant run. I am here to try and fix that. I installed haloce and it boots, shows intro videos, then when it starts the graphics it really screws up, sometimes just showing blocks of colors sometimes weird shapes, other mostly unintelligible problems. Anyway here is winetricks installed:

d3dxof
mfc42
vcrun6sp6
vcrun6

The graphics card is:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI M56GL [Mobility FireGL V5200]

which is more then capable of playing this old game. 

I have tried many things like installing more libraries and commandline switches, but i wont other listing them all. Ubuntu lists no proprietary drivers, but i have seen in many places that the open source ones should support 3d correctly.

---

### Post by LillyDragon on 2012-12-03
Wow, I still remember when this topic was fresh back in the day; this fills me with a lot of dejavu.

I think it would have been better to open a new thread with your question. And with WINE's current state of compatibility as it is now, you're not going to be able to play many high end 3D games on open source drivers. Maybe emulators and older idtech3-based shooters, but not HALO. D:

I'm honestly shocked your luck with AMD cards isn't much better than mine on Intel Graphics chipsets. You'll need at least an nVidea card with propriety drivers to run anything like Halo and beyond. WINE's compatibility isn't quite that perfect yet.

---

### Post by sona1111 on 2012-12-04
this firegl is in a thinkpad laptop computer so i can not really change the hardware and i do not believe that nvidia is offered even if I changed the whole mobo. 

Why are their no drivers just because it is AMD?

---

### Post by LillyDragon on 2012-12-05
nVidea officially provides support for Linux with their line of cards, while AMD supports only Windows. Obviously, this leaves the open-source community with a lot of legwork to cover themselves. D:

Also, changing video hardware in laptops has always been possible, but it wasn't until recently that they started making it easier for the end-user to do. Try Googling your model and see if anyone has written a tutorial on replacing the graphics card, or if it's integrated, installing a card.

Although the price of a new card probably wouldn't be worth it to play older shooters, you could easily buy a cheap refurbished desktop with an integrated nVidea chipset more than capable of playing Halo 1 or 2 on the PC, and then some. I don't know how you'd play Halo on a laptop anyway without a controller or setting it up on a desk with a USB mouse, touchpads are horrible for aiming even if you disable "Lock touchpad while typing.". XD

---

