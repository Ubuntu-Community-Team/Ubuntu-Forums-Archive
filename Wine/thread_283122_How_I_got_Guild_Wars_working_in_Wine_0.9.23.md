---
title: "How I got Guild Wars working in Wine 0.9.23"
date: 2006-10-23
forum: Wine
---

### Post by Jarn on 2006-10-23
**EDIT (08/09/07) - UPDATED *ONLY* THE 32-BIT SCRIPT FOR 0.9.42**
**EDIT (07/02/07) - UPDATED FOR 0.9.40**
**EDIT (06/28/07) - Cleared everything but the edit history and redid it to reflect the current status of Guild Wars in wine.**
**EDIT (03/31/07) - See the note below** - now defunct as the note was removed
**EDIT (03/30/07) - The 64-bit script is now updated. Everyone say "Thank you, Azakus!".**
**EDIT (03/25/07) - UPDATED FOR 0.9.33. *Note, the 64-bit scripts are not yet updated***
**EDIT (03/12/07) - Fixed some problems pointed out to me in the scripts.**
**EDIT (03/02/07) - UPDATED FOR 0.9.32**
**EDIT (01/27/07) - If you tried the installwine+gw.sh script prior to today, it most likely did not work. I had some typoes.**
**EDIT (01/25/07) - UPDATED FOR 0.9.30 - Added scripts for AUTOMATION! Also, added asterisks in the file paths so I only have to update the link to the source every time. ;)**
**EDIT (01/23/07) - UPDATED FOR 0.9.29**
**EDIT (About 01/01/07)- UPDATED FOR 0.9.28**

**NOTE: I have removed the old manual guide because I deemed it unnecessary due to the ease with which Guild Wars can now be run under Wine.**

Read the list before you do anything as you may just be able to use the package from the wine repositories.

Step 1: Download the script
[list]
[*]Download one of the attachments at the _bottom_ of this post. Get winebuild.sh if you are on a 32-bit computer AND you get the "Too many concurrent lights" error (a description of this is provided under Troubleshooting). If you are on a 64-bit computer, you can get the 64-bit version helpfully provided by Azakus. This is necessary even if you do not have the "Too many concurrent lights" error (I think; all speculation - ask Azakus if you want to know for sure) because Wine needs to be compiled differently under a 64-bit operating system. **Thanks, Azakus!**
[*]**NOTE: These scripts are for Edgy only but if you are using Breezy or Dapper it should be VERY easy to convert it to that. Just replace the word 'edgy' in the line "wget [http://kegel.com/wine/edgy.sh](http://kegel.com/wine/edgy.sh) -O ~/winestuff/pkgs.sh" with breezy or dapper.**
[/list]
Step 2: Run the script
```
sh <<insert the path to the script you downloaded>>
```

_Troubleshooting_
A common error seems to be that Guild Wars freezes with this output repeatedly in the command line: "fixme:dbghelp:SymInitializeW what to do ??". There appears to be two causes of this.

[list=1]
[*]The first is the "Too many concurrent lights" error. When this happens, the fixmes above are preceded by an error to the effect of "Too many concurrent lights". If this happens and you are on a 32-bit computer, run the winebuild.sh script. If you are on a 64-bit script, run Azakus' winebuild64.sh and tell it that, yes, you want to use the concurrent lights fix.
[*]Wine doesn't appear to use the new sound system that Guild Wars implemented in a recent update. This can be fixed in three ways: running it with the -dsound flag, the -nosound flag, or turning off sound in winecfg. To run it with those flags, you would run it pretty much the same way you always do but append that on to the end of your command:
```
wine "C:\Program Files\Guild Wars\Gw.exe" -dsound
```
[/list]

Good luck and happy gaming. :)

---

### Post by handy on 2006-10-24
Your how-to looks great! :KS  

How does GW play? Is it smooth, are there any zoning problems (lag after going through portals)?

I will have to put aside some time to try this out.

Thanks... :D

---

### Post by Jarn on 2006-10-24
It works great. For a few seconds after you zone, you have no mouse. But it comes back shortly, quicker if you right-click. I have about 30-35 fps average, so no lag :D. There is this, though:

[quote=Jarn]create a character. This does not work. When you try to type the name at the final stage of character creation, it freezes[/quote]

But you may not have that problem. I don't think I've seen anyone else complain of this problem with Guild Wars.

---

### Post by FyreBrand on 2006-10-24
I will be trying this soon.  I don't have an established .dat file anymore because I nuked my Windows partition after the Nightfall PvE preview.  So I guess I'll have to see how the login bug you talked about works out.  I have hopes.

---

### Post by Jarn on 2006-10-24
> **FyreBrand said:**
> I guess I'll have to see how the login bug you talked about works out.I have a feeling that that is not a common thing, that it's just an oddity of something about my system.

---

### Post by Jarn on 2006-10-24
Well, I found something else that doesn't work quite right, but it works well enough to play. I had never done any zoning besides in the Balthazar isles and I had extrapolated that all zoning would be the same. However, I just tried to zone in Prophecies - it works, all the cities show up, but when zoomed out it's all clouds and when zoomed in it's like black and orange clouds. :O

EDIT:Okay, I didn't do anything and now it's working. So apparently that sometimes works, sometimes doesn't. O.o Well, it always works, but sometimes it doesn't show the background correctly.

---

### Post by FyreBrand on 2006-10-24
I'm wondering if running the -image switch will be helpful or not.  Whenever ANet put out a major update or after a few weekly updates I used to run a GuildWars shortcut with the -image switch on so I could have all of the content decompressed.  It might help for the system not to have to decompress files from the .dat file on the fly.

I really can't wait to try this out and see if I can get it to work.  I'm pretty much of a Wine newbie so I'll do a little reading on how to configure that before I start.

---

### Post by Jarn on 2006-10-24
> **FyreBrand said:**
> I'm wondering if running the -image switch will be helpful or not.I don't know, I always use -image.

> **FyreBrand said:**
> I really can't wait to try this out and see if I can get it to work. I'm pretty much of a Wine newbie so I'll do a little reading on how to configure that before I start.I'm a newbie too. :( Good luck! I hope this works for you and it's not just that I got lucky or something like that.

---

### Post by FyreBrand on 2006-10-24
The wine install went pretty good, at least no errors, but I am getting a segmentation fault on winecfg.  I will do a little more reading and try again later.  I am using Edgy so I have to figure out if there is some version incompatibility somewhere between that and Dapper.

If nothing else I will do a quick Dapper reinstall over the holiday and see if it works under that before doing a fresh Edgy install.

---

### Post by Jarn on 2006-10-25
Did you have any luck?

---

### Post by FyreBrand on 2006-10-25
Yes and no.  I went through the setup and compile again and checked some packages in the requirement list.  There were a couple in that list that had broken dependencies on my machine.  This is mostly due to a couple edgy updates that have broken several packages.  So I successfully got those installed and the depends fixed.

I did the compile with no detected errors.  In fact it seemed to go smooth the whole way.  It was only at the point where I tried to run winecfg or wine itself that I got the Segmentation Fault.  I'm not really sure what is causing this or what the memory problem is.  The only thing I can figure is that you are running Dapper and the libraries  at that version work right for this compile.  I am thinking that Edgy has one or more of those libraries at different versions and that it breaks because of that.

I can't really nuke the OS until Thanksgiving (US) holiday or maybe even the beginning of Christmas holidays for me.

I hadn't ever intended on returning to Dapper because there are so many cool things about Edgy, but if I can run GW in Dapper but not Edgy then I will revert. :(

---

### Post by Jarn on 2006-10-26
Well, I may have just gotten lucky that GW worked for me. So it may not be worth it, you may do it and it may just not end up working anyway.

---

### Post by ThisNamePwnzUrz on 2006-10-27
Im getting stuck at the patch part

nimitz@nimitz-desktop:~/winestuff$ patch <~/winestuff/32mouse.patch
can't find file to patch at input line 8
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|Index: dlls/winex11.drv/mouse.c
|===================================================================
|RCS file: /home/wine/wine/dlls/winex11.drv/mouse.c,v
|retrieving revision 1.1
|diff -u -r1.1 mouse.c
|--- dlls/winex11.drv/mouse.c   16 Jun 2006 13:19:17 -0000      1.1
|+++ dlls/winex11.drv/mouse.c   24 Jun 2006 21:07:54 -0000
--------------------------
File to patch:

what do i do at this point?

---

### Post by ThisNamePwnzUrz on 2006-10-27
yeah never mind i got my freind to do it and its working great thx. :D

---

### Post by ThisNamePwnzUrz on 2006-10-27
i cant get the wine desktop to acutally display guild wars...it just shows the  mouse and a blue horizon....any suggestions???

---

### Post by ThisNamePwnzUrz on 2006-10-27
ok i basicly fixed everything, i can log on and all that but all the words are screwed up...1 problem leads to another....

---

### Post by der_joachim on 2006-10-28
> **Jarn said:**
> Well, I may have just gotten lucky that GW worked for me. So it may not be worth it, you may do it and it may just not end up working anyway.

There may be more. 

First of all: thank you for your guide. If I had still run Dapper, things would possibly have worked and that would have been a major step forward. 

I run edgy now and since some libs were updated, Wine gives me segmentation faults galore. Reading the forums, this problem is common to all wine versions an dnot just the patched ones. It is probably an edgy issue (no pun intended). 

There seems to be a new version of wine, but there is no edgy repo yet for edgy, so I will be patient some more then. ;)

---

### Post by erk on 2006-10-31
Anyone tried the 32 bit mouse cursor patch on Wine 0.9.24 source yet to see if it still works?

---

### Post by chadk on 2006-10-31
Will applying this WINE patch stop World of Warcraft from running on it's patched wine 9.21 or the other way around?

---

### Post by FyreBrand on 2006-11-01
> **chadk said:**
> Will applying this WINE patch stop World of Warcraft from running on it's patched wine 9.21 or the other way around?I'm not sure I understand exactly what you're asking.  If you are asking if you compile and install Wine 0.9.24 if that will interfere with earlier versions then the answer is yes.

The patches mentioned in the thread are mouse functionality patches and are applied at the time you compile Wine.  Wine version 0.9.24 isn't actually a patch but an entire version update.

If there is a method to install two different versions concurrently (outside of a virtual machine of some type) I'm not aware of it.  There very well could be.  Maybe someone with more experience can answer that detail.

---

### Post by chadk on 2006-11-01
I guess what I'm asking is.  Can I run WoW AND Guildwars from the same WINE install.  See, they both seem to require some special patch to wine in order to function correctly.  Can I install both patches to Wine in order to play one or the other at any given time?  Has anyone done this?

---

### Post by FyreBrand on 2006-11-01
I can't answer that question.  I'm sure it could be possible but I don't know.

---

### Post by Jarn on 2006-11-01
Wow, I haven't checked this thread in awhile. It got big! I haven't checked it because I've been playing Nightfall ;). Sadly, I've been experiencing some crashes in Nightfall so I switched back to playing Guild Wars in Windows. They weren't that common, and I think it may have just been specific to one mission, but I didn't want to get through it as quick as possible. Once I beat it on the first character, I'll be going back to Linux. I think it may just have been specific to one mission. I got to about level 14 and beat the first twoish missions, but, in the one where you're killing Apocrypha, I kept crashing as soon as I entered. So then I went back to Windows, and that's what I'm using currently to play Guild Wars.

---

### Post by FyreBrand on 2006-11-01
I got it running.  It's pretty choppy on my current card ATI X300, but I have a Geforce 6800 on it's way.  That should help a lot.

By the way.  The seg-faults were coming from a problem with the make file.  This [**thread provides a CFLAG export**]("http://www.ubuntuforums.org/showthread.php?t=287986") that is needed.

If I try and configure sound in winecfg then it crashes.  So I have no sound but everything else is working okay.

Thanks a lot for the info and links to files.  This was super duper helpful.  I don't know if I'm going to buy Nightfall yet, but I know I'm sure not putting a Win partition back on my machine.  I might just have to wait a while and see how it all goes.

Thanks again Jarn, you rock!

---

### Post by Jarn on 2006-11-01
> **FyreBrand said:**
> I have a Geforce 6800 on it's way.  That should help a lot.I <3 my Geforce 6800. I'm glad you got it working! Are you running it on 0.9.24 or 0.9.23? And are you running it on Edgy? Once I get my Paragon through Nightfall, I'll probably upgrade both Ubuntu and Wine and see how it goes from there.

---

### Post by FyreBrand on 2006-11-01
I'm running 0.9.24 and on Edgy

There were a couple modifications I made to the package install script.  Well actually I used aptitude to install them all by hand in small chunks.  There is a library near the bottom of that script that is older than one in the Edgy repo so I kept the newer version and it works okay I think.

I can input text in the login screen okay, but I have to wait a little for everything to load before it will let me.

I also have to wait a little for the mouse cursor to show up but it generally works good.

The only small problem I'm having so far is that  I have my virtual desktop set to 1280x1024 and I set my GW resolution to that but it seems to be staying at an actual size of 1024x768.  I can't find a way to force it to resize.  The option to configure on right-clicking the title bar isn't working.  No biggie I suppose.  Hopefully I will figure it out soon.

---

### Post by erk on 2006-11-20
Anyone tried 0.9.25 yet?

---

### Post by orgy on 2006-11-21
> **erk said:**
> Anyone tried 0.9.25 yet?

i have. i got no cursor and can only rotate camera left/up. Everything else works though.

---

### Post by FyreBrand on 2006-11-22
> **orgy said:**
> i have. i got no cursor and can only rotate camera left/up. Everything else works though.Did you apply the two mouse patches when you compiled or did they not work?

---

### Post by lioncoeur on 2006-11-22
> **FyreBrand said:**
> 
If I try and configure sound in winecfg then it crashes.  So I have no sound but everything else is working okay.


This actually seems to be a bug with the alsa or arts driver. What I did was find the two drivers in the installed wine directory and renamed them to alsa_crap arts_crap or something like that. Then when you open the sound tab, it will complain about not finding the drivers but will give you the option to use oss or esd without crashing. I remember reading about this on a wine thread, I think to do with Warcraft III. Can't really find it! In any case if it doesn't work for you, you can just rename the drivers back to what they were before.

Currently compiling wine as per your instructions Jarn. It would be neat to get this working :D I really like Guild Wars.

I use an Intel 915GM. A recurring problem I've had with games is that X doesn't seem to detect the 128 MB of Video Ram in this card. It pretends that it actually doesn't have any Video Ram and I really don't know how to get around this problem. Should I look into compiling X with that card's driver or something?

---

### Post by FyreBrand on 2006-11-22
> **lioncoeur said:**
> This actually seems to be a bug with the alsa or arts driver. What I did was find the two drivers in the installed wine directory and renamed them to alsa_crap arts_crap or something like that. Then when you open the sound tab, it will complain about not finding the drivers but will give you the option to use oss or esd without crashing. I remember reading about this on a wine thread, I think to do with Warcraft III. Can't really find it! In any case if it doesn't work for you, you can just rename the drivers back to what they were before.

Currently compiling wine as per your instructions Jarn. It would be neat to get this working :D I really like Guild Wars.

I use an Intel 915GM. A recurring problem I've had with games is that X doesn't seem to detect the 128 MB of Video Ram in this card. It pretends that it actually doesn't have any Video Ram and I really don't know how to get around this problem. Should I look into compiling X with that card's driver or something?

Thanks, that's interesting to know.

How does the current wine compile work for you?

---

### Post by xixsixxix on 2006-11-24
> **FyreBrand said:**
> I'm running 0.9.24 and on Edgy

The only small problem I'm having so far is that  I have my virtual desktop set to 1280x1024 and I set my GW resolution to that but it seems to be staying at an actual size of 1024x768.  I can't find a way to force it to resize.  The option to configure on right-clicking the title bar isn't working.  No biggie I suppose.  Hopefully I will figure it out soon.

I'm having the same resolution problem in 0.9.25 (on Debian Etch/Sid). X and virtual desktop are set to 1280x1024, but it always scales to 1024x768, regardless of how i attempt to change the settings. Running fullscreen changed my X resolution to 1024x768 which is no good either. Managed to get the game running beautifully in every other respect though. If anyone figures out how to patch/fix the resolution issue I'd love to hear it.

I don't think messing with window setting in gnome really counts as a "fix" since not everyone runs gnome, But if it works for you more power to ya =) No such luck here.

---

### Post by tekno62 on 2006-12-04
Sorry but Im new to Ubuntu - kinda still a noobe to Linux even tho I do ok with FC3/4

I get this error 

d[COLOR="DarkRed"]don@don-desktop:~/winestuff$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree... Done
patch is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
don@don-desktop:~/winestuff$ sh pkgs.sh
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
don@don-desktop:~/winestuff$
[/COLOR]

when I try step 3 ( sh pkgs.sh ) 

I have searched for the root access for Ubuntu but from what I have read you cant do that. 

hope someone has an idea on what Im doing wrong.

thanks

---

### Post by hikaricore on 2006-12-04
> **tekno62 said:**
> Sorry but Im new to Ubuntu - kinda still a noobe to Linux even tho I do ok with FC3/4

I get this error 

d[COLOR="DarkRed"]don@don-desktop:~/winestuff$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree... Done
patch is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
don@don-desktop:~/winestuff$ sh pkgs.sh
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
don@don-desktop:~/winestuff$
[/COLOR]

when I try step 3 ( sh pkgs.sh ) 

I have searched for the root access for Ubuntu but from what I have read you cant do that. 

hope someone has an idea on what Im doing wrong.

thanks

sudo is your friend:

```
sudo sh pkgs.sh
```

---

### Post by hikaricore on 2006-12-04
> **xixsixxix said:**
> I'm having the same resolution problem in 0.9.25 (on Debian Etch/Sid). X and virtual desktop are set to 1280x1024, but it always scales to 1024x768, regardless of how i attempt to change the settings. Running fullscreen changed my X resolution to 1024x768 which is no good either. Managed to get the game running beautifully in every other respect though. If anyone figures out how to patch/fix the resolution issue I'd love to hear it.

I don't think messing with window setting in gnome really counts as a "fix" since not everyone runs gnome, But if it works for you more power to ya =) No such luck here.

You could force it to run in a window:

```
wine explorer /desktop=guildwars,1024x768 **GW.EXE**
```

^Substitute GW.EXE for the name of the guildwars exe file as I don't play it I don't know the name of it.  This forces the game to run on a virtual wine desktop sized 1024x768, adjust as needed adding any extra flags you normally do to launch the game.

---

### Post by tekno62 on 2006-12-05
hey... I just got GW to work - thanks...  

Im tired and have some problems understanding step 10.

anyone able to help me out?

---

### Post by orgy on 2006-12-11
guildwars is working here 100%, using wine 0.9.27 and the two patches from the first post. :D

---

### Post by iMerlin on 2006-12-15
I followed your guide and I finally have a mouse cursor that I can see, hurray :)

However I'm stuck at 800x600 resolution in a bloody Window. I've tried all sorts of black magic like changing the virtual desktop and trying the Guildwars settings.

I didn't understand point "10". Made no sense to me. KDE specific?

In the Guildwars preferences there are two options in Graphics that work. Fullscreen (800x600) or Windowed. But Windowed does never get bigger than 800x600

I've also tried the Guildwars specific cli option -windowed without success. Anyone got this running in a higher resolution?

Running Dapper with the latest repository Nvidia drivers on my GT6600.

---

### Post by xixsixxix on 2006-12-15
iMerlin> Mine's stuck at 1024x768 -- so a higher resolution, but the same issue. At what resolution are you running your monitor?

> **orgy said:**
> guildwars is working here 100%, using wine 0.9.27 and the two patches from the first post. :D

I too am running 0.9.27 patched *almost* perfectly using the nvidia-1.0.9631 drivers on a geforce 6800 card.  Also got it running nicely on a core2duo laptop with a geforce go 7400 -- in both cases, however, the 1024x768 fixed res is the only remaining problem (particularly annoying when the laptop autoscales the 1024x768 to match the 1280x800 screen)

Don't suppose your "100%" includes changing resolutions, orgy? If so please post your setup =)

---

### Post by chronusdark on 2006-12-17
has anyone figured out how to fix the messed up text?

ie mixed up strings, and scrambled text graphics

---

### Post by xixsixxix on 2006-12-18
> **chronusdark said:**
> has anyone figured out how to fix the messed up text?

ie mixed up strings, and scrambled text graphics

Wow, picky issue compared to some of the others, lol =)  So far as I've encountered the only apparently scrambled text graphics I've come across are, as I've seen mentioned around some other boards, the seeminly double printed text as areas are loading.

Pretty sure this is simply an issue of an attempt to load actual text over prerendered graphics right before the fade transition between the load screen and the game environment so as to keep it on screen through the fade.  It's not really a bug as much as a variance in the way the fonts are being displayed in linux vs. windows.  The graphics prerendered in windows with M$ fonts aren't matching up with the real-time rendered fonts in wine -- not something I can think of any reasonable fix for, unfortunately.

Other than that all in-game text has appeared fine to me but I'm always up for hearing about more bugs to research =)

---

### Post by rmjb on 2006-12-18
I'm really liking this thread, since I'm a dormant Guild Wars player and an Ubuntu convert, so I'll be trying these steps out soon. A question though, these steps work for the newer editions of GuildWars too right? Like Factions and the new one that just came out?

- rmjb

---

### Post by chronusdark on 2006-12-18
> **xixsixxix said:**
> Wow, picky issue compared to some of the others, lol =)  So far as I've encountered the only apparently scrambled text graphics I've come across are, as I've seen mentioned around some other boards, the seeminly double printed text as areas are loading.

Pretty sure this is simply an issue of an attempt to load actual text over prerendered graphics right before the fade transition between the load screen and the game environment so as to keep it on screen through the fade.  It's not really a bug as much as a variance in the way the fonts are being displayed in linux vs. windows.  The graphics prerendered in windows with M$ fonts aren't matching up with the real-time rendered fonts in wine -- not something I can think of any reasonable fix for, unfortunately.

Other than that all in-game text has appeared fine to me but I'm always up for hearing about more bugs to research =)

what im getting is like when i type my username it instead displays "General Settings" or other strings from other menus

---

### Post by handy on 2006-12-20
> **rmjb said:**
> I'm really liking this thread, since I'm a dormant Guild Wars player and an Ubuntu convert, so I'll be trying these steps out soon. A question though, these steps work for the newer editions of GuildWars too right? Like Factions and the new one that just came out?

- rmjb


Same game engine runs the lot! :KS

---

### Post by orgyn on 2006-12-20
> **xixsixxix said:**
> 
Don't suppose your "100%" includes changing resolutions, orgy? If so please post your setup =)

hehe, i didnt test that :P i like to play in window mode, i guess it runs 99% then :P

---

### Post by orgy on 2006-12-24
patches and game working with wine-0.928

---

### Post by der_joachim on 2006-12-25
> **orgy said:**
> patches and game working with wine-0.928

Not here. I have lots of freezes. I have to zap my X session when that happens. :(

Oh well, I am a patient man.

[edit]Installed Nightfall yesterday. Unchecked "Allow window manager to control windows" . Run GW in windowed mode. Is a lot better. Even did some questing.

---

### Post by xixsixxix on 2006-12-27
Been pretty successful with wine 0.9.28 and the Nvidia 1.0.9631 drivers.  GW resolution switching FINALLY works in 0.9.28, though it requires restarting the game.

The 32-bit mouse cursor patch is still required to make the mouse visible.  I also found the dirty lighting hack is still required for both my Nvidia GeForce 6800 and 7400 cards to avoid the "Too many concurrent lights" error crash on certain maps, though I've heard some ATI users say they don't need it.

In any case I've attached updated [0.9.28] versions of both the mouse and lighting patches for anyone that needs them.  The attached patches are for the files *dlls/winex11.drv/mouse.c* and *dlls/wined3d/device.c*.  Only apply the lighting hack (device.c) if you find that you need it.

There are only two remaining issues now:
(1) blocky shadows when using antialiasing and medium/high quality shadows (I just set all settings to high and then drop shadow quality to low to get around this)
(2) combat sounds don't work -- as I understand it this issue only applies to systems with alsa installed -- see my full post on this issue on the winehq boards [here]("http://appdb.winehq.org/appview.php?iVersionId=5903") and continued [here]("http://appdb.winehq.org/commentview.php?iAppId=2243&iVersionId=5903&iThreadId=16458").

Any insight into either issue would be much appreciated =)

---

### Post by typhoon006 on 2006-12-30
first, sorry for my english but i'm french ...... 


i've test a  0.9.28 version of wine , but i'don't know  where and how apply the patch, if  somebody can help me ....

i'm not a Linux and Wine expert  :-? 
thank's

---

### Post by xixsixxix on 2006-12-31
> **typhoon006 said:**
> first, sorry for my english but i'm french ...... 


i've test a  0.9.28 version of wine , but i'don't know  where and how apply the patch, if  somebody can help me ....

i'm not a Linux and Wine expert  :-? 
thank's

No problem.  Here's an example of how to apply the patches. Adjust the patch file paths as necessary, and skip the wined3d (device.c) patch if you don't need it.

Starting from your wine-0.9.28 source base directory:

[B]$ cd dlls/winex11.drv/
$ patch mouse.c <patch.mouse.c.txt
$ cd ../wined3d/
$ patch device.c <patch.device.c.txt[/B]

After applying the patches you can drop back to your source base directory and run *make* again to recompile the winex11.drv and wined3d modules.  Assuming you have already compiled once this will only recompile the two changed modules -- a full recompile isn't neccesary =)

EDIT: I would recommend you back up the original files before patching

---

### Post by nikinostyler on 2007-01-05
Thank you for posting this how-to, it saved me from a lot of head-banging in to the wall :D
if you dont mind i have some updates on what you wrote.

i have an intel845G based Mainboard and a Geforce4MX440 Video card(With the Nvidia Drivers found in synaptic)
i used a plain Edgy install(Alternate CD), and **wine 0.9.28** compiled almost the same way like you did. 
The only difference is that i neded to add WineHQs repo before doing anything else.

For Ubuntu Edgy (6.10):
**deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main**

[B]'sudo apt-get update'

'sudo apt-get install wine' 

'apt-get build-dep wine'[/B]

so i got all the nescesary libs what where needed to compile wine with D3D and X11 support
after doing that i folowed the instructions you wrote (with filenames for 0.9.28),

an other bug what i encountered that using **virtual desktop** somehow made D3D errors and the game ran very slow, and the mouse look function of the game just worked to right and down.
the folowing options made the game run at a normal speed (50-75% of speed under windows)
-Disabling the virtual desktop 
-running the game in fullscreen 
-Vertex shader : none
-Pixel shader disabled

hope it will help some people.

PS: some links i used to get the solution
[I][http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
[http://appdb.winehq.org/appview.php?iVersionId=5903](http://appdb.winehq.org/appview.php?iVersionId=5903)
[http://appdb.winehq.org/appview.php?iVersionId=5386](http://appdb.winehq.org/appview.php?iVersionId=5386)[/I]

---

### Post by Jarn on 2007-01-06
First time I've checked this thread in awhile. I've been pretty busy lately, but now that it's winter break I've had some free time. I upgraded from Dapper to Edgy last night and now I'm about to begin the process of installing the newest wine.

nikinostyler, the problem you described with the mouse requires a patch to fix. It was one of the patches that I had in my post, but those probably would not work with the newest version. In this post, [http://www.ubuntuforums.org/showpost.php?p=1935421&postcount=48](http://www.ubuntuforums.org/showpost.php?p=1935421&postcount=48), someone posted an updated patch.

Also, for those who asked about Step 10, it is indeed KDE-specific. Sorry I didn't put that in there. :(

EDIT: Also, for those of you who don't use the "Emulate virtual desktop" setting in wine, did you need to do anything to get it to work? Or does it just work? For me, as soon as the game goes fullscreen, the screen gets distorted. It's sizes changes a bit and I have slight black bars running through the screen. That's why I said to set that in my original post. That's also what Step 10 is for, to make it APPEAR full screen even though it's in a virtual desktop.

EDIT2: I accidentally didn't install the patch to prevent the camera only rotating two directions, yet it still rotates correctly. Does this work for everyone? Was it fixed since 0.9.23? Also, I updated the first post to work for 0.9.28 - and I took out the part about the aforementioned patch. So if it is just me, someone please notify me and I will add that back in.

---

### Post by FyreBrand on 2007-01-07
Hi Jarn.  If you're the same Jarn as on GWO, then  I saw your post in the GWO tech forum in the "What do you use thread"  :)  very nice

I'm getting ready to reinstall wine on Edgy (I use KDE too).  I will try your original thread and see how it goes.  I would really love get this working again.  Do you use Beryl or Compiz on your desktop?  I'm curious if it interferes with the game running.  Anyways I will work on it this week and post back.

---

### Post by Jarn on 2007-01-07
I do not use those. I updated the main post so the links etc. are for 0.9.28, and it worked for me. I followed the first post myself when I installed it, just using the new links. When I was done, I edited those in and I made some other minor changes. Everything works great except no sounds in battles and no shadows. And that is me on the GWO forums ;). Who are you on the GWO forums?

---

### Post by FyreBrand on 2007-01-07
I use the same user name 'Fyre Brand'.  I've done the preliminary package installs and have downloaded the source.  I'll be compiling here in a bit.  You write a really nice how-to.  It's clear and easy to follow.  One question.  Did you have to export the: ```
CFLAGS=-fno-stack-protector ./configure
``` to prevent a segmentation fault in Edgy or has the gcc compiler been changed?  I'll be exporting that because I had the seg fault problem on my last compile (about a month or so ago).

---

### Post by Jarn on 2007-01-07
I didn't have to. I saw that page after I had already compiled, so I didn't know about it when I compiled and it still compiled fine. So I think the gcc compiler has been changed. Or I just got lucky. But the page that that recommendation was on did not make it sound like it only happens sometimes, it made it sound like it happens all the time, so I would guess the compiler has been changed.

> **FyreBrand said:**
> You write a really nice how-to.  It's clear and easy to follow.Thank you. :D

---

### Post by FyreBrand on 2007-01-07
Everything compiled and runs mostly fine.  I copied my gw.dat file from my windows partition.  I did have one total freeze in the Nightfall newbie island.  I have a Geforce 6800XT and I think I might need to install the device patch like xixsixxix posted.  I'm going to try installing the patch and see what happens.

I also might need to do a little xorg.reconfiguring as that might be the problem.  I'm using the nvidia driver from tseliots repo and haven't had any problems with it.  The only thing is while xorg.conf says to use the "nvidia" driver kde system settings seems to think I'm using the "nv" driver.  I'm not really sure which is taking precedence so I will try and figure that out before applying the patch.  That way I can be sure there is no problem with my video driver.

---

### Post by Jarn on 2007-01-08
Did you have to apply any patches besides the one I had in the first post? Specifically, the one that previously was necessary to allow the camera to rotate correctly? I didn't have to and I'm wondering it it was fixed.

---

### Post by FyreBrand on 2007-01-09
I got a freeze up out in the instance that locked up my machine pretty good.  I do think I will have to apply the patch that xixsixxix is talking about.  I thought the 'nv' driver was loading at the same time as the nvidia driver, but I was wrong.  Classes have started so I might not be able to work on it until the weekend.

---

### Post by Jarn on 2007-01-10
Great, a few days after I upgrade from 0.9.28 they release 0.9.29! :P I probably won't get a chance to upgrade until Monday, so if someone else does it before I do, tell me if it goes alright.

---

### Post by orgyn on 2007-01-11
everything works fine with 0.9.29

---

### Post by FyreBrand on 2007-01-11
orgyn would you mind posting some specifics about the install?

What os version you are using?

If you used Edgy did you have to export the "CFLAGS=-fno-stack-protector" ?

What patches if any you applied.

If you have an nvidia card did you need to use the light patch xixsixxix posted above?

---

### Post by orgyn on 2007-01-12
> **FyreBrand said:**
> orgyn would you mind posting some specifics about the install?

What os version you are using?

If you used Edgy did you have to export the "CFLAGS=-fno-stack-protector" ?

What patches if any you applied.

If you have an nvidia card did you need to use the light patch xixsixxix posted above?

sure,

- using edgy
- did NOT export:  "CFLAGS=-fno-stack-protector"
- 32bitmouse patch
- nvidia driver v1.0-9631 (nvidia 6600 GO)
- did NOT use the light patch
- wine 0.9.29

---

### Post by FyreBrand on 2007-01-12
> **orgyn said:**
> sure,

- using edgy
- did NOT export:  "CFLAGS=-fno-stack-protector"
- 32bitmouse patch
- nvidia driver v1.0-9631 (nvidia 6600 GO)
- did NOT use the light patch
- wine 0.9.29
Thanks orgyn.  I'll compile and install this as soon as I can and report back how it all went.  I'm so looking forward to the day I can get this working reliably.  I don't mind regular hero/henching, but I still log into Windows to do Tombs, AB, or anything where my guild is relying on me.

---

### Post by User_Program on 2007-01-12
I have GW's installed with the latest wine with the mouse patch and everything is working "fine" but that is alittle misleading.  It is working but the performace is failing.  Only with everything turn down to low is the game playable with very few lag spikes (not network  more like video)  

But I am happy with the development so far it shouldn't be to long now before wine is up to par with cedega running Guild Wars.  I do notice somethings that are beter with wine then cedega.  For one it's far less laggy on the network side running wine , Loading maps after leaving towns is quicker too.   

It's fun testing it out and all but that's about all it is for me,  a test.   Running games this way kinda takes the fun outa playing the game if you know what I mean?   Not that Cedega does that better of a job at it either.  So I wouldn't get your hopes up to high, with getting guild wars running like it does in windows. But one day hopefully soon it will be possible *fingers crossed*  

Question:  Not so much releated to Guild War but more of wine...  Does anyone know of any projects that deal with using files from an exsisting windows install or from the cd itself (of course if you own the copy)  to run games and other programs inside of Linux ?  Yes this would break EULA but surely this has been tried right?

---

### Post by handy on 2007-01-12
GW runs fantastically on my machine via Cedega.  No issues at all.  Double right mouse clicking after zoning to get the mouse back really is nothing...

I do look forward to being able to play at the same level via Wine, it will happen...

---

### Post by orgyn on 2007-01-12
tried it on another computer:

- using edgy
- did NOT export: "CFLAGS=-fno-stack-protector"
- 32bitmouse patch
- nvidia driver v1.0-9631 (nvidia 5200)
- this time i had to use the light patch (the game doesnt freeze anymore)
- wine 0.9.29

---

### Post by orgyn on 2007-01-12
> **handy said:**
> GW runs fantastically on my machine via Cedega.  No issues at all.  Double right mouse clicking after zoning to get the mouse back really is nothing...

I do look forward to being able to play at the same level via Wine, it will happen...

for me it has the same performance in wine. Except for the sound :P still i always play with music so, no combat sound doesnt bother me.

---

### Post by Jarn on 2007-01-12
> **handy said:**
> GW runs fantastically on my machine via Cedega.  No issues at all.  Double right mouse clicking after zoning to get the mouse back really is nothing...

I do look forward to being able to play at the same level via Wine, it will happen...
It is ALMOST there now. Via the info in the first thread, you can get Wine running GW perfectly except for battle sound. Wine also needs the mouse to be right-clicked to see it after zoning, apparently like Cedega.

---

### Post by handy on 2007-01-12
> **Jarn said:**
> It is ALMOST there now. Via the info in the first thread, you can get Wine running GW perfectly except for battle sound. Wine also needs the mouse to be right-clicked to see it after zoning, apparently like Cedega.

Great news! :KS

---

### Post by Snu Woods on 2007-01-14
That was really helpful!
I'm new to Linux, so it took me a while, but I got it.
At first, when GW loaded it would come up with the server connecting screen and then freeze.
I found that disabling the virtual desktop emulation thing fixed it.  
Just now I started GW up...minimized it....and then :-k  it wouldn't restore the window when I unminimized it.  So, if anyone could tell me what was wrong, maybe fix it, I'd really appreciate it.
Thanks :KS

edit: It seems now that my mouse is gone....I tryed the mouse patch, but I was wondering *is this compatible with wine 9.29?*. Would that even be the case?

---

### Post by EvanPMeth on 2007-01-15
> 
[*]Download a script to install the programs needed to compile wine for Dapper [here]("http://kegel.com/wine/dapper.sh") - save it as pkgs.sh. If you use breezy, download [this one]("http://kegel.com/wine/breezy.sh")). If you are using Edgy, there is no script, but you can see the necessary packages [here]("http://wiki.winehq.org/Recommended_Packages"). If anyone ever writes a script for it, it will be posted there.



Actually the easier way and more proper way of doing this is to add the repositories and use "apt-get build-dep":

Follow this link [Wine Dependencies]("http://www.winehq.com/site/download-deb")

or add this to your /etc/apt/sources.list file:

```
deb http://wine.budgetdedicated.com/apt edgy main
deb-src http://wine.budgetdedicated.com/apt edgy main
```

then add the key set for wine if you get the ERROR
 ```
W: GPG error: http://wine.budgetdedicated.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
```
then do:

```
gpg --keyserver subkeys.pgp.net --recv 387EE263 && gpg --export --armor 387EE263 | sudo apt-key add -
```

after that just type in ```
sudo apt-get build-dep wine
```

and then you have all the dependencies you need and more :D .

 -evanpmeth

---

### Post by Apt_Quadruped on 2007-01-22
alright, I got Guild Wars to load, but the no cursor bug annoys me. I'm using wine version 0.9.29 on ubuntu 6.10 edgy and I haven't been able to figure out a way to patch wine (I searched everywhere). If somebody could explain exactly how to specificly patch Guild Wars with the patch for the no cursor bug it'd be greatly appreciated. Thanks in advance!

---

### Post by User_Program on 2007-01-22
> **Apt_Quadruped said:**
> alright, I got Guild Wars to load, but the no cursor bug annoys me. I'm using wine version 0.9.29 on ubuntu 6.10 edgy and I haven't been able to figure out a way to patch wine (I searched everywhere). If somebody could explain exactly how to specificly patch Guild Wars with the patch for the no cursor bug it'd be greatly appreciated. Thanks in advance!

Did you read the first page of this thread.  It's right there.  First post first pages.

---

### Post by enopepsoo on 2007-01-22
nice avatar!

---

### Post by Apt_Quadruped on 2007-01-22
> **enopepsoo said:**
> nice avatar!

Thanks, I like your avatar too! lol

> **User_Program said:**
> Did you read the first page of this thread.  It's right there.  First post first pages.

Yes, it is right there, for version 0.9.23 to 0.9.28 but I have version 0.9.29 which makes the guide (for me) worthless since half of the commands don't work. I may be mistaken but I can't follow along with it.

---

### Post by Jarn on 2007-01-23
Nothing in there is specific to 0.9.28 except for MAYBE the patch, I haven't tested. The file names will have changed from 0.9.28 to 0.9.29 to reflect the change in version. I updated the first post to reflect the change in source number. I also updated the links. The patch may or may not work with 0.9.29, the only way I know is if someone else has done it before. I have not yet upgraded because I've been doing other things, so I'm still using 0.9.28. But if you try the patch and don't get an error, it worked. Again, I also updated the first post to use 0.9.29 instad of 0.9.28, so you SHOULD be able to use that now.

---

### Post by Apt_Quadruped on 2007-01-23
alright, thanks for revising the guide for me! At the moment I'm patching the source with the mouse patch you've provided, but it's been about 5 minutes since I started to patch it. Once it is finally installed I'll let you know if it works, thanks!

---

### Post by Jarn on 2007-01-23
Hrm... IIRC it was near instant. That's odd that it's taking so long. Did you have any luck?

---

### Post by ngdias on 2007-01-24
I tried using this guide to fix the mouse issue, using wine 0.9.29 in Ubuntu Edgy 6.10 64-bits. 

The page mentioned in this guide to get the necessary files to compile wine is for 32-bits, but on that page there is a link with [instructions for 64-bits]("http://wiki.winehq.org/WineOn64bit#head-56206e8bc74083807ffe06ccb471d3f964cb670a") and I followed it. 

There it has instructions for several systems, including Debian and Dapper (no edgy). Following those Dapper instructions, I wasn't able to download libc6-dev-i386 due to this error:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev-i386_2.4-1ubuntu12.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev-i386_2.4-1ubuntu12.2_amd64.deb)
  403 Forbidden [IP: 195.248.90.35 80]

I tried compiling anyway, but got this output:

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Any ideas?...

EDIT: applying the mouse patch didn't create any errors. the filenames don't match though.

---

### Post by Apt_Quadruped on 2007-01-24
> **Jarn said:**
> Hrm... IIRC it was near instant. That's odd that it's taking so long. Did you have any luck?

nope, I didn't have any luck... I gave up after 30 minutes of waiting. I think I might try again today, but I doubt that it'll work. If it does work this time I'll post, but anyways, any ideas?

> tony@APPLE:~/wine-0.9.29/dlls/winex11.drv$ patch <~/winestuff/32mouse.patch
bash: /home/tony/winestuff/32mouse.patch: No such file or directory
Is this the correct command (it returns in error)?

> tony@APPLE:~/wine-0.9.29/dlls/winex11.drv$ patch /winestuff/32mouse.patch
This is the Command that makes it just "load" forever.

---

### Post by Jarn on 2007-01-24
> **Apt_Quadruped said:**
> Is this the correct command (it returns in error)?It looks like you didn't save it in the same spot as in the guide. Where did you save it?

---

### Post by Apt_Quadruped on 2007-01-24
Alright, Jarn you just made me feel like the stupidest person in the world! Yes, you were right, I didn't save it in the right spot, infact I had all my files scattered! I thank of you for catching my mistake, at the moment I'm compiling wine. I'll post back soon!

---

### Post by Jarn on 2007-01-24
Good luck. All those commands are based off saving the files in the places indicated in the first post. ;)

---

### Post by Apt_Quadruped on 2007-01-24
> tony@APPLE:~$ wine "C:\Program Files\Guild Wars\Gw.exe"
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
fixme:advapi:SetFileSecurityW (L"C:\\Program Files\\Guild Wars\\Gw.tmp") : stub
fixme:advapi:SetFileSecurityW (L"C:\\Program Files\\Guild Wars\\Gw.dat") : stub
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

Alright, I successfully patched wine, but once I attempted to run Guild Wars I retrieved this error. If someone could point me in the right direction I'd be very thankful.

~*this happens with everything in wine*~

---

### Post by ngdias on 2007-01-25
The same thing is happening to me. Since libc6-dev-1386_2.4-1ubuntu12.2 can't be downloaded (the access forbiden error) I decided to download and install the next version - 12.3 for libc6, libc6-dev and libc6-i386. At some point I got a warning that one package (I think libc6-i386) was  conflicting with libc6-dev, but now it seems that libc6-dev is conflicting with itself. 

All this mess is probably related with the libc6 issue currently being worked out - I couldn't dl the 12.2 version (the recomended one) and i decided to give 12.3 a try. I guess there was bad timming, trying to get wine and GW to work this week...

Other than that I didn't detect any warnings or errors in the terminal at the end of each task. And I also get the same error messages as Apt_Quadruped when trying to use wine.

---

### Post by Jarn on 2007-01-25
Sorry, I don't know what the problem is. :/

---

### Post by Mazza558 on 2007-01-25
I need help with this... I followed the guide, but got stuck at "mv GWSETUP.EXE ~/.wine/drive_c"

```
mv: cannot move `GWSETUP.EXE' to `/home/james/.wine/drive_c': No such file or directory

```


The folder apparently didn't exist, so I created a folder called "/.wine/drive_c/" and the command worked. However, It will not install. Where am I going wrong?

---

### Post by Jarn on 2007-01-25
What are the errors? And have you run winecfg?

---

### Post by Apt_Quadruped on 2007-01-25
Alright, I think I'll just wait untill some other day to mess with the patching stuff again. Anyways... Jarn could you help me uninstall everything of wine? I tried it through a package manager, but i can still use wine in terminal! I also tryed reinstalling but I still get that error!
*wine 0.9.30 has been released!*

---

### Post by Jarn on 2007-01-25
There really isn't that much that you need to get rid of. I think 'locate wine' will tell you the locations of the wine binary. I'm not at home right now, so I don't remember where the binary is placed. However, all you should need to remove would be the binary, ~/winestuff, and ~/.wine - and HOORAY for a new version of wine! :) But wow, does that mean I've been slow updating the main page! I only updated it to 0.9.29 two days ago! I'll update it to 0.9.30 tonight, probably, and make sure all the patches work while I'm at it.

---

### Post by Apt_Quadruped on 2007-01-25
Alright, I just found a command to remove wine...
```
apt-get remove wine
```
Anyways... I'm installing 0.9.30 now... Thanks for trying to get Guild Wars to work correctly, but I'll have to find another way.

---

### Post by Mazza558 on 2007-01-25
RIght, i've got GW running, but when it starts the 3D Rendering, I get a low-colour GW cursor and a green background.

---

### Post by Apt_Quadruped on 2007-01-25
> **Mazza558 said:**
> RIght, i've got GW running, but when it starts the 3D Rendering, I get a low-colour GW cursor and a green background.

how did you get the cursor, and what version of wine are you using?

---

### Post by Mazza558 on 2007-01-25
> **Apt_Quadruped said:**
> how did you get the cursor, and what version of wine are you using?

I used the 32bit patch on the first page. My version of wine is .29, not .23

However, my winecfg now won't run, with this in terminal:

```
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x2e00007
  Serial number of failed request:  13
  Current serial number in output stream:  15

```

---

### Post by Apt_Quadruped on 2007-01-25
hm... I guess you must have something installed on your comp that I don't. I got that error that I previously metioned, but I'm installing guild wars right now (reinstalled wine).

---

### Post by Mazza558 on 2007-01-25
I wonder if there's a command to reset wine settings.

---

### Post by orgyn on 2007-01-25
wine 0.9.30 still needs the 32bit mouse patch

---

### Post by Apt_Quadruped on 2007-01-25
alright, turns out that no version of wine is working for me! I still get the same X11 error.
```
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.
```
Does anyone know how to get around this (I've been googling for a while with no luck...)?

---

### Post by Apt_Quadruped on 2007-01-25
Okay, I just discovered how to get out of my hole! I got onto the winehq IRC channel and I got everything solved out. It turns out that I didn't have everything that I needed for wine to work properly. I had to download...
```
http://kegel.com/wine/edgy.sh
```
Then I just ran...
```
chmod +x edgy.sh
./edgy.sh
```
After I downloaded/installed all of that I was able to go through this guide without error! I hope this helps others that were experiencing the same problem as me, thanks once again Jarn for helping me with Guild Wars!

---

### Post by Jarn on 2007-01-26
> **Apt_Quadruped said:**
> I had to download...
```
http://kegel.com/wine/edgy.sh
```UGH! I literally JUST made a script that does the exact same thing. The wine page had one listed from the same guy for dapper and breezy, but not for edgy. Well, I can take mine down and replace it with his. :P I'm also writing script that will do the entire process, from start to finish. I'm running it right now, to upgrade myself to 0.9.30 and to see if it works. If it does, I'll post it.

EDIT: It is up! I have added two scripts that will do the entire guide, from start to finish! updatewine.sh does steps one through six. It is for if you have already installed GW at a previous time and only want to update to the newest version of the source. installwine+gw.sh does all the mandatory steps (one through nine) and is for if this is the first time you have installed GW. Also, installwine+gw.sh requires edgy since it apt-gets the packages needed to compile wine. It is really easy to edit, however, and I have posted instructions in the first post. I would like to note that I have not run the installwine+gw.sh (since I didn't need it) and only have run updatewine.sh. installwine+gw should work, though, because it is just updatewine with the extra steps added.

---

### Post by Mazza558 on 2007-01-26
[[IMG]http://img180.imageshack.us/img180/6576/screenshotpy9.th.png[/IMG]](http://img180.imageshack.us/my.php?image=screenshotpy9.png)

This is what my desktop looks like now... it hangs just after GW says "unsupported graphcs card", and I can't close it. Where am I going wrong?

EDIT: It now comes up with something like "out of memory" in a tiny message box. What now?

(I'm running wine .29, if that means anything)

---

### Post by misuher on 2007-01-26
where can i Get installwine+gw.sh?

---

### Post by ngdias on 2007-01-26
I was digging around yesterday and found some other guides to install wine. At this moment I have 0.9.29 installed and GW working with mouse visible, but crashing with the 'too many concurrent lights' error. I don't have combat sound and since I reinstalled wine the ALSA sound driver is not showing up in winecfg. I'm still testing and looking for info on this sound issue.

I'm also under the impression that graphics were better with my previous setup - 0.9.23 (compiled by someone else for 64-bits), but I'll have to do some more testing to find out. I can tell that before I could change gama ingame and now it's not working. Antialiasing options atm are 'none' only.

I'm also using Nvidia+Beryl and I don't notice anything worse compared to Metacity (Gnome default)- I had to activate a wine option in beryl manager to get full screen working properly though.

I think what me and Apt_Quadruped were missing while compiling wine was this symlink:
```
sudo ln -s /usr/lib32/libXrender.so.1 /usr/lib32/libXrender.so
```

-------------------------------------------------------------------

Anyway this was roughly what I did. Maybe it will help you:

1. Download the source code file and unzip it to a folder. I used 0.9.29 from [http://prdownloads.sourceforge.net/wine/wine-0.9.29.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-0.9.29.tar.bz2). I'm not sure it's there anymore, but 0.9.30 is out already, so...

2. Use [this guide]("http://www.ubuntuforums.org/showthread.php?t=291620") to get your system ready to compile wine (for 64-bit systems). Just complete all of step 2.

3. Now patch wine to get the mouse working and fix all other bugs. I only used the mouse patch but I think there are other patches (not sure if they're needed for 0.9.30). The link for the patch file and the instructions to patch were taken from Jarn's guide at the very begginng of this thread:

- Download a patch you will need [here]("http://www.ubuntuforums.org/attachment.php?attachmentid=21723&d=1167218291") - save it as 32mouse.patch
- apply the patch
```
cd wine_folder_path_here/dlls/winex11.drv
patch <~/winestuff/32mouse.patch
```

3. Compile wine and install it (the code is the step 3 from the same guide mentioned at step 2):
```
CFLAGS="-fno-stack-protector -O2" ./configure --verbose
make depend && make
sudo make install
```

4. I also applied the Sidenet script as described [here]("http://www.ubuntuforums.org/showthread.php?t=185557"), but I'm not sure its really necessary.

5. Follow steps 7 through 11 of Jarn's guide to configure wine and install GW.

---

### Post by Jarn on 2007-01-26
> **misuher said:**
> where can i Get installwine+gw.sh?
At the bottom of the first post, it's attached to the first post.

> **ngdias said:**
> crashing with the 'too many concurrent lights' errorThere's a patch for that in the first post, step 11. To sate my curiosity, does that come up in an error box or in the terminal?

---

### Post by Apt_Quadruped on 2007-01-26
could anyway help me make it so that Guild Wars actually gets a higher fps then 10? On Windows I usually got at the least of 20 (in exteme combat at max settings).

---

### Post by Jarn on 2007-01-26
I don't know why you don't get about the same as you do in Windows, I know I do. I get between 30 and 45, which is the same as what I get in Windows. Sorry. :/

---

### Post by FyreBrand on 2007-01-26
I have wine compiled and installed correctly with 0.9.29.  I used kegel's new script.  It's funny that you said that about the script Jarn because I was about half way done with one and was checking his site for more info when I ran across the completed version.  There are some things in that script I wouldn't have known to put in though.

Interestingly enough I can't enable the virtual desktop or it doesn't work.  I have to use the mouse.patch and the lightingh-hack.patch in order for it to work (Nvidia 6800XT).

I copied my gw.dat file over from my Windows partition.  It worked fine until I I went into a certain zone and then I got stuck.  I was testing out the install with a pre-sear character and was heading to Barradin's Estate.   About half way there the hard drive started working hard and thrashing.  So I figure my gw.dat file was pretty fragmented from the NTFS partition and didn't copy well.  If I understand it properly the gw.dat file is something like a virtual drive.  So I will try and download a completely new .dat file.

I'm also not sure if it was that or possibly a networking issue at home.  Every once in a while I get and err=58.  But as far as wine goes it's working better than it ever has.  It's pretty impressive the improvements they've made.

---

### Post by Jarn on 2007-01-26
> **FyreBrand said:**
> as far as wine goes it's working better than it ever has.  It's pretty impressive the improvements they've made.It is indeed! Five, maybe even four, months ago Guild Wars rating was usually garbage or bronze. Now it seems to be generally silver or gold. That is a huge improvement!

FyreBrand, if you decide to update to 0.9.30, check out the script I made. It's pretty nice. ;)

---

### Post by ngdias on 2007-01-26
> **Jarn said:**
>  To sate my curiosity, does that come up in an error box or in the terminal?

Terminal.

I know about the lights patch, I just was hoping .30 wouldn't need it.

Here's an update on my progress:
Things were not very bright, so i decided to turn off beryl, remove wine completely and start again.

I followed this [https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64) to install 0.9.29, but since I didn't compile it, the bugs are still there. On the positive side, I can control gamma ingame now. I copied the GW folder back into 'Program Files' and ran gwsetup.exe again.

Audio quality is poor (I tried both OSS and ALSA) and giving a lot of errors in terminal.

I'm going to compile .30 next and see what happens.

@FyreBrand: Virtual desktop was disabled in all versions I compiled so far and everyone needed the 2 patches.

---

### Post by FyreBrand on 2007-01-26
> **Jarn said:**
> It is indeed! Five, maybe even four, months ago Guild Wars rating was usually garbage or bronze. Now it seems to be generally silver or gold. That is a huge improvement!

FyreBrand, if you decide to update to 0.9.30, check out the script I made. It's pretty nice. ;)Ugh!  I can't believe there is a .30 already. hahaha.  I will uninstall .29 and compile .30 in the coming week or so and then report back. Thanks for making a script. I will definitely check it out.

ngdias - I did have beryl installed a few weeks ago to test it out.  It does not play well with GuildWars at all.  I would suggest logging into kwin or metacity first and making sure beryl and emerald are not running.

---

### Post by Jarn on 2007-01-26
So what happens with the "Too many concurrent lights" error? Does it happen every time? I heard that users of nVidia must use the patch for it, but I've never had any problems.

ngdias: Sorry you're having problems with 64-bit. That's why I installed 32-bit even though I have a 64-bit capable processor, since 32-bit is more used. ;)

---

### Post by FyreBrand on 2007-01-26
> **Jarn said:**
> So what happens with the "Too many concurrent lights" error? Does it happen every time? I heard that users of nVidia must use the patch for it, but I've never had any problems.

ngdias: Sorry you're having problems with 64-bit. That's why I installed 32-bit even though I have a 64-bit capable processor, since 32-bit is more used. ;)With the light-hack.patch I don't seem to have that error, but then I haven't verified that.  Even though I leave the terminal open when I'm playing when it's crashed hard it's pretty much crashed my whole system so I haven't been able to see if the too many concurrent lights error was the problem.

I deleted my gw.dat file and I'm letting it rebuild from scratch.

I do have one problem that I'm not sure about.  I don't have the ALSA sound option available in the config.  I use ALSA sound drivers.  I figure I've just missed an obvious step or I need to reconfigure ALSA.  If you have any suggestions I'm listening.

---

### Post by Jarn on 2007-01-26
I have no suggestions, I'm sorry, every time when I've compiled it I have had ALSA in my Audio tab.

---

### Post by FredDie3785 on 2007-01-27
Well I've downloaded your newest script for Edgy Eft. I've done everything what you suggested and now I don't know what to do. Script downloaded gw.exe but I don't know how to run it.

Sorry for this noobish question, I'm a rookie in Ubuntu, but I can't stand the Windows anymore.

---

### Post by Apt_Quadruped on 2007-01-27
> **FredDie3785 said:**
> Well I've downloaded your newest script for Edgy Eft. I've done everything what you suggested and now I don't know what to do. Script downloaded gw.exe but I don't know how to run it.
Change your directory to where gw.exe is (in terminal) and then type...
```
wine gwsetup.exe
```
Just replace "gwsetup.exe" with whatever the exe is called. By the way... I don't find Guild Wars to be playable in wine (at least for me). My fps in wine is about 5-10 just at the login screen! Anyways... I just use windows for gaming now... since my fps is about 3-4 times better in it.

---

### Post by FredDie3785 on 2007-01-27
I've got Radeon 9200, 1GB RAM, AthlonXP 2200+ and the default ati drivers in Ubuntu. Someone tested GW under that configuration??

---

### Post by Jarn on 2007-01-27
What script did you use, out of curiosity?

From what I have heard, ATI cards generally don't work very well in Linux. But the only way to find out is to try. Good luck!

EDIT: Looking over my installwine+gw.sh script, I had a typo in it. So if anyone had run that, you probably would have gotten an error. It's fixed now.

---

### Post by FredDie3785 on 2007-01-27
I've got another questions...

1. Can I use default Ati drivers which are installed with Ubuntu, or should I install other drivers??

2. Can I translate your guide on polish Guild Wars forum, of course I will add that it's your guide. I will only translate it.

---

### Post by Jarn on 2007-01-27
> **FredDie3785 said:**
> 1. Can I use default Ati drivers which are installed with Ubuntu, or should I install other drivers??Your best bet would be to ask someone who uses an ATI card, I have no idea. I would imagine the ones with Ubuntu are fine, though.

> **FredDie3785 said:**
> 2. Can I translate your guide on polish Guild Wars forum, of course I will add that it's your guide. I will only translate it.Sure. But I would like you to put in it that it may be out of date, unless you plan on updating it every time I update mine (usually with every new release of wine).




I edited the installwine+gw.sh script... again.

---

### Post by FredDie3785 on 2007-01-27
Of course I will be updating it...thx broe...

---

### Post by FyreBrand on 2007-01-27
Ok Jarn here's the feedback scoop.  Wine 0.9.29 and 0.9.29 both work pretty good.  I've expereienced no new problems in .30 and overall it does seem smoother.  Here are some things of note starting in .28.
1. I could no longer get the game to execute under the version setting Win98.  I had to use WindowsXP setting.  The good thing is the WinXP setting finally works.

2. The virtual desktop setting didn't work that well.  I would work some but I was still having sizing issues.  The game was larger than the virtual desktop size even when I resized it at the login screen.  It's like the resize got ignored. On a positive note the game seemed to work okay (not using the virtual desktop) especially when I set it to my desktop resolution.  I did have some problems with the game resetting my desktop refresh rate to 60hz whenever I logged in, but that went away in version .30.

3. I'm having a file problem in these later versions that I didn't have before.  The game will be running fairly smooth and then the framerate will start to drop off down to 10fps or less and the hard drive will start chunking away as though the gw.dat file is fragmented.  The framerate will eventually drop down to 1fps and then freeze with occasional graphic updates.  Then the game will crash.  This seems to happen after an hour or maybe even two.  It has happened in pre-searing and also in Abbadon's mouth.  I haven't spent a lot of time in Cantha or Elona while in wine so it could happen there as well.

4. I still need the device.c.patch and the 32mouse.patch.

It is playable but I still only go with henchies when I'm in wine so I don't crash in the middle of someones mission.  I log in to Windows when I group.

---

### Post by Jarn on 2007-01-27
> **FyreBrand said:**
> The virtual desktop setting didn't work that well.  I would work some but I was still having sizing issues.  The game was larger than the virtual desktop size even when I resized it at the login screen.What did you resize? The virtual desktop?

> **FyreBrand said:**
> as though the gw.dat file is fragmented.  The framerate will eventually drop down to 1fps and then freeze with occasional graphic updates.  Then the game will crash.Have you tried defragmenting the file?

> **FyreBrand said:**
> I still need the device.c.patch and the 32mouse.patch.So what happens with the "Too many concurrent lights"? Does the game just crash? Freeze? What happens?


Thanks for the update! It's good to know how others are fairing.

---

### Post by FyreBrand on 2007-01-27
I tried the virtual desktop at 1280x1024 (my desktop rez) and also 1024x768.  I tried resizing the GuildWars client in both and it wouldn't resize.

I originally copied the gw.dat file from my ntfs partition.  I also deleted it and let it download a new one.  Other than copying the file from one location to another I'm not sure how to defragment the files inside the .dat file.  In any event it has happened with the old file and with a completely new file.

I'm not sure how to test if "too many concurrent lights" is the problem.  Whenever the system has crashed it's really crashed the desktop hard.  The hard drive is working away like mad.  fsck and smart both haven't reported any problems, but that doesn't mean the drive isn't the problem, but I don't think so since it's behavior is reliable elsewise.

I'll test again in a week or two after doing some research and see if I come up with any answers.

It's always good to see you post back and update though.  It's very encouraging.  From reading a few threads on guildwarsonline.net there are more of us than I thought.  Most use Cedega though.

---

### Post by Jarn on 2007-01-27
> **FyreBrand said:**
> I'm not sure how to test if "too many concurrent lights" is the problem.I wasn't suggesting it was, I just thought previously you had said you had had that problem (maybe it was someone else) and I still don't know anything about it. I was just trying to find out more about it, I wasn't suggesting it was your problem. ;)

---

### Post by FyreBrand on 2007-01-28
You know I was just assuming it was because I did have a different type of complete freeze before it was installed.  I also use an NVidia 6800XT which is a very similar card to xisixisxis (i can't remember exactly how he spells that lol).

---

### Post by FredDie3785 on 2007-01-28
Well I've got this error while installing gwsetup.exe

> libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
Failed to open the service control manager.
wine: '/root/.wine' created successfully.
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!


---

### Post by rmjb on 2007-01-28
> **FredDie3785 said:**
> I've got another questions...

1. Can I use default Ati drivers which are installed with Ubuntu, or should I install other drivers??

I use my ATi card to play GW in cedega and it works fine. See here [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) for a guide on how to install it. I used Method 1.

- rmjb

---

### Post by Jarn on 2007-01-28
> **FredDie3785 said:**
> Well I've got this error while installing gwsetup.exe
Did you install it as root? I don't know what your problem would be, but it looks like you ran the script as root. That's not really necessary. It uses sudo so it should just prompt you for your password when it needs it. You could try asking in #winehq what that error means. But I would not install it as root, if I was you.

---

### Post by FredDie3785 on 2007-01-28
Ok I installed drivers correctly [my Radeon 9200 is being detected by fglrxinfo] and now I've got this error...

> configure: WARNING: X development files not found. Wine will be built without
configure: WARNING: X support, which currently does not work, and probably
configure: WARNING: isn't what you want anyway. You will need to install devel
configure: WARNING:  packages of Xlib/Xfree86 at the very least.

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:

configure: WARNING: Your system appears to have the FreeType 2 runtime librariesconfigure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FreeType is missing.
configure: WARNING:

I'm trying to install it manually. Any suggestions...

---

### Post by Jarn on 2007-01-28
> **FredDie3785 said:**
> Ok I installed drivers correctly [my Radeon 9200 is being detected by fglrxinfo] and now I've got this error...



I'm trying to install it manually. Any suggestions...
It looks like your missing a lot of stuff. O.o. Did you run the script that installed the packages you needed? And probably try installing freetype-devel.

---

### Post by FredDie3785 on 2007-01-28
Damn probably my card acceleration isn't supported by wine.

> wine: creating configuration directory '/home/freddie/.wine'...
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Failed to open the service control manager.
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
wine: '/home/freddie/.wine' created successfully.
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!


---

### Post by Jarn on 2007-01-28
Try asking in the #winehq channel on irc.freenode.net, they could probably help you.

---

### Post by Azakus on 2007-01-28
The installwine+gw.sh script on the front has some typo errors with some extra space characters. I made one that works and here it is.
{EDIT}Fixed accidental removal of patch :( {/EDIT}

---

### Post by Jarn on 2007-01-28
> **Azakus said:**
> The installwine+gw.sh script on the front has some typo errors with some extra space characters. I made one that works and here it is.Thanks! But why did you remove the 'sudo apt-get install patch' line? I'll add it to the front page, but with that line back in, because patch is a necessary app to have.

---

### Post by Azakus on 2007-01-28
Here's a 64-bit install file and modified files necessary for a 64-bit build.
Building Wine by default in 64-bit fails because the libsicuuc.a file cannot be ported to 32-bit by ./configure or make for the gdi32.dll file, so included is the proper libsicuuc.a file and a modified make file for gdi32. It is all automated with the new install script.
Read the readme if you have any questions.
{EDIT}Mess up in the install script now fixed. Sorry for accidentally removing the line for installing patch.{/EDIT}

---

### Post by Azakus on 2007-01-28
> **Jarn said:**
> Thanks! But why did you remove the 'sudo apt-get install patch' line? I'll add it to the front page, but with that line back in, because patch is a necessary app to have.

Whoops. Didn't mean to get rid of that
I'll add it back in.

---

### Post by Jarn on 2007-01-28
Thanks for creating a 64-bit version! Also, I don't understand the other two differences between my original script and yours (32-bit). You changed 'sudo sh pkgs.sh' to 'sudo sh ./pkgs.sh' - what's the difference, both point to the current directory. Was it just to make it more specific? Also, what is the difference between #!/bin/bash and #!/bin/sh? I don't know much about scripts, I just took a look at a different one to see the format of them and it had #!/bin/sh so I put that in mine. Was that wrong? I'll add the 64-bit to the front page.

---

### Post by Azakus on 2007-01-29
The whole difference is just what terminal shell processes the commands. I prefer to use the bash shell (#!/bin/bash), but for maximum compatibility, sh is better (#!/bin/sh).
Also, the big difference is that I modified the one Makefile for gdi32 because it can't be made with the default script in 64-bit, and added the 32-bit version of the file gdi32.dll depends on, libsicuuc.a.

---

### Post by Azakus on 2007-01-29
Whoops. Ran into some problems with my current script (no ALSA drivers), so I modified the script with the enhancements on Wine's Wiki.

---

### Post by User_Program on 2007-01-29
Thats great that others are joining in on creating scripts for no hastle install.  How about you to collaborate your efforts?  Maybe somthing cool could come out of it (not that the scripts arn't cool) .

---

### Post by Jarn on 2007-01-29
Has anyone run the installwine+gw.sh script? I am trying but I keep getting errors. I don't understand, I get errors even in the parts that WORK in the updatewine.sh script. The whole thing is one giant error!

```
jarn@legion:~/bin$ sh installwine+gw.sh
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package patch
: No such file or directoryh
sh: Can't open ./pkgs.sh
: No such file or directoryurce.tar.bz2
: No such file or directorye.patch
tar: winesource.tar.bz2\r: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
cd: 10: can't cd to wine-*/dlls/winex11.drv
: No such file.sh: 11: cannot open /home/jarn/winestuff/32mouse.patch
cd: 12: can't cd to /home/jarn/winestuff/wine-*
: not found+gw.sh: 13: ./configure
'.  Stop. No rule to make target `depend
: not found+gw.sh: 15: make
'.  Stop. No rule to make target `install
--17:42:14--  http://www.guildwars.com/downloads/gwsetup.zip
'          => `/home/jarn/gwsetup.exe
Resolving www.guildwars.com... 206.127.153.151
Connecting to www.guildwars.com|206.127.153.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81,466 (80K) [application/zip]

100%[===================================================================================================>] 81,466       223.88K/s

' saved [81466/81466]) - `/home/jarn/gwsetup.exe

cd: 18: can't cd to ~
.ZIP.or gwsetup.zip or open gwsetup.zip
: not found+gw.sh: 20: wineprefixcreate
mv: cannot stat `/home/jarn/GWSETUP.EXE': No such file or directory
cd: 22: can't cd to /home/jarn/.wine/drive_c
: Permission denied23: cannot create /dev/null
installwine+gw.sh: 23: wine: not found
Complete! Good luck and have fun! - Jarn
```

All I can do is recommend the updatewine.sh script and then follow the manual instructions from there.

EDIT: Okay, that was odd. I simply retyped it and it works now. It's almost the exact same (I slightly changed the order) but it works now. Or atleast, it's running. Still downloading :P. I'll put it up when it finishes, if it finishes without errors.

---

### Post by Azakus on 2007-01-29
You had some really odd characters in that script. They looked like spaces, but where really some weird unicode placefiller spaces. I don't quite know how you got those in there, but that is what was killing the script.

---

### Post by Jarn on 2007-01-29
> **Azakus said:**
> You had some really odd characters in that script. They looked like spaces, but where really some weird unicode placefiller spaces. I don't quite know how you got those in there, but that is what was killing the script.That is odd. They didn't show up with nano. Well, now I know the script works, since I tested it. I'll upload an updated version in a minute, I added something else to it.

EDIT: I put up an updated version of updatewine.sh and installwine+gw.sh.

---

### Post by der_joachim on 2007-01-30
Shouldn't this thread be made sticky or something? Or even be included in the HOWTO forum? GWOS wiki anyone?

Dang. guild practice in 56 minutes and I still have to do the dishes. :(

---

### Post by Sir_Penguin on 2007-01-31
> **Azakus said:**
> The installwine+gw.sh script on the front has some typo errors with some extra space characters. I made one that works and here it is.
{EDIT}Fixed accidental removal of patch :( {/EDIT}
Thanks *heaps* for that. I'm actually trying to get CSS working but wine itself wasn't working. I wasn't actually sure what that script was meant to do but it worked :D Now WINE is running great :)

---

### Post by Balachmar on 2007-02-03
Hi this howto is great!
I used the install everything script at the first post.
And it runs pretty smoothly, it is now updating itself.
But I don't have any sound... Is that normal or is there a fix for it?

---

### Post by Apt_Quadruped on 2007-02-03
it's normal to not have sound in guild wars through wine.

---

### Post by Azakus on 2007-02-03
In Winecfg, change sound to Emulated. That will at least give you background sounds (though battle sounds are still missing).

---

### Post by Catsworth on 2007-02-04
Anybody able to tell me how long the 'install everything' script should take once it's downloaded everything it needs?

It seems to be doing something (can't tell what) but it's been doing it for 20 minutes or so now and there doesn't seem to be an end in sight.

Here's an example of the output in the console:

```
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -D_RPCRT4_ -DCOM_NO_WINDOWS_H -DMSWMSG -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o rpcss_np_client.o rpcss_np_client.c
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./rpcrt4.spec    cproxy.o cpsf.o cstub.o ndr_clientserver.o ndr_fullpointer.o ndr_marshall.o ndr_ole.o ndr_stubless.o rpc_binding.o rpc_epmap.o rpc_message.o rpc_server.o rpc_transport.o rpcrt4_main.o rpcss_np_client.o        -o rpcrt4.dll.so -lsecur32 -liphlpapi -ladvapi32 -lkernel32 -lntdll -Wb,-dsecur32 -luuid ../../libs/port/libwine_port.a  
make[2]: Leaving directory `/home/rob/winestuff/wine-0.9.30/dlls/rpcrt4'
make[2]: Entering directory `/home/rob/winestuff/wine-0.9.30/dlls/rsabase'
../../tools/winegcc/winegcc -B../../tools/winebuild -shared ./rsabase.spec            -o rsabase.dll.so  -lrsaenh -lkernel32   ../../libs/port/libwine_port.a  
make[2]: Leaving directory `/home/rob/winestuff/wine-0.9.30/dlls/rsabase'
make[2]: Entering directory `/home/rob/winestuff/wine-0.9.30/dlls/rsaenh'
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o des.o des.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o handle.o handle.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o implglue.o implglue.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o md2.o md2.c
gcc -c -I. -I. -I../../include -I../../include  -D__WINESRC__ -DCOM_NO_WINDOWS_H -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith  -g -O2  -o mpi.o mpi.c
gcc -c -I. -I. -I../../include -I../../
```

Thanks.

---

### Post by jcquik on 2007-02-04
it takes awhile.  mine took 30 min and then the guild wars download started.

---

### Post by Catsworth on 2007-02-04
Yeah, thanks for that - the GW download just started (and it looks like it's going to take a while - downloading at 15Kb/s and very spikey to say the least.....).

Cheers.

---

### Post by Jarn on 2007-02-04
It takes awhile. Compiling things always takes awhile. The speed will vary based on your processor.

EDIT: Er... apparently I wasn't at the last post, I thought I was. My bad. :P

---

### Post by Catsworth on 2007-02-04
Ok, all installed.

The problem now would appear to be that because GW was installed under 'sudo' it can't be run because the file permissions are wrong on the folders that contain the application files.

Anybody know which permissions I need to change, and to what?

Thanks.

---

### Post by rmjb on 2007-02-04
sudo chmod 777 <files> will work. Where are the guild wars files? If they're in your home directrory chaning the owner to you should be the better thing. You can always gksu nautilus to get a root file browser and from there use the GUI tools to change owner and permissions as you like.

- rmjb

---

### Post by Catsworth on 2007-02-04
> **rmjb said:**
> [...]Where are the guild wars files?

Not a clue, they were installed by the automated script (I'm assuming under WINE) but I haven't a clue where they went :confused:

---

### Post by rmjb on 2007-02-04
Check in /home/<your username>/.wine or, if it was done as root under /root/.wine.

- rmjb

---

### Post by Catsworth on 2007-02-04
Ok, found it and (after some fiddling) changed the permissions so that I can launch the application.

Now I have two new problems:

1.  GW changes the screen resolution when it launches.  In Windows it gets changed back when the application is closed, in Ubuntu it doesn't.
2.  As soon as I open GW my processor fan comes on full whack and GW slows to a crawl.  I can't even get all of the elements of the login screen to load fully, everything just slows down so much it's unreal.

I'm guessing that #2 is because I'm running it through WINE, if that's the case then there's not a lot of point in worrying too much about #1 if it's not going to be playable anyway.

I'll have a read through the thread from the beginning and see if anybody else has had the same trouble.

Thanks for the help.

---

### Post by Jarn on 2007-02-04
> **Catsworth said:**
> Ok, all installed.

The problem now would appear to be that because GW was installed under 'sudo' it can't be run because the file permissions are wrong on the folders that contain the application files.

Anybody know which permissions I need to change, and to what?

Thanks.GW was installed as root? Did you sudo the install script?

---

### Post by Azakus on 2007-02-04
> **Catsworth said:**
> Ok, found it and (after some fiddling) changed the permissions so that I can launch the application.

Now I have two new problems:

1.  GW changes the screen resolution when it launches.  In Windows it gets changed back when the application is closed, in Ubuntu it doesn't.
2.  As soon as I open GW my processor fan comes on full whack and GW slows to a crawl.  I can't even get all of the elements of the login screen to load fully, everything just slows down so much it's unreal.

I'm guessing that #2 is because I'm running it through WINE, if that's the case then there's not a lot of point in worrying too much about #1 if it's not going to be playable anyway.

I'll have a read through the thread from the beginning and see if anybody else has had the same trouble.

Thanks for the help.

For #1, run Guild Wars in windowed mode.
For #2, are you running Beryl or Compiz? Neither like Guild Wars at all, so I'd drop back into Metacity for it. If not, try running it with the tag "-dx8" in the launcher and see if it gives you faster performance.

---

### Post by FyreBrand on 2007-02-05
> **Catsworth said:**
> Ok, found it and (after some fiddling) changed the permissions so that I can launch the application.

Now I have two new problems:

1.  GW changes the screen resolution when it launches.  In Windows it gets changed back when the application is closed, in Ubuntu it doesn't.
2.  As soon as I open GW my processor fan comes on full whack and GW slows to a crawl.  I can't even get all of the elements of the login screen to load fully, everything just slows down so much it's unreal.

I'm guessing that #2 is because I'm running it through WINE, if that's the case then there's not a lot of point in worrying too much about #1 if it's not going to be playable anyway.

I'll have a read through the thread from the beginning and see if anybody else has had the same trouble.

Thanks for the help.Like Azakus said make sure you are using either metacity (in gnome) or kwin (in kde) as your window managers.  3d compositing window managers like compiz or beryl don't always work well with other 3d apps especially games.

Another thing to check out is which video driver you're using.  I found that using the proprietary driver for both ATI and Nvidia helped out a lot.  The open radeon driver works better than the open nv driver for 3d apps, but really fglrx (ati) and nvidia proprietary drivers work better.

A quick way you can check how well your card and driver are dealing with 3d is to open the konsole or terminal and type:
```
glxgears -printfps
```This will bring up 3d gears that rotate and also print the framerate that your card is processing them..  It will also give you a few error messages if it's not working well.  If you do get error messages I can't really help you with them, but check the audio, video, multi-media forum.  There are lots of threads there on how to get 3d working better.

---

### Post by cahumphrey on 2007-02-07
First off, thanks for the script!
It worked perfectly for me, and I was able to load Guild Wars....

I tried the game today, in windowed mode, which seems to be a bit more compliant, and I now have a mouse pointer 95% of the time, but still have no sound. Any advice??

I am VERY new to linux, but I am really really liking Ubuntu 6.10, and hoping to push through some of these issue and enjoy linux all the time, instead of having to put up with a dual boot. :)

---

### Post by Jarn on 2007-02-08
Sound doesn't seem to work in Guild Wars at the moment. AFAIK, no one has sound. Sorry. :(

---

### Post by FyreBrand on 2007-02-09
> **Jarn said:**
> Sound doesn't seem to work in Guild Wars at the moment. AFAIK, no one has sound. Sorry. :(I'm wondering if other people are getting sound with their wine games or if it's just Guild Wars.  I also wonder if we might be leaving a library out when we compile.   I used to have sound in GW under wine, but now I don't either.  Kind of odd.

I haven't been playing under wine anymore.  I kept getting those weird hard drive freezes, so I'm going to put it on the back burner for the moment.

---

### Post by der_joachim on 2007-02-09
> **FyreBrand said:**
> I'm wondering if other people are getting sound with their wine games or if it's just Guild Wars.  I also wonder if we might be leaving a library out when we compile.   I used to have sound in GW under wine, but now I don't either.  Kind of odd.

I haven't been playing under wine anymore.  I kept getting those weird hard drive freezes, so I'm going to put it on the back burner for the moment.

Steam has sound. In GW, it is only the combat sounds that do not work. AFAIK there's music and background sound. I have both alsa and OSS enabled, but enabling only alsa does the same for me. 

Here, GW is pretty stable in wine. I run at 1680x1050 full screen at roughly the same frame rate as XP.

---

### Post by Catsworth on 2007-02-09
Thanks guys, not had a chance to look at this yet as I haven't got Internet at home - it's all connected now so I'll take a look at this at the weekend and try out your suggestions.

Cheers.

---

### Post by FyreBrand on 2007-02-09
I only show OSS available in winecfg.  I use ALSA for everything else and have great sound in Amarok, Firefox, Konqueror, etc.  I probably just don't have sound configured properly.  I looked at some HowTo's for configuring onboard Intel sound, but I'm not ready to fiddle with that yet.

---

### Post by Mblackwell on 2007-02-11
Wow, using the 32mouse patch I actually got the thing going in 9.30 basically out of the box (although performance kinda sucks and adjusting settings doesn't help much). 

I do miss battle sounds and the like, but it's really really playable (and to note, I'm running it on a DX9 path so I get all the pretty effects). Too bad shadows are a bit crazy.

Hopefully by the next official Wine release we can see this in "Gold" status.

My big bugs are that I HAVE to run it with the virtual desktop (which is okay I suppose), and that it seems to get stuck in an endless loop during the intial load sometimes (often enough to be annoying). Luckily I run Wine from the terminal, so I can always just CTRL+C out.

---

### Post by axcairns on 2007-02-14
My GW is cactus. I had previously installed wine 0.9.30 and used it to install GW. I then came across this thread and downloaded and ran the updatewine script. When I try to launch GW it changes resolution (shutting down my second monitor) but then nothing. If I run from console and alt-tab back to it at this point I get lines very much like this one scrolling by at a rapid rate -

> err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 1b3b353b while expecting dc4315be)

Allan

---

### Post by Jarn on 2007-02-14
> **axcairns said:**
> My GW is cactus.Cactus?

---

### Post by Mblackwell on 2007-02-14
> **axcairns said:**
> My GW is cactus. I had previously installed wine 0.9.30 and used it to install GW. I then came across this thread and downloaded and ran the updatewine script. When I try to launch GW it changes resolution (shutting down my second monitor) but then nothing. If I run from console and alt-tab back to it at this point I get lines very much like this one scrolling by at a rapid rate -



Allan

I have that too. If I CTRL+C out and run it again immediately it works.

---

### Post by axcairns on 2007-02-14
> **Jarn said:**
> Cactus?

Cactus - broken, busted, disabled, down, fallen apart, faulty, feeble, gone, haywire, imperfect, in disrepair, inoperable, kaput, not functioning, out, ruined, run-down, screwed up, shot, spent, unsatisfactory, weak, wracked

---

### Post by Jarn on 2007-02-14
> **axcairns said:**
> Cactus - broken, busted, disabled, down, fallen apart, faulty, feeble, gone, haywire, imperfect, in disrepair, inoperable, kaput, not functioning, out, ruined, run-down, screwed up, shot, spent, unsatisfactory, weak, wrackedApparently I'm not up on the latest lingo. As for your problem, does it affect other apps or only GW?

---

### Post by axcairns on 2007-02-15
> **Mblackwell said:**
> I have that too. If I CTRL+C out and run it again immediately it works.

I tried your suggestion -

First time - the CRC error. Ctrl-C
Second time - game launched successfully but the mouse cursor disappeared after a couple of seconds. I managed to click on the close button.
Third time -  game launched successfully but the mouse cursor disappeared after a couple of seconds. I missed the close button and got the maximise/restore button next to it. This caused the whole thing to hang. Alt-tabbed to terminal and Ctrl-C
Fourth and all subsequent times - CRC error

:(

---

### Post by axcairns on 2007-02-15
> **Jarn said:**
> Apparently I'm not up on the latest lingo. As for your problem, does it affect other apps or only GW? 

Just GW. I have Warcraft III, Frozen Throne, Starcraft and Brood War running happily through wine. 

Allan

---

### Post by Jarn on 2007-02-15
Did you try right-clicking when the mouse dissapears? Normally if the mouse dissapears, you can just right-click a few times and it will come back.

---

### Post by axcairns on 2007-02-16
Progress! 

The CRC error isn't happening anymore. Not sure what changed - I rebooted a couple of times since I last tried and GW downloaded a few more updates.

Bad news is the mouse still disappears. I tried right-clicking as you suggested but no improvement. It disappears when I mouse-over one of the links on the front page.

Cheers,

Allan

---

### Post by axcairns on 2007-02-18
I got the 0.9.31 update today. No change. I'll wait for the updated patch.

Quick question - I looked at the patch file in the winestuff directory - should it have that html wrapper?

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
	<title>untitled</title>
	<style type="text/css">
		#sBar {text-align: center; margin: 0; margin-bottom: 10px; padding: 5px 0px;  width: 528px; background-color: #fff; border: 1px solid #dfdfdf;}
		#sBar li {display: inline; } 
		#sBar li a, #sBar li a:visited {font: bold 11px tahoma,arial; text-decoration: underline; color: #004891; margin: 0px 5px;}
	</style>
</head>

<body>
<table cellspacing="0" cellpadding="0" border="0" align="center">
	<tr>
		<td align="center" valign="top">
			<ul id="sBar">
		         <li><a href="http://www.bravenet.com/webhosting/" target="_new">Web Hosting</a></li>
		         <li><a href="http://www.bravenet.com/webtools/guestbook/" target="_new">Guestbooks</a></li>
		         <li><a href="http://www.bravenet.com/webtools/chat/" target="_new">Live Chat</a></li>
		         <li><a href="http://www.bravenet.com/webtools/forum/" target="_new">Message Boards</a></li>
		         <li><a href="http://www.bravenet.com/webtools/journal/" target="_new">Journals</a></li>
		         <li><a href="http://www.bravenet.com/webtools/elist/" target="_new">Mailing List</a></li>
		     </ul>
		</td>
		<td valign="top"><a href="http://www.bravenet.com/c/o.php?id=35910"><img src="http://assets.bravenet.com/common/images/shell/badges/free_hosting.gif" border="0"></a></td></tr>
	<tr>
		<td colspan="2" valign="top">
			<div align="center" style="z-index: 9000; margin-bottom: 10px;">
				<script language="javascript" type="text/javascript" src="http://mercury.bravenet.com/rover/a?dbfile=SPONSORBAR_DB&serv=hosting-sites"></script><noscript><iframe src="http://mercury.bravenet.com/rover/a?dbfile=SPONSORBAR_DB&js=false&serv=hosting-sites" width="754" height="90" allowTransparency="true" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"><img src="http://mercury.bravenet.com/rover/d?dbfile=SPONSORBAR_DB&serv=hosting-sites" alt="" border="0"></iframe></noscript>
				<div style="clear: both;"></div>
			</div>
		</td>
	</tr>
</table>
<script src="http://jupiter.bravenet.com/rover/f?cid=bravenet&ctype=24"></script>
--- dlls/winex11.drv/mouse.c	2006-12-22 08:17:47.000000000 -0800
+++ dlls/winex11.drv/mouse.c	2006-12-26 23:43:32.000000000 -0800
@@ -412,16 +412,19 @@
         }
         else
         {
-            int     rbits, gbits, bbits, red, green, blue;
+            int     rbits, gbits, bbits,abits, red, green, blue, alpha;
             int     rfg, gfg, bfg, rbg, gbg, bbg;
             int     rscale, gscale, bscale;
             int     x, y, xmax, ymax, bitIndex, byteIndex, xorIndex;
             unsigned char *theMask, *theImage, theChar;
             int     threshold, fgBits, bgBits, bitShifted;
-            BYTE    pXorBits[128];   /* Up to 32x32 icons */
+            BYTE    pXorBits[128], pAndBits[128];   /* Up to 32x32 icons; could use same array but ...  */
+            int failure = 0;
 
             switch (ptr->bBitsPerPixel)
             {
+            case 32:
+                abits = 8;
             case 24:
                 rbits = 8;
                 gbits = 8;
@@ -463,13 +466,16 @@
             ymax = (ptr->nHeight > 32) ? 32 : ptr->nHeight;
 
             memset(pXorBits, 0, 128);
+            memset(pAndBits, 0, 128);
             for (y=0; y<ymax; y++)
             {
                 for (x=0; x<xmax; x++)
                 {
                    	red = green = blue = 0;
+                        alpha = 255;   // This is visible?
                    	switch (ptr->bBitsPerPixel)
                    	{
+                        case 32:
                    	case 24:
                    	    theChar = theImage[byteIndex++];
                    	    blue = theChar;
@@ -477,6 +483,11 @@
                    	    green = theChar;
                    	    theChar = theImage[byteIndex++];
                    	    red = theChar;
+                            if (ptr->bBitsPerPixel == 32)
+                            {
+                                theChar = theImage[byteIndex++];
+                                alpha = theChar;
+                            }
                    	    break;
                    	case 16:
                    	    theChar = theImage[byteIndex++];
@@ -488,8 +499,18 @@
                    	    break;
                    	}
 
-                    if (red+green+blue > threshold)
+                    //bg or fg?
+                    // If there is alpha for fg color then we should calculate avarange
+                    // alpha and use that to create transperancy for cursor (at least my gnome 
+                    // has transperancy with xorg 7)
+                    if (alpha < threshold>>3)
                     {
+                        // Transparent
+                        pAndBits[xorIndex] |= bitShifted;
+                    }
+                    else if (red+green+blue > threshold)
+                    {
+                        // Foreground
                         rfg += red;
                         gfg += green;
                         bfg += blue;
@@ -498,6 +519,7 @@
                     }
                     else
                     {
+                        // Background
                         rbg += red;
                         gbg += green;
                         bbg += blue;
@@ -530,7 +552,16 @@
             }
             else bg.red = bg.green = bg.blue = 0;
             pixmapBits = XCreateBitmapFromData( display, root_window, (char *)pXorBits, xmax, ymax );
-            if (!pixmapBits)
+            if (ptr->bBitsPerPixel == 32)
+            {
+                pixmapMask = XCreateBitmapFromData( display, root_window, (char *)pAndBits, xmax, ymax );
+                if (!pixmapMask)
+                {
+                    XFreePixmap( display, pixmapAll );
+                    failure = 1;
+                }
+            }
+            if (!pixmapBits && failure)
             {
                 XFreePixmap( display, pixmapAll );
                 XFreeGC( display, gc );
@@ -546,7 +577,13 @@
             /* Put the image */
             XCopyArea( display, pixmapBits, pixmapAll, gc,
                        0, 0, xmax, ymax, 0, ptr->nHeight );
+            if (ptr->bBitsPerPixel == 32)
+            {
+                XCopyArea( display, pixmapMask, pixmapAll, gc,
+                        0, 0, xmax, ymax, 0, 0);
+            }
             XFreePixmap( display, pixmapBits );
+            XFreePixmap( display, pixmapMask );
         }
         image->data = NULL;
         XDestroyImage( image );
<br>
<div style="text-align: center">
	<a href="http://www.bravenet.com/webhosting/" style="font: 11px tahoma, sans-serif; color: #004891;">Web Hosting</a> 
	&middot; 
	<a href="http://www.bravenet.com/webtools/journal" style="font: 11px tahoma, sans-serif; color: #004891;">Blog</a>
	&middot; 
	<a href="http://www.bravenet.com/webtools/guestbook/" style="font: 11px tahoma, sans-serif; color: #004891;" target="_blank">Guestbooks</a> 
	&middot; 
	<a href="http://www.bravenet.com/webtools/forum/" style="font: 11px tahoma, sans-serif; color: #004891;" target="_blank">Message Forums</a> 
	&middot; 
	<a href="http://www.bravenet.com/webtools/elist/" style="font: 11px tahoma, sans-serif; color: #004891;" target="_blank">Mailing Lists</a><br>

	<a href="http://allwebcodesign.com/" style="font: 11px tahoma, sans-serif; color: #004891;" targetr="_blank">Allwebco Web Templates</a> 
	&middot;
	<a href="http://www.sbgglobal.com/b1/10136.html" style="font: 11px tahoma, sans-serif; color: #004891;" targetr="_blank">Online Casino</a> 
	&middot;
	<a href="http://www.quotemedia.com/" style="font: 11px tahoma, sans-serif;color: #004891;" target="_blank">Financial Data</a>
	&middot; 
	<a href="http://resources.bravenet.com" style="font: 11px tahoma, sans-serif; color: #004891;" targetr="_blank">Audio, Fonts, Clipart</a><br>

	<a href="http://www.bravenet.com" target="_blank" style="text-decoration: none; color: #004891; font: bold 10px tahoma, sans-serif; display:block; padding-top: 10px;">powered by <img src="http://assets.bravenet.com/bravenet/images/poweredby.gif" border="0" alt="a free webtools company" style="vertical-align: middle;"> bravenet.com</a>
</div><br>

</body>
</html>

```

Cheers,


Allan

---

### Post by fktt on 2007-02-18
umm.. i have guite a bizzarre reguest: could someone tell me how i could chmod my guildwars  folder, there are some spaces in the dir. like: "Program Files/Guild Wars" :S makes it difficult to get there through the terminal..

---

### Post by axcairns on 2007-02-18
> **fktt said:**
> umm.. i have guite a bizzarre reguest: could someone tell me how i could chmod my guildwars  folder, there are some spaces in the dir. like: "Program Files/Guild Wars" :S makes it difficult to get there through the terminal..

Easiest way to reference those folders is to put a \ character before each space.

Allan

---

### Post by fktt on 2007-02-18
thanks axcairns, ill have to check it out, right now :)
EDIT: just gotta love the terminal! :) thanks!

---

### Post by Jarn on 2007-02-18
> **axcairns said:**
> Quick question - I looked at the patch file in the winestuff directory - should it have that html wrapper?

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
	<title>untitled</title>
	<style type="text/css">
		#sBar {text-align: center; margin: 0; margin-bottom: 10px; padding: 5px 0px;  width: 528px; background-color: #fff; border: 1px solid #dfdfdf;}
		#sBar li {display: inline; } 
		#sBar li a, #sBar li a:visited {font: bold 11px tahoma,arial; text-decoration: underline; color: #004891; margin: 0px 5px;}
	</style>
</head>

<body>
<table cellspacing="0" cellpadding="0" border="0" align="center">
	<tr>
		<td align="center" valign="top">
			<ul id="sBar">
		         <li><a href="http://www.bravenet.com/webhosting/" target="_new">Web Hosting</a></li>
		         <li><a href="http://www.bravenet.com/webtools/guestbook/" target="_new">Guestbooks</a></li>
		         <li><a href="http://www.bravenet.com/webtools/chat/" target="_new">Live Chat</a></li>
		         <li><a href="http://www.bravenet.com/webtools/forum/" target="_new">Message Boards</a></li>
		         <li><a href="http://www.bravenet.com/webtools/journal/" target="_new">Journals</a></li>
		         <li><a href="http://www.bravenet.com/webtools/elist/" target="_new">Mailing List</a></li>
		     </ul>
		</td>
		<td valign="top"><a href="http://www.bravenet.com/c/o.php?id=35910"><img src="http://assets.bravenet.com/common/images/shell/badges/free_hosting.gif" border="0"></a></td></tr>
	<tr>
		<td colspan="2" valign="top">
			<div align="center" style="z-index: 9000; margin-bottom: 10px;">
				<script language="javascript" type="text/javascript" src="http://mercury.bravenet.com/rover/a?dbfile=SPONSORBAR_DB&serv=hosting-sites"></script><noscript><iframe src="http://mercury.bravenet.com/rover/a?dbfile=SPONSORBAR_DB&js=false&serv=hosting-sites" width="754" height="90" allowTransparency="true" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"><img src="http://mercury.bravenet.com/rover/d?dbfile=SPONSORBAR_DB&serv=hosting-sites" alt="" border="0"></iframe></noscript>
				<div style="clear: both;"></div>
			</div>
		</td>
	</tr>
</table>
<script src="http://jupiter.bravenet.com/rover/f?cid=bravenet&ctype=24"></script>
--- dlls/winex11.drv/mouse.c	2006-12-22 08:17:47.000000000 -0800
+++ dlls/winex11.drv/mouse.c	2006-12-26 23:43:32.000000000 -0800
@@ -412,16 +412,19 @@
         }
         else
         {
-            int     rbits, gbits, bbits, red, green, blue;
+            int     rbits, gbits, bbits,abits, red, green, blue, alpha;
             int     rfg, gfg, bfg, rbg, gbg, bbg;
             int     rscale, gscale, bscale;
             int     x, y, xmax, ymax, bitIndex, byteIndex, xorIndex;
             unsigned char *theMask, *theImage, theChar;
             int     threshold, fgBits, bgBits, bitShifted;
-            BYTE    pXorBits[128];   /* Up to 32x32 icons */
+            BYTE    pXorBits[128], pAndBits[128];   /* Up to 32x32 icons; could use same array but ...  */
+            int failure = 0;
 
             switch (ptr->bBitsPerPixel)
             {
+            case 32:
+                abits = 8;
             case 24:
                 rbits = 8;
                 gbits = 8;
@@ -463,13 +466,16 @@
             ymax = (ptr->nHeight > 32) ? 32 : ptr->nHeight;
 
             memset(pXorBits, 0, 128);
+            memset(pAndBits, 0, 128);
             for (y=0; y<ymax; y++)
             {
                 for (x=0; x<xmax; x++)
                 {
                    	red = green = blue = 0;
+                        alpha = 255;   // This is visible?
                    	switch (ptr->bBitsPerPixel)
                    	{
+                        case 32:
                    	case 24:
                    	    theChar = theImage[byteIndex++];
                    	    blue = theChar;
@@ -477,6 +483,11 @@
                    	    green = theChar;
                    	    theChar = theImage[byteIndex++];
                    	    red = theChar;
+                            if (ptr->bBitsPerPixel == 32)
+                            {
+                                theChar = theImage[byteIndex++];
+                                alpha = theChar;
+                            }
                    	    break;
                    	case 16:
                    	    theChar = theImage[byteIndex++];
@@ -488,8 +499,18 @@
                    	    break;
                    	}
 
-                    if (red+green+blue > threshold)
+                    //bg or fg?
+                    // If there is alpha for fg color then we should calculate avarange
+                    // alpha and use that to create transperancy for cursor (at least my gnome 
+                    // has transperancy with xorg 7)
+                    if (alpha < threshold>>3)
                     {
+                        // Transparent
+                        pAndBits[xorIndex] |= bitShifted;
+                    }
+                    else if (red+green+blue > threshold)
+                    {
+                        // Foreground
                         rfg += red;
                         gfg += green;
                         bfg += blue;
@@ -498,6 +519,7 @@
                     }
                     else
                     {
+                        // Background
                         rbg += red;
                         gbg += green;
                         bbg += blue;
@@ -530,7 +552,16 @@
             }
             else bg.red = bg.green = bg.blue = 0;
             pixmapBits = XCreateBitmapFromData( display, root_window, (char *)pXorBits, xmax, ymax );
-            if (!pixmapBits)
+            if (ptr->bBitsPerPixel == 32)
+            {
+                pixmapMask = XCreateBitmapFromData( display, root_window, (char *)pAndBits, xmax, ymax );
+                if (!pixmapMask)
+                {
+                    XFreePixmap( display, pixmapAll );
+                    failure = 1;
+                }
+            }
+            if (!pixmapBits && failure)
             {
                 XFreePixmap( display, pixmapAll );
                 XFreeGC( display, gc );
@@ -546,7 +577,13 @@
             /* Put the image */
             XCopyArea( display, pixmapBits, pixmapAll, gc,
                        0, 0, xmax, ymax, 0, ptr->nHeight );
+            if (ptr->bBitsPerPixel == 32)
+            {
+                XCopyArea( display, pixmapMask, pixmapAll, gc,
+                        0, 0, xmax, ymax, 0, 0);
+            }
             XFreePixmap( display, pixmapBits );
+            XFreePixmap( display, pixmapMask );
         }
         image->data = NULL;
         XDestroyImage( image );
<br>
<div style="text-align: center">
	<a href="http://www.bravenet.com/webhosting/" style="font: 11px tahoma, sans-serif; color: #004891;">Web Hosting</a> 
	&middot; 
	<a href="http://www.bravenet.com/webtools/journal" style="font: 11px tahoma, sans-serif; color: #004891;">Blog</a>
	&middot; 
	<a href="http://www.bravenet.com/webtools/guestbook/" style="font: 11px tahoma, sans-serif; color: #004891;" target="_blank">Guestbooks</a> 
	&middot; 
	<a href="http://www.bravenet.com/webtools/forum/" style="font: 11px tahoma, sans-serif; color: #004891;" target="_blank">Message Forums</a> 
	&middot; 
	<a href="http://www.bravenet.com/webtools/elist/" style="font: 11px tahoma, sans-serif; color: #004891;" target="_blank">Mailing Lists</a><br>

	<a href="http://allwebcodesign.com/" style="font: 11px tahoma, sans-serif; color: #004891;" targetr="_blank">Allwebco Web Templates</a> 
	&middot;
	<a href="http://www.sbgglobal.com/b1/10136.html" style="font: 11px tahoma, sans-serif; color: #004891;" targetr="_blank">Online Casino</a> 
	&middot;
	<a href="http://www.quotemedia.com/" style="font: 11px tahoma, sans-serif;color: #004891;" target="_blank">Financial Data</a>
	&middot; 
	<a href="http://resources.bravenet.com" style="font: 11px tahoma, sans-serif; color: #004891;" targetr="_blank">Audio, Fonts, Clipart</a><br>

	<a href="http://www.bravenet.com" target="_blank" style="text-decoration: none; color: #004891; font: bold 10px tahoma, sans-serif; display:block; padding-top: 10px;">powered by <img src="http://assets.bravenet.com/bravenet/images/poweredby.gif" border="0" alt="a free webtools company" style="vertical-align: middle;"> bravenet.com</a>
</div><br>

</body>
</html>

```It has never affected the patch for me. It still works. I think patch just ignores it, though I keep meaning to host it somewhere else that hopefully won't do that. I'll host it at my googlepage and I'll put it in when I update the scripts for 0.9.31. That won't be for a few days though, since I have a lot I need to do this weekend. Probably Tuesday.

---

### Post by falsenames on 2007-02-20
Upgrading is a pain...  I had everything working well on a patched version 0.9.28 until Guild Wars had some update a few weeks ago, so I took a break.  Now I've upgraded to 0.9.31, and I'm having worse concurrent light issues than before.  Now it's happening in fields and towns instead of just in caverns.  On a brighter note, the textures and colouring is FAR suprior with just three minor revisions.  I was quite impressed, since this update got rid of the need for the mouse patch for me, and got rid of the bug where sometimes various characters would be shaded black.  I eagerly await your patch, as I have no clue how to muck about with this graphics stuff.

---

### Post by der_joachim on 2007-02-20
Hmmm... GW in 0.9.31 just does not start for me. No worries though. I still had a .deb which I built from 0.9.30 and I am happily playing again. 

Elsewhere in this subforum there is a thread about 0.9.31 and it seems to have quite a few regressions. Perhaps we will have more luck with 0.9.32.

---

### Post by falsenames on 2007-02-20
Well, given the recent revision dates, we can probably expect 0.9.32 within a few weeks.  The Wine dev team seems to not be sleeping much as of late, or they all got vacations from work at the same time.  I've been enjoying the monthly releases, espeically since it seems most of the work is going into the 3D development.

Bit of an odd question though.  How do you force Wine to use a specific directX interface?  Someone in an earlier post said that they were using a directX9 path, and I'd like to see if I could use the same.

---

### Post by Azakus on 2007-02-21
To force a direct x path, just add "-dxN" (N being the direct x version you want) to the end of the program's launcher.
For example, Guild Wars with Direct X 8 would look like this:
```
 wine "C:\\ThePathToGuildWars\\Gw.exe -dx8"
```

---

### Post by Jarn on 2007-02-21
> **falsenames said:**
> I'm having worse concurrent light issues than beforeThere's a patch for the concurrent lights glitch in the first post in the Manual section. It's near the end. I didn't include it in the script because not everyone needs it.

---

### Post by erk on 2007-02-22
Can someone email the Ubuntu/Wine package maintainer the 32 bit mouse cursor patch to include in future releases?  I don't really know much about it so it's better if someone who does know emails him. 

BTW The OpenSUSE Wine 0.9.30 package already has a patch installed that uses the X11 cursor in GW when I tried it a couple of weeks ago. It ran like a snail on my Thinkpad R52, completely useless, but the cursor worked :)

---

### Post by Jarn on 2007-02-22
> **erk said:**
> BTW The OpenSUSE Wine 0.9.30 package already has a patch installed that uses the X11 cursor in GW when I tried it a couple of weeks agoOo, interesting... would people like that more than the current patch that (badly) reproduces GW's mouse?

---

### Post by falsenames on 2007-02-22
Well this is fun...  I apparently forgot to patch the mouse in my 0.9.30 build, just the concurrent lights issue.  A new build for GW came out today, and when I loaded it up again, the mouse disappeared, so I went back and double checked everything, patched mouse.c, and now gw crashes as soon as it is finished connecting to ArenaNet.  Here's the error message:
```
fixme:d3d_surface:IWineD3DSurfaceImpl_UnlockRect unsupported unlocking to Rendering surface surf@0x21c350 usage(WINED3DUSAGE_RENDERTARGET)
X Error of failed request:  BadPixmap (invalid Pixmap parameter)
  Major opcode of failed request:  54 (X_FreePixmap)
  Resource id in failed request:  0x7e764d60
  Serial number of failed request:  150
  Current serial number in output stream:  174
```

I also thought I posted this next part before, but the message somehow got lost.  The 0.9.31 device.c is greatly different from the previous releases.  The patch no longer works for the concurrent light issue.

---

### Post by axcairns on 2007-02-23
> **Jarn said:**
> Oo, interesting... would people like that more than the current patch that (badly) reproduces GW's mouse?

Yes please. The patch never worked for me.

Allan

---

### Post by FyreBrand on 2007-02-24
The person who makes the debs for Ubuntu made a thread here (in the games forum) asking for feedback and talking a little bit about releases.  You should search for that thread, post there and also PM him.  He sounds like a really nice guy and very interested in making wine a good thing in Ubuntu.

Something to consider is that adding the patches to the deb might break other games or applications.  Just because it works for GW doesn't mean it's going to work for everything, though it might.

---

### Post by Flyser on 2007-02-24
Hi I ported the the 32-Bit Cursor and the "Too many current lights" Patch to wine 0.9.31
The Cursor works perfectly and the lights-patch is untested (still compiling).
Except some lock-ups because of the lights-problem Guild Wars is running perfectly! Even the perfomance is better (very playable for me now)

EDIT: After applying the lights-patch everthing works nearly perfect now! (still there are some very rare and minor graphic bugs, nothing that affects gameplay)
In the Wine AppDB I would rate it gold now!


My patches:

---

### Post by axcairns on 2007-02-24
> **FyreBrand said:**
> The person who makes the debs for Ubuntu made a thread here (in the games forum) asking for feedback and talking a little bit about releases.  You should search for that thread, post there and also PM him.  He sounds like a really nice guy and very interested in making wine a good thing in Ubuntu.

Something to consider is that adding the patches to the deb might break other games or applications.  Just because it works for GW doesn't mean it's going to work for everything, though it might.

Care to point us to the thread? I just trawled through the games forum with no luck.

Allan

---

### Post by axcairns on 2007-02-24
I thought I'd try flyser's mouse patch and noticed a problem when running ./configure - my system (recent edgy build) was missing a couple of key packages (flex and bison). The same error probably also occurred when running jarn's updatewine script but the subsequent commands in the script would quickly have pushed the error off screen. 

Jarn, do those packages appear in your howto?

Cheers,


Allan

---

### Post by axcairns on 2007-02-24
> **Flyser said:**
> Hi I ported the the 32-Bit Cursor and the "Too many current lights" Patch to wine 0.9.31
The Cursor works perfectly and the lights-patch is untested (still compiling).
Except some lock-ups because of the lights-problem Guild Wars is running perfectly! Even the perfomance is better (very playable for me now)

EDIT: After applying the lights-patch everthing works nearly perfect now! (still there are some very rare and minor graphic bugs, nothing that affects gameplay)
In the Wine AppDB I would rate it gold now!


My patches:

Just tried your mouse patch but no luck. Mouse disappears first time I mouseover a link.

Allan

---

### Post by Flyser on 2007-02-24
huh? really? well its exactly the same as the 0.9.28 patch on the first page, I just corrected the linenumbers.
Are you sure the source code is patched correctly and without errors?
You  may also try clicking right three times, while moving the mouse. I have to do this sometimes

---

### Post by FyreBrand on 2007-02-24
> **axcairns said:**
> Care to point us to the thread? I just trawled through the games forum with no luck.

AllanHere is the link to that thread: [**Wine 0.9.31 Thread by YokoZar**]("http://www.ubuntuforums.org/showthread.php?t=364256&highlight=wine").

> **axcairns said:**
> I thought I'd try flyser's mouse patch and noticed a problem when running ./configure - my system (recent edgy build) was missing a couple of key packages (flex and bison). The same error probably also occurred when running jarn's updatewine script but the subsequent commands in the script would quickly have pushed the error off screen. 

Jarn, do those packages appear in your howto?

Cheers,


AllanRead the instructions and the initial script closely.  You need certain packages installed before you can compile wine and Bison is one of them.  It should compile just fine for you, just check that you've met all the prerequisites first.

---

### Post by falsenames on 2007-02-25
For those who are experiencing problems with the mouse patch not working, it's not always needed.  For some odd reason, I only have issues with the mouse if I install any mouse patches, but most people do need them.  I also need a concurrent lights patch all the time, and most people don't.  Each system has it's own unique quirky behaviour, and you just have to find out what works for you.  Also, as Flyser said, sometimes you have to cause several mouse events to happen before the cursor appears on the screen.

** EDIT **

I forgot, mouse issues also are a bigger problem if you have set the game at full screen mode.  It's the only time I ever have it act up on my computer.   Running in window mode seems to work much better.  This is the windowing set within GW's options, not within Wine's

---

### Post by Flyser on 2007-02-25
Yup I think this depends in your X-Configuration (color-depth and various driver switches) and on the graphiccard+drivers. (I am using a ATI Mobility Radeon 9700 + fglrx 8.34.8; tried opensource-radeon-driver but doesnt work)

---

### Post by falsenames on 2007-02-25
I'm not sure about ATI's open source driver, but nVidia's is starting to become almost useful.  I still recommend using the binaries at nVidia's site, since they are making a huge effort at becoming compatable with Linux's kernel, if not it's open source ideals.  The companies that make these cards obviously have an advantage for being able to make the driver if they choose to.  I'm just glad they have finally started to, even if I can't figure out any reason they would not make these drivers open source.  I'm sure a very large complicated legal department decided it was releasing company secrets.

---

### Post by Jarn on 2007-02-26
> **axcairns said:**
> Jarn, do those packages appear in your howto?Yes. What the script from the Wine website doesn't install, apt-get build-dep wine will - between the two you should have everything you need and some you don't.

---

### Post by FredDie3785 on 2007-02-27
Ok now I've got 3d acceleration with my ATi Radeon 9200 and GW seems to work properly.
Right now I'm downloading game files and I've got a question how to install GW from CDs [I have all campaigns].
I tried to install "Prophecy" but I had problems with 2nd CD. The installation doesn't want to continue....

EDIT: Holy mother of god it works great. Thx Jarn and everyone, but I've got some minor problems with textures but nvm

Here I've got another question. Is there any possibility to apply those two patches if I'm installing WINE from repositories. 
As someone wrote it earlier you should send email to WineHQ with your work, Jarn...

---

### Post by Azakus on 2007-02-27
No, you have to build wine yourself if you want the patches as they need to be applied before being compiled.

---

### Post by Jarn on 2007-02-27
> **FredDie3785 said:**
> As someone wrote it earlier you should send email to WineHQ with your work, Jarn...I didn't do anything. O.o. All I did was put all the information I could find in one place. And I wrote the two 32-bit scripts. But the patches and things already existed, they were just hard to find.

---

### Post by Flyser on 2007-02-28
It would be useful to update the howto on the first page, since there are a lot of performance boosts in 0.9.31

---

### Post by Vexed Arcanist on 2007-02-28
> **FredDie3785 said:**
> 
Right now I'm downloading game files and I've got a question how to install GW from CDs [I have all campaigns].
I tried to install "Prophecy" but I had problems with 2nd CD. The installation doesn't want to continue....

Off topic from thread but on topic for the above quote, if you have all 3 campaigns you should only install Nightfall (or the latest in case where you have 2).  Everything up to that campaign's release will be on that set of discs.

For those using this method to install (CDs vs Client download) you will knock out about 50000 of 80000 files this way.

---

### Post by Azakus on 2007-02-28
BIG NEWS!!!!
I found a script that makes the 32-bit libsicuuc.a file needed for WINE on AMD64, so now the build script is much smaller! All that in the gzip file now is the modified Makefile for gdi32 and the new 64-build script!

---

### Post by Jarn on 2007-02-28
> **Flyser said:**
> It would be useful to update the howto on the first page, since there are a lot of performance boosts in 0.9.31
I know, I keep meaning to, but I've been really busy. I'll try to get to it this weekend, but I have a Science Olympiad state competition on Saturday, so I'm not sure if I'll have time.

---

### Post by Fasga on 2007-02-28
Still a total nooby at all this, and I probably did this wrong, but, here's a 0.9.31 deb with the mouse patch: [http://jtorials.com/debs/wine_0.9.31-1_i386.deb](http://jtorials.com/debs/wine_0.9.31-1_i386.deb)

---

### Post by FredDie3785 on 2007-03-01
Sorry for another offtop...
And if I want to remove completely old ver of W.I.N.E installed from sources??

---

### Post by axcairns on 2007-03-01
> **FredDie3785 said:**
> Sorry for another offtop...
And if I want to remove completely old ver of W.I.N.E installed from sources??

While in the directory where you did the build -

```
sudo make uninstall
```

Allan

---

### Post by FredDie3785 on 2007-03-01
I've read that there is other way to apply the patch. Just install the newest version of W.I.N.E.
Then move to it's category:

> cd ../wine 

Then just apply patch with:
> cat <patch> |patch -s -p0 --dry-run 

And if it's not working do this:

> cat <patch> |patch -s -p0 

Actually I haven't tested it yet, but I will when the GW will download!

EDIT: Well it's not working...:( Please someone do the sources...

---

### Post by Flyser on 2007-03-01
Whats new about this??

---

### Post by Fasga on 2007-03-01
I often get this when the game finishes loading a new area.  It keeps spitting it out and it crashes the entire game:
```
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got **(differs)** while expecting **(differs)**)

```

---

### Post by falsenames on 2007-03-02
Check up in the scroll to see if you have the concurrent lights issue.  When I ran 0.9.31 before the patches Jarl posted, I got that spammed a LOT right after the warning for concurrent lights.  A nice quick way to see if that's the case is by running gw with this command:
```
wine Gw.exe 2> grep concurrent
```
If you see a warning pop up after gw freezes, then you need to patch wine with the devices.c.0.9.31.lights.patch.txt file.

---

### Post by Azakus on 2007-03-02
There were a few regressions in the Direct3D portion of WINE for the 0.9.31 release. That might explain your errors. Should be fixed by 0.9.32

---

### Post by Jarn on 2007-03-02
Looking at more about 0.9.31, should I even update the scripts etc. for 0.9.31? The regressions in Direct3D could be bothersome and we know 0.9.30 works.

---

### Post by FyreBrand on 2007-03-02
I would say just to wait until the next version and see how that one goes especially if you're short on time.  With the rate they've been pumping out releases I would say it won't be long anyways.

---

### Post by Jarn on 2007-03-02
Will do.

---

### Post by falsenames on 2007-03-02
Personally, I see much better quality in the graphics with 0.9.31 than I did even with 0.9.30.  There isn't a problem with my character being shadowed in the inventory screen anymore.  I rarely have issues with armour not appearing on people anymore.  The display for dyes actually shows the new colour now.  Regression is not always a bad thing when it's going back and fixing things that were wrong.

Also, the bad CRC error message is the same exact one that shows up in 0.9.30 when you have the concurrent lights issue, so the regression doesn't matter there.  Especially Jarl posted the working patch for devices.c for 0.9.31

---

### Post by Flyser on 2007-03-02
Does any1 know WHY the Combat-Sound isn't working? maybe it is possible to write a patch for this issue :)

---

### Post by Azakus on 2007-03-02
So far, the regressions have only been found in two games, but it's still not really clear.
More details: [http://winehq.com/?issue=323#Direct3D%20Breakage%20in%200.9.31](http://winehq.com/?issue=323#Direct3D%20Breakage%20in%200.9.31)

---

### Post by Azakus on 2007-03-02
Wine 0.9.32 Just released, with the Direct3D problems apparently fixed.
Updating scripts.
{EDIT}
Wine no longer needs a modified makefile for GDI32 in AMD64, so now it is all in one shell script!
{/EDIT}

---

### Post by Jarn on 2007-03-02
Well, I'll probably update this today! Science Olympiad was canceled due to snow so I find myself with several hours of free time I was not planning on. :D

EDIT: Okay, I'm about to change the script, but before I do: should I put the concurrent lights patch in it? Since a lot of people have that problem and it shouldn't negatively effects those who don't, I figure I might as well. Sound good? Also, I'm going to edit the script so it uses checkinstall to create a deb - that way if a later release of wine breaks your current, you can just uninstall the deb and install your old version.

---

### Post by Fasga on 2007-03-02
Would it be too hard to make two?  If it would, add it.  Mostly because I think that might be my problem.  :p

---

### Post by Jarn on 2007-03-02
It wouldn't be too hard to make two. Only, I'd rather have just one script for the sake of simplicity. I think I'll just throw in the lights patch, because I don't think it will negatively affect those who DON'T have that problem and it will benefit those who do. I updated the script and I'm running it now. If it works, I'll post it when it's done.

EDIT: Hrm. It worked, but I think my FPS went down. I'm going to install an older version to see if it did or if it's just my imagination.
EDIT2: Yeah, it did. And not just in 0.9.32, either. It did in 0.9.31. At 0.9.30, I get about 30 FPS while PvPing. With 0.9.31 I get about 20. Now, with 0.9.32, I get about 10. I have to lower my settings to get decent FPS.

---

### Post by Jarn on 2007-03-02
Okay, I updated it for 0.9.32 now. And I decided I need more RAM. :P

---

### Post by FyreBrand on 2007-03-03
> **Jarn said:**
> Okay, I updated it for 0.9.32 now. And I decided I need more RAM. :P
Hahaha.  RAM makes it all good. :)  Thanks for the update Jarn.  You're awesome.

---

### Post by FredDie3785 on 2007-03-03
If I have installed Wine 0.9.30 so I must run updatewine.sh. to update it to 0.9.32?? Am I correct??

---

### Post by Flyser on 2007-03-03
Today I played a bit with the Direct3D-Registry-Keys the results are not that bad:
DirectDrawRenderer:
gdi(default)
opengl -> Better perfomance and no errors

RenderTargetLockMode: -> Changing this does not change anything in perfomance, quality or anything for me
auto (default)
disabled
readdraw
readtex
texdraw
textex

Nonpower2Mode: -> Didn't try, I dont think this is useful for Guild Wars
y
n (default)

OffscreenRenderingMode:
backbuffer (default) -> best
pbuffer -> Works but drops performance
fbo -> Unplayable slow and graphicbugs

UseGLSL
disabled (default)
enabled -> Seems to add support for Shader (Either Pixel or Vertex, but not both); it seems safe to enable this even if you dont use shader

VideoMemorySize:
64 (default)
Must be higher or equal than "8" (this means 8MByte) otherwise Guild Wars wont start
If this value is low (e.g. 8 ) there are LOTS of texturebugs (trees which looks like giant footprints; difficult to explain ;) )
If its high (e.g. 512) you will barely see any texturebugs (still there are some)

--------

I recommend setting:
VideoMemorySize to "512"
UseGLSL to "enabled"
DirectDrawRenderer to "opengl"

A overview over this switches (what they do and where to find them) can be found at: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

gl&hf

---

### Post by Azakus on 2007-03-03
I figured out how to get ALSA support for AMD64. You have to install lib32asound2-dev and libasound2-dev before compiling.
I'll add it into the script later.

---

### Post by Jarn on 2007-03-03
> **Flyser said:**
> I recommend setting:
VideoMemorySize to "512"
UseGLSL to "enabled"
DirectDrawRenderer to "opengl"Woah! Guild Wars is a lot more responsive now! Even opening menus etc. is a lot quicker. Of course, it could be my imagination, but I don't think it is.

---

### Post by Flyser on 2007-03-03
No reason :) :) :) 

Is the 32-bit-cursor- and the "too many currently active light"-patch still needed in wine-0.9.32? What about the performance-fixes, which were mentioned in winehq-changelog is it much faster?

Is there need in a new version of those patches? I would post them when wine-0.9.32 hit the gentoo-portage!

---

### Post by Jarn on 2007-03-03
> **Flyser said:**
> Is the 32-bit-cursor- and the "too many currently active light"-patch still needed in wine-0.9.32?I don't know. I put them in without checking.
EDIT: Looking over the changelog, the files that the patches modify (device.c and mouse.c) weren't edited, so they're most likely still necessary.

> **Flyser said:**
> What about the performance-fixes, which were mentioned in winehq-changelog is it much faster?I dunno, I think it's about the same. Your registry tweaks, however, made a noticeable difference.

> **Flyser said:**
> Is there need in a new version of those patches?Nope, the ones for 0.9.31 still work.

---

### Post by Lincolns_back on 2007-03-03
hey im not sure how to psot inmy own forum or make on so im postign here my wine was fien  one day i went into winecfg then clickedadd program and it came up with this 

err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\lincoln\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder 

so i cant add programs with it adn cant install stuff it jsut freezes on stuff plz help i tryed reinstalloing it but didnt work

---

### Post by Flyser on 2007-03-03
just do a
```
rm -r ~/.wine
```
as your local user
NOTE: this deletes all programs you installed in wine previously and removes all files that might  be in your virtual-windows-directory

EDIT: Well do it as Jarn said (next post) though this is a Guild Wars + wine and NOT a everything-to-do-with-wine thread

---

### Post by Jarn on 2007-03-03
> **Lincolns_back said:**
> hey im not sure how to psot inmy own forum or make on so im postign here my wine was fien  one day i went into winecfg then clickedadd program and it came up with this 

err:shell:SHGetFolderPathW Failed to create directory 'L"z:\\home\\lincoln\\Desktop"'.
err:commdlg:IShellBrowserImpl_BrowseObject could not browse to folder 

so i cant add programs with it adn cant install stuff it jsut freezes on stuff plz help i tryed reinstalloing it but didnt work
Go into the forum and click the button that says "Make New Post". It's right over "Threads in Forum : Gaming & Leisure"

---

### Post by Ryan H on 2007-03-04
I tried to compile it and got this error:
```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I can't seem to get it to work, I saw someone else also had this error, but I didn't see a solution for it. Any help would be greatly appreciated! :) 

Thank you.

-Ryan H

---

### Post by Jarn on 2007-03-04
I've never seen that before, but maybe config.log would give more information.

EDIT: Flyser, I just found something out. Turning on the UseGLSL registry entry causes CS:S to behave the same as it did in 0.9.31, namely, not work. It just sits at a black screen. So if anyone enables that and CS:S doesn't work... now you know why.

---

### Post by Flyser on 2007-03-04
Well you can use different wine-directories, I have CS1.6, Guild Wars and XFire in their own dir and start Guild Wars like this:

WINEPREFIX="/home/yourusername/.wine.gw" WINEDEBUG=trace-all,fixme-all,err+all wine C:\\Program\ Files\\GW\\Gw.exe -perf -dx8 -noshaders -noshader &>/var/tmp/guildwars.log &

---

### Post by Azakus on 2007-03-04
> **Jarn said:**
> I've never seen that before, but maybe config.log would give more information.

EDIT: Flyser, I just found something out. Turning on the UseGLSL registry entry causes CS:S to behave the same as it did in 0.9.31, namely, not work. It just sits at a black screen. So if anyone enables that and CS:S doesn't work... now you know why.

Actually, I got it to work with GLSL on, but I had to modify my ALSA configurement to provide direct access to the card, other wise I'd have a screen all perfect, but when I tried to click something, it would freeze upon one of the options going "click".

---

### Post by Pugwash on 2007-03-04
Ok, when I start guildwars.exe (I've already installed it through wine) I see no mouse cursor and the thing runs really slowly. I'm on the latest wine. Could someone point me towards the right direction here.

Cheers

---

### Post by Flyser on 2007-03-04
[http://ubuntuforums.org/showthread.php?t=283122](http://ubuntuforums.org/showthread.php?t=283122)
;)

---

### Post by Ryan H on 2007-03-04
My config.log file shows this
```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by Wine configure 0.9.32, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = ryan-ubuntu
uname -m = x86_64
uname -r = 2.6.15-28-amd64-generic
uname -s = Linux
uname -v = #1 SMP PREEMPT Thu Feb 1 15:53:41 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = x86_64
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1895: checking build system type
configure:1913: result: x86_64-unknown-linux-gnu
configure:1935: checking host system type
configure:1950: result: x86_64-unknown-linux-gnu
configure:2015: checking whether make sets $(MAKE)
configure:2036: result: yes
configure:2093: checking for gcc
configure:2120: result: gcc -m32
configure:2358: checking for C compiler version
configure:2365: gcc -m32 --version >&5
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2368: $? = 0
configure:2375: gcc -m32 -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:2378: $? = 0
configure:2385: gcc -m32 -V >&5
gcc: '-V' must come at the start of the command line
configure:2388: $? = 1
configure:2411: checking for C compiler default output file name
configure:2438: gcc -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:2441: $? = 1
configure:2479: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Wine"
| #define PACKAGE_TARNAME "wine"
| #define PACKAGE_VERSION "0.9.32"
| #define PACKAGE_STRING "Wine 0.9.32"
| #define PACKAGE_BUGREPORT "wine-devel@winehq.org"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2486: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=x86_64-unknown-linux-gnu
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_XMKMF_set=
ac_cv_env_XMKMF_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=x86_64-unknown-linux-gnu
ac_cv_prog_ac_ct_CC='gcc -m32'
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ALSALIBS=''
AR=''
ARTSCCONFIG=''
ARTSINCL=''
ARTSLIBS=''
AS='as --32'
AUDIOIOLIBS=''
BISON=''
BUILTINFLAG=''
CARBONLIB=''
CC='gcc -m32'
CFLAGS=''
COREAUDIO=''
COREFOUNDATIONLIB=''
CPP=''
CPPBIN=''
CPPFLAGS=''
CROSSCC=''
CROSSTEST=''
CROSSWINDRES=''
CRTLIBS=''
CXX=''
CXXFLAGS=''
DEFS=''
DEPENDENCIES=''
DISKARBITRATIONLIB=''
DLLEXT=''
DLLFLAGS=''
DLLTOOL=''
DLLWRAP=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
ESDCONFIG=''
ESDINCL=''
ESDLIBS=''
EXEEXT=''
EXTRACFLAGS=''
EXTRA_BINARIES=''
FONTFORGE=''
FONTSSUBDIRS=''
FREETYPEINCL=''
FREETYPELIBS=''
GLU32FILES=''
GPHOTO2INCL=''
GPHOTO2LIBS=''
GREP=''
HALINCL=''
ICULIBS=''
IMPLIBEXT=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
IOKITLIB=''
LCMSLIBS=''
LD='ld -m elf_i386'
LDAPLIBS=''
LDCONFIG=''
LDD=''
LDDLLFLAGS=''
LDEXECFLAGS=''
LDFLAGS=''
LDPATH=''
LDSHARED=''
LEX=''
LEXLIB=''
LEX_OUTPUT_ROOT=''
LIBDL=''
LIBEXT=''
LIBOBJS=''
LIBPOLL=''
LIBPTHREAD=''
LIBS=''
LIBWINE_LDFLAGS=''
LINT=''
LINTFLAGS=''
LN=''
LN_S=''
LTLIBOBJS=''
MAIN_BINARY=''
MINGWAR=''
NASLIBS=''
OBJEXT=''
OPENGLFILES=''
OPENGL_LIBS=''
PACKAGE_BUGREPORT='wine-devel@winehq.org'
PACKAGE_NAME='Wine'
PACKAGE_STRING='Wine 0.9.32'
PACKAGE_TARNAME='wine'
PACKAGE_VERSION='0.9.32'
PATH_SEPARATOR=':'
PKG_CONFIG=''
PRELINK=''
QUARTZFILES=''
RANLIB=''
RESOLVLIBS=''
SANEINCL=''
SANELIBS=''
SET_MAKE=''
SHELL='/bin/sh'
SOCKETLIBS=''
STRIP=''
TOOLSDIR=''
WIN16_FILES='$(WIN16_FILES)'
WIN16_INSTALL='$(WIN16_INSTALL)'
WINDRES=''
XFILES=''
XLEX=''
XLIB=''
XMKMF=''
XML2INCL=''
XML2LIBS=''
XSLTINCL=''
XSLTLIBS=''
X_CFLAGS=''
X_EXTRA_LIBS=''
X_LIBS=''
X_PRE_LIBS=''
ac_ct_AS=''
ac_ct_CC='gcc -m32'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build='x86_64-unknown-linux-gnu'
build_alias=''
build_cpu='x86_64'
build_os='linux-gnu'
build_vendor='unknown'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
ft_devel2=''
ft_devel=''
gphoto2_devel=''
gphoto2port_devel=''
host='x86_64-unknown-linux-gnu'
host_alias=''
host_cpu='i386'
host_os='linux-gnu'
host_vendor='unknown'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sane_devel=''
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ------------------- ##
## File substitutions. ##
## ------------------- ##

MAKE_DLL_RULES=''
MAKE_IMPLIB_RULES=''
MAKE_PROG_RULES=''
MAKE_RULES=''
MAKE_TEST_RULES=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "Wine"
#define PACKAGE_TARNAME "wine"
#define PACKAGE_VERSION "0.9.32"
#define PACKAGE_STRING "Wine 0.9.32"
#define PACKAGE_BUGREPORT "wine-devel@winehq.org"

configure: exit 77

```

That's a lot of stuff, I don't know if it's any help.

-Ryan H

---

### Post by Jarn on 2007-03-04
> **Ryan H said:**
> ```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

```
I think that is the part that is giving you problems. I don't know what it means, though. Try asking in the #winehq irc channel on irc.freenode.net.

---

### Post by falsenames on 2007-03-05
I had this problem when I tried running a 64 bit version of Gentoo earlier.  You need to run ldconfig as superuser to fix up a few incompatible libraries.  After installing a 32 bit version of MEPIS though, I haven't had to deal with it, so I forget how.  Whatever version of wine you're using is for the wrong chipset, or can't find the gcc libraries for the correct chipset.

Here's the problem from your config.log if you don't have the 32bit versions of those libraries.
/bin/arch              = x86_64
...
configure:2120: result: gcc -m32

---

### Post by PsychoStorm on 2007-03-05
The sound problem

Does the combat sound in Guild Wars work for someone here?
I found something that might be interesting:
Actually the sound works but it's very very quiet.
If you have working music and working interface sound, try this:
Use headphones and turn the volume as high as possible and make sure that this is the only source sound can come from, so turn off any music because music would be louder anyway.
Now you should hear the combat sound.
Even then it's still quiet but it works.

P.S.: I'm sorry if this has been posted before but I didn't read the whole thread, just the first and the last two sites. :shame:

---

### Post by Flyser on 2007-03-05
mh if you are treu and the sound is just quite, it would be fairly easy to write a patch, wouldn't it?

---

### Post by aswells on 2007-03-05
Even after running the command wineprefixcreate in the same folder as my copiled wine source code my regedit tool does now show any of the registry keys that are suggested to be changed. I used the updatewine.sh script.

---

### Post by Jarn on 2007-03-05
> **aswells said:**
> Even after running the command wineprefixcreate in the same folder as my copiled wine source code my regedit tool does now show any of the registry keys that are suggested to be changed. I used the updatewine.sh script.The script does not change those registry entries, you have to do that manually. Changing those in a script is beyond my powers. If someone else knows how, I would love to know.

---

### Post by aswells on 2007-03-06
For example, Flyser says to change the value in RenderTargetLockMode and DirectDrawRenderer. I have neither of these keys to change the value of. I dont even have a Direct3d folder in the registry.

---

### Post by falsenames on 2007-03-06
the direct3d folder should be at HKEY_CURRENT_USER -> Software -> Wine -> Direct3D
As for the registry keys, you have to right click, and select new -> String Value and put in the name of the new key you want to add, then edit the value.  I had to add them myself, and I've seen a minor increase in performance, but I don't exactly have a lot of memory to toss at the graphics card.  You can even have overrides for specific programs.

---

### Post by Jarn on 2007-03-06
> **aswells said:**
> For example, Flyser says to change the value in RenderTargetLockMode and DirectDrawRenderer. I have neither of these keys to change the value of. I dont even have a Direct3d folder in the registry.Create them. I didn't have them either.

---

### Post by Azakus on 2007-03-06
I made the entries for you using WINE's regedit export. Just save this file as a .reg file and import it in regedit by clicking "Registry -> Import"
```
REGEDIT4



[HKEY_CURRENT_USER\Software\Wine\Direct3D]

"DirectDrawRenderer"="opengl"

"OffscreenRenderingMode"="backbuffer"

"opengl"="enabled"

"RenderTargetLockMode"="auto"

"UseGLSL"="enabled"

"VideoMemorySize"="256"


```

---

### Post by aswells on 2007-03-06
I added the keys, set the values and now all is well :D

I am a little confused by falsenames post, as I though they were supposed to be keys, not strings, and thats what worked for me.

---

### Post by LilYoda on 2007-03-06
Hey guys.

Thanks for the help.  Now that I applied the script, and the regedit file above, GW works perfectly (except for the battle sounds, but I can live without them :D

Big thumbs up!!!

---

### Post by FyreBrand on 2007-03-06
> **aswells said:**
> I added the keys, set the values and now all is well :D

I am a little confused by falsenames post, as I though they were supposed to be keys, not strings, and thats what worked for me.Well we're talking apples and apples here.  They are strings in the programming sense of the word.  The keys are just a series of text strings that Windows reads.  Think of config files for different Linux programs like PHP, Apache, Amarok, etc.

---

### Post by cor2y on 2007-03-06
i don't know what happened between version 9.30 and 9.32 but i too have noticed a slow down in GW being launched as well as Frame Rate and the audio for me has gone down.

---

### Post by falsenames on 2007-03-07
> I am a little confused by falsenames post, as I though they were supposed to be keys, not strings, and thats what worked for me.
Sorry about that, I was going through what regedit lists in its menus.  A "key" there is a new sub directory, and a "string" is the name of a value in there.  Quite backwards looking, but MS made the standard there :)

I've noticed a spike in zone loading time, a minor slowdown in fps, but much better quality each step going from 0.9.30 0.9.32 so far.  Optimizations should be coming soon for the reworking as far as I can tell from the wine-dev mailing list.

---

### Post by cor2y on 2007-03-07
with this latest version of wine for me guild wars stutters the audio (it did stutter before but i hardly ever noticed it and it takes a grand total of 5 mins to go from the login screen to the character selection screen because the frame rate is so slow.

I would say it was my sys specs were it not for the fact i have 1gb of ram and 256mb vid card, and my cpu is one of the last Athlon XP cpus made before AMD went to 64 bit.
Since this is the only game i got to run via wine i can't say what could be the problem , i have tried other apps via wine they run as they did in 0.9.30 but they are nothing cpu/ram/video card intensive  like say a copy of photoshop etc.
Also i tried first manually then using the reg file settings posted here to see if that was the problem.
Still slow framerates.
I may have to roll back to 0.9.30

---

### Post by Factory on 2007-03-07
I get this output when trying to run updatewine.sh:
```

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

/home/cabbage/.wine updated successfully.
Complete! Good luck and have fun! - Jarn
```


It is most obviously not updated successfully, as first of all the install failed, and second of all the mouse still is invisible.

---

### Post by FyreBrand on 2007-03-07
> **Factory said:**
> I get this output when trying to run updatewine.sh:
```

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

/home/cabbage/.wine updated successfully.
Complete! Good luck and have fun! - Jarn
```


It is most obviously not updated successfully, as first of all the install failed, and second of all the mouse still is invisible.
Make sure you are right clicking the mouse a couple of times to get it to show up.

How did you initially install wine?  Did you use the script or compile it manually?  What patches did you apply?  What version of Ubuntu are you using and did you make sure you have all the pre-reqs met?  I haven't read through Jarn's script so maybe he takes care of the pre-reqs for you.


Jarn --  I did a manual compile and install and then used checkinstall (which I've never used before).  I"m using Feisty and as far as I can tell the pre-reqs and manual instructions for Edgy work just fine.  The only thing I deviation I made was that I installed 'build-essential'  as well.

I then used the registry list Azakus compiled from the thread (thanks flyser, falsenames, and azakus) and imported that into the registry.  I didn't do a before/after comparison, but everything is still working fine.

In fact I have better framerates than I've had since last version ( I think that was 0.9.28 ).  To test the install I went to Nolani to dink around a bit.  I had a short peak framerate of 85 - 90fps.  Tha'ts better than any fps I ever get in Windows.  I usually max out at around 75fps.

I don't have any sound but that could also be because I'm using Feisty and something might be jiggy with the sound and wine.  I do have the ALSA drivers available for the first time, but just no sound yet.

I've been running GW in full screen mode at 1280x1024.

I left most of the winecfg settings at their default:
Windows Version: 2000

Graphics:
-Allow the window manager to control the windows: true
-Allow Pixel Shader (if supported by hardware): true

Audio::
-ALSA Driver
-Hardware Accel: Full
-Default Sample Rate: 22050
-Bit Depth: 8

Now if I can just get DungeonRunners working.  The stupid NC launcher wants .NET2.0 and the mono install for Windows isn't cutting it.  Well that's another project.

---

### Post by aswells on 2007-03-08
> **Factory said:**
> I get this output when trying to run updatewine.sh:
```

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

/home/cabbage/.wine updated successfully.
Complete! Good luck and have fun! - Jarn
```


It is most obviously not updated successfully, as first of all the install failed, and second of all the mouse still is invisible.

I had the same error message. I narrowed it down to this line of code in the installer.

```
cd ~/winestuff/wine-* && ./configure
```

My terminal didnt recognize the && as a break between a new command and didnt run ./configure, so it cant "make" anything. All you have to do is edit the installer script to put ./configure on its own line after cd ~/winestuff/wine-* and remove the && symbols.

---

### Post by der_joachim on 2007-03-08
> **cor2y said:**
> with this latest version of wine for me guild wars stutters the audio (it did stutter before but i hardly ever noticed it and it takes a grand total of 5 mins to go from the login screen to the character selection screen because the frame rate is so slow.

I would say it was my sys specs were it not for the fact i have 1gb of ram and 256mb vid card, and my cpu is one of the last Athlon XP cpus made before AMD went to 64 bit.


What video card do you have and what driver version do you use? My GeForce 5600FX works quite happily in wine. 

My sound though is quite choppy, which may require me to go back to 0.9.30 as well. I do not mind not having any combat sounds, but the choppy sounds irritate me a bit too much.

[edit]: It appears that the choppiness is caused by the background sounds. Entirely disabling background sound will solve the choppiness. Forground is still silent and I seem to miss the music as well.

---

### Post by Factory on 2007-03-08
Got it to work. I apt-get remove'd what wine I had previously installed and then used sh installwine+gw.sh and now it works.

ALso, I had to install two packages: flex and bison. Not a single clue what these two guys do, but whatever they are they did the trick it seems.

And no, I didn't re-install guild wars.

Geforce 7600 GT 256MB under Edgy. The official nVidia drivers, too.

---

### Post by Jarn on 2007-03-08
> **aswells said:**
> My terminal didnt recognize the && as a break between a new command and didnt run ./configure, so it cant "make" anything. All you have to do is edit the installer script to put ./configure on its own line after cd ~/winestuff/wine-* and remove the && symbols.Woah, I've never heard of that before. I thought all terminals did that. I'll change it then so it's on two lines.

> **Factory said:**
> ALso, I had to install two packages: flex and bison. Not a single clue what these two guys do, but whatever they are they did the trick it seems.You used the install script, correct? Not the update one? And it didn't get those itself?

---

### Post by cor2y on 2007-03-08
Well my problem is solved.
All it took was the manual compiling of wine with the patches as well as a new .wine directory.
I don't know why but now Guild Wars is not running slow anymore.
And has been noted before the audio has gone wonky with this release of wine but you can play your own music in the background and turn audio off.

---

### Post by Factory on 2007-03-08
> You used the install script, correct? Not the update one? And it didn't get those itself?

Correct, Jarn. it is possible that the mirrors were down at the time, but you never know.

Bottom line: I'm quite pleased now.

---

### Post by Jarn on 2007-03-08
> **Factory said:**
> Correct, Jarn. it is possible that the mirrors were down at the time, but you never know.Hrm... That is the only explanation I can think of since I checked the script and it does install them.

---

### Post by Timbuck.3 on 2007-03-10
Is there a way to apply the mouse patch, with wine and GW already installed ???

---

### Post by Mblackwell on 2007-03-10
If you apt-get remove wine and then compile wine yourself you'll be fine. I would suggest using the method listed on Wine's site to compile Wine, where you use apt-get to build and install everything. Just kill the process when it's doing the configuration (after it's downloaded the source), apply the mouse patch, and then go back to your compiling again. Simple.

This patch should really get worked on more though so that actual 32bit mouse support is there and can be committed. Then we wouldn't have to go through all this trouble every time ;).

---

### Post by Timbuck.3 on 2007-03-10
Merci

I will do that
( hope it works )

---

### Post by FyreBrand on 2007-03-10
> **Timbuck.3 said:**
> Merci

I will do that
( hope it works )
There are instructions in the first post on updating a pre-existing install.  If you used the repo's wine package remove it.  Make sure you copy your GW.dat file to another directory so you won't have to download it again.  Then delete your .wine directory.  Install using the instructions Jarn wrote.

If you compiled your wine from source then following the instructions for upgrading a pre-existing install from source.

---

### Post by raven3x7 on 2007-03-10
I get an error during  the compilation of wine on 64bit:
ay idea whats that about 
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.Witb7I.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/raven/winestuff/wine-0.9.32/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/raven/winestuff/wine-0.9.32/dlls'
make: *** [dlls] Error 2

---

### Post by FyreBrand on 2007-03-10
> **raven3x7 said:**
> I get an error during  the compilation of wine on 64bit:
ay idea whats that about 
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.Witb7I.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/raven/winestuff/wine-0.9.32/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/raven/winestuff/wine-0.9.32/dlls'
make: *** [dlls] Error 2Azakus has put together the 64-bit script and procedure for wine.  Wine is a 32-bit application so I don't think it's going to compile with 64-bit headers.  Read through what Azakus has to recommend.

---

### Post by Factory on 2007-03-11
Hey guys. At a different house this time. This house has a radeon 9600, so I wasn't exactly expecting it to work flawlessly in the least.

I get this error when trying to run the installwine+gw.sh :


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for wine

```

Running edgy here, too.

Edit: Screw it. I just installed wine on it's own, then ran the updatewine.sh script. Hopefully that does the trick.. installing GW now.

Ninja Edit: Well, It kind of works. Except gw appears as a tiny little box in the bottom left hand corner of my screen. I have no idea why.

MOAR EDITS: I followed the guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Now I'm at the point where the guildwars loading screen comes up, then my screen changes resolution and freezes. I can move my mouse, but I can't use any of the other programs unless I alt+tab and then kill the gw process. I guess that could be isolated to a wine problem, right?

---

### Post by Azakus on 2007-03-12
> **Factory said:**
> Hey guys. At a different house this time. This house has a radeon 9600, so I wasn't exactly expecting it to work flawlessly in the least.

I get this error when trying to run the installwine+gw.sh :


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for wine

```

Running edgy here, too.

Edit: Screw it. I just installed wine on it's own, then ran the updatewine.sh script. Hopefully that does the trick.. installing GW now.

Ninja Edit: Well, It kind of works. Except gw appears as a tiny little box in the bottom left hand corner of my screen. I have no idea why.

MOAR EDITS: I followed the guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Now I'm at the point where the guildwars loading screen comes up, then my screen changes resolution and freezes. I can move my mouse, but I can't use any of the other programs unless I alt+tab and then kill the gw process. I guess that could be isolated to a wine problem, right?

Woah, no wonder you got an error. Build-Dep only works when you have a wine listing under /etc/apt/sources.list

The script doesn't need it in my opinion.
Put an "#" in front of this line "sudo apt-get build-dep wine"

---

### Post by Mblackwell on 2007-03-12
> **Factory said:**
> Hey guys. At a different house this time. This house has a radeon 9600, so I wasn't exactly expecting it to work flawlessly in the least.

I get this error when trying to run the installwine+gw.sh :


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for wine

```

Running edgy here, too.

Edit: Screw it. I just installed wine on it's own, then ran the updatewine.sh script. Hopefully that does the trick.. installing GW now.

Ninja Edit: Well, It kind of works. Except gw appears as a tiny little box in the bottom left hand corner of my screen. I have no idea why.

MOAR EDITS: I followed the guide here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Now I'm at the point where the guildwars loading screen comes up, then my screen changes resolution and freezes. I can move my mouse, but I can't use any of the other programs unless I alt+tab and then kill the gw process. I guess that could be isolated to a wine problem, right?

Try running in a virtual desktop.

---

### Post by aswells on 2007-03-12
Im having a problem now. Guild Wars ran fine for weeks, and all of a sudden I am unable to connect to ArenaNet with wine. Guild Wars still runs fine in windows and in cedega. I tried re-installing wine and re-installing guild wars. Has this happened to anyone else?

---

### Post by Azakus on 2007-03-12
Working fine for me.

---

### Post by Factory on 2007-03-12
> **Mblackwell said:**
> Try running in a virtual desktop.

When I try to do this, the virtual desktop crashes. However, when I run it in console, it comes up to the login screen, although it's extremely chunky (to the point where it's unplayable). Alot of output when I try to run in console... so much that it goes up past the point where I'm able to scroll up. Any way to log the output from the command line so I can show you guys what the output is?

---

### Post by FyreBrand on 2007-03-12
Unless your CPU and hardware support VM extensions Guild Wars probably won't run in a VM.  It requires hardware calls that aren't going to be able to be made in the VM.  That's why wine works so well it's able to translate that through the magic of, well.... wine. hahah  I don't know how they do it, but I read about using a VM and in order to get it really working right your CPU and hardware have to support that.

---

### Post by Jarn on 2007-03-12
> **Factory said:**
> Any way to log the output from the command line so I can show you guys what the output is?wine /path/to/file 2>~/gwlog.txt

I think that should work. Also, when you don't want to see anything you can replace ~/gwlog.txt with /dev/null ;).

---

### Post by Flyser on 2007-03-13
Does any1 else experience problems with double-clicking in wine applications (not just) GW, when I do a double click the game or program closes. And has any1 tried to make screenshots? when I press [PRINT] the screenshot, which is saved in my Guild Wars folder is just ... black, the resolution etc. is right but the whole picture is black

---

### Post by Jarn on 2007-03-13
> **Flyser said:**
> Does any1 else experience problems with double-clicking in wine applications (not just) GW, when I do a double click the game or program closes. And has any1 tried to make screenshots? when I press [PRINT] the screenshot, which is saved in my Guild Wars folder is just ... black, the resolution etc. is right but the whole picture is blackI haven't had problems with the mouse. I haven't checked Guild Wars in-game screenshots, I just use kscreenshot (I think that's what it's called).

---

### Post by Factory on 2007-03-14
Here's the output of the file at pastebin. [http://pastebin.com/898713](http://pastebin.com/898713)

It seems what's happened now is that the game will load to the login screen, but it'll run unplayably choppy. This seems to be the same with all other games that I try to use under wine.

Once again, running on a radeon pro 9600 with this as fglrxinfo:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by Flyser on 2007-03-14
The login-screen is choppy for me 2 but the rest of the game not, just try logging in an adjusting video-options

---

### Post by MonsterBox on 2007-03-16
I ran the script for wine+gw and got an error at the end (I think) when it was trying to set-up Guild Wars. I will attach a screenshot of what I see in the window. With any luck it'll help a bit.

Additionally, I have no idea how to run Wine. Please be gentle I'm a **total** Ubuntu/Linux newbie. I've tried running the commands wine and winecfg from the terminal, but no matter where I am (directory) it tells me: "bash : wincfg : command not found". When I went looking at the documentation at Wine HQ, it mentioned /usr/local/bin/winecfg but when I do an ls in the bin directory it is empty...

I'm totally stumped. Any help at all would be greatly appreciated. Sorry for the incredibly elementary question, I'm sure it is something ridiculously simple, but I can't for the life of me figure out what to do.

Thanks!

---

### Post by Jarn on 2007-03-16
> **MonsterBox said:**
> I ran the script for wine+gw and got an error at the end (I think) when it was trying to set-up Guild Wars.Yes, you did. You don't have checkinstall. I'll see if the script installs it - I thought it did, but it must not since you don't have it. Either that or you weren't connected to the internet. Regardless, to install wine, you can type "sudo apt-get install checkinstall". Then, type "cd ~/winestuff/wine-*". Then, do:
```
sudo checkinstall
wget http://www.guildwars.com/downloads/gwsetup.zip -O ~/gwsetup.zip
cd ~
unzip gwsetup.zip
wineprefixcreate
mv ~/GWSETUP.EXE ~/.wine/drive_c/
cd ~/.wine/drive_c
wine GWSETUP.EXE 2>/dev/null
echo "Complete! Good luck and have fun! - Jarn"
```

> **MonsterBox said:**
> Additionally, I have no idea how to run Wine. Please be gentle I'm a **total** Ubuntu/Linux newbie. I've tried running the commands wine and winecfg from the terminal, but no matter where I am (directory) it tells me: "bash : wincfg : command not found".There's two reasons for that. First of all, wine isn't installed because of the above. Second of all, you typoed winecfg - you typed wincfg instead of winecfg. Once you do what I said above, you will be able to type 'winecfg' and 'wine' and it will work - but not 'wincfg'.

Once you have installed stuff with wine, it is very easy to run. You just type "wine /path/to/the/file". So, for example, Guild Wars will be "wine ~/.wine/drive_c/Program\ Files/Guild\ Wars/gw.exe".

Good luck!

EDIT: Yeah, I feel really bad. I forgot to have installwine+gw.sh install checkinstall... the updatewine.sh one does, but not installwine+gw.sh - sorry!

---

### Post by MonsterBox on 2007-03-16
No need to apologize, thank you very much for the clarification. I will do that the next time I boot into Ubuntu and see what works out.

Thanks for such a quick response, I appreciate it. :)

Oh yeah, and for the portion in the code block, should I type each in succession at the prompt? (except for the echo of course)

---

### Post by Jarn on 2007-03-16
> **MonsterBox said:**
> No need to apologize, thank you very much for the clarification. I will do that the next time I boot into Ubuntu and see what works out.

Thanks for such a quick response, I appreciate it. :)

Oh yeah, and for the portion in the code block, should I type each in succession at the prompt? (except for the echo of course)
You can type it in or you should be able to copy and paste it in. Yeah, that echo was in there just because I copied and pasted it right out of the script. My bad. :P

---

### Post by FyreBrand on 2007-03-16
Yep, type each line in one at a time.

---

### Post by Jarn on 2007-03-17
I'm leaving town for a week. So I may or may not respond any messages hereafter.

---

### Post by Azakus on 2007-03-17
Wine 0.9.33 released. Updating 64-bit script.
Also, creating updatewine64 script.

---

### Post by Jarn on 2007-03-17
If you could just post it here when you do it, that would be great. I'll update the scripts to 0.9.33 when I get back. In the meantime, for anyone that wants to get it right away, all that should be necessary is editing the link to the source in the scripts and maybe porting a patch. But the only way to find out if porting a patch is necessary is to give it a try. ;)

EDIT: I don't know much about patch, but I think that the 32-bit cursor patch worked since it didn't produce any errors. The concurrent lights patch produced:
```
patching file device.c
Hunk #1 succeeded at 2379 (offset -2 lines).
```I don't know if that means the whole thing succeeded or just part. If it means the whole thing succeeded than all that is necessary is changing the line in the scripts to point at the new source.

---

### Post by Azakus on 2007-03-17
Alrighty, here's the new scripts. Ver 0.9.33
{EDIT}
Needed fixes, go here [http://ubuntuforums.org/showpost.php?p=2314687&postcount=308](http://ubuntuforums.org/showpost.php?p=2314687&postcount=308)

---

### Post by Flyser on 2007-03-17
I'll post a updated version of the patches here when 0.9.33 hits the gentoo-portagetree.

---

### Post by Jarn on 2007-03-17
> **Flyser said:**
> I'll post a updated version of the patches here when 0.9.33 hits the gentoo-portagetree.Is it necessary to port the patch? Or will the current ones still work with the current source?

And this actually will be my last post before I leave, seeing as my ride to the airport should be here in 15 minutes. :P

---

### Post by Flyser on 2007-03-17
Dont know if I a new version is needed, anyway i ported the patches and it might be interisting for users of the lights-patch because I changed the error-message of  "Too many concurrently active lights" from ERR to FIXME so it won't spam the console anymore

---

### Post by darksong on 2007-03-17
Is there 0.9.32 mouse patch about - there isn't any listed on this forum.

---

### Post by falsenames on 2007-03-17
The 0.9.33 mouse patch should work for 0.9.32 since the file didn't change.  The device.c file changed quite a bit though, so if you needed the concurrent lights patch, use the 0.9.33 version of the script.

---

### Post by darksong on 2007-03-17
thanks for the speedy reply :D - i will give it a go right away

Edit:

The guide tells me to put these files in a directory that does not exist - my G/W is working - just the pointer is not there, i installed wine separately as the guides way only put wine tools on my pc :S where can i install these files?  It seems when i installed wine through synaptic, it seems it only installed a .wine directory, i have searched my pc and no winetools folder found :S - any suggestion much appericated, Many thanks

DS

---

### Post by KamiCrazy on 2007-03-17
Err double post soz

---

### Post by KamiCrazy on 2007-03-17
I am unable to install gw using azakus's script at all.

The first error that appears is that apt can't find a package called libjack, however i managed to install libjack anyway using synaptic.

After that it does everything and gets to compiling wine. It fails at one point and then ends everything.

Then it runs checkinstall and that fails too ending with

```
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls/ddraw'
make[1]: *** [ddraw/__install-lib__] Error 2
make[1]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls'
make: *** [dlls/__install-lib__] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

```

I have no idea what is wrong.

---

### Post by Azakus on 2007-03-17
Oops, thanks for pointing out that libjack had an incorrect version number in the script. As for your libXext problems, did you using the install script, or the update script? Install script uses an extra script that definately installs the necessary library libXext.a (that file is libxext-dev).
Be sure to use the the installwine+gw64.sh script if it is your first time using a 64-bit build for WINE.
--Included below is the correct install and update scripts--
{EDIT}
Had to fix them again, so go here: [http://ubuntuforums.org/showpost.php?p=2314687&postcount=308](http://ubuntuforums.org/showpost.php?p=2314687&postcount=308)

---

### Post by KamiCrazy on 2007-03-17
In an attempt to isolate what is wrong I opened the script and stepped through it one line at a time.

Everything works fine (apart from the libjack thing) until I get to configuring the wine compile where I get this

```
configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

configure: WARNING: Your system appears to have the FreeType 2 runtime libraries
configure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FreeType is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished.  Do 'make depend && make' to compile Wine.

```

Is this normal or is there something else wrong with my system? I thought I do have an OpenGL library as I only just freshly installed the nvidia drivers!

---

### Post by Azakus on 2007-03-17
> **KamiCrazy said:**
> In an attempt to isolate what is wrong I opened the script and stepped through it one line at a time.

Everything works fine (apart from the libjack thing) until I get to configuring the wine compile where I get this

```
configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.

configure: WARNING: Your system appears to have the FreeType 2 runtime libraries
configure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FreeType is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished.  Do 'make depend && make' to compile Wine.

```

Is this normal or is there something else wrong with my system? I thought I do have an OpenGL library as I only just freshly installed the nvidia drivers!

Hmm. I was sure that was in the pkgs.sh file, but I guess it was moved out.
Install libfreetype6-dev, which I will now add to the scripts.
Try it now.

---

### Post by KamiCrazy on 2007-03-18
Freetype6 is installed on my computer.

when I run your new script, the first line doesn't do anything. I went into synaptic to check and sure enough Freetype6 is checked and installed.

However when I run the config line before making wine it gives me the same error above.

Any clue why it's giving me that error despite having Freetype6 installed?

EDIT: Okay I can definitely run freetype-config, so how do I put it into my PATH?

---

### Post by KamiCrazy on 2007-03-18
Okay I did a little more investigating

```
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so

```

This part of your script ends up creating a whole bunch of broken symbolic links for me. As these files do not exist in lib32. I was able to find them in /usr/lib. However are you supposed to be linking to the ones in /usr/lib?

---

### Post by falsenames on 2007-03-18
Each build of Wine that's released, I try playing guild wars without the patches to see what's changed.  I'm really happy with 0.9.33 so far.  I haven't had the concurrent lights bug, which I've had in each previous release.  I also haven't had to put in the mouse patch on this one, but I didn't have to patch the previous two releases for that either.  Another great thing has been for objects that are far away.  It used to be that there were huge black rectangles that disappeared when you got closer.  Now there seems to be a hazy mesh of the terrain.  The colours are occasionally psychadelic looking, but this is much better to look at than the huge black spots covering the horizon.

Granted, this is off of only one day of testing, so if I find out I really do need one of the patches, I'll keep everyone posted.

---

### Post by FyreBrand on 2007-03-18
> **falsenames said:**
> Each build of Wine that's released, I try playing guild wars without the patches to see what's changed.  I'm really happy with 0.9.33 so far.  I haven't had the concurrent lights bug, which I've had in each previous release.  I also haven't had to put in the mouse patch on this one, but I didn't have to patch the previous two releases for that either.  Another great thing has been for objects that are far away.  It used to be that there were huge black rectangles that disappeared when you got closer.  Now there seems to be a hazy mesh of the terrain.  The colours are occasionally psychadelic looking, but this is much better to look at than the huge black spots covering the horizon.

Granted, this is off of only one day of testing, so if I find out I really do need one of the patches, I'll keep everyone posted.That's good to hear falsenames.  What video card are you using?  If it turns out that we don't have to patch wine anymore we might just be able to install the deb and not hassle with compiling all together.

---

### Post by falsenames on 2007-03-18
*points to his sig* an Asus EN6200LE.  Not a great card by any stretch of the imagination.  I believe that nVidia also came out with a new driver recently, but I'm not sure if that affects my card, so I haven't bothered to download it yet.

Also, wine has been bouncing back and forth with how well the releases have been working.  0.9.29 completely didn't work at all, and I can't remember which of 31 and 32 worked better, since I had to change back and forth between them so much.  With all the revisions the dev team has been doing, they seem to be taking two or three steps forward, then one step back over and over again.  Not a bad system considering the rapid progress they are making from what I've seen.

---

### Post by darksong on 2007-03-18
agreed, the progress they are making is brilliant - hopefully the fps will get better with future releases - atm the best i have got out of any version is 15 fps on a:

Amd 2400xp
512mb ram
fx5200 128mb

on windows i can run it at full settings around 35 fps, here on low is 15, i guess with future releases this will get better :D

---

### Post by Azakus on 2007-03-18
> **KamiCrazy said:**
> Okay I did a little more investigating

```
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so

```

This part of your script ends up creating a whole bunch of broken symbolic links for me. As these files do not exist in lib32. I was able to find them in /usr/lib. However are you supposed to be linking to the ones in /usr/lib?

Are all the links broken for you? That's really weird. Do you have your universes repository enabled? That might be causing this to fail. On my system, all the /usr/lib32 files were created automatically when the files were installed.

---

### Post by FyreBrand on 2007-03-18
> **falsenames said:**
> *points to his sig* an Asus EN6200LE.  Not a great card by any stretch of the imagination.  I believe that nVidia also came out with a new driver recently, but I'm not sure if that affects my card, so I haven't bothered to download it yet.

Also, wine has been bouncing back and forth with how well the releases have been working.  0.9.29 completely didn't work at all, and I can't remember which of 31 and 32 worked better, since I had to change back and forth between them so much.  With all the revisions the dev team has been doing, they seem to be taking two or three steps forward, then one step back over and over again.  Not a bad system considering the rapid progress they are making from what I've seen.I wasn't sure if that was the card or not.  I have a 6800.  I've noticed the 3 steps forward 1 step back thing too.  I don't mind it either.  The progress they are making is amazing.  I wouldn't have expected to see in 6 months the progress they make in 6 weeks. 0.29 didn't work for me either.

I had to reconfigure my hardrive for a project I'm doing so I don't have GuildWars on Windows or Linux at the moment.  I'll be recompiling wine and installing this week after finals are over.

> **darksong said:**
> agreed, the progress they are making is brilliant - hopefully the fps will get better with future releases - atm the best i have got out of any version is 15 fps on a:

Amd 2400xp
512mb ram
fx5200 128mb

on windows i can run it at full settings around 35 fps, here on low is 15, i guess with future releases this will get better :DThe framerate has been getting better for me with every release that works.  In .28 I got topped out at 35fps in Linux and 75fps in Windows.  In 0.32 I peaked out at 80fps in some places in Linux and no change in Windows.  Towns I usually get 15 - 35fps and the instance is where my framerate goes back to normal.

I'll report back after in a few days after I install everything.

---

### Post by darksong on 2007-03-18
Thanks fyrebrand. My current version of wine is 0.9.32 - should i upgrade this to get better fps. How would i update wine without installing it again from the start, or is that not possible? :confused: 

My current wine graphic settings are as followed:

-Allow DirectX to stop mouse from leaving their window
-Allow window manager to control the window
-Emulate a virtual desktop (Resolution 1024x768) 
-Allow pixel shader is supported by hardware (hardware)

My guildwars i set on everything low apart from textures which are set to medium.

Thanks 
DS

---

### Post by KamiCrazy on 2007-03-18
> **Azakus said:**
> Are all the links broken for you? That's really weird. Do you have your universes repository enabled? That might be causing this to fail. On my system, all the /usr/lib32 files were created automatically when the files were installed.

Yes every link ye make in the lib32 directory is broken. I do have the universe repository enabled as that was how I managed to get it to find checkinstall.

My installation is completely fresh, I've installed nvidia drivers and attempted to run your script for wine+gw.

EDIT: Looking in my /usr/lib directory, there are symbolic links also in there that also have the same names. I am not sure what created these links.

I've also since updated to nvidia 9755 drivers, I'm guessing these "missing" libraries are from the driver packages 32 bit opengl compatability, but I always choose Yes when asked to install them. I could be wrong though, are these files supposed to be part of a standard ubuntu install?

EDIT2: actually one of the symbolic links works now. libGL.so links to libGL.so.1 which links to libGL.so.1.0.9755 fyi. The other ones are still broken.

---

### Post by florent522 on 2007-03-18
impossible download updatewine.sh why???

---

### Post by darksong on 2007-03-18
> **florent522 said:**
> impossible download updatewine.sh why???

Is this a direct download issue, if you want i can email you the updatewine.sh 

If it will not update, you may be running the newest version of wine....

---

### Post by FyreBrand on 2007-03-18
> **darksong said:**
> Thanks fyrebrand. My current version of wine is 0.9.32 - should i upgrade this to get better fps. How would i update wine without installing it again from the start, or is that not possible? :confused: 

My current wine graphic settings are as followed:

-Allow DirectX to stop mouse from leaving their window
-Allow window manager to control the window
-Emulate a virtual desktop (Resolution 1024x768) 
-Allow pixel shader is supported by hardware (hardware)

My guildwars i set on everything low apart from textures which are set to medium.

Thanks 
DSI don't know if you should update or not.  Sometimes there are regressions that reduce performance.  If you do want to update then use Jarn's update script.  I'm not sure if he's updated it yet though, so it might be better to wait a while.

Have you had any success with running the game in full screen mode?  By that I mean not emulating a virtual desktop.  Somewhere in the last couple of versions I could start doing this, before that it would often cause the game to freeze.  Another thing I've been trying is running the game emulating Win2k instead of Win98.  Also the registry tweaks mentioned earlier in the thread sure seemed to help me out (at least they didn't hurt).

---

### Post by KamiCrazy on 2007-03-19
I am having absolutely no luck compiling wine.

I just nuked my ubuntu64 install and reinstalled edgy from the live CD, updated the installation, installed nvidia 9755 drivers and then proceeded to step through your script one line at a time again.

I am still missing those files in lib32. I am not sure what I can do to fix this issue at all.

---

### Post by FyreBrand on 2007-03-19
> **KamiCrazy said:**
> I am having absolutely no luck compiling wine.

I just nuked my ubuntu64 install and reinstalled edgy from the live CD, updated the installation, installed nvidia 9755 drivers and then proceeded to step through your script one line at a time again.

I am still missing those files in lib32. I am not sure what I can do to fix this issue at all.
This is the shell script from kegel.  Go through and manually check that each package is installed.  You can just use apt-get install.  If the package is already installed it won't do anything.  When you get to an error or it doesn't work then post the output.

Here is what you need to install from the shell script:
```
#!/bin/sh
# Script showing how to set up a Wine development environment
# on Ubuntu 06.10 (Edgy)
#
# A few Ubuntu tips:
#
# Some packages, like cogito and libjack-dev, are only available 
# in the Universe repository, so you need to uncomment out
# the appropriate line in /etc/apt/sources.list or check the 'universe'
# checkbox in the GUI package manager 'synaptic'.
#
# If you see a prompt to insert the CD when installing software
# with apt-get, comment out the initial reference to the cdrom in /etc/apt/sources.list.
# See https://launchpad.net/distros/ubuntu/+source/apt/+bug/37888
#
# If you see "open /dev/snd/seq failed",
# add snd_seq_oss to /etc/modules
# See http://ubuntuforums.org/archive/index.php/t-1654.html
#
# If you see "cannot create mcop directory"
# when you run winecfg and click on the audio tag,
# do "mkdir -p $HOME/.kde/socket-`hostname`".
# See https://launchpad.net/distros/ubuntu/+source/alsa-lib/+bug/31699
#

# Get basic source management tools
apt-get install cvs git-core cogito

# Get basic C compiler tools
apt-get install gcc libc6-dev flex bison make linux-libc-dev m4

# Get font tools
apt-get install fontforge

# Get libraries needed by Wine
apt-get install \
libaudio-dev \
libcapi20-3 \
libcapi20-dev \
libcupsys2-dev \
libdbus-1-dev \
libesd0-dev \
libexif-dev \
libexpat1-dev \
libfontconfig1-dev \
libfreetype6-dev \
libgcrypt11-dev \
libgl1-mesa-dev \
libglib1.2-dev \
libglib2.0-dev \
libglu1-mesa-dev \
libgnutls-dev \
libgpg-error-dev \
libgphoto2-2-dev \
libhal-dev \
libice-dev \
libicu34-dev \
libieee1284-3-dev \
libjpeg62-dev \
liblcms1-dev \
libldap2-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libmad0 \
libmad0-dev \
libmng-dev \
libncurses5-dev \
libodbcinstq1c2 \
libogg-dev \
libopencdk8-dev \
libpng12-dev \
libpopt-dev \
libqt3-headers \
libqt3-mt \
libqt3-mt-dev \
libsane-dev \
libsm-dev \
libssl-dev \
libtasn1-3-dev \
libtiff4-dev \
libtiffxx0c2 \
libusb-dev \
libvorbis-dev \
libvorbisfile3 \
libx11-dev \
libxau-dev \
libxcursor-dev \
libxdmcp-dev \
libxext-dev \
libxfixes-dev \
libxft-dev \
libxi-dev \
libxinerama-dev \
libxml2-dev \
libxmu-dev \
libxmu-headers \
libxrandr-dev \
libxrender-dev \
libxslt1-dev \
libxt-dev \
libxv-dev \
libxxf86vm-dev \
mesa-common-dev \
odbcinst1debian1 \
qt3-dev-tools \
render-dev \
unixodbc \
unixodbc-dev \
x11proto-core-dev \
x11proto-fixes-dev \
x11proto-input-dev \
x11proto-kb-dev \
x11proto-randr-dev \
x11proto-render-dev \
x11proto-video-dev \
x11proto-xext-dev \
x11proto-xf86vidmode-dev \
x11proto-xinerama-dev \
x-dev \
xtrans-dev \
zlib1g-dev

```In that long list make sure that you just go through a few at a time and install them.  I wouldn't go through the whole list at once (or else you would just be running the script).  Also make sure patch and checkinstall are both installed.  This script doesn't do that.

---

### Post by KamiCrazy on 2007-03-19
> **FyreBrand said:**
> This is the shell script from kegel.  Go through and manually check that each package is installed.  You can just use apt-get install.  If the package is already installed it won't do anything.  When you get to an error or it doesn't work then post the output.

Here is what you need to install from the shell script:
```
#!/bin/sh
# Script showing how to set up a Wine development environment
# on Ubuntu 06.10 (Edgy)
#
# A few Ubuntu tips:
#
# Some packages, like cogito and libjack-dev, are only available 
# in the Universe repository, so you need to uncomment out
# the appropriate line in /etc/apt/sources.list or check the 'universe'
# checkbox in the GUI package manager 'synaptic'.
#
# If you see a prompt to insert the CD when installing software
# with apt-get, comment out the initial reference to the cdrom in /etc/apt/sources.list.
# See https://launchpad.net/distros/ubuntu/+source/apt/+bug/37888
#
# If you see "open /dev/snd/seq failed",
# add snd_seq_oss to /etc/modules
# See http://ubuntuforums.org/archive/index.php/t-1654.html
#
# If you see "cannot create mcop directory"
# when you run winecfg and click on the audio tag,
# do "mkdir -p $HOME/.kde/socket-`hostname`".
# See https://launchpad.net/distros/ubuntu/+source/alsa-lib/+bug/31699
#

# Get basic source management tools
apt-get install cvs git-core cogito

# Get basic C compiler tools
apt-get install gcc libc6-dev flex bison make linux-libc-dev m4

# Get font tools
apt-get install fontforge

# Get libraries needed by Wine
apt-get install \
libaudio-dev \
libcapi20-3 \
libcapi20-dev \
libcupsys2-dev \
libdbus-1-dev \
libesd0-dev \
libexif-dev \
libexpat1-dev \
libfontconfig1-dev \
libfreetype6-dev \
libgcrypt11-dev \
libgl1-mesa-dev \
libglib1.2-dev \
libglib2.0-dev \
libglu1-mesa-dev \
libgnutls-dev \
libgpg-error-dev \
libgphoto2-2-dev \
libhal-dev \
libice-dev \
libicu34-dev \
libieee1284-3-dev \
libjpeg62-dev \
liblcms1-dev \
libldap2-dev \
libltdl3 \
libltdl3-dev \
liblzo-dev \
libmad0 \
libmad0-dev \
libmng-dev \
libncurses5-dev \
libodbcinstq1c2 \
libogg-dev \
libopencdk8-dev \
libpng12-dev \
libpopt-dev \
libqt3-headers \
libqt3-mt \
libqt3-mt-dev \
libsane-dev \
libsm-dev \
libssl-dev \
libtasn1-3-dev \
libtiff4-dev \
libtiffxx0c2 \
libusb-dev \
libvorbis-dev \
libvorbisfile3 \
libx11-dev \
libxau-dev \
libxcursor-dev \
libxdmcp-dev \
libxext-dev \
libxfixes-dev \
libxft-dev \
libxi-dev \
libxinerama-dev \
libxml2-dev \
libxmu-dev \
libxmu-headers \
libxrandr-dev \
libxrender-dev \
libxslt1-dev \
libxt-dev \
libxv-dev \
libxxf86vm-dev \
mesa-common-dev \
odbcinst1debian1 \
qt3-dev-tools \
render-dev \
unixodbc \
unixodbc-dev \
x11proto-core-dev \
x11proto-fixes-dev \
x11proto-input-dev \
x11proto-kb-dev \
x11proto-randr-dev \
x11proto-render-dev \
x11proto-video-dev \
x11proto-xext-dev \
x11proto-xf86vidmode-dev \
x11proto-xinerama-dev \
x-dev \
xtrans-dev \
zlib1g-dev

```In that long list make sure that you just go through a few at a time and install them.  I wouldn't go through the whole list at once (or else you would just be running the script).  Also make sure patch and checkinstall are both installed.  This script doesn't do that.

Already done that twice, stepped through the script 1 command at a time. Everything is fine with kegel's script. Everything installs fine.

---

### Post by KamiCrazy on 2007-03-19
fixed! sudo apt-get install -u ia32-libs

EDIT: Compiling wine now gives me the error

winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls'
make: *** [dlls] Error 2


:(

---

### Post by darksong on 2007-03-19
> **FyreBrand said:**
> I don't know if you should update or not.  Sometimes there are regressions that reduce performance.  If you do want to update then use Jarn's update script.  I'm not sure if he's updated it yet though, so it might be better to wait a while.

Have you had any success with running the game in full screen mode?  By that I mean not emulating a virtual desktop.  Somewhere in the last couple of versions I could start doing this, before that it would often cause the game to freeze.  Another thing I've been trying is running the game emulating Win2k instead of Win98.  Also the registry tweaks mentioned earlier in the thread sure seemed to help me out (at least they didn't hurt).

Thanks :D - I am running win98 atm so i will change this when i get back home.  I will also stop running in wine desktop then, i havn't tested this out, hopefully it will give some extra preformance :D. Is their a possiblitiy of messing up guildwars/wine if you tweak the resgistery, i don't want to re-install over again :popcorn: 

Thanks for the advice, you will be sure to hear back from me :D

---

### Post by FyreBrand on 2007-03-19
> **darksong said:**
> Thanks :D - I am running win98 atm so i will change this when i get back home.  I will also stop running in wine desktop then, i havn't tested this out, hopefully it will give some extra preformance :D. Is their a possiblitiy of messing up guildwars/wine if you tweak the resgistery, i don't want to re-install over again :popcorn: 

Thanks for the advice, you will be sure to hear back from me :DNo it shouldn't mess anything up that I know of.  Try the other two first and leave the registry alone if you're uncomfortable with that.  At worst wine won't like the changes and crash your system.  If that happens return the settings to how they were before.  On some systems running wine apps in full screen mode works and some it doesn't.

---

### Post by Azakus on 2007-03-19
> **KamiCrazy said:**
> fixed! sudo apt-get install -u ia32-libs

EDIT: Compiling wine now gives me the error

winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2
make[2]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls/gdi32'
make[1]: *** [gdi32] Error 2
make[1]: Leaving directory `/home/deon/winestuff/wine-0.9.33/dlls'
make: *** [dlls] Error 2


:(

Ok. that error is fixable with this command.
```
#!/bin/sh
cd ~/winestuff
wget ftp://ftp.software.ibm.com/software/globalization/icu/3.6/icu4c-3_6-src.tgz
tar zxvf icu4c-3_6-src.tgz
cd ./icu/source
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc -m32" CXX="g++ -m32" ./configure
make
ar t /usr/lib/libsicuuc.a | sed -e 's/ao$/o/' | perl -e 'while(<>){ chomp($_); print "find . -name $_ | xargs ar ruv libsicuuc.a\n"; }' > mkar.sh
sh mkar.sh
sudo cp libsicuuc.a /usr/lib32/
```

---

### Post by KamiCrazy on 2007-03-19
> **Azakus said:**
> Ok. that error is fixable with this command.
```
#!/bin/sh
cd ~/winestuff
wget ftp://ftp.software.ibm.com/software/globalization/icu/3.6/icu4c-3_6-src.tgz
tar zxvf icu4c-3_6-src.tgz
cd ./icu/source
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc -m32" CXX="g++ -m32" ./configure
make
ar t /usr/lib/libsicuuc.a | sed -e 's/ao$/o/' | perl -e 'while(<>){ chomp($_); print "find . -name $_ | xargs ar ruv libsicuuc.a\n"; }' > mkar.sh
sh mkar.sh
sudo cp libsicuuc.a /usr/lib32/
```

I can assure you azakus that I have not skipped that part of your script. The compiled libsicuuc.a is not working. I must have compiled that and copied it to /usr/lib32 about 5 times now :(

I found a pre-compiled one from another website which had the same problem. Strangely enough using that one gdi32 managed to compile fine with no errors. However I end up with segmentation errors once I get to user32.

---

### Post by florent522 on 2007-03-19
> **darksong said:**
> Is this a direct download issue, if you want i can email you the updatewine.sh 

If it will not update, you may be running the newest version of wine....

you can send file by mail please? florent522_A_T_gmail.com

Thank you i speak a bad english, i'm french

---

### Post by Azakus on 2007-03-19
I honestly have no idea why it isn't working for you. As a token of my frustration, here's the .deb I made. (Please don't everyone download this, it is from my home server, which will undoubtedly crash if everyone just tries it).
[http://azakusfiles.homelinux.net/wine_0.9.33-1_amd64.deb](http://azakusfiles.homelinux.net/wine_0.9.33-1_amd64.deb)

---

### Post by KittyKitty on 2007-03-19
Following the instuctions posted on how to get gw working on in wine...

and using 
[http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)
to suplement me on requirement packages

I finally got it to NOT say that it wouldn't support directx during compile/configure ...
but then it still yells that it doesn't when I try to start the game

I'm just wondering wtf I need to do, I don't have a lead on how to troubleshoot it.

---

### Post by Apocrypha on 2007-03-19
Just tried this tonight, not really that big into linux but I really don't want Vista so now's the time to learn. I've tried FC4, gentoo and slackware before anyway.

The hardware: 3700+ San Diego
1 gig o' ram
X1950 Pro Powercolor (seems to be working fine in UT2004, installed drivers based on some previous link in this thread)
Soundblaster X-Fi so I don't expect sound anyway

Running Edgy 64 bit Ubuntu, ran the script just fine.
It appears that I don't have a .wine directory though:
```
apocrypha@Pandora:~$ ls -a
.               .gconfd            .recently-used
..              .gimp-2.2          .recently-used.xbel
.bash_history   .gksu.lock         .sudo_as_admin_successful
.bash_logout    .gnome             .thumbnails
.bash_profile   .gnome2            .Trash
.bashrc         .gnome2_private    Unreal Tournament Game of the Year Edition
.BitTornado     .gstreamer-0.10    .update-manager
.config         .gtkrc-1.2-gnome2  .update-notifier
Desktop         GWSETUP.EXE        UT
.dmrc           gwsetup.zip        ut2004
.esd_auth       .ICEauthority      .ut2004
Examples        .local             winestuff
.fonts.cache-1  .metacity          .Xauthority
.gaim           .mozilla           .xchat2
.gconf          .nautilus          .xsession-errors
```
That is where I should be looking right?

Edit: an IRC channel or at least someone to talk to on IRC would make this a lot faster.

---

### Post by Jarn on 2007-03-19
Try typing "wineprefixcreate". Are you using the 64-bit script?

---

### Post by cor2y on 2007-03-20
upgraded to the latest wine (0.9.33) via synaptic without applying the patches because i had read here that they seemed to be no longer necessary.

Anyhow here is the good news the light  patch doesn't seem to be needed.
Frame rates  and loading times have sped up once more for me.

The Bad news i will have to uninstal and custom compile 0.9.33, the mouse cursor for in game guildwars form is missing (looks sometimes like the regular mouse arrow or the horizontal exapand cursor on occasions) and the audio rendering still needs some work but overall it  looks like an improvement over  0.9.32 guildwars wise.

---

### Post by KamiCrazy on 2007-03-20
Thank you for the deb azakus. I have spent the better part of 2 days trying to get this to work. A lot of wasted time but strangely enough I have enjoyed learning more about linux.

I tried one more time tonight, to compile wine. On a few pages it recommends removing libicu34-dev. Even on the winehq site it says it won't build if you have that installed (for dapper).

So I removed it, the step with ar fails though since it can't find libsicuuc.a in /usr/lib, so I put it back, ran that command and then removed it.

Compiling worked past gdi32. However it failed finally with a segmentation fault.
That seems to be the biggest hurdle for me, 2 other solutions to get around the gdi32 dll problem now and they have all failed with segmentation faults. Usually when I am compiling wined3d or user32.

I've given up in the short term and just used your deb file. Works like a charm. However I would like to figure out for the long term why my system won't compile wine. Its not like its special or anything its a completely fresh install!

EDIT: Is there supposed to be sound btw? Mine doesn't have any sound. Not a biggie but just wondering if there are additional problems with my install. When I run winecfg it complains that it can't find libjack.so (it doesn't exist in /usr/lib32 but it does exist in /usr/lib)

---

### Post by Azakus on 2007-03-20
Try entering winecfg and switching to ALSA sound.

---

### Post by KamiCrazy on 2007-03-21
Yeah I gave that a go when I was initially playing with winecfg and seeing what the options do.

If I switch to ALSA, what happens then is when I start guildwars, it gets the loading screen connecting to arena net. Then after that finishes and it tries to render the login screen, I get nothing. Not a blank white nothing, but a whatever was on the screen at the time ie. the desktop nothing.

I can switch back to the desktop, do things then switch back and the image remains the same.

Not sure what that means.

---

### Post by dorath on 2007-03-22
I'd like to extend my thanks to everyone who has contributed to this thread.  You've been of immense help! :)

---

### Post by rillip on 2007-03-23
I don't know what did it, but running the update script and changing the settings to what you had worked for me.  Is there a way to find out, short of slogging through the 34 pages or so of this thread, what the script does for my edification?

---

### Post by Jarn on 2007-03-23
> **rillip said:**
> I don't know what did it, but running the update script and changing the settings to what you had worked for me.  Is there a way to find out, short of slogging through the 34 pages or so of this thread, what the script does for my edification?You could open the script with any text editor. But I can tell you what it does.

It downloads the Wine source and a few patches that make it work with Guild Wars. Then it installs all the packages needed to compile Wine. Then it applies the patches to the source and compiles it into a deb and installs the deb.

---

### Post by rillip on 2007-03-23
Thanks Jarn. You're right that I could have cracked open the script, but watching it install itself, I was pretty confident I wouldn't get what it was doing without an overview.  I'll have to check out those patches for myself and see if I can't get it working on my own with another computer; and as a backup, there's always the update.sh. :)  Man I love Linux!

Edit: I forgot to mention, when I first started, I got the error message "unable to initialize 3d ouput."  Last time I gave up after things like the patch didn't work, but this time I got the bright idea that my drivers might not be setup right; sure enough, it had the defualts, not my ati ones.  I found a guide on how to upgrade them, I think on these forums, but I couldn't re-find it to post a link.  After that it would freeze where it askes me if I was sure I wanted to continue with unsupported hardware. That's where the patch came in and saved the day.

---

### Post by FyreBrand on 2007-03-23
Jarn I did a quick experiment with the 0.9.33 in the repos.  It works great except no mouse.  I'm not sure if concurrent lights is still a problem, but I didn't get it while logged in.  It's almost to the point where we'll just be able to use the repositories.  I'm thinking of trying the budget-dedicated repo and see if that makes a difference, but I don't think it will.  Our MOTU for wine just rocks at keeping wine updated.

edit:  wow they have the same version as we do.  our motu really does rock!

---

### Post by Jarn on 2007-03-23
What is a MOTU?

---

### Post by FyreBrand on 2007-03-24
The masters of the universe. They maintain the universe and multiverse packages.  I think wine is in universe.  Anyway who ever is making and keeping wine .debs in the repos is doing a great job.

---

### Post by der_joachim on 2007-03-24
@Jarn & FyreBrand: I do not need the lights patch anymore. I did when I used 0.9.32 and below. However, I bought a new video card last week, so I am not entirely sure whether the lights issues have been solved or I have a better supported card. They're both NVIDIA.

---

### Post by Factory on 2007-03-24
I guess this doesn't work with .33 yet, huh.

---

### Post by Straumoy on 2007-03-24
Hello,

I've downloaded and run through the updatewine.sh script since I had Wine installed and copied the Guild Wars folder from my Windows machine. At any rate, when I start the little bugger up, I soon get a message that says I don't have DirectX 8 or higher, alternatively my video card driver is out of date. 

Any suggestions on how to work around this issue?

---

### Post by Apocrypha on 2007-03-24
[QUOTE=Jarn]Try typing "wineprefixcreate". Are you using the 64-bit script?[/QUOTE]

Hope that was directed at me, that command did nothing and I am using the 64bit script.

Edit: This is the last bit when I run the script:
> 
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/ddraw'
make[1]: *** [ddraw/__install-lib__] Error 2
make[1]: Leaving directory `/home/apocrypha/winestuff/wine-0.9.32/dlls'
make: *** [dlls/__install-lib__] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

--22:45:02--  [http://www.guildwars.com/downloads/gwsetup.zip](http://www.guildwars.com/downloads/gwsetup.zip)
           => `/home/apocrypha/gwsetup.zip'
Resolving [www.guildwars.com](www.guildwars.com)... 206.127.153.151
Connecting to www.guildwars.com|206.127.153.151|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81,466 (80K) [application/zip]

100%[====================================>] 81,466       449.82K/s             

22:45:02 (449.56 KB/s) - `/home/apocrypha/gwsetup.zip' saved [81466/81466]

Archive:  gwsetup.zip
replace GWSETUP.EXE? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: GWSETUP.EXE             
installwine+gw64.sh: 42: wineprefixcreate: not found
mv: target `/home/apocrypha/.wine/drive_c/' is not a directory: No such file or directory
cd: 44: can't cd to /home/apocrypha/.wine/drive_c
installwine+gw64.sh: 45: wine: not found
Build Complete. Wine is ready to go

And above it there are a lot of "No such file or directory" errors: (for a few hundred lines to the top of Terminal)
> /usr/bin/install: setting permissions for `/usr/local/lib/wine/avifil32.dll.so': No such file or directory
make[2]: Leaving directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/avifil32'
make[2]: Entering directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/browseui'
/usr/bin/install -c   browseui.dll.so /usr/local/lib/wine/browseui.dll.so
/usr/bin/install: setting permissions for `/usr/local/lib/wine/browseui.dll.so': No such file or directory
make[2]: Leaving directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/browseui'
make[2]: Entering directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/cabinet'
/usr/bin/install -c   cabinet.dll.so /usr/local/lib/wine/cabinet.dll.so
/usr/bin/install: setting permissions for `/usr/local/lib/wine/cabinet.dll.so': No such file or directory
make[2]: Leaving directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/cabinet'
make[2]: Entering directory `/home/apocrypha/winestuff/wine-0.9.32/dlls/capi2032'


---

### Post by FyreBrand on 2007-03-24
I'm seeing odd artifacts in the distance when I first map to some towns (Kamaden is one) where distant objects have this hazy artifact area around them.  Then it fades.  I'm wondering if this is caused by adding the device.patch (to solve the too many concurrent lights issue) when it wasn't needed.

As much as I'm getting bored of compiling and just want to play (Hey!  It's free FoW/UW weekend!) I'm going to remove wine and recompile it.

On a side note I installed yakuake.  I'm a pretty big fan of the terminal and I love Konsolel.  Yakuake is really nice.  I remapped the hotkey to Super + F12 instead of F12 (this solves a small Guild Wars logout issue).  It's great having the terminal available while in game.

---

### Post by der_joachim on 2007-03-25
> **FyreBrand said:**
> I'm seeing odd artifacts in the distance when I first map to some towns (Kamaden is one) where distant objects have this hazy artifact area around them.  Then it fades.  I'm wondering if this is caused by adding the device.patch (to solve the too many concurrent lights issue) when it wasn't needed.

It's not the lights patch. I run WIne without it, and I see the exact same things.

---

### Post by Jarn on 2007-03-25
I'm back from vacation, I'm updating the scripts right now... I'll upload them when I'm done.

EDIT: I'm using a different 32-bit cursor patch this time should make the cursor look the same way it does on Windows. I'm also changing the way the script works because I decided I want to keep backups of old patches on my website. Azakus, you may need to change where patches are downloaded in your 64-bit script. I'm not sure if you use the ones that I have, but if you do it will need to be changed.

EDIT2: Looking at your scripts, the download path to the patches will need to be changed. Other things will need to be changed also, you may want to look at my script to see some changes I've made. I'd do it myself, but it's your script and I don't know what some of the stuff in there does, so I figure I just won't touch it. ;)

EDIT3: I updated the first post, now.

---

### Post by Ancheron on 2007-03-25
Well, my terminal has been humming along for about 30 minutes now. Thanks for your work on this, Jam. With any luck, I may never touch my windows partition again.

---

### Post by Jarn on 2007-03-25
Good luck. :)

---

### Post by KrackerXIX on 2007-03-25
Okay! here we go. From my old post, here is my updated problem.

I got the graphics working just fine as of now. But the problem is, it is too slow. Way too slow.. like.. 15fps, which is quite slow. Also the sound of course is glitchy. Anyone know whats up?

---

### Post by Jarn on 2007-03-25
The sound can't be helped, I don't think anyone has gotten the sound to work correctly. As to the low fps, I don't know. What are the specs of your computer? Processor, RAM, graphics card? Why weren't the graphics working before, by the way?

---

### Post by KrackerXIX on 2007-03-25
im not sure why they werent workign properly. I made sure Envy installed the newest version by doing it manually, now they work!

There are my complete computer specs! (using a lappy btw Compaq Presario V2000)

Processor Name: Mobile AMD Turion 64 ML-37
Processor Speed: 2 GHz
RAM: 512 MB
Weight: 5.4 lb
Screen Size: 14.1 inches
Screen Size Type: widescreen
Graphics Card: ATI Mobility Radeon XPRESS 200M
Storage Capacity: 80 GB
Networking Options: 802.11g
Primary Optical Drive: DVD+/-RW (Plus Minus)

---

### Post by Jarn on 2007-03-25
I don't know much about Radeon cards and even less about Mobility Radeon cards... is that card decent? 200 is a pretty low number of the Mobility cards are anything like the regular ones.

---

### Post by KrackerXIX on 2007-03-25
I dont know much about the mobility series.. but i do know with windows, i could play the game 100% perfect on near max settings on this thing.

---

### Post by darksong on 2007-03-25
Those spec are much better than mine - on windows this pc easily handles g/w @ 30fps in towns - in linux it 10fps in towns and out of towns it manages 15 fps compared to 40-50ish

Amd Xp 2400 
512 mb ram
Fx5200 128mb 

No matted what i do to wine - req tweaks, graphic tweaks and running in all sorts of settings it won't go over 15fps. 

I personally think it will be solved as wine develops furthers - maybe in 6 months to a year they will have the same performance as windows.

---

### Post by KrackerXIX on 2007-03-25
thought i read it was handled smoothly xP oh well :p

---

### Post by Jarn on 2007-03-25
It does take a performance hit in Wine. It's not much of one, but if you have low-end hardware it can be the difference between it running smoothly and not. For me, I lose about 10 fps. But from 50 to 40, it still plays without lag. Sorry it didn't work out for you, but 15 isn't so bad. For the longest time I played with 5-10... then I got a new computer.

---

### Post by KrackerXIX on 2007-03-25
lol.. well it might be lower than 15 xP... btu meh sometimes its a lil unplayable for me.. like it bugs me! oh well though.. i place FFXI on my desktop.. so im content!

---

### Post by mrcefx on 2007-03-28
I'm having the same probs as darksong. amd xp2500+, 1gb ram, fx5200.
So...maybe a new AGP card or something.

Heh.  Sucks :(

---

### Post by Azakus on 2007-03-28
> **mrcefx said:**
> I'm having the same probs as darksong. amd xp2500+, 1gb ram, fx5200.
So...maybe a new AGP card or something.

Heh.  Sucks :(

Oof, fx5200? Sounds like it's time at least for a 6200. They're dirt cheap right now, most <$100.
[AGP Nvidia Cards on Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+106790703+1069609639&Subcategory=48&description=&Ntk=&srchInDesc=")

---

### Post by falsenames on 2007-03-28
I picked my 6200 up for $40 on Newegg.com.  I don't have a great fps, but it's usually fairly smooth for me.  I'm unfortunately too broke to get a new graphics card, but this one seems to be doing pretty much what I need it to.

---

### Post by Seggybop on 2007-03-28
Hii,

I've been playing the game for a few weeks using the instructions provided here, and it's worked very well. That is, until yesterday. It was going along nicely, and then suddenly the game froze and my hard drive became hyperactive. Rebooting, the game won't load at all anymore; it crashes right away and refuses to even allow itself to close. Its process also seems to be consuming at least 2gb of memory for no apparent reason.

aidplz?

---

### Post by Jarn on 2007-03-28
Does it give an error?

---

### Post by Seggybop on 2007-03-28
There is no error. It does nothing except create a window (but not fill it) and access the hard drive furiously.

---

### Post by Jarn on 2007-03-28
Not even in the terminal?

---

### Post by Seggybop on 2007-03-28
There was no error in the terminal-- it did nothing at all. Very strange.

In any case, I got it working again now... deleted and reinstalled. No closer to understanding what exactly was causing it; hopefully it won't happen again. Thanks for assistance though.

---

### Post by Jarn on 2007-03-29
Congratulations. Sorry I couldn't be of more help.

---

### Post by FyreBrand on 2007-03-29
> **Seggybop said:**
> There is no error. It does nothing except create a window (but not fill it) and access the hard drive furiously.I've had this problem before.  I'm not really sure what triggers it.  My framerate started dropping dramatically and then I was stuck at 0fps and the hard drive just chugging away.

I've read that the GW.dat file is more like a virtually mounted hard drive than just a simple archive file.  I'm guessing that something is getting corrupted or possibly horridly fragmented and Guild Wars just can't recover from it.  It also might have something to do with how EXT3 is setup compared to NTFS since Guild Wars is written for Windows.

Anyway I just thought I would let you know that I've had a similar if not the same problem.

---

### Post by Jarn on 2007-03-29
Good news for everybody... this guide may soon be rendered useless. The concurrent lights error doesn't affect many people and it appears that 32-bit cursors will work in the next version of Wine. [http://article.gmane.org/gmane.comp.emulators.wine.cvs/29196](http://article.gmane.org/gmane.comp.emulators.wine.cvs/29196)

---

### Post by Azakus on 2007-03-29
Hurray! That will cut down on the script's size and complexity. (Not by much, but enough)

---

### Post by Jarn on 2007-03-29
> **Azakus said:**
> Hurray! That will cut down on the script's size and complexity. (Not by much, but enough)It will render my script obsolete. :P

---

### Post by Philderbeast on 2007-03-30
im getting an error compiling wine with this

```
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
winegcc: gcc failed.
make[2]: *** [ddraw.dll.so] Error 2
make[2]: Leaving directory `/home/philbert/winestuff/wine-0.9.33/dlls/ddraw'
make[1]: *** [ddraw] Error 2
make[1]: Leaving directory `/home/philbert/winestuff/wine-0.9.33/dlls'
make: *** [dlls] Error 2
```

anyone able to help me

its a fresh install of 6.10 x64 and i have just installed beryl if that matters.

---

### Post by darksong on 2007-03-30
> **Azakus said:**
> Oof, fx5200? Sounds like it's time at least for a 6200. They're dirt cheap right now, most <$100.
[AGP Nvidia Cards on Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+106790703+1069609639&Subcategory=48&description=&Ntk=&srchInDesc=")

These card are perfectly fine for guildwars :) - its just a little strange why preformance varies so much between the OSes. I have Compiz running on Feisty at the same time this is bieng ran - may this have an effect on the proformance?

---

### Post by Azakus on 2007-03-30
Alright, here's a much cleaner version of the 64-bit script in line with Jarn's

---

### Post by FyreBrand on 2007-03-31
> **Jarn said:**
> Good news for everybody... this guide may soon be rendered useless. The concurrent lights error doesn't affect many people and it appears that 32-bit cursors will work in the next version of Wine. [http://article.gmane.org/gmane.comp.emulators.wine.cvs/29196](http://article.gmane.org/gmane.comp.emulators.wine.cvs/29196)That's really exciting.  We'll be able to install from the repos in no time.  No more compiling, patching and other such stuff.  Sweet!

You deserver a HUGE thank you from everyone here for initiating the effort, taking time to write the howto, and for maintaining it and keeping the research current.

Nice job Jarn!!  If there was still a karma system around here you would definitely get a point from me.

---

### Post by Jarn on 2007-03-31
> **FyreBrand said:**
> That's really exciting.  We'll be able to install from the repos in no time.  No more compiling, patching and other such stuff.  Sweet!I am very much looking forward to it. :D

> **FyreBrand said:**
> You deserver a HUGE thank you from everyone here for initiating the effort, taking time to write the howto, and for maintaining it and keeping the research current.

Nice job Jarn!!  If there was still a karma system around here you would definitely get a point from me.It wasn't a big deal, I was doing the stuff anyway. All I did that I wouldn't normally have done was to type it up, which is certainly not a big deal. Thanks, though. :)

Hey, are any of you in a guild that does stuff often? Preferable PvP? I'm considering leaving my current guild... I know the people well, but we don't really do much as a guild and I love to PvP. I'd love to get into GvG, but my guild hasn't done it in probably a year.

I'm so looking forward to Guild Wars 2... I'm not sure I can wait two years for it! I may die of impatience! ;)

---

### Post by Azakus on 2007-03-31
0.9.34 is out now.
Looks like the patches are unnecessary.
I'll post the full 64-bit script without the patches if it works for me.

---

### Post by Flyser on 2007-03-31
I hate GW2 :( I hope the Community of GW will not die after the release!
All this stuff like open level-end, ... *yuck*
And the Enigine will change -> maybe again not working with wine

---

### Post by Philderbeast on 2007-03-31
I'm currenly installing 0.9.34 on 6.10 i386 so ill let you know how it goes unpatched.

edit: confirmed no need to patch with wine 0.9.34 :)

YAY!

---

### Post by cor2y on 2007-03-31
yes the latest wine 0.9.34 requires neither the mouse or light patch for guildwars also runs at full speed.
The audio is a bit still off but it works and runs smooth.

---

### Post by FredDie3785 on 2007-03-31
Is it running at full speed because the W.I.N.E is optimized or you have uber machine:P??
What about crashes?? Do they occur??

---

### Post by Azakus on 2007-03-31
Alright, GW works without patches.
Here's the full 64-bit script for your viewing pleasure.
```
#/bin/bash
#This is a 64-bit only compile of WINE + Guildwars mouse hack
#Includes a script to build a 32-bit libsicuuc.a
VERSION=0.9.34
sudo aptitude install patch libc6-i386 libc6-dev-i386 checkinstall lib32asound2-dev libasound2-dev libjack0.100.0-dev libfreetype6-dev libfreetype6
mkdir ~/winestuff
cd ~/winestuff
wget http://umn.dl.sourceforge.net/sourceforge/wine/wine-$VERSION.tar.bz2 -O ~/winestuff/winesource.tar.bz2
wget http://kegel.com/wine/edgy.sh -O ~/winestuff/pkgs.sh
sudo sh ./pkgs.sh
tar -xjvf winesource.tar.bz2
cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so
#Creates 32-bit libsicuuc.a
echo "Creating 32-bit libsicuuc.a"
cd ~/winestuff
wget ftp://ftp.software.ibm.com/software/globalization/icu/3.6/icu4c-3_6-src.tgz
tar zxvf icu4c-3_6-src.tgz
cd ./icu/source
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc -m32" CXX="g++ -m32" ./configure
make
ar t /usr/lib/libsicuuc.a | sed -e 's/ao$/o/' | perl -e 'while(<>){ chomp($_); print "find . -name $_ | xargs ar ruv libsicuuc.a\n"; }' > mkar.sh
sh mkar.sh
sudo cp libsicuuc.a /usr/lib32/
cd ~/winestuff/wine-$VERSION
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
echo "Adding necessary 64-bit files"
make depend
make
sudo checkinstall
wget http://www.guildwars.com/downloads/gwsetup.zip -O ~/gwsetup.zip
cd ~
unzip gwsetup.zip
wineprefixcreate
mv ~/GWSETUP.EXE ~/.wine/drive_c/
wine "C:\\GWSETUP.EXE"
echo "Build Complete. Wine is ready to go"

```

---

### Post by cor2y on 2007-03-31
I don't know about an uber machine.

By today's standards my machine is old

Athlon XP 2500
1 gb ddr PC2700 ram
ATI 9600XT
80 gb 7200 rpm Samsung HD

As for wine i didn't optimize anything the past two realeases came from the Synaptic universe repo.
I haven't custome compiled since 0.9.32

---

### Post by der_joachim on 2007-04-01
My experience with wine is similar to the descriptions above: -10 fps compared to Windows XP   (30 to 20 with highest options on my spanking new GF7600GS), and choppy sound even when fully turned off (:?: ). I do not need any patches anymore.

---

### Post by Factory on 2007-04-01
Still awaiting a solution to running at 1 FPS with a 9600 Radeon Pro (128). 

Good news about the new version though! Progress!

Edit: Turned down the quality to low and none on everything. I'm now getting slightly below 10 FPS which is still bad, but still playable! =D

---

### Post by Azakus on 2007-04-01
Try these Registry settings. Bumped my framerates up by around 10.
(Save this as a .reg file and import it in regedit)
```
REGEDIT4



[HKEY_CURRENT_USER\Software\Wine\Direct3D]

"DirectDrawRenderer"="opengl"

"OffscreenRenderingMode"="backbuffer"

"opengl"="enabled"

"RenderTargetLockMode"="auto"

"UseGLSL"="enabled"

"VideoMemorySize"="256"


```

---

### Post by cor2y on 2007-04-01
i only get 10 fps or less when i am in the login and character screens in guildwars.
When i am actually playing it runs at 20-26 fps, on windows it usually ran at 56-60 fps.

---

### Post by Flyser on 2007-04-01
Mh 0.9.34 works fine now, but I still need the lights-patch?! Am I the only one who still needs it?

To test this it seems that the Jin Jea Monastry is the best place to do it (Factions/Cantha Tutorial) just walk around the city, while looking around. If your GW locks up you will need the patch

---

### Post by Factory on 2007-04-01
> **Azakus said:**
> Try these Registry settings. Bumped my framerates up by around 10.
(Save this as a .reg file and import it in regedit)
```
REGEDIT4



[HKEY_CURRENT_USER\Software\Wine\Direct3D]

"DirectDrawRenderer"="opengl"

"OffscreenRenderingMode"="backbuffer"

"opengl"="enabled"

"RenderTargetLockMode"="auto"

"UseGLSL"="enabled"

"VideoMemorySize"="256"


```

What is this even supposed to do. I personally noticed absolutely nothing. A little explanation as to what a registry file will do would help :p.

---

### Post by Azakus on 2007-04-01
> **Factory said:**
> What is this even supposed to do. I personally noticed absolutely nothing. A little explanation as to what a registry file will do would help :p.

Those registry entries make WINE use OpenGL to render files instead of the buggier GDI32, at the expense of some compatibility (or so I've heard). Earlier posts here have more detail. I'll dreg those up.
[http://ubuntuforums.org/showpost.php?p=2240683&postcount=231](http://ubuntuforums.org/showpost.php?p=2240683&postcount=231)
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by rillip on 2007-04-02
I got it running with the script, and I got roughtly the same performance, but I had a lot of trouble with rendering.  With things on auto detect (medium setting) I'd get flashes of unrendered ground, jumpy blocks, etc. Turned down to low this reduced to near zero, still very playable.  But after a while of playing (no specific time) things that were working would stop rendering.  The ground, just about every enemy, some armors, etc.  Mostly outside of town.  It made the game no fun to play - you can only kill so many enemies that are just white manikans before you get bored.  Did anyone else experience this?  Does the new version of Wine make it any better?

---

### Post by Factory on 2007-04-02
> **rillip said:**
> I got it running with the script, and I got roughtly the same performance, but I had a lot of trouble with rendering.  With things on auto detect (medium setting) I'd get flashes of unrendered ground, jumpy blocks, etc. Turned down to low this reduced to near zero, still very playable.  But after a while of playing (no specific time) things that were working would stop rendering.  The ground, just about every enemy, some armors, etc.  Mostly outside of town.  It made the game no fun to play - you can only kill so many enemies that are just white manikans before you get bored.  Did anyone else experience this?  Does the new version of Wine make it any better?

Simply 'yes'. With every new release of Wine Guild Wars seems to run better.

Hopefully we'll be at 100% conversion... I'm half-expecting version 1.0 to do this.

---

### Post by Zaiden on 2007-04-02
I have the latest version of wine, and installed Guild Wars. When the game starts up, it goes very, very slow, getting to the point where I can't even exit out normally. My system is somewhat old, but with the settings low, it could run guild wars without a huge problem.

Is there anything I could do to fix this?

---

### Post by falsenames on 2007-04-04
I seem to be experiencing the same slowdown issue.  I can play for maybe 10 minutes before the game grinds to a halt.

---

### Post by Flyser on 2007-04-05
Today I was testig around with various windows-versions (in the winecfg-menu) and was very surprised, that there was a difference between the fps I got. Here a list of the fps on one scene (Guildhall):

Win2.0 : 57
Win3.0 : 57-58
Win3.1 : 58-59
WinNT3.5 : 57-58
WinNT4.0 : 56-57
Win95 : 57
Win98 : 57
WinME : 57
Win2000 : 57
WinXP : 58
Win2003 : 57

I am using Win3.1 now. And I can recommend the tool "rovclock" which allows over- / underclocking of ati-cards, very usefull for me.
I recently tried the open source radeon drivers (r300 for me) and got it working (with not that good performance and graphic errors, but it is working) If you just start GW without changing anything to your system it will use software rendering. You will have to install the tool driconf, start it and switch off the "fallback anything" button and disable the first button on the next page. Then GW will run with hardware rendering

---

### Post by Zuuswa on 2007-04-05
I would suggest lowering the direct x level for better perfomance (it has probably been mentioned before on this thread, but I haven't the time nor patience to read 40 pages of posts)

simply append -dxlevel xx (where xx = the directx level, for instance to use level 7 you would type in 70, for 8 it would be 80)  It will most definately reduce image quality, but will have a much better fps.  Using standard settings I only had around 1fps, which is rediculously unplayable, whereas using dx7 I get 20-25 fps for the login screen (I just installed it, and am waiting to get to a playable area)

---

### Post by xixsixxix on 2007-04-06
Well, all was going well until Thursday's (April 5) update. Now apparently a lot of people can't load the game.

I've now tested on 4 systems (4 different intel processors) now using both Ubuntu Edgy and Debian Etch/Sid with both nVidia (6800GTOC, 7900, Go 7400) and onboard Intel cards with both Wine 0.9.31 and 0.9.34 using the nVidia 1.0-9631 and 1.0-9746 drivers as well as the standard i810 for the onboard -- I get a bit thorough when my GW stops working, lol.

So far the only working combination I have is 0.9.31 on the Celeron with the GeForce 7900 using 1.0-9746 drivers on a Debian 2.6.18-4-686 (etch) stock kernel.

Posted to the AppDB board as well. Hopefully it will be resolved soon.

---

0.9.31 errors/fixmes:

err:dbghelp:elf_load_debug_info_from_map Bad CRC for module (got 456eb58f while expecting 5eb0e104) 
fixme:dbghelp:SymInitializeW what to do ??
...repeat back and forth indefinitely...

---

0.9.34 errors/fixmes:

err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b30e80) : stub
fixme:dbghelp:SymInitializeW what to do ??
...repeat the dbghelp fixme indefinitely...

---

### Post by ObiWan2001 on 2007-04-06
GuildWars changed it's sound engine.
Just start the game with -nosound.

---

### Post by Zuuswa on 2007-04-06
hm yes today when I try to load GW it hangs at the loading splash "Connecting to Arenanet" after downloading files . . . then it continues to devour my remaining ram and swap until I cant do anything on my system . . . anyone else having this problem?  I am going to report it to AppDB as well

---

### Post by Jarn on 2007-04-06
I'm not having this problem. I'm still playing the same as before with and without -nosound.

---

### Post by Zuuswa on 2007-04-06
the -nosound flag is not working for me, it still does not load.  It was working yesterday, and now nothing :( just my luck to have the devs break the game right after I install it.

..::EDIT::..  someone over at the winehq forums said that yesterday's update also caused Windows clients to crash, but another release was put out that was 'supposed' to fix it, so maybe its not an issue with wine at all, just bad game code

---

### Post by FyreBrand on 2007-04-07
Here are some new command line switches for sound when starting the game.  I ganked these from a post on gwonline.net.

**Command-line Options Summary:**
[INDENT]-sndasio : attempts to use an ASIO driver in software mode
-sndwinmm: attempts to use the Windows Multimedia audio driver in software mode
-dsound : forces use of old DirectSound software mixer.[/INDENT]

---

### Post by cor2y on 2007-04-07
Just did the update, the main character/login screen still running at 9-10 fps.
upon entering a town i lost my cursor i had to move it outside of the wine screen before it came back.

I haven't experienced any lockups so far max fps 35 min fps 9-10

---

### Post by xixsixxix on 2007-04-07
Alright, so with the -dsound option we can get it back to working as it was before (woohoo!)

However, it ends up the "Too many concurrently active lights" issue is not completely resolved as of yet.  It doesnt happen in nearly as many areas as before, but I still managed to get it here and there with Kaineng Center and repeatedly with Shing Jae Monastery.

Same patch scheme as we've been using since 0.9.31 works for 0.9.34 with new line numbers so I'm just dropping in a quick lighting error patch file for those that still need it. =)

As usual the patch applies to **dlls/wined3d/device.c**

---

### Post by xixsixxix on 2007-04-07
Another quick note -- as of the thursday update, attempting to save skill templates can cause the game to lock up or crash.  In my experience this doesnt actually throw any errors, it just stops.

For anyone else experiencing the problem, a temporary workaround is to Ctrl+Click your skill bar in a town/outpost to display your "My equipped skills are..." message to the chat, then click the chat link and copy the template code manually to a .txt file in your GW Templates/Skills directory.  This works fine since the templates window now reloads the list every time it is opened.

---

### Post by Zuuswa on 2007-04-07
none of the -sound flags work for me, I am still unable to load the game :(.  Any suggestions?

---

### Post by Jarn on 2007-04-07
You could try turning sound off in Wine... uncheck all of the types in the Audio tab in winecfg. I don't know if that will help, but it's worth a shot.

---

### Post by Zuuswa on 2007-04-08
hey that actually worked!!!  Thanks Jarn!!  If only the -nosound option worked, I wouldnt have to change the options in winecfg everytime I want to play a differant game, as I would still like sound to work in counterstrike.  Oh well.  I do wonder why those flags werent working though, it seems that wine was just completely ignoring those switches.

---

### Post by mrThefter on 2007-04-08
actually, I remember reading about problems with using the ALSA sound driver with guildwars/wine. Use OSS, instead.

Curious, though, was that my message you saw on the winehq forums?

---

### Post by Jarn on 2007-04-08
> **Zuuswa said:**
> hey that actually worked!!!  Thanks Jarn!!Your welcome. I was just guessing, I'm glad it worked for you. :)

---

### Post by FredDie3785 on 2007-04-10
I've got question for you guys.

On which drivers WINE+GW will work better, with opensource or non-free drivers??

---

### Post by Brynster on 2007-04-10
I got guildwars working 95% in wine 0.9.34

did the install everything worked, added the flags -dxlevel 80 -noshader -nosound got a huge performance improvement

the down side is random textures ie coloured blocks that fade into what they should be when you get a little closer (nothing major trees and buildings etc). and a strange cloured patch work underneath my charecter looks like a patchwork quilt.

Thats its fully playable no zone lag or waiting a few seocnds for the cursor to reapear etc. roll on wine 0.9.35 lets see if we can sort the niggles out further!

---

### Post by Azakus on 2007-04-10
To get rid of that colored patch, turn off shadows in Guild Wars.

---

### Post by Brynster on 2007-04-11
excellent....

Switched shadows off as per advice and patchwork disappears many thanks.  :-)

---

### Post by calcium79 on 2007-04-11
Okay I'm using Wine 0.9.34 and Ubuntu Edgy and I have a problem with the mouse - I can't rotate left using the mouse. What happens is as soon as I right click the mouse immediately goes to the top left corner. Earlier on, I was in fact using the old 32-bit mouse hack so is this possibly a result of using that?
Any suggestions?

---

### Post by Jarn on 2007-04-11
> **calcium79 said:**
> Earlier on, I was in fact using the old 32-bit mouse hack so is this possibly a result of using that?Unless by earlier on you mean when you were still using version 0.9.34 (which I doubt since 0.9.34 comes with it), AFAIK it can't be. Beyond that, I have no idea.

---

### Post by AndrewRiedi on 2007-04-11
> **calcium79 said:**
> Okay I'm using Wine 0.9.34 and Ubuntu Edgy and I have a problem with the mouse - I can't rotate left using the mouse. What happens is as soon as I right click the mouse immediately goes to the top left corner. Earlier on, I was in fact using the old 32-bit mouse hack so is this possibly a result of using that?
Any suggestions?

You correctly spotted the issue as a mouse (ie. input problem).  However, the the 32-bit cursor patch fixes cursor issues, not mouse issues (ie. a rendering problem).  I am afraid that would be a regression.  Using the patch on page 1 here only alters the rendering, not the position.  Are you sure you use wine 0.9.34?  wine --version    will display it for you (in a terminal).  Anyhow, please file a bug report on bugs.winehq.org if this continues, or at least post here and I will transfer the information over if/when I get time.

Hope I can help you more, but I need more information first.

---

### Post by thom_raindog on 2007-04-12
> **mrThefter said:**
> actually, I remember reading about problems with using the ALSA sound driver with guildwars/wine. Use OSS, instead.

Curious, though, was that my message you saw on the winehq forums?

GW works for me. Provided I either use -nosound or set wine to use oss.
In either case, the game is completely mute, no sound at all...
Is that how it is supposed to be?

How would I use oss in wine AND get to hear the game sound?

---

### Post by AndrewRiedi on 2007-04-12
> **thom_raindog said:**
> GW works for me. Provided I either use -nosound or set wine to use oss.
In either case, the game is completely mute, no sound at all...
Is that how it is supposed to be?

How would I use oss in wine AND get to hear the game sound?

You try with just -dsound instead of -nosound and with OSS and/or ALSA?

PS:  I do not play GW, so I can only be of minimal help, but I do work on wine when I get time.

---

### Post by thom_raindog on 2007-04-12
I just tried using Alsa and -dsound. And indeed: 
I have sound!

No combat sound, though, but still. That's a lot better.. now if only I had combat sound...

---

### Post by AndrewRiedi on 2007-04-12
> **thom_raindog said:**
> I just tried using Alsa and -dsound. And indeed: 
I have sound!

No combat sound, though, but still. That's a lot better.. now if only I had combat sound...

Combat sound is still broken.  Sorry.  Hopefully [[COLOR="Blue"]this[/COLOR]]("http://code.google.com/soc/wine/appinfo.html?csaid=1804A40297BFD0B2") will fix it.

---

### Post by thom_raindog on 2007-04-13
Aha... sad, but ok. Thanks for the info.

Question: When using standard-wine from the ubuntu-repos, how can I add the patch for the "too many lights" problem?

---

### Post by AndrewRiedi on 2007-04-13
> **thom_raindog said:**
> Aha... sad, but ok. Thanks for the info.

Question: When using standard-wine from the ubuntu-repos, how can I add the patch for the "too many lights" problem?

You can't.  A patch changes the source code, and thus you must compile from source for a patch to actually do anything.

If you have a patch I would just recommend grabbing the source and patching it, then compiling it, but not installing it.  With wine, you can just run it from the directory without installing.  This way you can have the ubuntu wine and your patched wine both on the same computer.  Then, once you don't need the patched wine anymore, just delete the directory.

---

### Post by calcium79 on 2007-04-13
> **AndrewRiedi said:**
> You correctly spotted the issue as a mouse (ie. input problem).  However, the the 32-bit cursor patch fixes cursor issues, not mouse issues (ie. a rendering problem).  I am afraid that would be a regression.  Using the patch on page 1 here only alters the rendering, not the position.  Are you sure you use wine 0.9.34?  wine --version    will display it for you (in a terminal).  Anyhow, please file a bug report on bugs.winehq.org if this continues, or at least post here and I will transfer the information over if/when I get time.

Hope I can help you more, but I need more information first.

wine --version displays 0.9.37, but dpkg -l wine shows 0.9.34~winehq0.
It's odd because it worked before... but when they introduced that massive patch that among other things introduced the new audio that made me have to turn off the ALSA driver in Wine, that's when things got really wonky. The mouse acted a little oddly even before that, to tell the truth, but now it'll disappear (which is expected in Guild Wars) and completely refuse to move left, that is, right click + move the mouse left is meant to pan the camera left, but it doesn't. When the right mouse button is released, it always ends up in the same place - in the top left corner of the screen. Oddly enough, when I move the mouse to the right after holding the right mouse button down, it works (kinda) Sometimes it overreacts when I do this.

---

### Post by Flyser on 2007-04-14
Did any1 tried 0.9.35 yet? changes to the lights-problem? cursor broken again? or maybe even combat sound?

---

### Post by cor2y on 2007-04-14
yes the cursor seems to have vanished again.
the audio problem still exists but the visual errors appear to be gone in this update of wine.

---

### Post by Azakus on 2007-04-14
Well, looks like this thread gets to keep living after all.
With version 0.9.35, Guild Wars doesn't even start for me.
I launched from Terminal and it kept throwing me this error:
```
fixme:dbghelp:SymInitializeW what to do ??
```
EDIT:
Ooh, found a fix
Run Guild Wars with -dsound and the sound issues disappear!
Example:
```
wine "E:\\Guild Wars\\Gw.exe" -dsound
```

---

### Post by Azakus on 2007-04-15
> **cor2y said:**
> yes the cursor seems to have vanished again.
the audio problem still exists but the visual errors appear to be gone in this update of wine.

Yes, there was a reversion in Xcursor support documented in AppDB
[http://appdb.winehq.org/appview.php?iVersionId=7530](http://appdb.winehq.org/appview.php?iVersionId=7530)

---

### Post by thom_raindog on 2007-04-15
To get rid of the "...too many lights..." problem I tried kompiling wine myself instead of using ubuntu-repos.
As a result, GW refused to even start, claiming my grafic card would not meet the requirements...

How would I get rid of that?

---

### Post by chek2fire on 2007-04-15
> **Azakus said:**
> Well, looks like this thread gets to keep living after all.
With version 0.9.35, Guild Wars doesn't even start for me.
I launched from Terminal and it kept throwing me this error:
```
fixme:dbghelp:SymInitializeW what to do ??
```
EDIT:
Ooh, found a fix
Run Guild Wars with -dsound and the sound issues disappear!
Example:
```
wine "E:\\Guild Wars\\Gw.exe" -dsound
```

I have the same problem :( with the same message and at the end i get this message 
fixme:dbghelp: SymInitializeW what to do ??
fixme:dbghelp: pool_alloc OOM
fixme:dbghelp: SymInitializeW what to do ??
fixme:dbghelp: pool_alloc OOM
storage.c:365: hash_table_init: Assertion `ht->buckets' failed.
err:seh:setup_exception stack overflow 24 bytes in thread 000b eip b7de554f esp 7bcdefe8 stack 0x7bcdf000-0x7bdef000
[email]spiros@spiros-desktop:~/.wine[/email]/drive_c/Program Files/Guild Wars$

---

### Post by cor2y on 2007-04-15
Looks like for the best bet is at present to stick with 0.9.33 or 0.9.34 if you have no problems, rather than upgrade.

---

### Post by Flyser on 2007-04-15
I tested wine 0.9.35 and have absolutely no problem, the cursor is visible and some graphic-bugs vanished. But the lights-patch is still needed.

Anyway I tried to run gw in dx9 mode, but it doesnt work it always said dx8 ... What switches do I have to enable for dx9 or dx7?

---

### Post by chek2fire on 2007-04-15
can you tell me your wine settings?

edit:
i fixed it :)
i try this command wine "address" nosound and it works but i have some problems with performance

---

### Post by Jarn on 2007-04-15
> **Flyser said:**
> Anyway I tried to run gw in dx9 mode, but it doesnt work it always said dx8 ... What switches do I have to enable for dx9 or dx7?
I believe that is related to the version of Windows that Wine is set to emulate. I think if it's not an NT version, GW usues dx8.

---

### Post by Azakus on 2007-04-15
> **chek2fire said:**
> I have the same problem :( with the same message and at the end i get this message 
fixme:dbghelp: SymInitializeW what to do ??
fixme:dbghelp: pool_alloc OOM
fixme:dbghelp: SymInitializeW what to do ??
fixme:dbghelp: pool_alloc OOM
storage.c:365: hash_table_init: Assertion `ht->buckets' failed.
err:seh:setup_exception stack overflow 24 bytes in thread 000b eip b7de554f esp 7bcdefe8 stack 0x7bcdf000-0x7bdef000
[email]spiros@spiros-desktop:~/.wine[/email]/drive_c/Program Files/Guild Wars$

Run guildwars with -dsound outside of the quotes.
Ex: wine "C://pathtogw//Gw.exe" -dsound

---

### Post by cor2y on 2007-04-15
Flyser ,how did you get your cursor visible?
In a custom compile i can't add the mouse32 patch and simply compiling or using 0.9.35 from  the repos resulted in no  ingame mouse cursor what i did get was a cursor if i moved outside the wine borders and moved back quickly into it.

---

### Post by Flyser on 2007-04-15
I didn't do anything, just using the clean gentoo-ebuild with the lights-fix

---

### Post by Jarn on 2007-04-15
> **Flyser said:**
> I didn't do anything, just using the clean gentoo-ebuild with the lights-fixDid you see what I said about DirectX in reply to your previous post? And did it help?

---

### Post by chek2fire on 2007-04-15
> **Azakus said:**
> Run guildwars with -dsound outside of the quotes.
Ex: wine "C://pathtogw//Gw.exe" -dsound

it works only if i run it with this -nosound

---

### Post by AndrewRiedi on 2007-04-15
There is a problem with the Ubuntu package.  I just checked the 0.9.35 source code, and it still has my (Xcursor) code in it.  Note, this also explains why the other Gentoo user here had no problem with 0.9.35.  If you custom compile wine-0.9.35 (no need for patching it) it should work just fine, so long as it can find Xcursor on your system.  Anyhow, I wrote the code so that if it cannot find Xcursor, it just reverts to the legacy code (code prior to 0.9.34).  I will also attempt to update the legacy code to also support 32-bit cursors for 0.9.36 incase something like this happens again, but no guarantees.

Short version:  The cursor problem is known, and is being worked out.

Sorry about all this, and I will see what I can do.  -- Andrew

---

### Post by Azakus on 2007-04-15
I've set up a repository on my own server for the amd64 package of WINE (and for Audacious Media Player).

Add this to your repo if you want it:
```
deb http://azakusfiles.homelinux.net/ /
```

---

### Post by thom_raindog on 2007-04-16
@Andrew: Are you saying, if I were to use the source code from winehq and patch the light patch, I should be seeing a mouse pointer again? Provided I have Xcursor (Is that a package I can install using apt-get? I am at work right now and can't check...)?

---

### Post by Jarn on 2007-04-16
The guy who does the Ubuntu packages posted saying there was a bug and he uploaded a new one. If you get the packages again, it should have the cursor.

---

### Post by AndrewRiedi on 2007-04-16
> **thom_raindog said:**
> @Andrew: Are you saying, if I were to use the source code from winehq and patch the light patch, I should be seeing a mouse pointer again? Provided I have Xcursor (Is that a package I can install using apt-get? I am at work right now and can't check...)?

Yes, that is exactly what I am saying.  Please install libxcursor-dev though to make Wine know that you have Xcursor at compile-time.

---

### Post by thom_raindog on 2007-04-17
Ok, I installed lixcursor-dev. My already installed wine 0.9.35 still didn't have a cursor. So I used
```

sudo apt-get install wine=0.9.34.....
```
to get 0.9.34 back. That did the trick, I have a cursor (I  do have to rightclick after entering a zone, though, but that's alright)

If I were to upgrade to 0.9.35 I should still have the cursor, right?

---

### Post by AndrewRiedi on 2007-04-17
> **thom_raindog said:**
> Ok, I installed lixcursor-dev. My already installed wine 0.9.35 still didn't have a cursor. So I used
```

sudo apt-get install wine=0.9.34.....
```
to get 0.9.34 back. That did the trick, I have a cursor (I  do have to rightclick after entering a zone, though, but that's alright)

If I were to upgrade to 0.9.35 I should still have the cursor, right?

Only if you compile it by hand.  If you use a borked package, it won't work.

---

### Post by thom_raindog on 2007-04-17
Well, just for curiosities sake I installed 0.9.34 from the repos.
I have a cursor when I rightclick...
So I would have to compile a 0.9.35 including the light patch for the (right now) best playing experience?

---

### Post by YokoZar on 2007-04-17
All right, I fixed the 0.9.35 package to include libxcursor-dev.

**Run apt-get update and upgrade Wine to the latest package and the cursor issue that broke with earlier edgy 0.9.35 packages should be fixed**.

---

### Post by AndrewRiedi on 2007-04-17
> **thom_raindog said:**
> Well, just for curiosities sake I installed 0.9.34 from the repos.
I have a cursor when I rightclick...
So I would have to compile a 0.9.35 including the light patch for the (right now) best playing experience?

If you need the light patch, yes.  However, I talked to the Wine packager, and he said that he fixed the Xcursor problem now.  :)

---

### Post by chek2fire on 2007-04-18
today after the last wine update they fix the problem wtih the cursor
i have one more question :popcorn: .why i can play the game only with window 98 settings?with windows xp setting i have too many problems :( 
any idea ?

---

### Post by Azakus on 2007-04-18
> **chek2fire said:**
> today after the last wine update they fix the problem wtih the cursor
i have one more question :popcorn: .why i can play the game only with window 98 settings?with windows xp setting i have too many problems :( 
any idea ?

Win XP is not as well supported as 98 (different driver versions and compatibility code, I think). I use Windows 2000, which works pretty well for me.

---

### Post by thom_raindog on 2007-04-20
Ok.. I tried about every concievable variation of this and found:
The only way I get to play GW is using wine 0.9.34 from the winehq-ubuntu repos.
compiling 0.9.35 I dont get a mouse, using 0.9.35 from the repos I get no mouse...

in 0.9.34 I to at least get the mouse after wiggling it around when entering a zone...
That my be a pest, but at least it can be worked out..

---

### Post by chek2fire on 2007-04-20
my problems with the game now
first is the sound.is very bad and i get this message
err:dsound:DSOUND_MixInBuffer length not a multiple of block size, len = 4946, block size = 4
another problem is the performance with windows 98 settings
i try to play the game with windows xp and windows 2000 settings.. but look..
[IMG][[IMG]http://img224.imageshack.us/img224/5518/gw3gl8.th.png[/IMG]](http://img224.imageshack.us/my.php?image=gw3gl8.png)[/IMG]
the flying buildings :lolflag: 
any idea?

---

### Post by thom_raindog on 2007-04-22
I had just had the same problem.
Setting the quality to 44100 and 16 Bits in winecfg solved that.
I also have "emulation" activated

---

### Post by Mblackwell on 2007-04-22
Btw, what settings are people playing this game with? I'm using WinXP so I can use DX9 shaders, and in the last release of Wine shadows (except low quality ones) are pretty borked. Also performance sucks (17fps average, sometimes lower), and maybe it would be fine if I used DX8.1, but it's hard to want to give up the pretty bloom and haze effects that add a good amount of atmosphere.

Oh, and I noticed the water in the distance at the login screen doesn't render correctly. This has been the same for every version of Wine I've used.

---

### Post by chek2fire on 2007-04-22
i have the same problem i cant find a solution

---

### Post by anasofiapaixao on 2007-04-23
> **Mblackwell said:**
> Btw, what settings are people playing this game with? I'm using WinXP so I can use DX9 shaders, and in the last release of Wine shadows (except low quality ones) are pretty borked. Also performance sucks (17fps average, sometimes lower), and maybe it would be fine if I used DX8.1, but it's hard to want to give up the pretty bloom and haze effects that add a good amount of atmosphere.

Oh, and I noticed the water in the distance at the login screen doesn't render correctly. This has been the same for every version of Wine I've used.

You're better off than I am. Guild Wars doesn't run *at all* since I've upgraded to Feisty, tried to reinstall several times, tried to compile wine by hand - tried everything but still nothing. The gibberish it spits out is along these lines:
```
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"szCatName", 0x33f2d4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"szClsidCat", 0x33f2d4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"szName", 0x33f2d4)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: Analog Devices AD1981B"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"szClsidFilter", 0x33f2d4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"szName", 0x33f2c4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"dwMerit", 0x33f2c4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"dwInputs", 0x33f2c4)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x21cd20, L"dwOutputs", 0x33f2c4)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {fbf6f530-07b9-11d2-a71e-0000f8004788} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({fbf6f530-07b9-11d2-a71e-0000f8004788}) pEnum((nil))
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1bb7b8, L"DxDiag_DirectShowFilters", 0x21cd20)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x1bb7b8, L"DxDiag_DisplayDevices", 0x33f3ac)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x21ca30, L"0", 0x33f3a8)
fixme:dbghelp:SymInitializeW what to do ??

```

Does anyone else have the same problem?

---

### Post by Flyser on 2007-04-23
try running guildwars with the -dx8 flag

---

### Post by anasofiapaixao on 2007-04-23
It's not a problem of the DirectX version, for I have tried with seven and eight, tried the -noshaders flag... The installation doesn't end succefully (bla bla bla it's not able to continue, send a report to ArenaNet, etc) and when I try to run the program I get that output and a nice memory leak. It is strange no one else is having this kind of problem... Before upgrading it was working, randomly crashed/freezed from time to time but nothing more than that.

---

### Post by Abss1185 on 2007-04-23
Hi i tried the automated install and the other scripts by Autozak(srry if i spelt name wrong) and when i run GW(it shows the loading screen,says 100%) i get a weird debug script could someone tell me what the problem is? AMD 64 Turion 
expecting ad1ec702)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 06ece15d while expecting d89525da)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 89460e5c while expecting 9fc49373)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got a2e316ff while expecting 75824337)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 711795e7 while expecting 7458f7f5)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 013de68a while expecting d7e7fbee)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got ec9054f5 while expecting ade2d2d4)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 8b691573 while expecting 5ccd22a3)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 880f4bc2 while expecting 26b7de51)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 76f000d4 while expecting 5e9ad156)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got baf17e76 while expecting 8db9f7ac)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 9b63f623 while expecting 3d4fa456)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 9c88c6a5 while expecting b8c4b469)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 8eb47a6d while expecting 1b3e5bed)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 6d336127 while expecting d1274ddb)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 09764fdf while expecting 2abf7b2e)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 3d186dc0 while expecting 367d2f9e)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got a206cfc4 while expecting eeb9a1a6)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 860bf0d9 while expecting 753f95e9)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 024681c6 while expecting e2e6faf1)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 445d6274 while expecting 338745a4)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 9b4963ed while

More to it same stuff but you get the point plz help ;)

---

### Post by Azakus on 2007-04-24
Try adding  WINEDEBUG=-all to the launcher.

---

### Post by Abss1185 on 2007-04-24
No says couldnt start process i added it to the front of launcher dont know if thats right thx though. Any other solutions?

---

### Post by Mblackwell on 2007-04-24
kill the process (CTRL+C) and launch it again. Usually it will run for me, sometimes it takes a couple tries. I don't know what causes it.

---

### Post by Abss1185 on 2007-04-24
No good but thx for the help anyway.

---

### Post by Mblackwell on 2007-04-24
Make sure Compiz/Desktop-Effects is turned off.

---

### Post by Abss1185 on 2007-04-25
Still no good i get these 3 lines before he debug errors dont know what it is.
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x10e1a78) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x10e1f18) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x10e23b8) : stub
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 6db8a8fb while expecting d152a725)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got e6799640 while expecting 95dbe11e)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 1a158591 while expecting 47aa0767)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got f6d26009 while expecting ad1ec702)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 06ece15d while expecting d89525da)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 89460e5c while expecting 9fc49373)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got a2e316ff while expecting 75824337)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 711795e7 while expecting 7458f7f5)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 013de68a while expecting d7e7fbee)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got ec9054f5 while expecting ade2d2d4)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 8b691573 while expecting 5ccd22a3)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 880f4bc2 while expecting 26b7de51)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 76f000d4 while expecting 5e9ad156)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got baf17e76 while expecting 8db9f7ac)
err:dbghelp:elf_load_debug_info_from_map Bad CRC for module  (got 9b63f623 while expecting 3d4fa456)
plz help ill give you a minipet in game if you help me lol

---

### Post by Abss1185 on 2007-04-25
NVM IT WORKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! But i got no sound and on the login screen the water isnt there so i see a fish just swimming. Thx for all your help srry i ask for so much help also =D

---

### Post by chek2fire on 2007-04-25
...and the half buildings,rocks,trees..:lolflag:

---

### Post by Abss1185 on 2007-04-25
ya lol, anyway Mblackwell you whole restart thing worked so thx but i was wondering is there a way to make it so you don have to keep trying over and over again thx ;)

---

### Post by maaylix on 2007-04-25
Well here is yet another person who is having trouble running GW on his Ubuntu.

Here are my specs:

Athlon XP 3000+
512 mb of ram
Radeon 9600 Pro 128meg
Ubuntu 6.10
Wine 0.9.35

fglrxinfo output is:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6400 (8.35.5)

I installed Guild wars by simply downloading the client from guildwars.com, unziping and running the installer with wine.

Installation went fine, the ''base'' files downloaded decompressed, but when all that was finished, and the game was actually supposed to load, wine just seems to freeze, I see my hd led working like crazy and then suddenly stopping. I wait a bit more and decide it's time to force quit, I do that and my pc continues to be very unresponsive and only a reboot solves the problem.

I've tried  Win 98, 2000 and Xp modes, none seem to have different results. I've tried to emulate smaller virtual desktops (down to 800x600) and canceling the ''emulate virtual desktop'' option altogether. I messed around with this switching on and off with the rest of the graphics options. Nothing seems to have any effect, wine always ends up crashing after the downloader has finished downloading/decompressing.

Well if there is anything I can add to help you guys help me please let me know

---

### Post by Jarn on 2007-04-25
Try running it from the terminal to see if there are any errors. Also, when you close it and it's still running, did you check if there are any remnants of Wine still running? That can be done with ```
ps aux | grep wine
```

---

### Post by maaylix on 2007-04-26
> **Jarn said:**
> Try running it from the terminal to see if there are any errors. Also, when you close it and it's still running, did you check if there are any remnants of Wine still running? That can be done with ```
ps aux | grep wine
```

Ok, I ran gw.exe through the terminal, the moment wine stops responding the terminal displays this message:

```
fixme:dbghelp:SymInitializeW what to do ??
```

This message is repeated endlessly.

Here is the ouput from ''ps aux | grep wine''

```
rip       5012  0.0  0.1   2800   752 pts/0    S+   21:38   0:00 grep wine
```

rip is my user name

Also, whenever I start something wine related, like winecfg or winefile this message is displayed:

```
Warning: could not find DOS drive for current working directory '/home/rip', starting in the Windows directory
```

Could this be relevant to my problem?

---

### Post by Jarn on 2007-04-26
> **maaylix said:**
> ```
fixme:dbghelp:SymInitializeW what to do ??
```
Also, whenever I start something wine related, like winecfg or winefile this message is displayed:

```
Warning: could not find DOS drive for current working directory '/home/rip', starting in the Windows directory
```That fixme is a semi-common problem due to Guild Wars' new sound system. There are several different command line switches that can be used to attempt to remove it. These are -dsound, -sndasio, and -nosound. Try them one at a time, don't use more than one at a time. If neither of those three work you could also try disabling sound in winecfg by unchecking all of the driver options in the Audio tab.

As for your second problem, I have no idea what it's about, but it doesn't sound too serious since Wine uses a different directory.

---

### Post by maaylix on 2007-04-26
> **Jarn said:**
> That fixme is a semi-common problem due to Guild Wars' new sound system. There are several different command line switches that can be used to attempt to remove it. These are -dsound, -sndasio, and -nosound. Try them one at a time, don't use more than one at a time. If neither of those three work you could also try disabling sound in winecfg by unchecking all of the driver options in the Audio tab.

As for your second problem, I have no idea what it's about, but it doesn't sound too serious since Wine uses a different directory.

Many thanks for the help Jarn!

I switched off all sound in winecfg and the game loaded! 

The menu showed with no problems and I was able to log in but...

I'm getting a constant 100% cpu use, I'm using a 800x600 virtual desktop, with all graphic options tuned down to the minimum, guild wars resolution is down to 800x600, I also tuned down all the audio options. I closed all other aplications and left only guild wars running, but I still get 100% cpu use.

I even tried minimizing the guild wars window inside wine, to see if that would change anything, indeed it did, cpu use went down to about 70%, but then steadily rose back to 100%

As I only purchased the cd-key, I need to leave the game running to download all the necesary files from the internet, but I can't leave my pc running on a constant 100% cpu use.

Is there any tweak or something I should do to get more performance, or am I stuck with this?

---

### Post by Jarn on 2007-04-27
Well, games do traditionally use 100% of your CPU. But you could add the -image switch. That downloads all your files for you and then turns off. It doesn't open the game, either, so it shouldn't take up much CPU power. But it will have to download _a lot_ if you've never played before, like more than 2 gigs.

---

### Post by maaylix on 2007-04-27
> **Jarn said:**
> Well, games do traditionally use 100% of your CPU. But you could add the -image switch. That downloads all your files for you and then turns off. It doesn't open the game, either, so it shouldn't take up much CPU power. But it will have to download _a lot_ if you've never played before, like more than 2 gigs.

No probelm, where do I input this command/switch?

---

### Post by Jarn on 2007-04-27
When you run the program, run it with:
```
wine /path/to/Gw.exe -image
```

That is how command line switches work. That's the same way you would use the -dsound and other switches.

---

### Post by maaylix on 2007-04-27
> **Jarn said:**
> When you run the program, run it with:
```
wine /path/to/Gw.exe -image
```

That is how command line switches work. That's the same way you would use the -dsound and other switches.

The graphic intensive menu doesn't show up but I still get 100% cpu use with ''-image''

Though I discovered something by accident

If I run Guild wars normally, and then minimize the Guild Wars window inside wine and right click the guild wars icon, my processor use decreases dramatically, and the game continues to download. As long as I leave it like this:

[[IMG]http://img385.imageshack.us/img385/1821/screenshotsi8.th.png[/IMG]](http://img385.imageshack.us/my.php?image=screenshotsi8.png)

But for some reason, this stopped working, and I get 100% cpu use with this ''technique''

EDIT: Also, the graphic menu is now extremely laggy (The gw notification shows 3 FPS)... I don't know why as I didn't change any configuration, this is the messeage that is now repeating endlessly:

```
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAP
```

I tried the following switches with no success: -nosound -dx7 -dx8 -noshaders 

I also tried disabling shaders in winecfg, but the menu still lagged.

---

### Post by chek2fire on 2007-04-28
try to run guild wars alone not inside wine windows and with windows 2000 settings
 after type this
> 
wine "C:\\Program Files\\Guild Wars\\Gw.exe(or your path)" -dsound

---

### Post by maaylix on 2007-04-28
> **chek2fire said:**
> try to run guild wars alone not inside wine windows and with windows 2000 settings
 after type this

Didn't work, I tried running gw without emulating a virtual desktop, but I still get really low FPS on the login menu.

Also tried -dsound, terminal still gives me this error:

```
fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_BUMPENVMAP
```

---

### Post by maaylix on 2007-04-28
In the WineAppDB I found some tips about doing some registry tweaks:

[http://appdb.winehq.org/appview.php?iVersionId=7530](http://appdb.winehq.org/appview.php?iVersionId=7530)

But I didn't find any of the options they suggest to edit 

Do I need to create them? how would I do that?

---

### Post by Azakus on 2007-04-28
WINE 0.9.36 out now!
My 64-bit deb:
[http://azakusfiles.homelinux.net/dists/feisty/wine_0.9.36-1_amd64.deb](http://azakusfiles.homelinux.net/dists/feisty/wine_0.9.36-1_amd64.deb)
Compile Scripts included (64-bit).

---

### Post by ObiWan2001 on 2007-04-29
Finally water in the login-screen with directx 9

---

### Post by Jarn on 2007-04-29
Indeed. I <3 Wine.

---

### Post by Abss1185 on 2007-04-30
How do i get DirectX 9?

---

### Post by handy on 2007-04-30
I believe GW only used DX 8.

---

### Post by Annigma on 2007-04-30
There's an option on the GW installation screen to install DirectX 9... don't know if that'll help. I'm a newb at this and I've just made it to the login screen, but no graphics.. computer gets stressy and I'm trying to figure out what to do next.. I'm getting this at present:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture

Finding help is hard, as I often don't understand people's answers :(

---

### Post by Jarn on 2007-04-30
> **Annigma said:**
> fixme:wave:ALSA_AddCaptureDevice Add support for DSCaptureI have that too, but I don't believe it's serious. Guild Wars still runs fine for me. IIRC there were some changes to ALSA in 0.9.36 and I would guess that caused it. But it doesn't seem to be a problem.

> **Abss1185 said:**
> How do i get DirectX 9?Tell Wine to use Windows 2000 or XP, DX9 doesn't work in anything lower than 2000.

---

### Post by AndrewRiedi on 2007-04-30
Yes, that fixme is the result of some new ALSA code in 0.9.36.  Basically it found a Master (ie. regular volume control), but did not find some sort of Capture device.  Not a big deal.  :)

---

### Post by Abss1185 on 2007-04-30
Last question how do i get sound wokring cuz everytime i enable it i get debug error in terminal. And how to get water to show. Thx in advance

---

### Post by Jarn on 2007-04-30
As far as sound goes, it works sporadically/not at all, currently. As far as the water, more information than that would be needed and I wouldn't know how to help. Just make sure you have wine version 0.9.36.

---

### Post by Abss1185 on 2007-04-30
Thank you everyone for your replies.

---

### Post by handy on 2007-05-01
Turning ***Reflections*** on in the GW ***Options*** menu should give you water, but it probably slows the game down more than any other, I use Cedega, but don't use reflections ever.  You really don't notice that it isn't there in game play.  Well I don't anyway...

---

### Post by Annigma on 2007-05-01
Apart from the above error, which I'm going to ignore for now, due to your comments, I only installed one disc.. It got to 100% then didn't ask me for another. It pretty much froze my screen and if I dragged the GW window around it 'left it's imprint' all over the screen. I didn't have to restart though, which was nice - so used to windows just grinding to a halt when things go wrong!

Now, if I double click the GW icon on the desktop it will instantly load up and I get the login screen, but it kinda gets stuck there.. it will let me enter my login details, but that takes about 10 minutes! It's all black around the login bit, but I can see that it's 'trying' to show some graphics - a couple of purple patches with bits of image I can recognise..
It also resizes my desktop and all the nice 'neatness' I'm getting used to in Ubuntu is gone: everything's too big..

How do I get the second disc installed, and does it matter..?
What do I do to fix my graphics? I guess it's some kind of 3D acceleration problem, but I'm a bit out of my depth here :(

Apologies if this has been answered, and thank you in advance.

:)

---

### Post by YokoZar on 2007-05-01
> **Annigma said:**
> There's an option on the GW installation screen to install DirectX 9... don't know if that'll help.This won't help - Wine cannot use Microsoft's DirectX libraries, and must instead reimplement them on their own.  "Installing" DirectX in this way won't really do anything.

---

### Post by Annigma on 2007-05-01
Oh darn, and I was trying to be helpful 

:oops:

This is frustrating! I always manage to fix stuff in Windows. At least I know my way around it well enough to fiddle with stuff: I daren't fiddle around in Linux. I won't give up though. It feels nice not being in MS ;)

---

### Post by Jarn on 2007-05-01
As far as installing the second disc, it shouldn't be necessary. All the stuff that was on it can be downloaded from ArenaNet's servers. Just run Guild Wars with the -image switch. ```
wine /path/to/Gw.exe -image
```Or, you can probably edit your desktop shortcut to include it. Be warned, though, it will be a HUGE download. And for it changing your resolution, you can tell Wine to "Emulate a virutal desktop" in winecfg.

---

### Post by Annigma on 2007-05-01
Yeah, I'm familiar with the -image tag. Wasn't sure if I needed the second disc, so thanks :)

The option to emulate a virtual desktop is greyed out for me..

---

### Post by Jarn on 2007-05-01
The checkbox is greyed out?

---

### Post by Annigma on 2007-05-02
*peers around* There's an echo in here.. :p

Yep, not clickable/checkable/selectable/delectable... now I'm hungry

---

### Post by Jarn on 2007-05-02
Well, I wasn't sure if you meant the checkbox or the box where you type the size. If you had meant the type-boxes I would have told you to click the checkbox. Since you mean the checkbox, I'll tell you... a whole lot of nothing, because I have no idea.

---

### Post by ObiWan2001 on 2007-05-02
In winecfg you can only set an virtual-desktop global (standardconfiguration) not for an singe application (like gw.exe)

---

### Post by Annigma on 2007-05-02
Sorry Jarn, I was just messing about. I'm grateful for your input :)

Thanks Obi, that worked in as much as I could tick/check the 'Emulate a virtual desktop' field. However, it hasn't made any difference that I can spot, apart from not changing the resolution of everything in Ubuntu, so that I have to restart in order to get it 'tidy' again...

---

### Post by Annigma on 2007-05-03
Is this [WoW with Wine]("http://ubuntuforums.org/showthread.php?t=312482&highlight=world+of+warcraft") thread helpful..?

---

### Post by lordhebe on 2007-05-04
Well I got Guild Wars up and running with wine 0.9.36, but performance is terrible. I was able to achieve a playable (still crappy) framerate of 2-47 (with the average framerate being under 15, it only hit 47 if I was looking right at a wall, and very lucky) by using the -dsound -noshaders -dx8 flags. Any advice for improving performance? I have an ATI Radeon X1600 Pro drivers 8.36.5, and I know this graphics card isn't exactly favourable on linux, but still it shouldn't be quite this bad! I can run Half-life 2 on DirectX 8 mode with no framereate probs!

---

### Post by Annigma on 2007-05-04
I don't even know how to run GW without double-clicking the icon on the desktop! 
:blush:
I navigate to where it is (desktop...) but it doesn't 'recognise the module'...
:(

---

### Post by Jarn on 2007-05-04
> **lordhebe said:**
> Any advice for improving performance?There are some registry tweaks that can be done back in the depths of this thread somewhere. I'll see if I can dig them up.
EDIT: [http://ubuntuforums.org/showpost.php?p=2240683&postcount=231](http://ubuntuforums.org/showpost.php?p=2240683&postcount=231)

> **Annigma said:**
> I don't even know how to run GW without double-clicking the icon on the desktop!
To run it from a terminal, you can type:
```
wine ~/.wine/drive_c/"Program Files"/"Guild Wars"/Gw.exe
```This assumes that it is installed in the default location.

---

### Post by Annigma on 2007-05-04
Wow!... Progress!!
I looked at the properties of the GW file/shortcut on my desktop, cut and pasted the launcher address into the terminal, and put -nosound on the end.. the GW login screen came up and for the first time I actually had graphics!!! :D Not great graphics but still, beggars can't be choosers!!
I'll try the other commands now, hopefully I can just keep adding them. .like so: 'blah blah command blah' -nosound -nowhateveritwas -nosomethingelse.....

*squints down the tunnel* I see light!!

:D

---

### Post by Annigma on 2007-05-04
Oh thanks Jarn: dind't see your response till I'd posted ;o
I tried it with -dsound -noshaders -dx8 and I can actually 'see' the pictures! They're not right, and they're moving around in a rather jerky, sluggish way, but they're there!
The login screen is too slow to even 'log in', and the terminal is complaining about allsorts (something about my keyboard now, apart from other stuff..) but it's a definite improvement! :)

Sorry to keep posting, but it's becoming a useful tool in helping me remember what I did, as well as possibly helping someone else who's struggling as much as me... ^..^

I don't know if it's connected, but whilst I'm typing this I'm noticing a lot of typos, which isn't usual for me... it's like my keyboard's getting mixed up or something.. just wondering if it's linked to the keyboard 'complaints' my terminal was just 'scrolling' about...

Good luck anyone else who's struggling: don't give up! 

:)

---

### Post by Jarn on 2007-05-05
Wine is giving you complaints about your keyboard? O.o

What is it complaining about?

---

### Post by Annigma on 2007-05-05
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported

as well as:

fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1201900) : stub

over and over and over and over and......

I logged into GW last night and it was downloading the expected plethora of files so I left it.. got up early this morning (woke up as not feeling well) to find my character standing in one of the towns. Skill bars, and user windows like party and heroes looked great; graphics in general were ok. Movement was bad. I logged out and in my sleepy state I think I fiddled with the shell folder/link bit in Desktop Integration.. Now it won't start at all... Grr!

One step forward, two steps back..

---

### Post by el mariachi on 2007-05-05
the first time I ran GW it was fine (except for some small gfx glitches) but now I can't play anymore, it hangs in the first screen (the small one that says "Downloading"). I tried do reinstall, but the result was the same: the first time it runs it's fine but the second time it doesn't work.. :confused:lost

---

### Post by Jarn on 2007-05-05
> **el mariachi said:**
> the first time it runs it's fine but the second time it doesn't work..Try running it from the terminal so you can see if there are any errors.

---

### Post by Annigma on 2007-05-05
...... *tries not to swear*

I just tried to run GW having given my machine a nice long rest and I got...
"Repairing Data Archive"................... This is something I used to get on XP on an irritatingly regular basis!! I thought I'd left that behind!!

*sobs*

---

### Post by el mariachi on 2007-05-05
> **Annigma said:**
> ...... *tries not to swear*

I just tried to run GW having given my machine a nice long rest and I got...
"Repairing Data Archive"................... This is something I used to get on XP on an irritatingly regular basis!! I thought I'd left that behind!!

*sobs*

it happens from time to time with me. I guess that's just normal

---

### Post by Annigma on 2007-05-05
Yeah, I'm quite used to it. I just hoped Ubuntu would magically make it disappear! :o 
It does make me think that it seriously is time to upgrade my poor old machine! :(

Well I just loaded it up and logged in. The graphics are too bad to do anything, but it's a start :)
Not sure what to do next.. 'guess I'll just keep fiddling around in winecfg..

Sorry for posting so much; I hope it's not a problem for anyone..

^..^

Edit: Oh dear. Now winecfg just throws up a load of complaints... ELF this and Deferred that... hmm..

---

### Post by Flyser on 2007-05-05
Strange I never got such a error... neither in windows nor in wine! Maybe your harddrive has some badblocks

---

### Post by T3h_Dohtem on 2007-05-07
i am getting some keyboard errors from wine also, i have been running WoW and Steam/Halflife for months without any problem, but GW seems to hang as soon as the installer is done, right as it tries to load the game itself, and now I cant get the install to even load.

Update: Actually changing back to Windows XP is allowing the setup to run without problems thus far. (WoW has to run in 98 and install/update in NT 4.0)

Further Update: I still get nothing after the download/install is completed. It starts up, then just stops doing anything right after the "Logging into Arena.net" window. It just closes out.

---

### Post by Jarn on 2007-05-08
Try running it from the terminal to see what errors there are.

---

### Post by austaph on 2007-05-10
Runs great, except the terrain is 100% transparent.  Flowers, bushes, and stairs will display, but the terrain itself is just a deep, black void.

```
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1640020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1640020) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0xd543d68) : stub
fixme:d3d_shader:shader_get_registers_used Pixel shader uses texbem instruction on more than 1 sampler

```

Some fixme:d3d messages, inbetween a whole lot of fixme:keyboard messages.  Any idea how to troubleshoot this?

---

### Post by Jarn on 2007-05-10
If it works, I would say don't really worry about it.

---

### Post by lordhebe on 2007-05-10
> **austaph said:**
> Runs great, except the terrain is 100% transparent.  Flowers, bushes, and stairs will display, but the terrain itself is just a deep, black void.

```
err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1640020) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1640020) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0xd543d68) : stub
fixme:d3d_shader:shader_get_registers_used Pixel shader uses texbem instruction on more than 1 sampler

```

Some fixme:d3d messages, inbetween a whole lot of fixme:keyboard messages.  Any idea how to troubleshoot this?

Are you using an ATI card by any chance? Try running it with no shaders and in directX 8 mode. Do this by running with the -noshaders and -dx8 flags.

---

### Post by TorchSoul54 on 2007-05-10
Ok, I just got Guild Wars to work in Wine, after reading the last like 10 pages. 

The one little thing that I consider a problem is that my mouse disappears when I scroll through Guild Wars. I saw it for the first like 3 seconds then it disappears. I can still click on stuff on the screen but no mouse.

This is very frustrating when attacking. Anybody have this happen to them and is there a way to fix it?

Thanks in Advance

---

### Post by AndrewRiedi on 2007-05-10
> **TorchSoul54 said:**
> Ok, I just got Guild Wars to work in Wine, after reading the last like 10 pages. 

The one little thing that I consider a problem is that my mouse disappears when I scroll through Guild Wars. I saw it for the first like 3 seconds then it disappears. I can still click on stuff on the screen but no mouse.

This is very frustrating when attacking. Anybody have this happen to them and is there a way to fix it?

Thanks in Advance

I don't play Guild Wars, but I am developing Wine's cursor code.  I believe from talking to people that Guild Wars uses animated cursors in a few spots for a couple seconds, and currently Wine does not have animated cursor support.  There is some old patches that someone else wrote that will allow you to use animated cursors, and thus fix your problem if you are able to compile and patch Wine on your own.  

Anyhow, I am currently working on getting my hardware cursor patch accepted, so it will be a while before I work on animated cursors.  Once I do start working on them, don't expect them to get into Wine for quite a while after, because they are very difficult to implement properly.

---

### Post by Jarn on 2007-05-10
> **TorchSoul54 said:**
> I saw it for the first like 3 seconds then it disappearsDid you try right-clicking a few times? The mouse usually disappears when you zone, if you right-click a few times it comes back.

---

### Post by Annigma on 2007-05-11
Third time I've nearly finished this post then hit the wrong button! grrr!
How exactly do I add reg. keys? which are names, values, keys...?
Was trying to add 'gdi' and 'opengl'

Thanks

---

### Post by Flyser on 2007-05-11
> **AndrewRiedi said:**
> I believe from talking to people that Guild Wars uses animated cursors in a few spots for a couple seconds, and currently Wine does not have animated cursor support.

Guild Wars does not use animated Cursors, it changes the cursor sometimes, but thats not animation, right?

---

### Post by AndrewRiedi on 2007-05-11
> **Flyser said:**
> Guild Wars does not use animated Cursors, it changes the cursor sometimes, but thats not animation, right?

No, that would not be animation.

From what I have heard, it uses just one animated cursor.  The normal game play, however, uses just standard static cursors.

---

### Post by draegoonscythe on 2007-05-13
hey i love the guide. it worked fine for the whole install.

I'm a newb at Linux, so pardon for the questions. I did the auto guide procedure on feisty, and everything installed fine. Then the system kicked me out to the login screen, and when I tried to update the system it said that wine-dev was causing an error. I got rid of it, but now everytime I try to run GW it crashes, and I have to kill everything? Anything I can do about it?

---

### Post by lordhebe on 2007-05-13
Is anything different with wine 0.9.37? Sound issues are supposedly fixed with Oblvion, are they better with Guild wars?

---

### Post by lordhebe on 2007-05-14
Update: As of wine 0.9.37 Guild wars no longer locks up when I start it up without the -dsound flag. Performance in this mode however is worse but not drastically. Combat sounds still do not function.

---

### Post by PierreLinux on 2007-05-16
hmm. I installed this same script a time ago, and it worked nice except that ugly memory leak that will make gw crash after a while. 
But now when reinstalled ubuntu, everything keep being messed up in the terminal install.
Says this at the end:

15:00:44 (176.61 KB/s) - "/home/pierre/gwsetup.zip" sparad [81466/81466]

Archive:  gwsetup.zip
replace GWSETUP.EXE? [y]es, [n]o, [A]ll, [N]one, [r]ename: n
/home/pierre/Desktop/installwine+gw.sh: 39: wineprefixcreate: not found
mv: målet "/home/pierre/.wine/drive_c/" är inte en katalog: Filen eller katalogen finns inte
/home/pierre/Desktop/installwine+gw.sh: 41: wine: not found
Build Complete. Wine is ready to go
pierre@pierre-desktop:~$ 

after this nothing happens. I cant use winecfg or anything. it aint comming up any gw icon at the deskop or when i click at the ubuntu program logo theres no wine or gw icon there.

Wonder what have happend now. 
btw, has the script been modded? i looked in it and it says

#This is a 64-bit only compile of WINE
EDIT: Ok i fixed it now, must be some server down or something. I downloaded wine seperately and tried again. looky there, it works =)
(if anyone knows what cud be with the mem leak, plz post)
and where does the gw files saves? have to make the gw icon myself i belive

---

### Post by lordhebe on 2007-05-16
Actually I found that performance is NOT worse when not using -dsound, It was me having a bunch of other programs running in th background guzzling up CPU usage. So great! Now all we need is combat sounds ... :-x

---

### Post by ObiWan2001 on 2007-05-18
Still crashing without -dsound for me.

---

### Post by cor2y on 2007-05-19
so after playing around with feisty for a while and the eye candy i finally got around to installing the restricted ATI drivers to be able to play guild wars again.
I updated the software and wine.
ANd finally launched it only to be met with a message that i have unsupported hardware and do i wish to countinue launching guildwars.
Well i said yes and wow did the game look horrible.
I would hate to have to reinstall guildwars all over again (all the updates to download) does anyone know what the problem could be?

---

### Post by Jarn on 2007-05-20
It seems a couple people are complaining of this. I have no idea what the problem is, though.

---

### Post by lordhebe on 2007-05-20
> **cor2y said:**
> so after playing around with feisty for a while and the eye candy i finally got around to installing the restricted ATI drivers to be able to play guild wars again.
I updated the software and wine.
ANd finally launched it only to be met with a message that i have unsupported hardware and do i wish to countinue launching guildwars.
Well i said yes and wow did the game look horrible.
I would hate to have to reinstall guildwars all over again (all the updates to download) does anyone know what the problem could be?

Exactly how did it look? Does it have missing floor? I had this problem with my X1600 (I've switched to NVIDIA now) Try running it with -dx8 and -noshaders

---

### Post by cor2y on 2007-05-21
Neither do i Jarn the funny thing is with the open source mesa drivers the game looked better.Sure the frame rate was very slow and objects floated in midair but it looked better than what i am getting with the restricted drivers and the error that i have unsupported hardware.

lordhabe tried launching with -dx8 -noshaders, i already had -nosound enabled.
The login screen has a opaque turquoise blue ocean, the character select screen is there but the avatars of my characters are missing , In game the menus etc are there but the frame rate is super slow (slower it seems to me than when i tried with the open source drivers but i didn't take note of the fps so i can't be too sure) objects are the wrong color etc and with such a slow frame rate it takes a long while  to move around.At first i couldn't even see my avatar or others only the text to let you know the name of characters, but after five minutes of waiting finally my avatar and others in the town were drawn in along with objects such as grass etc.
Was it an update to guildwars that did this or perhaps wine?
If it was wine anyone tried an earlier version to see what version you should perhaps stick with?
Or was it none of the above and just the use of the latest ATI drivers?

---

### Post by Azakus on 2007-05-21
There were a couple of regressions in 0.9.37 that the latest snapshots fix.
[Wine's latest build info]("http://winehq.org/site/git")

---

### Post by sinaen on 2007-05-24
hmm  i followed your guide.but it didnt work. then i tried to install the latest wine version in feisty, and it works. but GuildWars freezes after a while. while loading. and eats up all my memory.

wine dumps this output in console-mode 
fixme:dbghelp:SymInitialize what to do ??

and i do most certainly not now what to do :D

ive checked and double checked all my settings in winecfg/wineconfig and they all match. 

on my laptop gw worked out of the box (almost) on an i855 card..
this i run on my current computer is an ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
please help me get this working

---

### Post by Jarn on 2007-05-24
> **sinaen said:**
> hmm  i followed your guide.but it didnt work. then i tried to install the latest wine version in feisty, and it works.It says in big, bold letters on the front post that the guide no longer is updated (and hence probably won't work) because the one from the repositories works now ;). Unless you're using 64-bit, that is. Then I think it's still necessary, not exactly sure.

> **sinaen said:**
> wine dumps this output in console-mode 
fixme:dbghelp:SymInitialize what to do ??It may have something to do with the sound. I know that a lot of people get that error due to Guild Wars' new sound system, but I think I've only heard of it happening on start-up, not after x minutes. However, you could try doing what fixes that - usually running it with the -dsound or -nosound switches.

---

### Post by Flyser on 2007-05-27
just use win98 for your windows version in winecfg

---

### Post by lordhebe on 2007-05-28
Well you may find that applying the no-lights patch to wine may help, it fixed the problem with me. Look at the first post on this thread.

---

### Post by Jarn on 2007-06-09
I don't know if anyone wants it, but I created a deb for myself with the no concurrent lights patch since I was getting that error.

If someone does want it, I would need a place to upload it to.

---

### Post by Pugwash on 2007-06-10
> **sinaen said:**
> hmm  i followed your guide.but it didnt work. then i tried to install the latest wine version in feisty, and it works. but GuildWars freezes after a while. while loading. and eats up all my memory.

wine dumps this output in console-mode 
fixme:dbghelp:SymInitialize what to do ??

and i do most certainly not now what to do :D

ive checked and double checked all my settings in winecfg/wineconfig and they all match. 

on my laptop gw worked out of the box (almost) on an i855 card..
this i run on my current computer is an ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
please help me get this working

I've had the same problem, I've had to do a cold shutdown twice because of it.

---

### Post by Jarn on 2007-06-10
That may or may not be related to the concurrent lights bug. I started having that problem too, recently. In the console it would say "Too many concurrently active lights" and then it would spit out the "what to do ??" error continuously. I fixed it by compiling wine with a patch - if you are using 32-bit and can recommend me a place to upload the deb, I can give you the deb. Else I can tell you how to patch it.

---

### Post by Pugwash on 2007-06-12
> **Jarn said:**
> That may or may not be related to the concurrent lights bug. I started having that problem too, recently. In the console it would say "Too many concurrently active lights" and then it would spit out the "what to do ??" error continuously. I fixed it by compiling wine with a patch - if you are using 32-bit and can recommend me a place to upload the deb, I can give you the deb. Else I can tell you how to patch it.

Hi, thanks for the response. Thats the exact problem I'm having. Could you give me details on how you patched wine. I hope you aren't offended, but I'm getting very security conscious these days.

Thanks

---

### Post by Jarn on 2007-06-12
Not at all - that's one of the greatest things drawing people to Linux, security - why compromise it by downloading a deb from a random person on the internet? I don't know where I could upload it, anyway. :)

1. Make a directory somewhere to store the things you'll need in (I recommend ~/winestuff and will be basing these instructions on that directory)

2. Get the wine source and put it in that directory. Extract it in there, also.

3. Download this file and put it in your directory: [http://eurus103.googlepages.com/lights-0.9.33.patch](http://eurus103.googlepages.com/lights-0.9.33.patch) (the version in the file name is 0.9.33, but it works for this version also).

4. Apply the patch.```
cd ~/winestuff/wine-*/dlls/wined3d
patch <~/winestuff/lights-0.9.33.patch
```
5. Then all you need to do is compile it!```
cd ~/winestuff/wine-*
./configure
make depend
make
sudo checkinstall

```
After that, you should be good to go! :)

---

### Post by Virgilius on 2007-06-13
After executing the script, how do I get to Guild Wars to start playing?

---

### Post by Jarn on 2007-06-13
By "script" I assume you mean the script on the front page...

In the terminal type:
```
cd ~/.wine/drive_c/Program\ Files/Guild\ Wars
wine "C:\Program Files\Guild Wars\Gw.exe"
```

---

### Post by Pugwash on 2007-06-15
> **Jarn said:**
> Not at all - that's one of the greatest things drawing people to Linux, security - why compromise it by downloading a deb from a random person on the internet? I don't know where I could upload it, anyway. :)

1. Make a directory somewhere to store the things you'll need in (I recommend ~/winestuff and will be basing these instructions on that directory)

2. Get the wine source and put it in that directory. Extract it in there, also.

3. Download this file and put it in your directory: [http://eurus103.googlepages.com/lights-0.9.33.patch](http://eurus103.googlepages.com/lights-0.9.33.patch) (the version in the file name is 0.9.33, but it works for this version also).

4. Apply the patch.```
cd ~/winestuff/wine-*/dlls/wined3d
patch <~/winestuff/lights-0.9.33.patch
```
5. Then all you need to do is compile it!```
cd ~/winestuff/wine-*
./configure
make depend
make
sudo checkinstall

```
After that, you should be good to go! :)


Thank you, you're a star! I'll try it and report back, hopefully I can get back to experiencing some uninterrupted guild wars goodness now. :D

---

### Post by Virgilius on 2007-06-16
Well, I tried to install it by using the automated script but it didn't work :( I installed and everything and the program downloaded the patches and all but when it came to the actual game, WINE just froze! :( and plus the window went all funny.

---

### Post by Azakus on 2007-06-17
I made a much more user-friendly install script for the 64-bit install build and install of wine. It will also ask if you want to install the concurrent lights patch, simplified all the various 64-bit scripts into one! :p

---

### Post by TheReconHunter on 2007-06-21
Hey. I just got Guild Wars to work, by running it on my already installed windows partition. It worked  fantastically, until I loaded beryl with it. Now, the initial screen appears, but it just disappears, and I can only hear audio come through, and when I open up the Ctrl+Alt+Del manager, it says its a sleeping or "zombie" process. Anyone know whats wrong?

---

### Post by ObiWan2001 on 2007-06-21
Just don't use beryl + wine games

---

### Post by Azakus on 2007-06-21
Beryl and WINE don't mix. It's like baking soda and vinegar. You just get a big mess.

---

### Post by helps on 2007-06-22
after all this all i get after asking me if i want to continue with video card is

fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??

and this infinite loops.

---

### Post by lordhebe on 2007-06-22
Try applying the lights patch (on the first page), some people, still have to apply it to avoid problems.

---

### Post by Jarn on 2007-06-23
I just got back from a fishing trip. Monday, when I have access to my Linux box, I'm going to put Azakus' new 64-bit script ([http://ubuntuforums.org/attachment.php?attachmentid=35665&d=1182102494](http://ubuntuforums.org/attachment.php?attachmentid=35665&d=1182102494)) on the front page (I'd do it now but the last time I did that on my Windows box it added some funky spaces) and I'm going to update it with explicit instructions on doing the concurrent lights patch for 32-bit. I may or may not do a script for it, I'm not sure since it is pretty easy to do.

EDIT: Azakus, I took a look at your new script, and it looks really nifty. Nice work!

---

### Post by Jarn on 2007-06-28
Okay, I updated the first page. I did end up making a script for the 32-bit install with a concurrent lights fix, though it's probably unnecessary since it's pretty easy. Regardless, it's there. ;)

Azakus, I modeled my script after yours because it's awesome. :D

---

### Post by JakZ on 2007-06-29
I downloaded Wine with your script. However, when it prompts me to make the install (the Y/N) it's not possible because you're not in the correct path in the script.
I changed to the path and made the install manually and GW is not downloading ;)

---

### Post by JakZ on 2007-06-29
> **Virgilius said:**
> Well, I tried to install it by using the automated script but it didn't work :( I installed and everything and the program downloaded the patches and all but when it came to the actual game, WINE just froze! :( and plus the window went all funny.

I got the exact same thing.

---

### Post by Azakus on 2007-06-29
> **JakZ said:**
> I downloaded Wine with your script. However, when it prompts me to make the install (the Y/N) it's not possible because you're not in the correct path in the script.
I changed to the path and made the install manually and GW is not downloading ;)

Looks like they changed the name of the executible.
GWSETUP.EXE is now GwSetup.exe

---

### Post by Jarn on 2007-06-29
> **Azakus said:**
> Looks like they changed the name of the executible.
GWSETUP.EXE is now GwSetup.exe

It's times like this that I wish Linux WASN'T case-sensitive. :P

---

### Post by Azakus on 2007-06-29
Wine 0.9.40 released. I've made more modifications to the script (fixes the new GwSetup executible, uses lsb_release to determine which Ubuntu version you have (feisty, edgy, etc) and download the correct dependency packages).
{EDIT} I don't know about anyone else, but patch is choking on the concurrent lights patch. As I'm not exactly a master of patch, I'll leave it up to Jarn.
Full source:
```
#!/bin/bash
#64-bit compiling script for Wine, and certain Guild Wars patches, if selected.
#CHANGE VERSION NUMBER UPON NEW RELEASE!
#Version: 6/29/2007
VERSION=0.9.40
if test `uname -m` != "x86_64"
then
echo "You don't need this because you don't have an x86_64 linux distro!"
exit
fi
sudo aptitude install patch libc6-i386 libc6-dev-i386 checkinstall lib32asound2-dev libasound2-dev libjack0.100.0-dev libfreetype6-dev libfreetype6
mkdir ~/winestuff
cd ~/winestuff
wget http://umn.dl.sourceforge.net/sourceforge/wine/wine-$VERSION.tar.bz2 -O ~/winestuff/winesource.tar.bz2
#Decide which pkgs.sh to download
DIST=`lsb_release -c -s`
if [ $DIST = "feisty" ]
then
DIST="edgy"
fi
wget http://kegel.com/wine/$DIST.sh -O ~/winestuff/pkgs.sh
sudo sh ./pkgs.sh
tar -xjvf winesource.tar.bz2
cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.so
#Creates 32-bit libsicuuc.a, if necessary
#!/bin/bash
if test -e /usr/lib32/libsicuuc.a
then
echo "libsicuuc.a found"
else
	echo "Creating 32-bit libsicuuc.a"
	cd ~/winestuff
	wget ftp://ftp.software.ibm.com/software/globalization/icu/3.6/icu4c-3_6-src.tgz
	tar zxvf icu4c-3_6-src.tgz
	cd ./icu/source
	LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" CC="gcc -m32" CXX="g++ -m32" ./configure
	make
	ar t /usr/lib/libsicuuc.a | sed -e 's/ao$/o/' | perl -e 'while(<>){ chomp($_); print "find . -name $_ | xargs ar ruv libsicuuc.a\n"; }' > mkar.sh
	sh mkar.sh
	sudo cp libsicuuc.a /usr/lib32/
fi
cd ~/winestuff/wine-$VERSION
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure
#Ask to install con. light patch, needs to be before compile, after configure
echo "Install concurrent lights patch?"
echo "Should only be installed if Guild Wars outputs a 'Too many concurrent lights' error message"
echo -n "[y or n]:"
read CPATCH
if test $CPATCH = "y"
then
 wget http://eurus103.googlepages.com/lights-0.9.33.patch -O lights.patch
 patch ~/winestuff/wine-$VERSION/lights.patch
echo "Patch applied"
fi
make depend
make
checkinstall --requires=lib32asound2,libc6-i386,libfreetype6,fontforge --install=no --maintainer="Azakus" --nodoc
echo "Package created!"
echo -n "Install now? [y or n]:"
read INSTALL
if test $INSTALL = "y"
then
sudo dpkg -i wine*.deb
else
echo "Package not installed."
fi
echo -n "Install Guild Wars now? [y/n]:"
read GW
if test $GW = "y"
then
wget http://www.guildwars.com/downloads/gwsetup.zip -O ~/gwsetup.zip
cd ~
unzip gwsetup.zip
wineprefixcreate
rm ~/gwsetup.zip
mv ~/GwSetup.exe ~/.wine/drive_c/
wine "C:\\GwSetup.exe"
fi
```

---

### Post by Jarn on 2007-06-30
> **Azakus said:**
> As I'm not exactly a master of patch, I'll leave it up to Jarn.I'm hardly a master of patch - I didn't even make any of these. I just collected them from different places. When I first started this thread I didn't even know what patch was, just that it worked (and the obvious that it patches things). Though I think I've learned enough since then that I can get it figured out. Sadly, I won't have access to my linux box until Monday so until then anyone who needs the concurrent lights fix will need to keep using 0.9.39 until then.

EDIT 1: Azakus, you know a lot more about bash than I it appears (I know almost nothing - though I learned a bit from your script ;)), is there a way to feed input to a program in a script? In this case, checkinstall? I was thinking about automatically supplying the answers to its questions (Y to create docs and, if using concurrent lights fix, version could be changed to something like $VERSION-concurrent_lights_fix). If it was possible that could make the process even more automated. Then the questions about whether you want to install GW and things to the beginning of the script so questions need only be answered at the very beginning. Then it could be left running overnight and things with no worries that you'll wake up in the morning to find it prompting you halfway through (because, after all, who wants to stop playing GW to compile a new wine?).

EDIT 2: Also, Azakus, I don't know if you want to or not but I would encourage you to change this line "wget [http://eurus103.googlepages.com/lights-0.9.33.patch](http://eurus103.googlepages.com/lights-0.9.33.patch) -O lights.patch" to "wget http://eurus103.googlepages.com/lights-$VERSION.patch -O lights.patch" for the sake of continuity. I plan to keep the files on my googlepage updated to reflect this, though I don't have anything for 0.9.40 up.

---

### Post by DraeLee on 2007-06-30
Now Im trying to understand you say dont use compiz fusion with GW why is that?

I mean I am running it right now in windowed mode and besides the fact of no sound it looks great and is running fine.  You dont really know how much you miss something till its gone but thats ok with me for now.  So I am just trying to understand about the whole non compliant issue or is it beryl alone that has problems with GW??

---

### Post by Azakus on 2007-06-30
> In this case, checkinstall? I was thinking about automatically supplying the answers to its questions (Y to create docs and, if using concurrent lights fix, version could be changed to something like $VERSION-concurrent_lights_fix
checkinstall has the option -y to answer "yes" to all checkinstall questions. The only thing I can't get it to do is make a summary without the user typing. Oh well. Other than that, I got most of the questions answered with this line
```
checkinstall --requires=lib32asound2,libc6-i386,libfreetype6,fontforge --install=no --maintainer="Azakus" --nodoc
```
The only other way I can see is to prebuild the .doc-pak directory checkinstall makes with the necessary info on build, and then have the script download that .doc-pak directory and use it when anyone else makes the script.

---

### Post by Jarn on 2007-07-01
Are any of those options only for 64-bit or could I copy that line as a whole and put it into the 32-bit script? I had originally removed it because I assumed it was for 64-bit.

---

### Post by Azakus on 2007-07-01
> **Jarn said:**
> Are any of those options only for 64-bit or could I copy that line as a whole and put it into the 32-bit script? I had originally removed it because I assumed it was for 64-bit.

Nope, those options are for all versions of checkinstall.

---

### Post by MasterPatricko on 2007-07-01
I applied the 0.9.39 patch to 0.9.40 (32-bit)- seems to be working fine. The actual patch is extremely simple, so there is no reason why it should not work for all wine versions. It changes nothing of the actual wine code - it just changes the "Concurrent lights" error from a fatal error to a non-fatal one. I suggest simply removing the VERSION part of the filename on your server Jarn so that you wont have to bother renaming it every update.
Anyway, great job on the scripts! Saved me a lot of time.

EDIT: I just noticed the scripts are still listed as being only for Edgy. It seems to work fine on Feisty. Update the first post?

---

### Post by Azakus on 2007-07-01
> 
EDIT: I just noticed the scripts are still listed as being only for Edgy. It seems to work fine on Feisty. Update the first post?
Just remember that there is no actual package list for feisty, as it is exactly the same as edgy. In my script, I just had to override it. With the lsb_release -s -c command, now one script can be used for all versions of Ubuntu, not one for edgy, one for dapper, and one for breezy (if anyone is still using it).
```

DIST=`lsb_release -c -s`
wget http://kegel.com/wine/$DIST.sh -O pkgs.sh
```

---

### Post by Jarn on 2007-07-02
Yep, I just tried the patch and it worked for me, too. I don't know why it didn't work for you, Azakus. As Patricko said, it's a pretty hacky patch. It just changes "Too many concurrent lights" from an ERR to a FIXME and changes it from INVALIDCALL to OK.

EDIT: I updated the main page. Azakus, I got the effect I was trying to achieve through checkinstall with the --default option that you mentioned and --pkgversion=$VERSION-concurrent_lights_fix :)

---

### Post by Azakus on 2007-07-02
> **Jarn said:**
> Yep, I just tried the patch and it worked for me, too. I don't know why it didn't work for you, Azakus. As Patricko said, it's a pretty hacky patch. It just changes "Too many concurrent lights" from an ERR to a FIXME and changes it from INVALIDCALL to OK.

EDIT: I updated the main page. Azakus, I got the effect I was trying to achieve through checkinstall with the --default option that you mentioned and --pkgversion=$VERSION-concurrent_lights_fix :)

Thanks for the checkinstall options. I found out why patch was dying, I didn't have it change dirs to ~/winestuff/wine-$VERSION/dlls/wined3d, so patch was patching nothing. :)
I'll post up my latest version.

---

### Post by Jarn on 2007-07-02
I don't know if you meant to do that or not, but your script will set the version as $VERSION-concurrent_lights_fix even if they don't use the patch. You might want to set up another if that checks that variable again to decide which of two checkinstall commands to use.

---

### Post by JacenMandarin on 2007-07-03
Hi, I'm a total noob at this and was wondering if I could get some more in depth instructions. I'm currently running feisty. I've got the guild wars icon on the desktop but whenever I try to run it from there or from going into Wine it loads up and then freezes. I guess I'm doing something wrong. Please help.

---

### Post by Jarn on 2007-07-03
Try running it from the terminal to see what happens. From the description I would guess it's related to Guild Wars' new sound system, but a problem can't be diagnosed when you don't know what the problem is. To run it from the terminal, type:

wine "C:\Program Files\Guild Wars\Gw.exe"

It will output some stuff in the terminal and hopefully give you a better idea of what's going on.

---

### Post by JacenMandarin on 2007-07-03
I know this is a stupid question but how do I do that. I just started using this last night. ^^;

I really don't know what I'm doing but I want to learn. ^^

Nevermind, found it.

Okay, I tried that. It spewed out some stuff but it froze up again and I couldn't see it. I'm thinking maybe I don't have that script running or running right. Can you give me some step by step instructions on how to get it working?

---

### Post by Jarn on 2007-07-03
Which script did you use? The 32-bit (winebuild.sh) or the 64-bit (winebuild64.sh)? Further, if your whole computer freezes so you don't get to see the errors, you could direct the errors to a file like this:
```
wine "C:\Program Files\Guild Wars\Gw.exe" 2>~/error.log
```
That will create a file in your home directory called error.log that contains the output. Then you can upload it here or put it in pastebin or something.

---

### Post by JacenMandarin on 2007-07-03
The 32 bit. The thing is, I'm not even sure I have it running. I'm not completely sure how to set it up. If you think you could help me over IM I'll give you one of my accounts. Thanks for all your help so far too. ^^

Okay, I ran the script and when I tried to start up GW again it still freezes. It gives me the small box that says Guild Wars and the loading bar but when it gets done, the computer freezes. The mouse still moves but can't click anything and I have to reboot.

---

### Post by teevee on 2007-07-03
General question to everyone: How's your FPS, and what could be done to improve it? (Already have graphic settings set to minimal, still only 20 FPS at best, usually around 10...)

And any idea when we are going to get battle sounds? :)

---

### Post by Jarn on 2007-07-03
> **teevee said:**
> General question to everyone: How's your FPS, and what could be done to improve it? (Already have graphic settings set to minimal, still only 20 FPS at best, usually around 10...)Yes, my FPS aren't the greatest either (usually between 13 and 15). I seem to recall that it used to run better, so I don't know why it dropped. In my experience, the settings don't seem to impact the FPS (except Post-process Effects). If I have it all on high with Post-process Effects off or if I have it all on low with Post-process Effects off, I have the same FPS. I don't know what that means...

> **JacenMandarin said:**
> Okay, I ran the script and when I tried to start up GW again it still freezes. It gives me the small box that says Guild Wars and the loading bar but when it gets done, the computer freezes. The mouse still moves but can't click anything and I have to reboot.Why don't you try using that command that I posted up there to make a log of what wine is doing?
```
wine "C:\Program Files\Guild Wars\Gw.exe" 2>~/error.log
```
Run that from a terminal (a command line). I don't know if you're using KDE or Gnome so I don't know how you would open a terminal. If you're using KDE you can just hit Alt+F2 (Run Application) and type "Konsole". I don't know how you would open a terminal in Gnome. Then, in your home directory there should be a file called "error.log". This will tell us what is going on and maybe give clues as to how to fix it.

---

### Post by JacenMandarin on 2007-07-03
First off, I appologize for my ignorance but this is the first time I've ever attempted any of this. This is what the error log tells me:

bash: C:\Program Files\Guild Wars\Gw.exe: command not found

This is the full path to GW in wine:

Z:\home\joshua\.wine\drive_c\Program Files\Guild Wars\Gw.exe

Should I rename drive_c to C? This is Wine 0.9.4.0. Just in case it's needed I'm on a Pentium 4 3Ghz processor with an ATI Radeon x700 Pro Graphics Card which seems to be working fine so far. Thanks again for the help everyone.

---

### Post by Jarn on 2007-07-03
> **JacenMandarin said:**
> First off, I appologize for my ignorance but this is the first time I've ever attempted any of this.No big deal. Everyone has to start somewhere. :)

> **JacenMandarin said:**
> bash: C:\Program Files\Guild Wars\Gw.exe: command not foundThat's odd, it seems to be thinking you're trying to run that as a command. Rather, the command is wine and you're telling wine to run that... did you copy and paste the line I gave you exactly? You could also try this (delete the old error.log first):
```
wine ~/.wine/drive_c/Program Files/Guild Wars/Gw.exe 2>~/error.log
```Normally wine likes to be passed the full windows address but that should work also.

> **JacenMandarin said:**
> Should I rename drive_c to C?Definitely not! That would cause many, many problems.

---

### Post by JacenMandarin on 2007-07-03
Thanks. I'll try that tonight when I get home. :)

---

### Post by JacenMandarin on 2007-07-04
When I try and post the error log here, the forum keeps saying I'm trying to post a bunch of images which I'm not.

---

### Post by Jarn on 2007-07-04
Paste it into pastebin, then. Or upload it somewhere else.

---

### Post by Jarn on 2007-07-04
Well, people, I just got banned from Guild Wars for "using third-party programs". As I have never used third-party programs nor even farmed (not to my taste) I fear that Wine might be the culprit. This would surprise me however as a member of NCSoft said, and I quote, "We won't ban you for running on linux using an emulator. Do be aware, however, that we do not support non-Windows environments so if you encounter any issues our support team probably won't be able to assist you." ([http://www.guildwarsguru.com/forum/showpost.php?p=2496004&postcount=4](http://www.guildwarsguru.com/forum/showpost.php?p=2496004&postcount=4)). I'm sending them a question right now, pleading my case, but I doubt they will care. Apparently they say they "have no appeal process" so it will probably be ignored.

---

### Post by Jarn on 2007-07-04
I have now been unbanned. I have no idea if it was related to playing Guild Wars in Wine at all.

---

### Post by kspn on 2007-07-04
As a general question.

Is it possible to run Guild Wars in either VMWare or Virtual Box?

Fast is not a priority.8-[

---

### Post by erk on 2007-07-04
> **kspn said:**
> As a general question.

Is it possible to run Guild Wars in either VMWare or Virtual Box?

Fast is not a priority.8-[

I don't think they support Direct X so it probably won't launch.

---

### Post by erk on 2007-07-04
I  have Guildwars running under Wine 0.9.39/Ubuntu 7.04 on an IBM Thinkpad R52 that has the Intel 915GM graphics chip, it's only getting about 2-3 FPS, under XP the same machine gives about 18-20FPS.

The X11 driver config is:

Section "Device"
  identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
  boardname "Intel 915"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
EndSection



And the modules are:

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
EndSection



Any other tricks you can think of to get Wine up to about the same speed as XP?

---

### Post by JacenMandarin on 2007-07-05
Well, I got it running, at least to the sign in screen using this command:

wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -dx8 -noshaders -windowed >/dev/null 2>&1

that I found here: [http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine)

Unfortunately it was extremely slow and the mouse kept disappearing. Any idea what my next move should be?

This is the error log: [http://pastebin.com/942821](http://pastebin.com/942821) 

This is th log from before: [http://pastebin.com/942823](http://pastebin.com/942823)

---

### Post by Biffa2001 on 2007-07-07
Hi all,

Thanks for this useful guide. I have GW running almost ok using the setup script in the first post here and also the guide at [http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine).

I am running GW.exe with -dsound -dx9 -noshaders as I found this gave the most stability and I also run it as Win 2000 in winecfg.

The problem I am having is I am loading ok, selecting a party ok and going out to do missions ok but they for some unknown reason the game will just hang. Sometimes it's after a few minutes, sometimes sooner or longer - but it's been no longer than 5 mins max.

I have all the graphics set to absolute rock bottom.

Any clues as to what else I can try please?

---

### Post by buttons on 2007-07-07
Couple of things:

I just tried this for the first time today and WOW!  Upwards of 150 fps at points!  I was able to play for about 20 minutes before I got really annoyed by the lack of battle sounds.  I didn't need to use the lights patch, and my command line switches were -dsound -dx8 -noshaders.

Speaking of battle sounds, there was a patch submitted a day or two ago that fixes them, or at least makes them audible once more:

[The bug report]("http://bugs.winehq.org/show_bug.cgi?id=7670")

[The patch]("http://www.winehq.org/pipermail/wine-patches/attachments/20070705/e721d6e4/0002-Fix-bug-preventing-correct-calculation-of-the-sound.obj")

If I wasn't lazy I'd patch this up myself and try it ;)

---

### Post by Jarn on 2007-07-07
> **Biffa2001 said:**
> for some unknown reason the game will just hang. Sometimes it's after a few minutes, sometimes sooner or longer - but it's been no longer than 5 mins max.This sounds like the "too many concurrent lights" error. Try running it from the terminal and next time it freezes see what the terminal says. If it is it will have a lot of "what to do ??" repeated many times with a "too many concurrent lights" error at the beginning of those.

> **buttons said:**
> [The bug report]("http://bugs.winehq.org/show_bug.cgi?id=7670")

[The patch]("http://www.winehq.org/pipermail/wine-patches/attachments/20070705/e721d6e4/0002-Fix-bug-preventing-correct-calculation-of-the-sound.obj")Oh my! I will have to look into this. It may not be for awhile, though - I'm trying to get my Assassin all three Protector titles (hehe) so someone else may be better suited.

---

### Post by Biffa2001 on 2007-07-08
> This sounds like the "too many concurrent lights" error. Try running it from the terminal and next time it freezes see what the terminal says. If it is it will have a lot of "what to do ??" repeated many times with a "too many concurrent lights" error at the beginning of those.

I thought that but I don't get an error - jsut when I switch back to the terminal I can see my normal login details that just repeat over and over again (like I have just pressed "enter" in my terminal window 100 times!).

I think I may have solved my personal GW issues tho as I have moved over to Cedega!

---

### Post by ObiWan2001 on 2007-07-13
wine-0.9.41:

Battlesounds working
-dsound/-nosound no longer nessesary for me

---

### Post by buttons on 2007-07-13
> **ObiWan2001 said:**
> wine-0.9.41:

Battlesounds working
-dsound/-nosound no longer nessesary for me

Ahh! Damn! You beat me to it!

> Romain Iehl (3):
      dsound: Fix bug preventing correct calculation of the sound parameters
      dsound: Simplify the calculation of sound attenuation due to distance.
      dsound: Correct field access.

Yes!

EDIT: I still need the -dsound switch.

---

### Post by buttons on 2007-07-14
For the record, the concurrent lights fix is still needed, and the patch still applies correctly (and works quite well).

Simply edit the script on the front page to change the wine version from 0.9.40 to 0.9.41, and you're good.

---

### Post by Azakus on 2007-07-15
Hmm. Is anyone else getting these error messages?
[[IMG]http://img486.imageshack.us/img486/7535/gwerrorhw9.th.png[/IMG]](http://img486.imageshack.us/my.php?image=gwerrorhw9.png)
It may be my new video card, an XFX nVidia 8600 GT XXX, but I don't think so. I've never had this happen before. If it's not just me, it may be a regression in the code for Wine.
{EDIT} Nope, I've determined this to be a botched driver install. Fixed it, message is gone.

---

### Post by ChaOConnor on 2007-07-15
Hi!

How do I uninstall this?  I used the patch from the first page, but now that I've gotten to the end of the thread it looks like I should have changed the version to .41 but I already ran it for .40.

What should I do?  Should I just install Wine .41?  Please advise, thank you!

---

### Post by Azakus on 2007-07-16
> **ChaOConnor said:**
> Hi!

How do I uninstall this?  I used the patch from the first page, but now that I've gotten to the end of the thread it looks like I should have changed the version to .41 but I already ran it for .40.

What should I do?  Should I just install Wine .41?  Please advise, thank you!

You can just run the script again, but replace VERSION=0.9.40 wit VERSION=0.9.41 at the top of the script.

---

### Post by ChaOConnor on 2007-07-16
So if I already have the latest version of Wine installed, why do I need to run the script?  Shouldn't I be able to just execute the GWSetup using wine and be done with it?  Just curious... otherwise I'll re-run the script tonight.

---

### Post by Azakus on 2007-07-16
> **ChaOConnor said:**
> So if I already have the latest version of Wine installed, why do I need to run the script?  Shouldn't I be able to just execute the GWSetup using wine and be done with it?  Just curious... otherwise I'll re-run the script tonight.

Just install GW if you have the latest wine installed. Wine 0.9.41 is almost a necessary upgrade because it fixes battlesounds in Guild Wars that until now have been broken. No need to reinstall 0.9.41 if you already have it, but if you only have 0.9.40 I would suggest upgrading.

---

### Post by ChaOConnor on 2007-07-18
Okay, now I keep getting a 
"Unable to initialize 3D output.  Please verify that you have installed DirectX 8 and an updated video driver."

I ran Winecfg and added the d3d8.dll to the Wine Library and re-ran... no luck.  Please help!  After that error the install just quits.

Thanks!

---

### Post by der_joachim on 2007-07-22
Hmmmm... Since tuesday I have't been able to login. There was a big update which installed quite nicely, but when it tries to open a login screen, X just freezes. 

I tried the following things, all without success:
* - nosound / -dsound switches. 
* tinkered around with directX versions.
* Changed alsa driver back to oss in winecfg
* Changed windows version back to 98 (from 2000)
* created a custom X session, started from CLI. 
* tried both with and without winedebug
* Tried both vanilla and patched wine version.

The error.log is zipped and attached.

---

### Post by Azakus on 2007-07-22
> **der_joachim said:**
> Hmmmm... Since tuesday I have't been able to login. There was a big update which installed quite nicely, but when it tries to open a login screen, X just freezes. 

I tried the following things, all without success:
* - nosound / -dsound switches. 
* tinkered around with directX versions.
* Changed alsa driver back to oss in winecfg
* Changed windows version back to 98 (from 2000)
* created a custom X session, started from CLI. 
* tried both with and without winedebug
* Tried both vanilla and patched wine version.

The error.log is zipped and attached.

Same problem for me. Newest update killed Guild Wars I think.

---

### Post by Jarn on 2007-07-22
Well, I do believe that whoever said I should have a constant address for the concurrent lights patch was correct - I'm on vacation and cannot update my script.

---

### Post by Azakus on 2007-07-25
For everyone getting the weird error where Guild Wars appears to crash before the login screen, I've found a workaround. Add -windowed to the launcher at it will work. It looks like Guild Wars keeps trying to do fullscreen to a extremely tiny 1x1 pixel arrangement in the bottom left corner of the screen and will crash if you try to resize it. -windowed takes care of that.

---

### Post by wittewol on 2007-07-25
For all those people who like to fix problems, try this one 

execpt for  a couple of pages of fixme:dxdiag stuff

GW chookes on this error

err:d3d:IWineD3DImpl_CheckDepthStencilMatch unsupported format pair: WINED3DFMT_A4R4G4B4 and WINED3DFMT_D24S8

don't no how to solve the problem maybee you can

thxs

---

### Post by amlucent23 on 2007-07-25
Just out of curiosity, and because I want to dump windows, has anyone gotten this working smoothly with an ATI card? I had alot of trouble last time I attempted a few months back.

---

### Post by Azakus on 2007-07-25
Got a new version of my script with the CS:S hack to stop the random crashes in Counter Strike.

---

### Post by der_joachim on 2007-07-26
> **Azakus said:**
> For everyone getting the weird error where Guild Wars appears to crash before the login screen, I've found a workaround. Add -windowed to the launcher at it will work. It looks like Guild Wars keeps trying to do fullscreen to a extremely tiny 1x1 pixel arrangement in the bottom left corner of the screen and will crash if you try to resize it. -windowed takes care of that.

Confirmed, with one thing to add: I need either -dsound or -nosound as well. I prefer -nosound since sound is horribly choppy with dsound. 

Thank you for the tip. :)

---

### Post by RayneStorm on 2007-07-26
I have successfully installed Diablo II LOD and with wine last week in Feisty and it works way better here than it ever did in windows... 

So I decided to try and install Guild Wars hoping for the same luck... I have followed the guide on [http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine]("http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine") and I can get the login screen to come up by typing```
 WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -dx8 -noshaders -windowed >/dev/null 2>&1 

```.  However I can't type in my information on the screen... everything i type is being entered in my terminal box...  I'm sure I'm just missing something or haven't checked some box that I was supposed to, but I have researched for 2 hours and can't figure out anything...  

Thank you much!

Ben

---

### Post by kspn on 2007-08-08
Hi All,

This guide was **great** for getting guild wars working on my system.

I have a question tho.

How much of a difference does the graphics card make for the Guild Wars Game under WINE?

I am running integrated at the moment and I am wondering if I will see any benifit if I get an external Graphics Card?

---

### Post by Lordmarshal on 2007-08-08
ok i have a few problems... first when i start up guildwars in Wine .9.4 i got a bunch of these in terminal...

fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x2270020 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x2270020 ) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x2270020 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x2270020 ) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x2270020 ) : stub
 
and now i get this too

fixme:advapi:SetFileSecurityW (L"C:\\Program Files\\Guild Wars\\Gw.tmp") : stub

---

### Post by Linendail on 2007-08-08
**EDIT2: While referring to script, I talk of the compiling script and winestuff fetcher.**

Cheers for the script, but...

I decided to try it out even tho I had no "lights" problems. Only thing I was actually suffering of while running Guild Wars before scripting, was damn slow frame rates, like... 0.1 - 3 frames /second. I'm dual booting, and my system runs gw with full settings in Windows with fps'es ranging from 35 to 60. There fore I'm pretty sure this is not a plain hardware problem. I uninstalled wine (0.9.42) and run the script.

After running the script I run into problems. Previously completely functional ALSA started giving me this error while loading winecfg:
```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
```

Also, browsing to my wine registry, revealed that there was no direct3D section under h_key_current_user\software\wine\

Needless to say, this has dramatically affected my use of windows software on wine. Lots of them stopped working and lack of ALSA made some of them much less comfortable to use.

I guess I should not have used the script then? Who knows. Maybe something I had installed previously caused a conflict with it. But at least I now know this might happen - and now so do you.

Anyway, right now I'm going for a clean install of Kubuntu, and as I have hope in this approach,  I will run the script once more when I get it done - and report back with results.

If any of you recognizes my problem from what I have described or has any ideas, any and all tips and ideas are welcome.

**EDIT**
[COLOR="SeaGreen"]Problem solved, thanks for the great script![/COLOR]

Reinstalled an removed all files related to wine, any of the libraries this script installs, and all the files it downloads etc. and installed ati's commercial video card drivers, unlike last time, before running the script. Not sure if it was the clean install or the drivers that did it, but it works nicely now - except for the sounds. [COLOR="DarkRed"]Wine is, again, lacking ALSA as an option, and that DOES bother me alot. I would appreciate if anyone could tell me why it isn't there, as I liked it.[/COLOR]

Just in case you experience similar problems, my hardware is as follows: AMD 64 3500+ // ATI Radeon 9800 Pro 256MB // 2GB RAM // nForce 3 Motherboard (EPoX 9NDA3).

Once more, thank you. Now that I have Guild Wars on linux, I can drop my daily reboots into Windows.

---

### Post by Jarn on 2007-08-08
> **Linendail said:**
> I guess I should not have used the script thenI am sorry that I do not know how to fix your problem but I can say that the script did not break it. What the script does will do nothing for someone without the concurrent lights fix. All that it does is change the "Too many concurrent lights" error from something that makes Wine stop itself to something Wine ignores - if you aren't getting it it would not impact you at all.

---

### Post by Linendail on 2007-08-08
> **Jarn said:**
> I am sorry that I do not know how to fix your problem but I can say that the script did not break it. What the script does will do nothing for someone without the concurrent lights fix. All that it does is change the "Too many concurrent lights" error from something that makes Wine stop itself to something Wine ignores - if you aren't getting it it would not impact you at all.

Ack, sorry! When I talked about script, I referred to the compiler. I never used the "concurrent lights" script, I only used the compiler and wine installer part... and it got Guild Wars working, on the second try although, after doing a clean install of Kubuntu. Something I had not managed to do before, Big thanks for that. Only thing bothering me is the lack of ALSA from the Wine sound driver selection. Do you know of a way to enable it, or is it out for a reason?

---

### Post by Sneo on 2007-08-08
```
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??

```

Im just getting that over and over again. Any ideas?

---

### Post by darksong on 2007-08-08
> **kspn said:**
> Hi All,

This guide was **great** for getting guild wars working on my system.

I have a question tho.

How much of a difference does the graphics card make for the Guild Wars Game under WINE?

I am running integrated at the moment and I am wondering if I will see any benifit if I get an external Graphics Card?

Even though guildwars is not reasource hungry. A dedicated graphics card WILL lighten the load on the rest of your system and undoutedly give much better frames per second.

---

### Post by buttons on 2007-08-08
> **Sneo said:**
> ```
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??

```

Im just getting that over and over again. Any ideas?

Hmmm...first post in the thread?

---

### Post by Jarn on 2007-08-09
> **Sneo said:**
> ```
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??

```

Im just getting that over and over again. Any ideas?

It could be that you aren't running it with the -dsound flag or it could be that you don't have the concurrent lights patch. Or it could be something else that I have not yet encountered. ;)

If you aren't using -dsound, try that. If you are using -dsound then compile it with the concurrent lights patch. If you are doing both of those then I don't know what to do.

---

### Post by Sneo on 2007-08-12
mmm.. fixed that wasn't using the -dsound tag!

Now I'm getting this error, again in the hundreds.


err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support

Any reccomendadtion of what libgl package to get?

---

### Post by laforge on 2007-08-13
I seem to have a few problems with GW in Wine.  I can't see my mouse which makes me quite sad as it is hard to click things without seeing it.  And when I switched workspaces it crashed while loading all the files.  new install by the way.  I did have Beryl running so that might not of been the best idea and it lags a bit but I do have like a 5 series PCI Nvidia card on this so I guess I would expect that.

I was just wondering if anyone has ran into these problems and knows any fixes.  I will continue searching through this thread but 60+ pages is a lot. :(

---

### Post by Jarn on 2007-08-13
> **Sneo said:**
> mmm.. fixed that wasn't using the -dsound tag!

Now I'm getting this error, again in the hundreds.


err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support

Any reccomendadtion of what libgl package to get?Sounds more like a Wine problem than a Wine+GW problem, try asking in #winehq.

---

### Post by Jarn on 2007-08-13
> **laforge said:**
> I can't see my mouseWhat version are you using? You need to be using a version >=0.9.34 to see your cursor.

---

### Post by laforge on 2007-08-13
Hrmm ok I upgraded to the latest version of wine, lets see if it works now.  Should I be getting any sluggish gameplay with a 5200 Gforce?  Even the login screen runs a bit badly.

---

### Post by MonkeyBoy on 2007-08-13
I am using an FX5200 and I do get some slow bits.  It seems to not like water textures particularly.  It is perfectly playable the rest of the time though.

---

### Post by laforge on 2007-08-13
Hrmm ok, I turn everything down and it seems to run better now.  I do have a mouse now which is good.  Everything seems to work fine.  Thanks for the help. :KS

---

### Post by Lordmarshal on 2007-08-14
ok i tried doing some of the regedit stuff from wine appdb... but i went to the wine folder and i have no direct3d folder in there to add stuff to. so could someone help me out if i did something wrong of forgot something while i did the install. i installed .9.42 with the -dev. its wat works best with guildwars supposedly so im gonna hopefully give it a try.

---

### Post by amlucent23 on 2007-08-15
> **amlucent23 said:**
> Just out of curiosity, and because I want to dump windows, has anyone gotten this working smoothly with an ATI card? I had alot of trouble last time I attempted a few months back.

anybody? beuller... beuller... beuller

---

### Post by Lordmarshal on 2007-08-15
is there anything i can do to get rid of this fixme??

fixme:advapi:SetFileSecurityW (L"C:\\Program Files\\Guild Wars\\Gw.tmp") : stub

---

### Post by buttons on 2007-08-15
> **Lordmarshal said:**
> is there anything i can do to get rid of this fixme??

fixme:advapi:SetFileSecurityW (L"C:\\Program Files\\Guild Wars\\Gw.tmp") : stub

It's harmless, but if you don't like looking at it, start your program like this:

```
env WINEDEBUG=-all wine blah blah blah
```
or in a script,
```
export WINEDEBUG=-all
wine blah 
```

Should speed up most wine games as well.

---

### Post by Kementari on 2007-08-18
Hello,

So I've got GW running almost as good as I'd want it, with just two issues:

1. I'm using two monitors, of different resolutions. GW opens by default on the first monitor (a regular 19'') which is fine, but when I move the window to my widescreen, I am unable to resize the window larger than 1280*1024. Is this a X problem? I've been thinking of swaping the monitors, and running nvidia-config again to generate a new xconfig file with the monitors swaped.

2. I have no sound. My settings on the Audio tab are: ALSA audio driver, Hardware Emulation: Emulation, with the driver emulation box checked. The -dsound switch didn't seem to have any affect.

Lastly, I was wondering, what are the odds that the upcomming expansion GW:EN would break things?

---

### Post by Polygon on 2007-08-19
if it breaks something, then it will effect all 4 gw games as they all run off the same engine. so if something does break then im sure it will be addressed in a wine update....hopefully.

---

### Post by kspn on 2007-08-19
Hi all, I have a Z-Board Keyboard and I was wondering if anyone had gotten it working with the Guild Wars insert under Linux?

It would be really cool if I could get it working (else I have an interesting paperweight)

---

### Post by Kementari on 2007-08-22
Well the monitor issue I had was quickly fixed by swapping my monitor cords and fixing my xconfig file. It seems like something in Wine only looked at the first monitor when deciding max window size.

So that leaves sound as the only thing keeping me from having GW running perfectly. I've tried nearly every driver setting, and nothing has worked. Well, almost nothing. OSS worked for a little bit, but then for no apparent reason, it stopped working, and I can't get the sound back again. Around the same time, Amarok started crashing, I'm not sure if that was related to messing with driver settings, or some incompatibility with Wine's sound and Amarok.

Any ideas? Do I need some additional driver library to get this working properly?

Thanks!

---

### Post by azurelight1337 on 2007-08-24
My Guild Wars just freezes after the downloader thing is done...
[[IMG]http://img400.imageshack.us/img400/5330/screenshot2li7.th.png[/IMG]](http://img400.imageshack.us/my.php?image=screenshot2li7.png)
Help... :confused:

Also appears that I get this...
fixme:dbghelp:SymInitializeW what to do ??

Edit#2:

Ok, that's answered a few pages back, but how do I do the -dsound thing?

Edit#3:

And for looking like a complete noob, I fixed it. -dsound didn't work, but -nosound does. I have a login screen. Now to hope everything works in the game now... XD

---

### Post by azurelight1337 on 2007-08-24
And now I have no mouse on the login screen and the game just freezes after I press enter to login... :(

Edit: It appears my wine version was changed, so I'll try reinstalling the script...

Edit2: It works, but now my login screen has no background image and it's REALLY slow...

---

### Post by Ziggyz on 2007-08-25
how do you get the resolution to work? My game keeps crashing, and I have looked for a while to try to figure out how. Video settings dont work with Cedega, wine, Crossover Pro (Office). This is really starting to frustrate me.

At least CrossOver and Wine run it, without sound of course. Cedega wont get past teh video card unsupported error. Can anyone help me?

---

### Post by azurelight1337 on 2007-08-28
I got mine working by enabling the ATI Driver in the Restricted Drivers menu, and now it works fine.

---

### Post by amlucent23 on 2007-08-31
Well I have tried to fully ditch windows on my gaming machine several times now and could never get my only game I play (guild wars) working. I even purchased a subscription to cedega at one point, I got horrable results with zero support for my trouble. So as a gluton for punishment, I have decided to give wine and GW a shot. 

First I would like to say that I already have better luck than I had with cedega. What kind of frame rates are you guys getting though? I am currently getting about 5-9 fps when doing any activity and about 12fps spikes in optimal conditions and load (the same system gets around 30-40 consistently in XP) are there any tricks I am not aware of... or is it that ATI nix drives are still that bad?

wanting to know if I should just buckup and buy nvidia.. but then again... Ill want to upgrade to pci-e.. which means a new mobo/chip/ram... whole new pc basically. Will that solve my woes?

btw.. I am running this cmd to play gw

```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed -dx8
```

---

### Post by Polygon on 2007-08-31
i think its just the fact that the game is running through wine.... you really cant expect it to run amazingly well when its not only converting from windows to linux commands, but directx to opengl commands as well

im getting like 12-17 fps

---

### Post by amlucent23 on 2007-08-31
> **Polygon said:**
> i think its just the fact that the game is running through wine.... you really cant expect it to run amazingly well when its not only converting from windows to linux commands, but directx to opengl commands as well

im getting like 12-17 fps

I think I would murder for 12-17 fps.. that is at least playable. hmm.. I am thinking that a faster system would give me better FPS. I only have a athlon 64 2800+ (single core) and a ATI x1600 (agp). Ill just try again when I get a new PC.

---

### Post by cor2y on 2007-08-31
i get 15-29 fps when i am running via wine.
This is on a good day when the net connection is really flowing.

My system
ATI X850XT
1gb pc2700 ddr ram
Athlon XP 2800

On the bad days i stutter and stammer at 6-14fps and lose connections when i am instanced, i'll be in an area and suddenly the game will freeze and then resume but i can't move but i can turn left and right etc and all the monsters will just stand around and i will know i have lost net connection.
Don't know if its wine or the network.
This has happened with the last three wine updates but its not a game breaker.

---

### Post by blueamcat on 2007-09-01
I just got Guild Wars, so we'll see if I have to do any tweaking to make it work. Currently installing. Running Ubuntu 7.04 Feisty Fawn.

---

### Post by blueamcat on 2007-09-01
Okay, so installed, and tried to run. Got some error that wanted me to make sure I had DirectX 8 installed. Or maybe 9. I'm updating Wine now. Not sure which version I had because I'm fairly new to Ubuntu/Linux...only a few months old in this stuff.

---

### Post by dj_p03t on 2007-09-01
> btw.. I am running this cmd to play gw

```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed -dx8
```

i ran the command and got this then the game ran slow as heck jerky laggy slow downloads... maybe im screwing up? i am a total noob @linux used it for a few weeks about a year ago (fedora core 6) and now using ubuntu (I LOVE IT) but still total noob

```
dustin@dustin-laptop:~$ WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed -dx8
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering

```

---

### Post by Ferrat on 2007-09-01
> **dj_p03t said:**
> i ran the command and got this then the game ran slow as heck jerky laggy slow downloads... maybe im screwing up? i am a total noob @linux used it for a few weeks about a year ago (fedora core 6) and now using ubuntu (I LOVE IT) but still total noob

```
dustin@dustin-laptop:~$ WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed -dx8
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering

```

bring up a terminal windows and type 
```
 glxinfo | grep rendering

```

You should get this printout

```
direct rendering: Yes
```

---

### Post by mist_01 on 2007-09-02
> **Ferrat said:**
> bring up a terminal windows and type 
```
 glxinfo | grep rendering

```

You should get this printout

```
direct rendering: Yes
```

I get a no, what should i do.

---

### Post by amlucent23 on 2007-09-02
> **mist_01 said:**
> I get a no, what should i do.

If you have an ATI or Nvidia card that means that your correct video card drivers are not installed or at least not installed properly.

easiest way to install them is through restricted driver manager or you can do it the hard way and install them with driver from your card manufactures website.

EDIT:

sorry forgot to mention, the restricted drivers section is accessed by going to System, Administration, Restricted Driver Manager

---

### Post by Ferrat on 2007-09-03
Som tips and trix that helped me get Guild Wars running with good FPS (20-50 when questing ect, 10-20 in towns) using either latest wine (0.9.44 or the 0.9.42 with lightsfix)

never emulate winXP with wine, use Win98 or Win2000 instead 
you get the fixme:dbghelp:SymInitializeW what to do ?? bug alot less (almost never) 

open regedit 
```
wine regedit
```

Add the following values

HKEY_CURRENT_USER > Software > Wine > Direct3D
new string value = DirectDrawRenderer - opengl
new string value = VideoMemorySize - (your real videoRAM size, in my case 256 since wine by default sets it to 64) 
(look at thumb #1 for how it should look)
[COLOR="Red"]Warning! Regedit is case sensitive [/COLOR]

Set sound in winecfg to 
Hardware acc. Full
Sample rate: 22050
Bits per Sample: 16
and check Driver Emulation.
(look at thumb #2 for how it should look)
[COLOR="Red"]I use OSS driver for sound but for some ALSA works better, try them both and see what works for you[/COLOR]

Allways start GW with the 
-dsound [COLOR="Blue"]- needed for better sound[/COLOR]
sound
-noshaders[COLOR="Blue"] - isn't allways needed I get better FPS with out this but one of my comps becomes more unstable.[/COLOR]

-dx8 [COLOR="Blue"]- I never use this, atleast for me dx8 has more problems then running just normal with dx9 and my FPS goes way down with dx8[/COLOR]

-windowed[COLOR="Blue"] - In later versions of wine it isn't needed since GW can now managed windowed mode ect for itself.[/COLOR]

Inside the game make sure to set the sound option Use 3D Audio Hardware [COLOR="Red"](thumb 3)[/COLOR]

For grafic settings try to use the detected settings, often work best, however sometimes if you get a problem with the ground not showing up ingame and just see a reflection of the sky, try setting [COLOR="Blue"]terrain quality[/COLOR] to [COLOR="Red"]LOW[/COLOR], this usally brings back the ground :)

Will add more when I come to think of them :) 
I know most if not all (and other things that help) can be found on the appdb ect. but looking thru this thread seems alot of people miss them anyway, hope this helps abit :)

---

### Post by mist_01 on 2007-09-03
I am having a problem with GW.  I ran the script and am using WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed -dx8 
to run it.  However, the graphics apear very blockly.  (eg. when the smoke or snow moves across the load screen they apear as 40px wide boxes).  I have not yet finished downloading all of the dat file but i don't think that is my problem.  Please let me know if you have any ideas as to how i can fix this.  P.S. it seems to be running fairly soomthly from what i can see so far.

---

### Post by Ferrat on 2007-09-03
> **mist_01 said:**
> I am having a problem with GW.  I ran the script and am using WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed -dx8 
to run it.  However, the graphics apear very blockly.  (eg. when the smoke or snow moves across the load screen they apear as 40px wide boxes).  I have not yet finished downloading all of the dat file but i don't think that is my problem.  Please let me know if you have any ideas as to how i can fix this.  P.S. it seems to be running fairly soomthly from what i can see so far.

Yes this is a problem running without shaders I think, altho I get the same even without the -noshaders switch 
never seen it on Win bot it would be my guess however ingame you wont notice anything like that altho you will notice the prerendered fillers appearing as white, pink, green boxes but nothing major there unless you really really care about the looks since when you  get closer and the true 3D object is rendered you see it just as everyone else :)

---

### Post by mist_01 on 2007-09-04
Sounds good, once it gets done downloading i will try it.  That is the one other thing tho.  I should be getting close to 500kb/s but i am getting only like 13 when loading an area.  Anyone know if this can be imporved?
Thanks, you guys have made switching to Linux much easier :)

Edit: also, no sound..

---

### Post by gavinjb on 2007-09-06
Hi,

I just found this topic, I have installed guildwars with wine previously (through repo), but I had no mouse most of the time and it was a bit unstable, so I uninstalled and have since tried using the script, which has made guildwars more stable and has given me my mouse pointer :)

Only problem is I now the sound has completely gone (logon screen, in game + battles)

The settings I have configured for sound are:
Hardware Acceleration - Full
Default Sample Rate - 22050
Default Bits Per Sample 16
Driver Emulation - Yes

Sound Drivers:
EsounD Driver
OSs Driver (Ticked)
NAS DRiver

I think before I removed the version in the repo from my machine I had ALSA, but cant say 100%.

---

### Post by Ferrat on 2007-09-06
have you checked the "Use 3D audio hardware" in Guild Wars option?

do you start the game with the -dsound switch?

---

### Post by gavinjb on 2007-09-06
Hi,

These are the options I used to start GW

```

wine Gw.exe -dsound -noshaders flags -repair -image -dx8
```

When I goto the sound options in GW both "Use 3D Audio Hardware" and "Use EAX" are disabled/greyed out

---

### Post by Ferrat on 2007-09-06
> **gavinjb said:**
> Hi,

These are the options I used to start GW

```

wine Gw.exe -dsound -noshaders flags -repair -image -dx8
```

When I goto the sound options in GW both "Use 3D Audio Hardware" and "Use EAX" are disabled/greyed out

Then open winecfg and follow the sound setup in this post
[http://ubuntuforums.org/showpost.php?p=3301605&postcount=659](http://ubuntuforums.org/showpost.php?p=3301605&postcount=659)

---

### Post by gavinjb on 2007-09-07
Hi,

Thanks I had already made those changes, I have confirmed that the problem seems to be a wine + guildwars problem and not wine as I tried running Neverwinter Nights CD under Wine and I got the intro music.

Gavin,

---

### Post by mist_01 on 2007-09-07
Thats the same thing i have, exactly.

---

### Post by gavinjb on 2007-09-08
Well I had some luck lastnight and managed to get it to work, not sure exactly what I did that fixed it, but this is what I did.

1. I ran winecfg and added an app link to GW.exe and then configure the sound driver by removing OSS as the ticked driver and selected EsounD Driver

2. Uninstalled Wine and Installed Wine through Synaptic (sound worked but very unstable and slow)

3. Uninstalled and ran the install Script again

4. made sure I had the SounD Driver set under App GW.exe and ran GW.

5. All worked.

---

### Post by Ferrat on 2007-09-09
great =) 

btw anyone know how to limit the amount of RAM that wine can use, I get some problems when running for awhile Guild Wars uses all the RAM and I think when it tries to clear the system freezes as if the system doesn't have RAM to operate fast enough to clear it and I have to ALT+F4 and force quit and restart, takes only like 10-20seconds but would be great not to have to do this.

---

### Post by mist_01 on 2007-09-09
I still am having a lag problem.  It appears that GW is not using enough bandwith.  I should have plenty for it to run several times over with out lagging but the loading and in game speed is slow.  Is there a way i can config GW or Wine to allow it to use more bandwith?

---

### Post by mist_01 on 2007-09-09
> **gavinjb said:**
> Well I had some luck lastnight and managed to get it to work, not sure exactly what I did that fixed it, but this is what I did.

1. I ran winecfg and added an app link to GW.exe and then configure the sound driver by removing OSS as the ticked driver and selected EsounD Driver

2. Uninstalled Wine and Installed Wine through Synaptic (sound worked but very unstable and slow)

3. Uninstalled and ran the install Script again

4. made sure I had the SounD Driver set under App GW.exe and ran GW.

5. All worked.

the EsounD worked for me now too, however, i am still looking for a bandwith solution.

---

### Post by gavinjb on 2007-09-10
Thanks for all the help.

Ferrat I might have the same problem as you, as every now and then my machine locks up completly and I have to do a Ctrl + Alt + Backspace, this usally happens when I go from one area to the next most commonly when entering a town.

---

### Post by Ferrat on 2007-09-10
> **gavinjb said:**
> Thanks for all the help.

Ferrat I might have the same problem as you, as every now and then my machine locks up completly and I have to do a Ctrl + Alt + Backspace, this usally happens when I go from one area to the next most commonly when entering a town.

Yes that happens me sometimes aswell but for me it's more often if I've just been in town then start a misson/quest, but I just have to restart GW not X, I got 1,5GB RAM and GW's start taking like 500MB and that's cool then if I jump between alot of areas it's as if doesn't clean up but just builds and builds until it's too much, then when it tries to drop some it freezes, I can wait sometimes like when loading but ingame if I wait it takes to long and I get disconnected.

---

### Post by gavinjb on 2007-09-10
[quote]
Yes that happens me sometimes aswell but for me it's more often if I've just been in town then start a misson/quest, but I just have to restart GW not X, I got 1,5GB RAM and GW's start taking like 500MB and that's cool then if I jump between alot of areas it's as if doesn't clean up but just builds and builds until it's too much, then when it tries to drop some it freezes, I can wait sometimes like when loading but ingame if I wait it takes to long and I get disconnected.
[quoe]

Well my machine is a fairly good spec with 2GB of ram, I will have to bear with it, at least you can play GW with the occasional hickup rather than having to have a Win Partition.

Gavin,

---

### Post by Ferrat on 2007-09-10
> **gavinjb said:**
> [quote]

Well my machine is a fairly good spec with 2GB of ram, I will have to bear with it, at least you can play GW with the occasional hickup rather than having to have a Win Partition.

Gavin,

True, but why can't you get it running under Linux? there is even a install script in this thread I think =)

---

### Post by Azakus on 2007-09-10
I thinks it's been a while since I posted my 64-bit install script. So here it is, ready to go for WIne 0.9.44. I rewrote alot of it, so use this one (64-bit compile doesn't need some configure flags it needed before)
I also included a Counter-Strike patch to make CS work better if you're also using Steam.

---

### Post by mist_01 on 2007-09-11
Just wondering again if anyone has any idea about the bandwidth thing,  GW is only using about a 30ith of the availible bandwidth.

---

### Post by Ferrat on 2007-09-12
> **mist_01 said:**
> Just wondering again if anyone has any idea about the bandwidth thing,  GW is only using about a 30ith of the availible bandwidth.

I think it's more of a issue depending on where you live, I get pretty high ping from time to time 

From the Guild Wars home page 
> Latency Issue Update – 15 July

After a period of much-improved latency, some players—primarily in Europe—are experiencing a return of last week's latency problems. We are reviewing posts on fan forum and the Guild Wars Wiki and relaying them to the Network Teams. The Network Teams have asked players who are experiencing latency to send a –diag report or a tracert via a Support ticket. These reports will furnish the team with extremely helpful data that team members can use as they investigate the cause of the problem and find a lasting solution.

Correcting this situation and restoring your ability to play in a lag-free environment continues to be our highest priority, and we thank you for your patience as we continue to work towards a resolution.

---

### Post by Naike on 2007-09-12
Hey great, does it run smoothly, is there any performance or some other issues?
Or is there any other stuff like in wow that they bann you?

---

### Post by Ferrat on 2007-09-12
> **Naike said:**
> Hey great, does it run smoothly, is there any performance or some other issues?
Or is there any other stuff like in wow that they bann you?

first of no one atleast not in the last year or so have been banned from WoW for using wine.. 

No there is no banning, there are some issues

[LIST]
[*] Some people like myself experience crashes due to a memory leak, how much problem you get from it seems to be diffirent, for me it happens just sometimes and it takes 10-20seconds for me to restart and get back in the game.
[*] There are some latency issues but this seems to be Guild Wars and also affect others (mostly people in the EU)
[*] Grafics are good, nvidia get better FPS but *fingers crossed* ati is releasing a new version with a real prefomance boost according to early tests of it.
[*] The rendering of the 3D is great but some stuff in the distance that is pre-rendered won't look good, often just one color boxes or something like that but as you get close it looks better
[*] Some people have sound issues, I've noticed that sometimes when I crash voices in videos starts going in slowmotion sounding very weird
[/LIST]

But all in all it's playable with some small glitches.. 

[COLOR="Red"]*screenshot - ingame during combat ~20-50FPS in windowed mode, easy to switch to fullscreen with same result[/COLOR]

---

### Post by mist_01 on 2007-09-12
> **Ferrat said:**
> I think it's more of a issue depending on where you live, I get pretty high ping from time to time 

From the Guild Wars home page

However, I am doing this on a network with other people who are playing GW on windows machines with out problems.  I am just getting rediculusly low speeds.

---

### Post by Azakus on 2007-09-12
> **mist_01 said:**
> However, I am doing this on a network with other people who are playing GW on windows machines with out problems.  I am just getting rediculusly low speeds.

It might be that you need to open the ports GW needs in iptables. I'm not sure what they are though...

---

### Post by Ferrat on 2007-09-12
> **Azakus said:**
> It might be that you need to open the ports GW needs in iptables. I'm not sure what they are though...

Guild Wars needs the old game favorite 6112

---

### Post by mist_01 on 2007-09-12
How do I do this?  Btw, i do have firestarter installed.

---

### Post by mist_01 on 2007-09-13
Ok, I got the bandwidth problem fixed.  However (go figure) i have found another issue.  I can't use the mouse for some things.  eg i can't pic up my drops (very annoying).  I also can't click on people or npc.  I can't move with the mouse either.  However, i can use the mouse for the menus and to click on skills.  Any ideas?  Thanks again.

---

### Post by gavinjb on 2007-09-13
> **mist_01 said:**
> Ok, I got the bandwidth problem fixed.  However (go figure) i have found another issue.  I can't use the mouse for some things.  eg i can't pic up my drops (very annoying).  I also can't click on people or npc.  I can't move with the mouse either.  However, i can use the mouse for the menus and to click on skills.  Any ideas?  Thanks again.

Are you using the script or did you download wine through synaptics..., as I know when I tried the later I had loads of problems with GuildWars

---

### Post by mist_01 on 2007-09-14
> **gavinjb said:**
> Are you using the script or did you download wine through synaptics..., as I know when I tried the later I had loads of problems with GuildWars

Hmm I used the script posted on the original post on page 1.  That is the one I should be using correct?  However, I might just try a complete reinstall.

---

### Post by Ferrat on 2007-09-14
> **mist_01 said:**
> Ok, I got the bandwidth problem fixed.  However (go figure) i have found another issue.  I can't use the mouse for some things.  eg i can't pic up my drops (very annoying).  I also can't click on people or npc.  I can't move with the mouse either.  However, i can use the mouse for the menus and to click on skills.  Any ideas?  Thanks again.

How did you solve the bandwidth problem? 


the script on the first page if for wine 0.9.32 or something 

attaching a script for wine 0.9.44 with the lightfix

---

### Post by mist_01 on 2007-09-14
> **Ferrat said:**
> How did you solve the bandwidth problem? 


the script on the first page if for wine 0.9.32 or something 

attaching a script for wine 0.9.44 with the lightfix

Getting more of the data file downloaded decreased the lag a lot.  I think that must have been slowing me down, I still don't know why it shows a slow speed, but at least it is playable.

---

### Post by Ferrat on 2007-09-14
Anyone tried the new wine?? 0.9.45?? 
Broke my GW atleast, everything except the landscape became invisible, anyone else that can confirm this??

---

### Post by Ferrat on 2007-09-16
Just ran a regression test on wine 0.9.45  ( 3hours >_< )

well found the problem and have reported it, they where where quick on adressing it since it killed the 3D models i guess som hopefully this will be fixed in the next release :)

---

### Post by gavinjb on 2007-09-17
> **Ferrat said:**
> Just ran a regression test on wine 0.9.45  ( 3hours >_< )

well found the problem and have reported it, they where where quick on adressing it since it killed the 3D models i guess som hopefully this will be fixed in the next release :)

does this mean that GW is running on 0.9.45 ok now then, have you noticed any major differences from running earlier versions?

Also how do I update to 0.9.45 do I need a new script or do I have to download through apt-get (always had problems with GW when used apt-get method)

Thanks,


Gavin,

---

### Post by Ferrat on 2007-09-17
> **gavinjb said:**
> does this mean that GW is running on 0.9.45 ok now then, have you noticed any major differences from running earlier versions?

Also how do I update to 0.9.45 do I need a new script or do I have to download through apt-get (always had problems with GW when used apt-get method)

Thanks,


Gavin,

Right now if you update to 0.9.45 all your 3D models will be invisible ^^ not very playable

but Im testing a patch now that might help

---

### Post by Azakus on 2007-09-19
Don't worry people, already reported twinhair's post as spam. I really hate spam on forums.

---

### Post by mogwai on 2007-09-22
I am having some problems. Guild Wars worked perfectly until I passed the -windowed parameter, and now I can't get back to fullscreen.

I am thinking may be there is a parameter that I have missed?

Any ideas? :confused:


Running: 
Ubuntu 7.04
Wine 0.9.45 from official wine deb repo

---

### Post by Ferrat on 2007-09-22
> **mogwai said:**
> I am having some problems. Guild Wars worked perfectly until I passed the -windowed parameter, and now I can't get back to fullscreen.

I am thinking may be there is a parameter that I have missed?

Any ideas? :confused:


Running: 
Ubuntu 7.04
Wine 0.9.45 from official wine deb repo

The -windowed setting sets the games option to windowed, just go in to option and select a fullscreen mode, that should work, or press the fullscreen button upper right corner or press ALT+ENTER

---

### Post by mist_01 on 2007-09-25
I have been having a problem lately.  A few days ago my GW decided to stop working.  It still launchs, but after the loader the window goes away and nothing more is displayed.  I know it is still running since the prosses is still there and the music plays, but no visual.  I tried reinstalling GW but it made no difference.  Any ideas?  Thanks for any help in advance, it is great that you guys are willing to help.

---

### Post by gavinjb on 2007-09-26
I had a simular problem when I installed Wine through apt-get and a reboot got GW to work again.  

It might also be worth trying to re-install wine incase something has corrupted.

---

### Post by mist_01 on 2007-09-26
restart made no difference, and i installed wine through the script.

---

### Post by dtrot55 on 2007-09-28
Very sorry, I am a big Ubuntu Noob and I am a big GW player...and i am currently new to Ubuntu...so a lot of this is foreign to me.  But I am looking to eventually migrate to Ubuntu and just keep a Windows partition in-case i cant handle some of this still.  My question is a lot of these responses talk about Wine and Edgy ....  Can some one give me a idea of what both of these are? I'm assuming Wine is a installer / compiler or something? Plus I will be using the 64 bit version...so i havent seen  many responses about the 64bit?  Has anyone had issues with Wine installing on the 64bit system?  Also you Nvidia card users....can any of you help me find 6600gs drivers?

Thanks 

Dan <------THE Ubuntu NOOB....but I am learning

---

### Post by gavinjb on 2007-09-29
> **dtrot55 said:**
> Very sorry, I am a big Ubuntu Noob and I am a big GW player...and i am currently new to Ubuntu...so a lot of this is foreign to me.  But I am looking to eventually migrate to Ubuntu and just keep a Windows partition in-case i cant handle some of this still.  My question is a lot of these responses talk about Wine and Edgy ....  Can some one give me a idea of what both of these are? I'm assuming Wine is a installer / compiler or something? Plus I will be using the 64 bit version...so i havent seen  many responses about the 64bit?  Has anyone had issues with Wine installing on the 64bit system?  Also you Nvidia card users....can any of you help me find 6600gs drivers?

Thanks 

Dan <------THE Ubuntu NOOB....but I am learning

Hi Dan, 

Edgy is the previous version/build of Ubuntu (6.10), currently most people are running Ubuntu Feisty Fawn (7.04) and in a few weeks the latest version is released which is code named Gutsy Gibbon (7.10).

As for Wine, wine is a bit of software which to my understanding (correct me if I am wrong) implements certain Windows Libraries and allows you to run a selection of Windows applications and some games under Linux.

With Nvidia Cards you should have a restricted drivers icon on your task bar which should allow you to install the NVidia drivers (I cant tell you much more about this as my Laptop runs ATI)

Gavin,

---

### Post by gavinjb on 2007-09-29
Hi,

I have just to install Wine/Guildwars on my second PC with the Wine 0.9.44 script and all I get is the following when trying to download the source, is this the latest script or should I be using a script for 0.9.45.

```

--12:07:12--  http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.44.tar.bz2
  (try: 4) => `/home/gavin/winestuff/winesource.tar.bz2'
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... failed: Connection timed out.
Retrying.

```

Thanks,



Gavin,

---

### Post by Instigator on 2007-09-29
I've included an attachment to fix your "Connection timed out." problem. Basically just changed the source servers. Also changed from "gutsy" to "fiesty".

64 Bit SH down below.

---

### Post by gavinjb on 2007-09-30
Thanks, one quick question though, what do I need to change to make this work with 32 bit Ubuntu

---

### Post by Sementis on 2007-10-01
Yeah, an updated winebuild.sh (32bit) would be awesome :)

---

### Post by Ferrat on 2007-10-01
> **Sementis said:**
> Yeah, an updated winebuild.sh (32bit) would be awesome :)

Just download the winebuild.sh that's in this thread and edit it in a texteditor just change to 

```
VERSION=0.9.44
``` 

the run it =)

---

### Post by gavinjb on 2007-10-01
Has anyone tried 0.9.46 yet, as I noticed the other it has been released.

---

### Post by Ferrat on 2007-10-01
> **gavinjb said:**
> Has anyone tried 0.9.46 yet, as I noticed the other it has been released.

I get the same problem with 0.9.46 as I get with 0.9.45, no 3D models render and text gets jumbled after a while, the problem has been noticed by the coders.

---

### Post by gavinjb on 2007-10-01
thanks, hopefully when they release 0.9.47 they have fixed it.

---

### Post by gavinjb on 2007-10-01
Thanks for the help, I managed to get the install script for 0.9.44 to run, bot only problem is that GW is not working, I am getting a lot of the Fixme errors in the console when trying to run Gw, can anyone help.

I am not sure what info you will need posted if any.

Thanks,



Gavin,

---

### Post by RuB3N on 2007-10-07
I got GW working long time ago...

but now when i open it through the terminal by

WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders -windowed

it opens but then the screen for the game doesnt pop up.... it only plays the sound


how can i get the screen back?

---

### Post by Drake2k on 2007-10-10
I'm Running wine version 0.9.46
Do I still need to patch?

I got the mouse to work by selecting "Allow DirectX apps to stop the mouse from leaving their window" in the graphics tab in winecfg.  Before it would vanish after zoning and I had to wiggle it around and right click to get it to come up.

The sound works fantastic using OSS (SoundBlaster Audigy)

I had a problem with the game locking up my entire system when I try to exit.  I got that cleared up thanks to another user here by selecting the "Emulate Virtual Desktop" option.

The graphics look great til you play the game.  Everything is tolerable until you get to the snowy regions.  Huge blocks are either blurred out with some strange pattern or they're black or white boxes, until you get close then a tree or house will appear out of nowhere.  Makes it difficult to see targets in the distance.

User nVidia 9600 XFX 256meg  Card.  Latest nVidia drivers.

Any suggestions?

---

### Post by Drake2k on 2007-10-10
> **Drake2k said:**
> 

Any suggestions?


Also,  I tried it with -image as a command line switch.  The areanet downloaded a TON of files, about 2 gigs worth, but when it was finished it just shut down.  When I try to re-launch the game, it will shut itself down as soon as it's done connecting and before I get a log in screen.  So the -image switch I don't think is going to work for me.

Any 'other' suggestions?

---

### Post by Azakus on 2007-10-10
> **Drake2k said:**
> Also,  I tried it with -image as a command line switch.  The areanet downloaded a TON of files, about 2 gigs worth, but when it was finished it just shut down.  When I try to re-launch the game, it will shut itself down as soon as it's done connecting and before I get a log in screen.  So the -image switch I don't think is going to work for me.

Any 'other' suggestions?

All -image does is copy every map and data file that normally is downloaded on a need basis all at once, so it doesn't help that much.

---

### Post by Drake2k on 2007-10-10
> **Azakus said:**
> All -image does is copy every map and data file that normally is downloaded on a need basis all at once, so it doesn't help that much.

Well, as it turns out, the graphics issues aren't nearly as bad in non-snowy fields.  It's the winter zones that are really hard on me.  They're still annoying in all other zones but just not to the point where it's effecting my game play.

---

### Post by nescontroller on 2007-10-11
> **Sementis said:**
> Yeah, an updated winebuild.sh (32bit) would be awesome :)

Here you go

---

### Post by sinaen on 2007-10-11
to get  wine-0.9.46 to work properly i switched to gnome (it was something that i removed when autoupdate or such removed something i needed. and gnome is much more userfriendly)
but i do not know if you have the same troubles the text on the buttons dissapear. and no text whatsoever on the enemies/friends or in the dialouge buttons etc...

have any of you experienced the same problem and solved it? or have you also trouble with this??

---

### Post by Ferrat on 2007-10-12
> **sinaen said:**
> to get  wine-0.9.46 to work properly i switched to gnome (it was something that i removed when autoupdate or such removed something i needed. and gnome is much more userfriendly)
but i do not know if you have the same troubles the text on the buttons dissapear. and no text whatsoever on the enemies/friends or in the dialouge buttons etc...

have any of you experienced the same problem and solved it? or have you also trouble with this??

This is an confirmed issue,  I did a backtrace on this regression when it popped up in 0.9.45, it's a Z-lenght fix for models that creates the problem, most games run better and more stable with this new code but a few like GW and I think it was Homeworld 2 or something didn't like it at all.

---

### Post by sinaen on 2007-10-12
> **Ferrat said:**
> This is an confirmed issue,  I did a backtrace on this regression when it popped up in 0.9.45, it's a Z-lenght fix for models that creates the problem, most games run better and more stable with this new code but a few like GW and I think it was Homeworld 2 or something didn't like it at all.

Bugger!

---

### Post by Drake2k on 2007-10-12
> **sinaen said:**
> to get  wine-0.9.46 to work properly i switched to gnome (it was something that i removed when autoupdate or such removed something i needed. and gnome is much more userfriendly)
but i do not know if you have the same troubles the text on the buttons dissapear. and no text whatsoever on the enemies/friends or in the dialouge buttons etc...

have any of you experienced the same problem and solved it? or have you also trouble with this??

I've never experienced anything like that.

---

### Post by soujiro14 on 2007-10-13
I was wondering if anyone had this problem and a possible solution: the mouse pointer disappears in-game.  Clicking of any sort doesn't make it appear and I have to use the Ctrl key to see where my pointer is.

---

### Post by amlucent23 on 2007-10-13
> **soujiro14 said:**
> I was wondering if anyone had this problem and a possible solution: the mouse pointer disappears in-game.  Clicking of any sort doesn't make it appear and I have to use the Ctrl key to see where my pointer is.

as soon as i zone in I just hit "m" to bring up the map then hit "m" again to close it and I will always have mouse pointer, try that as a work around.

---

### Post by Ferrat on 2007-10-13
> **Drake2k said:**
> I've never experienced anything like that.

Are you running wine 0.9.45 or 0.9.46 without any fixes?



saw that 0.9.47 is out, will try it later

---

### Post by Drake2k on 2007-10-13
> **Ferrat said:**
> Are you running wine 0.9.45 or 0.9.46 without any fixes?



saw that 0.9.47 is out, will try it later

Hey Ferrat.  I'm running 46.  I also am using nVidia using (as far as I know) the latest drivers.  My card is a GForce 7600 (I think) 256Meg Video by XFX.

---

### Post by Ferrat on 2007-10-14
Hmm weird, need to look in to that then thx for the info =)

---

### Post by soujiro14 on 2007-10-16
> **amlucent23 said:**
> as soon as i zone in I just hit "m" to bring up the map then hit "m" again to close it and I will always have mouse pointer, try that as a work around.

Tried.  No beans. :(

---

### Post by Ferrat on 2007-10-17
Hmm I get the same problem with Z range in 0.9.47 

Anyone with a ATI card not getting this bug?

Anyone with a nVIDIA card getting this bug?

bug: missing textures, invisible chars, broken text ect-

---

### Post by ObiWan2001 on 2007-10-17
If GLSL is enabled, disable it.

---

### Post by Azakus on 2007-10-18
I have to do an overhaul of my 64-bit script to compile on Gutsy (they moved 32-bit support out of the main gcc package, so more packages need to be installed, and I'm still looking to see if any more dependencies are needed).
I should have it ready soon.

---

### Post by narehart on 2007-10-18
ARRGH! I am getting really frustrated! I am trying to get guild wars running under wine 9.47 in Gutsy but it's not working.  I keep reading about how easy it is to get this game working in wine but it's not happening for me. Can anyone help?

EDIT: I figured out what was going on here.  Guild Wars wasn't starting because the OSS sound driver was selected in wine.  Unfortunately, ALSA is not available for some reason.  I can't figure out why.

---

### Post by JimmyVD on 2007-10-20
i can get guild wars running, and running with a real good frame rate 60-70 fps, on my amd x2 6000+ but for some reason the textures dont load correctly, and the majority of the game is invisible, i got an ATI x1950 GT and i havn't got a clue whats wrong, i tried installing manually and with your latest set-up script both get the same problem, any ideas?

---

### Post by Ferrat on 2007-10-20
> **JimmyVD said:**
> i can get guild wars running, and running with a real good frame rate 60-70 fps, on my amd x2 6000+ but for some reason the textures dont load correctly, and the majority of the game is invisible, i got an ATI x1950 GT and i havn't got a clue whats wrong, i tried installing manually and with your latest set-up script both get the same problem, any ideas?

It's a wine bug that appeared in 0.9.45, seems that it only applys to ATi cards but hasn't gotten that 100% confirmed.

---

### Post by paulr on 2007-10-20
0.43 is probably the best bet. 0.47 won't install at present (a bug makes the Gw.dat file read only ....) and 0.45,0.46 sometimes just don't display the bits on screen correctly - sometimes missing the bits of the game, and sometimes just not rendering the text ; run it with -dx8 -noshaders -dsound and it should run fine (and having -windowed initially helps too, you can always set the resolution later)

I don't know about 0.44 as I'm running x64 and there isn't an x64 .44 build for some reason.

---

### Post by atomicblue on 2007-10-20
Guild Wars has a good walkthrough on their website:

[http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine#Tuning_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine#Tuning_Wine)

It helped me.. ^__^

---

### Post by Azakus on 2007-10-20
Alright, I redid the 64-bit script a bit to make it more user friendly. Now it will automatically assess what version is current and download it.
Enjoy!

---

### Post by TirShar on 2007-10-26
I got GW running with Wine 0.9.47. I just need to chmod the dat file before I run it, and then it works. Still there is that bug for ATI-cards that makes parts of the world invisible. It works with the parameters "-dx8 -noshaders", but with far worse FPS (around 20, I think).
Can anyone tell me where I can "track" this bug?

---

### Post by Ferrat on 2007-10-26
> **TirShar said:**
> I got GW running with Wine 0.9.47. I just need to chmod the dat file before I run it, and then it works. Still there is that bug for ATI-cards that makes parts of the world invisible. It works with the parameters "-dx8 -noshaders", but with far worse FPS (around 20, I think).
Can anyone tell me where I can "track" this bug?

[http://bugs.winehq.org/show_bug.cgi?id=9659](http://bugs.winehq.org/show_bug.cgi?id=9659)

---

### Post by gavinjb on 2007-10-26
Hi,

I am trying to re-install wine on my new installed Gutsy PC, but when I run ./winebuild I get the following error, I am running the script I used last time I installed GW which was configure for Wine .44

```

checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.
make: *** No rule to make target `depend'. Stop.
make: *** No targets specified and no makefile found. Stop.

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.9.44-concurrent_lights_fix" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

This package will be built according to these values:

0 -  Maintainer: [ gavin@gblaptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ wine ]
3 -  Version: [ 0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ wine-0.9.44 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

Package created!
dpkg: error processing wine*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine*.deb
gavin@gblaptop:~/Documents/Install$

```

On the plus side, I did find away to improve the FPS on GW the other day, it is very useful if you run Compiz with Xgl-server, but it seems to make a difference even without (my GW went from 15FPS to 45FPS)

```

DISPLAY=:0 wine Gw.exe -dsound -noshaders flags -repair -image -dx8

```

Anyway if someone can please help with the error above.

Thanks,


Gavin,

---

### Post by Azakus on 2007-10-26
Arg, I hate typos. And I made one in my script, that I just figured out now because 0.9.48 is out.
Here's the fixed copy.

---

### Post by karth on 2007-10-26
To anyone having issues with the read-only bug under 0.9.47

I found a workaround by chowning Gw.dat to root:root and then chmod 0777.

From the Guild Wars install dir, in terminal:

```
sudo chown root:root Gw.dat
sudo chmod 0777 Gw.dat
```

The game is unable to change the file owner, thus also unable to change the file permissions.

---

### Post by gavinjb on 2007-10-27
> **gavinjb said:**
> Hi,

I am trying to re-install wine on my new installed Gutsy PC, but when I run ./winebuild I get the following error, I am running the script I used last time I installed GW which was configure for Wine .44

```

checking for the directory containing the Wine tools... $(TOPOBJDIR)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.
make: *** No rule to make target `depend'. Stop.
make: *** No targets specified and no makefile found. Stop.

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "0.9.44-concurrent_lights_fix" is not a
*** Warning: debian policy compliant one. Please specify an alternate one

This package will be built according to these values:

0 -  Maintainer: [ gavin@gblaptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ wine ]
3 -  Version: [ 0 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ wine-0.9.44 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

Package created!
dpkg: error processing wine*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wine*.deb
gavin@gblaptop:~/Documents/Install$

```

On the plus side, I did find away to improve the FPS on GW the other day, it is very useful if you run Compiz with Xgl-server, but it seems to make a difference even without (my GW went from 15FPS to 45FPS)

```

DISPLAY=:0 wine Gw.exe -dsound -noshaders flags -repair -image -dx8

```

Anyway if someone can please help with the error above.

Thanks,


Gavin,

found the solution I had to install the packages flex and bison before the script would work, this looks like Gutsy has a few packages removed that were in earlier releases.

Gavin,

---

### Post by gavinjb on 2007-10-27
Well I sort I had fixed it only problem is after wine install if I run winecfg I get the following error

```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
gavin@gblaptop:~/GW$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

And if I try to install GW (I have the DVD so I install from that) I get the following

```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

Any ideas


Gavin,

---

### Post by Ferrat on 2007-10-27
Looks like you need the **x11-proto-core-dev** pkg from synaptic, not 100% but belive that's the one

---

### Post by gavinjb on 2007-10-27
Thanks,

I installed the X11Proto-core-dev package, but wine still gives me the same error, looks like Gutsy has removed some files from that were included as standard on Fiesty.

Gavin,

---

### Post by karth on 2007-10-28
I sort of have a problem here...

Guild Wars ran fine a couple days ago, but now the game window doesn't show up.

I get the dialog saying "Connecting to Arenat Net", then it completes, and nothing comes. I can here the music from the main menu of Guild Wars (login prompt), but the window is invisible... Any clue?

---

### Post by Ferrat on 2007-10-28
> **gavinjb said:**
> Thanks,

I installed the X11Proto-core-dev package, but wine still gives me the same error, looks like Gutsy has removed some files from that were included as standard on Fiesty.

Gavin,

Hmm ok, installing/reinstalling build-essential

---

### Post by gavinjb on 2007-10-28
I just tried uninstalling build-essential and installing again I also uninstalled wine and re ran the wine build script, but I still got the same error.

I am tempted to re build my pc, by installing Fiesty, then configuring to me needs and then running the upgrade from fiesty as fiesty always worked fine with the wine build script, but it will take a while to do, that and if I can find an easy way around, I would rather go for that, as I am not sure if the upgrade process will upgrade wine to the repo version.

I have also noticed that the Update Manager also constantly sees an update for wine 0.9.46 and reports the script as 0-1.


Gavin,

---

### Post by karth on 2007-10-28
I fixed my issue, I'll tell how

The fact is, that Wine doesn't support weird resolutions such as a windowed I resized using the mouse. Instead, I launched Guild Wars in a Wine desktop using the desired resolution, an ran the game in fullscreen mode. 

That did it.

---

### Post by blueamcat on 2007-10-29
Just wanted to say that I've got Guild Wars working! I updated Ubuntu to Gutsy and tried it just for fun, and it works! Sound works and everything. Runs great! And I have the newest version of Wine. Still don't know a ton about Ubuntu and Wine, but I'm loving it.

---

### Post by gspearing on 2007-11-01
I have upraded to Gutsy, and running Wine 48 with Nvidia. I ma using Xgl and Compiz in Gnome. When running Guild Wars it complained that there wasn't opengl. I have borrowed the start script from above (many thanks):

DISPLAY=:0 wine Gw.exe -dsound -noshaders flags -repair -image -dx8

This has got GW up and running, full screen, without any windows borders (Display=:0?).

Is this the best I can hope for while running with all the Xgl Compiz eye candy?

Cheers

---

### Post by undadecor on 2007-11-06
> **gavinjb said:**
> Well I sort I had fixed it only problem is after wine install if I run winecfg I get the following error

```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
gavin@gblaptop:~/GW$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

And if I try to install GW (I have the DVD so I install from that) I get the following

```

Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

Any ideas


Gavin,

I had the same problem (upgrade to Gusty, with the same error message) and running this prior to installation of WINE worked:
```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

```
I did this because I was following [this guide]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine").

---

### Post by gavinjb on 2007-11-06
Thanks will give that a try when I get home tonight.

I found an intresting website last night called PlayOnLinux which has scripts to install and run Windows Games on Wine, this includes GuildWars and loads of other Games, might be worth a look if anyone wants to try and running any particular Win Games on Linux.


Gavin,

---

### Post by Dave Jr on 2007-11-08
Hi guys, im trying to make it all work but,, as usual, its not working. but my problem, im a newb at ubuntu. Im at the step that i have to type in the terminal wine C:/program files etc. etc. till ive got to start gw.exe

but, the terminal can't find that path. And when i open the wine file, i see when i go to c:/ , then program files. And then theres only the map common files. And i can't find anything in that map! Where's my program files??

Please help me:(

---

### Post by maslasic on 2007-11-08
Howdy,

Recently switched over to Ubuntu from Windoze and would like to be able to continue playing Guild Wars.  Installed Wine, ran the AMD64 script provided in this thread (thanks, btw!).  Now have Guild Wars installed, but when it starts up the graphics are fuxored! :-k

Any help would be appreciated!  I've attached a screenshot...

---

### Post by Azakus on 2007-11-09
> **maslasic said:**
> Howdy,

Recently switched over to Ubuntu from Windoze and would like to be able to continue playing Guild Wars.  Installed Wine, ran the AMD64 script provided in this thread (thanks, btw!).  Now have Guild Wars installed, but when it starts up the graphics are fuxored! :-k

Any help would be appreciated!  I've attached a screenshot...

Wow. That's the worst I've seen that actually started up.
Are you trying any terminal flags with it, or just wine GW.exe?
If not, try running it in a terminal like this:
```
wine Gw.exe -dsound -noshaders  -dx8
```
I'm sure there are others to try too, but see if that helps.
Also, make sure Compiz, Compiz Fusion, XGL, and Beryl are disabled when trying to play.

---

### Post by Trampis on 2007-11-09
when I run your script I get 

"--23:44:08--  [http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.42.tar.bz2](http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.42.tar.bz2)
  (try: 5) => `/home/john/winestuff/winesource.tar.bz2'
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... failed: Connection timed out.
Retrying."

but i circumvented that and installed via the website download, it popped up a couple of times but now when i attempt to run the program i get the error message that the program is not accessible either b/c it is not readable or it is in use.

ok so then it stopped even getting me to the login screen, i uninstalled it then attempted to reinstall it.
the message i get now is
Unable to Install 
the installer could not write guild wars in the specified directory. Please check that you have admin privaleges, and that there is sufficent space.

i have admin and the space.

---

### Post by Azakus on 2007-11-10
> **Trampis said:**
> when I run your script I get 

"--23:44:08--  [http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.42.tar.bz2](http://umn.dl.sourceforge.net/sourceforge/wine/wine-0.9.42.tar.bz2)
  (try: 5) => `/home/john/winestuff/winesource.tar.bz2'
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... failed: Connection timed out.
Retrying."

but i circumvented that and installed via the website download, it popped up a couple of times but now when i attempt to run the program i get the error message that the program is not accessible either b/c it is not readable or it is in use.

ok so then it stopped even getting me to the login screen, i uninstalled it then attempted to reinstall it.
the message i get now is
Unable to Install 
the installer could not write guild wars in the specified directory. Please check that you have admin privaleges, and that there is sufficent space.

i have admin and the space.

The newest version is 0.9.49. Depending on whether it's the 32 or 64 bit script, there's two different actions you need to take.
32-bit: Edit VERSION= line to 0.9.49
64-bit: Get the latest copy of my script.

---

### Post by Azakus on 2007-11-22
Found an interesting article on how to enable DirectX 9.0c support in Wine by using the Microsoft DirectX installer and tweaking sone wineconfig dll paths. This should enable much better graphics and fix many of the problems experienced with Guild Wars. I'll check it out after Thanksgiving is over, but the guide is very detailed if you want to do it now.
[http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html)

---

### Post by RJ Fighter on 2007-11-23
Having trouble playing.  The main screen has an FPS of about one, and nothing I've done so far has fixed it.  Anyone have any ideas as to why?

---

### Post by erk on 2007-12-05
Anyone solved the problem whereby the GW.dat and temp files become not writable during an update due to the permissions getting set wrong each attempt?

---

### Post by karth on 2007-12-05
As I said in page 75, I found a workaround:

> **karth said:**
> To anyone having issues with the read-only bug under 0.9.47

I found a workaround by chowning Gw.dat to root:root and then chmod 0777.

From the Guild Wars install dir, in terminal:

```
sudo chown root:root Gw.dat
sudo chmod 0777 Gw.dat
```

The game is unable to change the file owner, thus also unable to change the file permissions.

---

### Post by Torgas Prim on 2007-12-06
> **gspearing said:**
> 
DISPLAY=:0 wine Gw.exe -dsound -noshaders flags -repair -image -dx8



Where and how do we get this command line?
I looked everywhere and cannot figure out where it goes or how to run it.

<---still a n00b

---

### Post by karth on 2007-12-06
Right Click on the desktop or an opened window -> "Create launcher"

You just have to paste that line in the "Command field" and voila!

Double click on your new launcher and the game will run with the specified parameters.

---

### Post by Torgas Prim on 2007-12-06
Thank you so very much :-)

Another thing...I did put those parameters in my GW shortcut. When I ran GW a lot of sounds were missing, and get this...TeamSpeak would not work. I could not talk or here people in TS.
When I removed the -dsound..it worked.

---

### Post by Torgas Prim on 2007-12-06
Hmmm, I did what you said but all I got was an error: "Failed to execute child process DISPLAY=:0 wine Gw.exe -dsound -noshaders flags -repair -image -dx8


I do something wrong?

It is in the command line of the launcher

---

### Post by karth on 2007-12-07
There's probably a problem with the path to Gw.exe, which is relative in this example...

With Wine, you can specify the path to the .exe using Windows syntax, given you have installed the game under the Wine tree (i.e. under .wine/drive_c/whatever...)

Therefore, an absolute path using Windows syntax for the default install of Guild Wars would be "C:\Program Files\GUILD WARS\Gw.exe"

Your command becomes, then: ```
DISPLAY=:0 wine "C:\Program Files\GUILD WARS\Gw.exe" -dsound -noshaders flags -repair -image -dx8
```

Don't forget the quotes to wrap the windows-like path.

---

### Post by devosion on 2007-12-07
After much time spent I finally managed to get Guild Wars running on my ATI card. Although there are still some problems and I am hoping that I can get some help to get these resolved.

The first are the most frequent fixme errors that I am encountering from terminal.

> fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x145b90) : stub
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported



The first one sounds like a direct 3d problem and am not sure how I could go about getting it fixed. If it helps I just recently installed dx9c with this guide.

[http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html]("http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html")

The second error seems to be a problem with my keyboard, because every key I press on my keyboard makes this error pop up. Not only this but if I try holding my backspace key it doesnt respond with a prolonged deletion, but only does it once.

The other problems that occur are boxes that appear during gameplay. They only seem to appear in the Eye of the North expansion though. I also have no way of turning anti-aliasing on, probably a bug and im guessing there is no way of changing this. And lastly some problems with seams on occasion, most notably on the log in screen.

Oops and almost forgot about the terrible framerate which rarely exceeds 20fps. :)

Any help will be appreciated. Thanks!

---

### Post by Torgas Prim on 2007-12-09
Thanks for all the help.
I get gw running good but cant go full screen without the bottom buttons all disappearing on me.
Tried several resolution changes but all I can get to look good is a 1280x1024 window. Hmmmmmmmm

I have to look deeper in these boards...lol

---

### Post by Keilious on 2007-12-11
Arg, I've been struggling for hours trying to solve this problem:
The guild wars loader works, but it says "Unable to initialize 3D output..."
Meanwhile, in the terminal wine says 
```
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported

```

Edit: Oh, and I've tried turning off beryl/compiz, and flgrxinfo and glxinfo return nothing out of the ordinary.
I'm running on a radeon x1900xtx, with AIGLX, if that helps.

Help?

---

### Post by Torgas Prim on 2007-12-11
What distro are you running?
I had no issues like that and I am on Gutsy Gibbon.
I also installed the latest Wine.

I found something that may help though...install Wine Doors, run the program and then select DirectX  to install.
This of course is if you still have a Windows partition installed on your PC/Laptop.

---

### Post by Beren Camlost on 2007-12-11
> **Keilious said:**
> ```
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
```

The problem seems to reside here, but it baffles me since I have no wined3d.dll in my own Wine installation.

---

### Post by Keilious on 2007-12-11
> **Torgas Prim said:**
> What distro are you running?
I had no issues like that and I am on Gutsy Gibbon.
I also installed the latest Wine.

I found something that may help though...install Wine Doors, run the program and then select DirectX  to install.
This of course is if you still have a Windows partition installed on your PC/Laptop.
I'm using Kubuntu Gutsy 64-bit. I installed wine by using the file given in the first post of this thread. The latest version of wine just throws the concurrent lights error at me.
I'll look into this Wine Doors thing...

Edit: No success, DX9 says I have no Direct3D apparantly,  
```
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?
```

Edit: Fixed! Horray! I formatted and reinstalled kubuntu, then followed the instructions in the sticky here on how to install the latest version of wine, then:
```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
sudo ln -s /usr/lib32/libGL.so.1.2 /usr/lib32/libGL.so.1
```

Next problem!: I'm only getting about 1fps on minimum graphics on my Radeon X1900XTX. :( *starts searching*

---

### Post by Tristam Green on 2007-12-12
help me out here.  what if i want to uninstall the stuff in this script?  the install is going kinda hairy and i don't feel comfortable with it just yet.

thanks

---

### Post by Torgas Prim on 2007-12-12
Tristam, I never installed the script so do not know that one.

Keilious, 1fps?!?!?! I am lucky to get 10fps now. :mad:
But I think you may want to look at your ATI card on these forums. Most posts are against ATI as a supported card on Linux.

---

### Post by Azakus on 2007-12-12
> **Torgas Prim said:**
> Tristam, I never installed the script so do not know that one.

Keilious, 1fps?!?!?! I am lucky to get 10fps now. :mad:
But I think you may want to look at your ATI card on these forums. Most posts are against ATI as a supported card on Linux.

The next version of the ATI drivers (at least according to Phoronix) has VASTLY improved rendering.

---

### Post by Tristam Green on 2007-12-13
> **Torgas Prim said:**
> Tristam, I never installed the script so do not know that one.

Keilious, 1fps?!?!?! I am lucky to get 10fps now. :mad:
But I think you may want to look at your ATI card on these forums. Most posts are against ATI as a supported card on Linux.
well, i manually uninstalled *some* of the components from the script, just previously uninstalled pieces that the script loaded up.

i never even completed the script install, but i am still interested in getting GW to work.

just saw you live in columbia; i'm in charleston.  maybe the next time i'm up that way i'll PM you via forums and you can show me wtf to do lol.

~Tristam

---

### Post by subs on 2007-12-13
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)
^^^^^
chk this

---

### Post by Torgas Prim on 2007-12-13
> **Tristam Green said:**
> well, i manually uninstalled *some* of the components from the script, just previously uninstalled pieces that the script loaded up.

i never even completed the script install, but i am still interested in getting GW to work.

just saw you live in columbia; i'm in charleston.  maybe the next time i'm up that way i'll PM you via forums and you can show me wtf to do lol.

~Tristam


No problem. Give me a shout when coming

---

### Post by devosion on 2007-12-15
*sigh* And here I thought all my problems had been solved with a video card switch.

I had just gotten Guild Wars running, windowed, and I attempted to switch workspaces while it was running. The moment I did so Guild Wars stopped running and disappeared from my taskbar. I found this odd so I restarted and tried to bring it up again. When I did so it started up, launcher window, but before anything else occured the icon disappeared and the launcher was gone. When I check my system  monitor Gw.exe is still running, but it is sleeping.

Im not quite sure what happened but im guessing that even if I restart again this problem will persist. Will somebody please tell me how to bring the program back up? 

Oh and I read somewhere that I should run it in a new X process to fix this from happening. Unfortunately I dont know how to do that. I am using compiz.

---

### Post by vertexoflife on 2007-12-15
Okay, in Kubuntu 7.10 with WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed -dx8 -noshaders I can get Guild Wars to run, but at about a rate of not even 1 fps. Any idea?

---

### Post by Torgas Prim on 2007-12-16
wine "C:\Program Files\GUILD WARS\Gw.exe" -dsound -dx8

That is what I have and it is the fastest setup I can find for GW so far.
I use window manager but turned off Emulate Virtual Desktop. It allows me to be more free with window sizes and stuff.

I still get at most 10fps :(

Until it gets better I hate to say it but XP is the best way to play GW for now.

---

### Post by vertexoflife on 2007-12-16
It seems like a lot of other people are managing to run guild wars very well under Wine, at 50+fps. I wonder if it might actually be my hardware or not, why else are there people who no problems with it at all?

---

### Post by Azakus on 2007-12-16
For everyone having problems with low speeds: what graphics cards are you running? I wrote my script with an Nvidia card in mind (because I don't have any ATI cards) and I don't know if it translates equally to an ATI card.
Also, as a point of reference, my Nvidia 8600 GT got ~30 fps, when in windows it got much higher. Any slower cards might see a dramatic decrease in fps.

---

### Post by Torgas Prim on 2007-12-17
My setup:
Pent4 64 bit 2ghz
1gb Ram
GF FX5500 w/256mb GPU
Audigy 24bit sound

I just used Envy to install the nVidia driver yesterday, and it is worse now.
I get 5fps.
I am going back to the restricted drivers.

---

### Post by Tristam Green on 2007-12-17
ATI Graphics listed in my sig, running restricted drivers.


I finally got GW to run two days ago using the howto on Wine's website.  I did not get the concurrent lights error, but was never able to faster than 2-5 fps.

I just uninstalled and will run GW for now on my Windows desktop; I wish I had more time to devote to this :|

---

### Post by Azakus on 2007-12-18
I'm going to have to say that WINE does indeed suffer from a large fps hit because of translation to Linux APIs. There's just no way to avoid it thus far. The older/slower your card is, the lower fps you'll get. Some of it may be fixed in newer drivers (nVidia's 169.04 beta it said to do wonders for speed upgrades, as will the Catalyst 7.12 drivers for ATI), but those low speeds might just be the max for Guild Wars' current engine. It's not the most WINE friendly engine. :(
EDIT: BTW, this is a known bug: [Bug 9263 - Guild Wars terribly slow]("http://bugs.winehq.org/show_bug.cgi?id=9263")

---

### Post by Torgas Prim on 2007-12-18
Yeah, I knew I already had a crap card...lol...just trying to nurse it along till I can afford a better one. (6600GT).
I looked at all the bug reports and tried several changes but they did not work really.
Last night I tried to remove the driver through Envy and it blew my resolutions out. Reinstalling the restricted driver did not fix it....so word to the wise. :(
Re-installing the driver by Envy did not fix it.
OS reinstall oh well.
At least I got a clean install again of Gutsy and am just going to have to play GW on Xp for now until I get a new card or ANet comes out with a linux client/script.

---

### Post by Tristam Green on 2007-12-18
> **Torgas Prim said:**
> or ANet comes out with a linux client/script.

I'll just wait for all the other unfulfilled promises issued by software companies and the Apocalypse ;-)

---

### Post by Azakus on 2007-12-18
> **Torgas Prim said:**
> Yeah, I knew I already had a crap card...lol...just trying to nurse it along till I can afford a better one. (6600GT).
I looked at all the bug reports and tried several changes but they did not work really.
Last night I tried to remove the driver through Envy and it blew my resolutions out. Reinstalling the restricted driver did not fix it....so word to the wise. :(
Re-installing the driver by Envy did not fix it.
OS reinstall oh well.
At least I got a clean install again of Gutsy and am just going to have to play GW on Xp for now until I get a new card or ANet comes out with a linux client/script.

Just try sudo dpkg-reconfigure xserver-xorg

---

### Post by Torgas Prim on 2007-12-19
I could have used sudo dpkg-reconfigure xserver-xorg
but it was quicker to re-install than mess with settings I could have blown anyway.
But thanks :KS

---

### Post by falsenames on 2008-01-06
I'm only having issues with Guild Wars after I've zoned more than a dozen times or so.  I'm running Wine 0.9.52, and as you can see by my sig, I don't exactly have a stellar gaming box.  Just half a gig of RAM, and an nVidia 6200 card.  I've been getting pretty good fps when I start, but after I've zoned a few times, I think it's chewing up all my memory.  Can't wait for my new ram, processor, and video cards to come in.

I usually run Guild Wars with the default settings, at Win98 compatibility.  Using the -dsound or -dx8 tags haven't helped me out one bit, but I can't deal with trying to run it as Win2000 or XP.  I'm hoping that the new parts will help me out, since the video and sound quality are about up to par as when I play on my friend's XP box, just really choppy.

One actual hint in this post...  if you are running Guild Wars from the command line, I'd suggest using the following line to run it.  Getting rid of the "fixme" messages has helped me immensely.  Just run as normal if you are actually  crashing through, since that way you can see what errors come up.
```
wine "Gw.exe" 2> /dev/null
```

---

### Post by Azakus on 2008-01-07
A better way to get rid of the "fixme" messages is to run with the WINEDEBUG variable set to -all.
Example:
```
WINEDEBUG=-all wine "Gw.exe"
```

---

### Post by Crylos on 2008-01-07
Hey everyone! I've been reading all your posts, trying to get some info on this and been having a hard time... I'm a Linux noob so I would like some help yet I managed to install GW and Wine. I can "play" the game but at a very slow rate though. In some rare occasions the frame rate rises to 10~12 fps but only for some moments. I think my laptop can handle it fine so I'm thinking maybe I can still change something to make this run smooth...
The laptop is currently installed with Ubuntu 7.10 Gutsy Gibbon, has 256 Mbs of memory and an Intel Celeron 1.4GHz (this IS a very old laptop :P). My Wine version is 0.9.52.
I've tried using many flags to help with performance...-image -dx8 -noshaders -nosound/dsound -opengl(can it be used simultaneously with dx8?) and maybe some more. Does anyone know what else I can do?
One last thing: while updating Wine using the Terminal, I seemed to have changed something I shouldn't... Now I can't install some of the updates. Anyone knows how to reverse/correct this? Thanks in advance!

---

### Post by Azakus on 2008-01-08
Guild Wars is still graphics intensive enough to need relatively decent hardware. The age of your laptop is likely the greatest hindrance. There's little you can do to raise the framerate any higher I'm afraid.

---

### Post by Crylos on 2008-01-08
I had thought about it before but since the framerate is stable sometimes I hoped it would still work... GW isn't very demanding compared to other modern games. Anyway, thanks for your help.

---

### Post by falsenames on 2008-01-13
Crylos:

Taking a quick look at the box for Guild Wars, I notice that the minimum requirement for RAM is 256MB, which is what your laptop has.  However, check to see if you have a separate bank of RAM for your video processing.  Most laptops will share out the RAM instead of having VRAM.  And with 64MB of video RAM required on top of the 256MB of system RAM, you are going to have a hard time running this game well.  That's also just for the minimum playable configuration, the 'recommended' one is at least 512MB of RAM, and I'm bumping into swapping issues with that much.  Laptop drives swap lower than desktop drives, so there is yet another bog on resources.

I'll see if my frame rate increases after I get new RAM, but I forgot my last paycheck included over a week of missed work, so I'll have to put that off until next month.  I have noticed for myself though, that if I use -nosound, I do get slightly better results now, although still in the low teens for fps when I rotate the screen.

---

### Post by ensoriki on 2008-01-19
Blah now I need some help T_T

Im running wine 0.9.52
I installed GW, but when I try to run it, it appears on that menu tray at the bottom of the screen then disappears, but never created a window.

When I go to system monitor, There is Gw.Exe as a Zombie

If I try to open it up again without killing the process I get

Guild Wars is unable to open the archive file
blah blah blah blah.
Make sure it is readable and writeable.

Wtf is that?

---

### Post by wuild on 2008-01-20
Hey all.. 
ive just got one quick question.
my GuildWars is like ******* up... after some time some textures dissapears.
Any chanse that its WINE that doesnt work ? i dont even know what version i have or how to patch it :D please help
[[COLOR="Navy"]**Screenshot**[/COLOR]]("http://infinity-games.org/downloads/Screenshot.png")
its also ingame. any idea what it can be and what i can do to fix ?

---

### Post by falsenames on 2008-01-21
Ensoriki:  If you have a zombie process in WINE, and you want to kill it, just type 'wineserver -k' in a command line.  Be warned though, this will kill all windows apps being run.  As for not opening a window, that happened to me when I tried running the game off of an old install when I switched distros.  Is this a fresh install?

Wuild:  The textures can be a bit hazy through wine.  My only recommendation is to make sure you are running the most recent version of WINE, which I believe is currently wine-0.9.53.  They have been clearing up the graphics rather rapidly from version to version.  You should have seen what it looked like with the original postings to this thread when we were all running 0.9.23.

---

### Post by karth on 2008-01-21
> **ensoriki said:**
> Wtf is that?

It's called a bug.

GW is known to screw up it's permissions on Gw.dat . A workaround consists in```
sudo chown -R root:root ~/.wine/Program Files/GUILD WARS/*
```
```
sudo chmod -R 0777 ~/.wine/Program Files/GUILD WARS/*
```

Provided you installed Guild Wars with defaults, under ~/.wine/, it will change the permissions to writable and will remove Wine's capacity to change the permissions.

**@wuild:**
Yes, there is a strong chance that it's Wine that's messing up with your game. Check your version by typing in a console: ```
wine --version
```
I had best results using the 0.9.5x series of Wine.
Also, which graphics card brand do you have?

---

### Post by wuild on 2008-01-21
**@karth:** Well i have a Ati Radeon 9800 pro. but i dont know how to install it. i installed Envy but when i install the ati drivers. its like ******* up.
linux is saying that its running on low grahpic settings. and when i try to change it says the same. and max resolution is 800x600
and im useing 1600x900 atm :D and if i change my screen settings its going crazy and its like war of the ants and i cant change back. only way is to reinstall linux
xD and i need some seriously help :D

---

### Post by ensoriki on 2008-01-21
Anyways I got pass my error before.

Now what I believe to be the final problem.

Im running a ATI Radeon HD 2400 installed with envy, on gutsy and when I run GW.
it tells me it has come across an unrecoverable graphics error.

The driver seems to be working since I can open ATI catalyst, yet GW says it can't detect my graphics card or whatever.

Really annoying now.

---

### Post by syczu on 2008-02-05
Guild Wars on ATI graphic works really bad. I tried Radeon 9600pro and Geeforce 4 and Geeforce 4 works much better, but in reality is worse than radeon. Worse drivers for ATI don't work properly with GW.

---

### Post by Melhisedek on 2008-02-06
Under what Windows version in winecfg should I run GW? Or does it matter at all?

---

### Post by falsenames on 2008-02-08
@Melhisedek: It is starting to matter less and less, but I usually have the best luck running in Win98 mode.  Although recently for a week I had it set to WinXP without noticing at all until I poked at winecfg for another program.

---

### Post by Melhisedek on 2008-02-08
Do you guys all run GW with -dx8 flag? Anyone running with good results without it and what graphics card do you have?

---

### Post by Toffeeapple on 2008-02-08
I run mine as win98 so I think that automatically makes it run dx8, I get 60fps in windowed mode stretched to fill the screen (1440x900) with 'wait for vertical sync ' on, it drops to around 20fps in large towns with lots of players.

thats with wine 0.9.46, and the -dsound switch thing.

---

### Post by Melhisedek on 2008-02-08
I have same card as you but weaker CPU mine is Opteron 165 @ 2.6 GHz. And I'm nowhere near those numbers. I get at most 35 FPS when I'm on a mission, in towns I get somewhere around 10-20 fps. 
What does -dsound flag do? I've tried it but didn't notice any difference to be honest

---

### Post by Toffeeapple on 2008-02-08
err.. I don't actually know what -dsound does : ) I suspect something to do with direct sound something or other... I dunno.. I have recently found and use a program called 'PlayOnLinux' ..and that put it there.

turn down antialiasing and anisotropic filtering, mine are 4xbiliniar and 4x respectfully... it seems to run better windowed too.

My card is the BFG 8800 GTS OC but I wouldn't think the OC actually makes that much difference other than to price.

---

### Post by falsenames on 2008-02-09
Using -dsound is telling Wine to use it's own DirectSound hardware emulation.  This is usually a "safer" way to run anything requiring DirectSound because some cards are very picky about the sampling rates that are sent to it.  Generally speaking, having Wine convert everything to sane sampling rates will make the program run smoother than when it has to deal with the card constantly spitting back messages of "What the heck was that mess you just sent me?"

Note:  All quotes from sound cards have been paraphrased.

---

### Post by ObiWan2001 on 2008-02-11
> **falsenames said:**
> Using -dsound is telling Wine to use it's own DirectSound hardware emulation.

No *-dsound* tells Guild Wars to use the old DirectSound engine instead of the new FMOD soundengine.
It has nothing to do with wine.

---

### Post by pablo spd on 2008-02-22
hey i'm really new to Ubuntu and wine and i'm trying to get Guild Wars to run smoothly and with sound but i aint having any luck. i'm getting a whole bunch of fixme errors and have no idea what to do with them. could somebody please help?

---

### Post by gavinjb on 2008-02-25
I also get fixme errors and ignore them as GW seems to run ok for me.


Does anyone use GW with an intel graphics card and if you do what is the performance like and do you have any issues, I am looking at a new PC and the PC is currently with ATI (had issues with ATI in the past) or Intel graphics Cards.

---

### Post by Torgas Prim on 2008-02-26
> **pablo spd said:**
> hey i'm really new to Ubuntu and wine and i'm trying to get Guild Wars to run smoothly and with sound but i aint having any luck. i'm getting a whole bunch of fixme errors and have no idea what to do with them. could somebody please help?

pablo, follow the directions on the first post, they will help you get sound and the 'fixme' errors resolved.

---

### Post by pablo spd on 2008-02-26
i've done that a couple of times but i still can't play it without the -dsound flag and it's really choppy

i just did it again and GW won't run without -dsound and i get a butt load of: 

fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??


so a simple question, what do i do so i can tell it what to do

---

### Post by Torgas Prim on 2008-02-26
If you have edgy or dapper, run the File 'winebuild.sh'  that  the OP posted to download.
If not I can't think of what to do.
You running on an older laptop or something with integrated graphics?

---

### Post by pablo spd on 2008-02-27
no i'm on a fujitsu that i just got a little less than a year ago with an ATI radein graohics card. i played around with winecfg and got sound but it's still choppy. is that because of my graphics card or i'm i doing something else wrong?

---

### Post by Torgas Prim on 2008-02-27
Well I just re-installed 7.10 and puled the latest Wine and this is what I get to look at right now :(
[[IMG]http://img186.imageshack.us/img186/6707/screenshotba0.png[/IMG]](http://imageshack.us)

---

### Post by Torgas Prim on 2008-02-29
Fixed, I got Linux Mint reinstalled which is far superior to any other distro for gaming afaiac.
:)

---

### Post by Dryfter on 2008-03-03
^ I agree ^

I just installed Mint under VMware.  I got guild installed, but i'm getting like 2 fps.  I've tried the -nosound -windowed -dx8 tags those just helped me getting into the game.  I have the graphics all way down.  I'm guessing whats killing me is being in VMware.  I'll have to test it on a different system....

---

### Post by Torgas Prim on 2008-03-05
I am getting like 8-10 fps full install of Mint. Hopefully soon Wine will be able to handle the memory pages better, or work better with video drivers.
When playing GW, the 8-10fps is not so bad until all the skill animations activate in a battle, then it skips, stutters, and rebounds while fighting groups  larger than 4 enemies.

---

### Post by VincentKriek on 2008-03-06
I cant seem to get my Guild Wars working:(

I've installed wine 0.9.56 on Gutsy Gibbon. The Guild Wars install went smoothly so i started the game, but sometimes i get an error after loading:

err:seh:setup_exception stack overflow 16 bytes in thread 0012 eip 7bc40ad2 esp 7cf43ff0 stack 0x7cf44000-0x7d054000

But the number are different sometimes. And when i get through it looks like this:

[[img]http://xs225.xs.to/xs225/08104/schermafdruk-default_-_wine_desktop259.png[/img]](http://xs.to)

I've tried -dsound -nosound -noshaders -dx8 -windowed, nothing worked. Please someone help:(

---

### Post by Toffeeapple on 2008-03-07
use wine version 0.9.51

If you want a hassle free wine experience use [PlayOnLinux]("http://www.playonlinux.com/en/").. that way you can install multiple versions of wine and tweak each game individually.

0.9.51 works best for me with Guild Wars.. I get on average 20fps in heavily populated locations up to 60fps (I have sync on) in instances missions and such.. I run it windowed.. [see here]("http://files.myopera.com/louitrilobite/Stuff/Screenshot.png")..

run it as windows 98, you get less eye candy but twice as much fps.

Also.. from my own personal experience Nvidia works much better that ATI

---

### Post by Llewxam on 2008-03-07
hey all. 

running the latest version of wine i'm triyng to install guild wars and all i get is an error that it cannot connect to anet servers. anyone know or has had this before and can help or guide me the right way to fixing it?

ran the diagnostic tool from anet to see what my problem was. i got this: 
ArenaNet diagnostic utility [25362]

Windows version: 5.1
Build 2600
Service Pack 2


==============================================================================
= Gathering adapter settings
==============================================================================
*--> ipconfig /all  <--*
Exec() failed 2
File not found
Completed in 0.04 seconds


==============================================================================
= Detecting network connections
==============================================================================
*--> netstat -n  <--*
Exec() failed 2
File not found
Completed in 0.00 seconds


==============================================================================
= Discovering external address
==============================================================================
Current IP Address: 

Completed in 6.60 seconds


==============================================================================
= Checking server connectivity
==============================================================================
Diag.ArenaNetworks.com
 216.107.245.77:6112 - connect succeeded
   216.107.245.77:80 - connect succeeded
 216.107.245.41:6112 - connect succeeded
   216.107.245.41:80 - connect succeeded
 206.127.146.41:6112 - connect succeeded
206.127.147.153:6112 - connect succeeded
   206.127.146.41:80 - connect succeeded
  206.127.147.153:80 - connect succeeded
   203.70.18.55:6112 - connect succeeded
     203.70.18.55:80 - connect succeeded
  222.231.12.42:6112 - connect succeeded
    222.231.12.42:80 - connect succeeded

File1.ArenaNetworks.com
 216.107.245.41:6112 - connect succeeded
 216.107.245.77:6112 - connect succeeded
216.107.245.113:6112 - connect succeeded
   216.107.245.77:80 - connect succeeded
   216.107.245.41:80 - connect succeeded
  216.107.245.113:80 - connect succeeded

Auth1.ArenaNetworks.com
216.107.245.120:6112 - connect succeeded
 216.107.245.86:6112 - connect succeeded
 216.107.245.70:6112 - connect succeeded
 216.107.245.84:6112 - connect succeeded
 216.107.245.85:6112 - connect succeeded
 216.107.245.87:6112 - connect succeeded
216.107.245.121:6112 - connect succeeded
  216.107.245.120:80 - connect succeeded
   216.107.245.70:80 - connect succeeded
   216.107.245.84:80 - connect succeeded
   216.107.245.85:80 - connect succeeded
   216.107.245.86:80 - connect succeeded
   216.107.245.87:80 - connect succeeded
  216.107.245.121:80 - connect succeeded
  216.107.245.117:80 - connect succeeded
  216.107.245.118:80 - connect succeeded
  216.107.245.119:80 - connect succeeded
216.107.245.117:6112 - connect succeeded
216.107.245.118:6112 - connect succeeded
216.107.245.119:6112 - connect succeeded

Completed in 10.23 seconds


==============================================================================
= Tracing network paths
==============================================================================
*--> pathping -4 -q 4 -w 700 216.107.246.36 <--*
Exec() failed 2
File not found
*--> pathping -4 -q 4 -w 700 203.70.17.228 <--*
Exec() failed 2
File not found
*--> pathping -4 -q 4 -w 700 206.127.145.228 <--*
Exec() failed 2
File not found
*--> pathping -4 -q 4 -w 700 222.231.14.228 <--*
Exec() failed 2
File not found
Completed in 0.09 seconds


==============================================================================
= Running DirectX diagnostic
==============================================================================
*--> dxdiag /whql:off /t C:\windows\temp\GWT4759.tmp <--*
Exec() failed 2
File not found
Completed in 0.03 seconds


==============================================================================
= Result
==============================================================================
Test complete
<EOF>

now, it will connect at times then just hang when trying to go into a city or outpost. please someone help me on this. really busting my head over it. already got gw withdrawl :(

---

### Post by Torgas Prim on 2008-03-10
Possible firewall, NIC, or router issues it looks like.
You are not always connecting to the net.

What distro are you using?
Does GW work on a Windows PC in your home?

I hate to say it, but LinuxMint is the best distro I have seen that runs Windows games the best.

Just my 2 cents

---

### Post by Llewxam on 2008-03-10
i'm using gutsy 32bit with latest wine. 
yes i have a comp with windows that i use for games alone. guild wars is in that and connects/works. last night and just this morning it connected and ran fine but got booted 'cause i forgot to turn off messenger so the screen went to black and i couldn't recover after getting a new message. now once again i get the same can't connect error. 
:(

---

### Post by Torgas Prim on 2008-03-10
On the Windows PC if GW is now not working, I would delete the tmp and dat files from the game folder and re-download the game. Or copy them over from your Linux box if you don't want to update GW again.

The Gutsy install should work, but you will get a look similar to my screenshot posted above. That is why I went to LinuxMint. It just works better for games.

Ultimately though you still have connection issues that could be related to a NIC failing or your router has been taken hostage.

A firmware update for your router and a new password would be a good suggestion here to narrow down what is causing your intermittent connection issues. The firmware update should reset the router to factory specs and would remove any conflicting settings that could be in place.

Hope this helps

---

### Post by Llewxam on 2008-03-10
guessing it is the router. version is latest and i've never had any issues with it. the step of copying the files i did but vice versa. copied the .dat file from windows. that helped when the game seldom does connect. bleh, guess i'll keep trying and find a way to open the ports. or just take advantage when the game connects.

---

### Post by Guinness70 on 2008-03-11
i also had graphics issues. the login screen looked like it had been  smashed and someone mixed up all the pieces.
then i wanted to have a peek at the snazy "extra magic" settings for the desktop and it installed the latest drivers for my graphics card geforce6000
went back to the "normal" settings.

i started GW and yes... it worked!
wrong resolution so the mouse was all over the place.
went into the game and F11 for the menu
into the graphics menu
and set it to the correct resolution and it worked fine
mouse ok
still bit slow and choppy

but then read about setting Wine to run in Win98 for GW
did that and its working great! no longer choppy.
no special launcher codes
```
"/home/yournamehere/.wine/drive_c/Program Files/Guild Wars/Gw.exe"
```
with the " " quotation marks! coz of the spaces in the path ...

---

### Post by Llewxam on 2008-03-11
[IMG]http://i30.tinypic.com/2irorcm.jpg[/IMG]
this is my everlasting issue. my headache and madness. now i tried running the game in a friends house and guess what? WORKED FROM THE GET GO! i was able to log in five times in a row. i opened up all the ports in my firewall, i allowed EVERYTHING to be open and nothing at all. i dunno if it's an issue with wine, or an issue with the router. 
running in terminal with debug i had this error at the end when i got the above picture/error:

```
fixme:winsock:WSACancelAsyncRequest
```

---

### Post by Guinness70 on 2008-03-13
> **amlucent23 said:**
> as soon as i zone in I just hit "m" to bring up the map then hit "m" again to close it and I will always have mouse pointer, try that as a work around.
tried it : that ISNOT workign for me...

i cant get to the end of a dungeon with out it dissapearing!
major pain up the bumm!
would REALLY REALLY like to get this sorted
swapping out of the game isnt working, if i do that (with the help function) evrything goes belly up.

---

### Post by Guinness70 on 2008-03-13
someone in this thread suggested to have a look at
[http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine)

i used that Wine configuration and launcher setting.
```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed
```
it works and now the Alt key is useable again :-)
i did not use the -dx8 -noshaders
[COLOR="Red"][SIZE="5"]lets hope it solves my mouse dissappearing problem.[/SIZE][/COLOR]

>  Extra configuration

The process above will in the majority of cases land you with a working Guild Wars installation. However, for those systems where this doesn't happen, or where you are unsatisfied with the performance and want to try tinkering with the settings to get a better game experience, the following instructions may help.
[edit] Tuning wine

Start winecfg and, if your hardware supports it, configure the following options.

In the Graphics tab **Allow Pixel Shader** and set **Vertex Shader Support to Hardware**. **Also it is highly recommended that Allow the window manager to control the window be disabled**, this will prevent common desktop hotkey to activate during play. (eg: Switch desktop, cycle window, ...)

In the Audio tab enable the driver that support your audio hardware, ALSA Driver will work in most installation. The following audio options are recommended, Hardware Acceleration select Emulation and make sure Driver Emulation is checked.
[edit] Configuring Gw.exe

*The Wine implementation of Microsoft DirectX9 can be lacking. If that is the case, try running Gw.exe with the flags -dx8 -noshaders.* You can also change the Windows version Wine emulates in the Wine Configuration panel.** Several people have better luck getting it to work in Windows 98** mode than others. However this mode causes a massive number of graphics anomalies since the Eye of the North updates. It is possible to force Guild Wars to run in a window instead of fullscreen; this can be useful if you run into problems. To do this the flag -windowed is added to the gw.exe command. We will use this until we are satisfied with the results.

Also because Wine will generate a lot of debugging output when running, this can slow the game, environment variable WINEDEBUG will be set to -all (minus all) to prevent any debug output on the console.

```
WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed
```


---

### Post by spayced on 2008-03-14
Figured I'd jump in and contribute absolutely nothing. GW running fantastic but pretty ugly. Gutsy, Dell Dimension 4700C, wine .9.46.

---

### Post by Llewxam on 2008-03-14
well i gave up trying to run it. it just won't connect at all. even after opening the ports, changing into a ethernet cable, et cetera et cetera. 
i believe then, that it could be my router. it's a 2wire 1800 hw build 3.5.36.

i did however, tried out at my friends house. she's got the same brand but a newer model and the game connected and it runs fine. *sigh* guess i should start saving up for a new router :(

---

### Post by Torgas Prim on 2008-03-14
2wire routers are a real pain in the rear. When I was at Dell, we all hated those calls :mad:

---

### Post by Llewxam on 2008-03-14
i hear ya. this is the only second time it's given me any issues. first was when i first got it and it wouldn't want to work at all XD

---

### Post by Loiri on 2008-03-15
Umm... I've tried to do everything what is said in the first post and the debug-thingy, but all I get is this screen: 

[[img]http://xs125.xs.to/xs125/08116/gw657.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs125&d=08116&f=gw657.jpg)

The screen is quite much messed up as one can see + It's damn laggy.
So does anyone know what should I do?

---

### Post by Guinness70 on 2008-03-29
wondering if there has been a solution for the image of the cursor dissapearing?

---

### Post by jose158 on 2008-04-08
I can't seem to get GW to open at all. After I downloaded GW and opened it, nothing happened. any help?

---

### Post by gavinjb on 2008-04-09
How are you running GW, I have a script to run GW which is as follows and as long as Wine & GW are installed correctly there are no problems.

```

CD {path to gw.exe here}
DISPLAY=:0 wine Gw.exe -dsound -noshaders flags -repair -image -dx8

```

---

### Post by jose158 on 2008-04-09
I just click on the icon...

---

### Post by gavinjb on 2008-04-09
That might be your problem, as I know when I last ran GW, I used to get similar errors (jumpy graphics and sound mainly).

---

### Post by jose158 on 2008-04-09
NVM i got it working:popcorn:

---

### Post by Whisperwind on 2008-04-10
Question,

I've been playing Guild Wars for quite some time in Windows and I have a huge .dat file containing my explored areas, is it possible to import, or move this file across to Ubuntu and use it in wine, as it will save me alot of time.

Of course there is the build templates file as well, but if this works i imagine i can apply the same technique.

Thanks in advance, :)

Whisper.

---

### Post by gavinjb on 2008-04-10
yes you can, what I do is create a GW Install folder and copy the contents of the install CD into the folder and then copy the .dat and .exe form the GW install from Windows.  Then all you need to do it run this.

---

### Post by 4th guy on 2008-04-12
You can also link the folders by using ctrl+shift+drag from the folder to desired location.

---

### Post by Virgilius on 2008-04-14
Is there anyway else to make GW less jerky other than what was suggested, because I tried and it's still very slow.

---

### Post by Flash619 on 2008-04-20
I have launch errors when gild wars reaches 100%

```

err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:pool_alloc OOM
fixme:dbghelp:SymInitializeW what to do ??
fixme:dbghelp:pool_alloc OOM
err:seh:setup_exception stack overflow 128 bytes in thread 0024 eip b7e983df esp 7dc11f80 stack 0x7dc12000-0x7dd22000

```

---

### Post by Flash619 on 2008-04-23
ok i managed to fix the "What to do?" error but it still crashes.
```
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```
What does this mean??? I'm not all that familiar with linux.
Also the fact of having to boot up Vista every time i want to play just annoys.

---

### Post by DarK SouL on 2008-04-26
I am having problems with GW :(

I run it with this

env WINEPREFIX="/home/nievesj/.wine" wine "C:\Program Files\Guild Wars\Gw.exe" -windowed -nosound -noshaders


And these are the errors I get.  At the end it just stays there doing nothing, so I have to kill it.

I am running Wine 0.9.59

```

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f04c,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f0271d8, L"dwDirectXVersionMajor", 0x7f21f258)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f0271d8, L"dwDirectXVersionMinor", 0x7f21f258)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f0271d8, L"szDirectXVersionLetter", 0x7f21f258)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f0271d8, L"szDirectXVersionEnglish", 0x7f21f258)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f0271d8, L"szDirectXVersionLongEnglish", 0x7f21f258)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f0271d8, L"bDebug", 0x7f21f258)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_SystemInfo", 0x7f0271d8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_SystemDevices", 0x7f025290)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_LogicalDisks", 0x7f025300)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"ddraw.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dplayx.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dpnet.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dinput.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dinput8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dsound.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dswave.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"d3d8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"d3d9.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmband.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmcompos.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x7f025368,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szPath", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szName", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bExists", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szVersion", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szAttributes", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"szLanguageEnglish", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeHigh", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"dwFileTimeLow", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bBeta", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f025368, L"bDebug", 0x7f21eaa8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DirectXFiles", 0x7f025368)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f02b8e8, L"0", 0x7f02b908)
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21eb2c,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szDeviceName", 0x7f21f248)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szDescription", 0x7f21f238)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szDisplayMemoryLocalized", 0x7f21f228)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szDisplayMemoryEnglish", 0x7f21f218)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"dwWidth", 0x7f21f208)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"dwHeight", 0x7f21f1f8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"dwBpp", 0x7f21f1e8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szVendorId", 0x7f21f1d8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szDeviceId", 0x7f21f1c8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szKeyDeviceKey", 0x7f21f1b8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02b908, L"szKeyDeviceID", 0x7f21f1a8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DisplayDevices", 0x7f02b8e8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f02c080, L"DxDiag_SoundDevices", 0x7f02c0a0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f02c080, L"DxDiag_SoundCaptureDevices", 0x7f02c0f0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DirectSound", 0x7f02c080)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DirectMusic", 0x7f02c1b0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DirectInput", 0x7f02c218)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DirectPlay", 0x7f02c280)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x7f02c600)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02c618)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02c630)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02cd08)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02d0f8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02d6e0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02db08)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02df30)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02e358)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02e780)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c600, 1, 0x7f02ebd8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x7f02c3d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x7f02c3d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x7f02c3d8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c3d8, 1, 0x7f02c3f0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dsnoop:1"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x7f02c3a0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c3a0, 1, 0x7f02c3b8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x7f02c3d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c3d0, 1, 0x7f02efa8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"Hauppauge WinTV PVR-150"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{1B544C22-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x7f02c3d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c3d0, 1, 0x7f02fdf0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"DirectSound: dmix:1"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	IEnumMoniker_Next(0x7f02c3d0, 1, 0x7f02c340)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szCatName", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidCat", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Name:L"dmix:1"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer 	Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szClsidFilter", 0x7f21ea80)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"szName", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwMerit", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwInputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x7f02c2e8, L"dwOutputs", 0x7f21ea70)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x7f0271b8, L"DxDiag_DirectShowFilters", 0x7f02c2e8)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x7f0271b8, L"DxDiag_DisplayDevices", 0x7f21f308)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x7f02b8e8, L"0", 0x7f21f304)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x7f02b908, L"szDisplayMemoryEnglish", 0x7f21f2e4)
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x7f0464d8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x7f0469c8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x80710638) : stub
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x7f0464d8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x807105e8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x80a204f0) : stub
err:seh:setup_exception_record stack overflow 1120 bytes in thread 0045 eip b7cee1e3 esp 7e038ed0 stack 0x7e038000-0x7e03a000-0x7e149000
err:ntdll:RtlpWaitForCriticalSection section 0x7e6058a0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0025, blocked by 0045, retrying (60 sec)

```


lspci
```
00:00.0 Host bridge: nVidia Corporation Unknown device 0070 (rev c1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:06.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:07.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
06:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

```

---

### Post by om1 on 2008-04-28
ok i have a different problem im running 8.04 X86 with wine 0.9.60

i launch wine with wine "C:\Program Files\Guild Wars\Gw.exe" and ill i get back is 

Segmentation fault 

any ideas or suggestions?

---

### Post by Virgilius on 2008-04-29
I am running GW on a program called Wine-doors (a derivative of WINE) and it works a lot faster. But, the problem now is this; my graphics for the game (the 3D graphics) are missing and there's blue in the background, like pixel tears :( Is there a way around this?

---

### Post by gavinjb on 2008-04-30
Hi,

I haven't played GW for a while but from what I remember your issue with the graphics not drawing correctly is to do with either

1. The Install (I always used the install script on this post)
2. Your Graphics driver, I know that there have been with some versions of Wine big issues with shaders and ATI Graphics Cards

---

### Post by Torgas Prim on 2008-04-30
I was wondering if we can just install VMWare and run GW inside of it....
Will that work better than all this crap we have to go through to get a game to work properly?

Someone test it out for us and see.

---

### Post by om1 on 2008-04-30
> **Torgas Prim said:**
> I was wondering if we can just install VMWare and run GW inside of it....
Will that work better than all this crap we have to go through to get a game to work propeerly?

Someone test it out for us and see.

if you have a computer that can handle running windows inside of your ubuntu system... vmware is just a way to have virtual computers (virtual machines) so infact you would be running an os inside of an os with guild wars running inside of the second os

---

### Post by Djembe on 2008-05-01
> **om1 said:**
> ok i have a different problem im running 8.04 X86 with wine 0.9.60

i launch wine with wine "C:\Program Files\Guild Wars\Gw.exe" and ill i get back is 

Segmentation fault 

any ideas or suggestions?

I had the same issue but fixed it by adding -windowed to the end of the command string.  It seems to be running fine now except I don't have sound

---

### Post by Guinness70 on 2008-05-03
well, i gave up on Wine : all the issues with mouse and keyboard, graphics, audio and what not.

im testing the payable version : [Crossover]("http://www.codeweavers.com/products/")

keyboard and mouse now OK. cursoricon now only goes missing when mapping but as soon as you move it reappears.
audio is good. graphics are ok, some pixels now and then, not really bothering me.

works great. one thing i cant do in the game is minimize the window
becoz that will result in a Force Quit.
but i switch desktops if i need to check the net or run another program.
nother thing is simultanuously getting sound in TeamSpeak and GW.
its either one or the other.

i use the CrossOver for Linux (not the "for Games"), perhaps this "for Games" version would resolve the above issues.

---

### Post by Torgas Prim on 2008-05-12
I have tried just about everything I can following everyone's tips.....
Wine + Guild Wars = fatal video error
Crossover Games + Guild Wars = hanging before logon screen

I think HH and the latest Wine are bunk personally.
I used to get GW to run beautifully on LinuxMint, but that is when I had a crappy FX5500. Now that I have an HD2400, the only version of linux that will work is HH, but there is the rub...no games will work on it
:(

---

### Post by DarK SouL on 2008-05-12
I had the same problems and I just gave up and went back to Vista until the driver problems are sorted out.

---

### Post by unused_bagels on 2008-05-17
Ok, so the Wine page says that GW works perfect ("Platinum") on the newest Wine, on Hardy. I have both of these, and I could open it the first time, but it ran at a steady whopping 5 FPS (using all recommended tags, otherwise it wouldn't run at all). Now (without changing anything) it won't let me type in my password, but the sound magically works.
It said to play with the registry, but I can't find the folder these are in:
> If you are having graphics issues, use regedit to try some registry keys:*

    * UseGLSL=disabled
    * DirectDrawRenderer=opengl
    * OffscreenRenderingMode=pbuffer
    * RenderTargetLockMode=auto

Is there a thread for wine 1 or Hardy anywhere, or has anyone gotten it working on said versions who could hold my hand through this? ](*,)

---

### Post by om1 on 2008-05-17
this may help
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by S0VERE1GN on 2008-05-18
I'm haveing the problem everyone else is having here on hardy, but I can't seem to get this fix to work for me, the exact same thing keeps happening... I can't even get guild wars to open, it does the recurring lights glitch i think....

---

### Post by S0VERE1GN on 2008-05-18
i did he steps, all went well, but i still have the same problem. 

i get this...

fixme:win:EnumDisplayDevicesW ((null),0,0x32f034,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x1330a Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x22005b0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200aa : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2200fa0) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x1330a Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2510050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x147900) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2820050) : stub
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

---

### Post by Rplus9 on 2008-06-18
Running on Hardy: with up-to-date wine as of 18June2008.


Is there any current HowTo that addresses all the little configure things to get GW working?  I've been playing World of Warcraft awesomely on linux/wine (v.50 worked best for using additional mouse buttons)

I find it hard to believe that GW is working so poorly.

---

### Post by Torgas Prim on 2008-06-18
Naw, WoW was originally developed with a Linux and Windows client concurrently, so there is better front-end support from the beginning for WoW.

Anet has always stated they will never develop GW for Linux....so the hard time people are having getting GW to run properly on Linux.:(

---

### Post by 50below on 2008-06-29
i have a problem with guildwars says _**"unrecoverable graphics error and it must exit"**_ it's most prob mentioned in this thread somewhere but i couldnt find it using the search thread...i got an ATI X1650 using most recent version of wine...any ideas?

---

### Post by 50below on 2008-06-29
anyone?

---

### Post by 50below on 2008-06-30
well i kinda sorted my problem out im now using my onboard Geforce 6 and guildwars works...looks like my x1650 is out the job :(

---

### Post by STVA on 2008-06-30
Has anyone ever gotten Guild Wars working on ANY ATI video card?

---

### Post by 50below on 2008-06-30
it USED to work ages ago....dunno what i did though but it USED too work :(

---

### Post by Naiki Muliaina on 2008-07-01
Radeon HD2400, tis a no go. Says i dont have a good enough graphics card (or summit like that). Hardy Heron ubuntu.

I know that doesnt add much but just addin me voice to the non working ATI band :)

*Edit*

Message i get is unrecovorable graphics error once it moves of the initial loading screen.

The line i use to run GW is : wine "C:\Program Files\Guild Wars\Gw.exe" -dsound -noshaders flags -repair -image -dx8

and i run it in windows 98 mode.

---

### Post by 50below on 2008-07-01
i might try guildwars in cedega later..with my ati unless someone has tried???

---

### Post by laurielegit on 2008-07-03
> **50below said:**
> i have a problem with guildwars says _**"unrecoverable graphics error and it must exit"**_ it's most prob mentioned in this thread somewhere but i couldnt find it using the search thread...i got an ATI X1650 using most recent version of wine...any ideas?

same here... exept now when i start it i just get a black screen and the GW mouse. the computer then is not responsive to anything but ctr-alt-del, and when i try and log out it fails and freezes.

Please dont ask me anything to tecnical.. im only a linux noob/idiot/scum of the earth.

EDIT: oh and im using a ATI grafiscs card

---

### Post by Torgas Prim on 2008-08-02
Well, after all this muck trying to get Ubuntu, Wine, and Guild Wars to play nice with an ATI card, I just plain gave up.

I decided after a month or so to give it a whirl again but this time I took my crappy old FX5500 nVidia card and reinstalled it.
Re-installed Ubuntu, got all updates, installed latest Wine from HQ, and installed GW. And you know what???? It runs BETTER than on XP and Vista!

Oh, and Firefox3 is now awesomely fast and not eating all my CPU anymore.

WineHQ put it to Platinum while I was away and now if I can get Ventrilo and TeamSpeak to work properly, windoze is history on my machine

:)

---

### Post by sinaen on 2008-08-10
winehq.org have a faq about this in the apps-list of useful regedit keys

it says that the release of wine 1.0.0 something its something with the ATI code that scrambles the graphics....

here it says like this

 +-Direct3D
      |  |
      |  +->Multisampling
  [Allows/disallows the use of multisampling.]
  At the time of writing (a few days before the           release      of Wine 1.0) at least Nvidia
      |  |  their drivers suffer from GLXBadDrawable errors which are triggered in some cases
      |  |  by our multisampling code. It are bugs in their drivers but it affects a lot of
      |  |  important games like Halflife2. Further there are some FBO multisampling interaction
      |  |  issues. For that reason multisampling is not allowed by default although it works fine
      |  |  in a lot of cases. When set to 'enabled' programs can use multisampling.

---

### Post by sinaen on 2008-08-10
and in the faq i find

2.30. Running winecfg has No text or damaged text displayed

or

2.31. Using wine over remote X11 sessions and No text or damaged text displayed

Please make sure not have added any fonts to wine. Font conflicts can sometimes cause a similar issue. If a fresh wine prefix.(A copy of wine that nothing has been done to yet) Is having this problem. Try setting following in registry

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

Place above in text file and it can be inserted into registry by "regedit settings.txt".

This was report as been required of OS X on the 1 Dec 2007. This may change. Please apply only as required.

---

### Post by sinaen on 2008-08-14
http://www.petitiononline.com/gwlinux/

have you heard about this?

---

### Post by devosion on 2008-08-18
> **sinaen said:**
> [http://www.petitiononline.com/gwlinux/]("http://www.petitiononline.com/gwlinux/")

have you heard about this?

Nope but it is linkified and I have signed it.

---

### Post by devosion on 2008-08-18
> **STVA said:**
> Has anyone ever gotten Guild Wars working on ANY ATI video card?

Guild Wars was working well under my X1300 back on Gutsy. But ever since that card went caput, and i've switched to an nvidia 8500gt and Hardy, i havent been able to get Guild Wars to get past the first loading screen.

---

### Post by Torgas Prim on 2008-09-08
I had to reinstall Ubuntu after all the crap I added onto it :lolflag:
After all the updates and all GW looks like crap again.
Why does a game work, then not work after a fresh os wipe
? Anyone have any clues?

---

### Post by Ferrat on 2008-09-08
First guess would be that you had a setting before like in wine regedit or likewise that made it work?

---

### Post by Torgas Prim on 2008-09-08
Believe it or not, all I do is install Ubuntu, update and then install Wine. Change settings in Wine for GW to be Win2000 and OSS audio and that is it. I never do the regedit deal except for WoW and DiabloII.

I have done probably 50 installs of Ubuntu playing with everything and each time and it seems like a coin toss to get a game to work at the next install.

---

### Post by sinaen on 2008-09-08
Might be that you updated your drivers for the graphic card you have, or a later version of wine. Cause it seems that it is something in wines codes that make the directx games look like crap with the drivers from ati :( and it is a shame but what could someone do? also ive read that wine released a new version that was to be said to handle directx games more proper recently (read 1-3 weeks ago)

Right now i am sitting in windows. but the game is still looking like **** to me and i cannot play:confused: it in windows either now so im going to return to linux soon.. (it was mostly interest to see if i could get GW to work proper in windows but i couldnt with the latest graphics drivers or the game :( )

---

### Post by Torgas Prim on 2008-09-09
When I had Ubuntu installed about 5 weeks ago, all my games looked and ran smoothly.
Installed and updated Ubuntu, installed Wine and updated.
Installed the nVidia restricted driver and disabled desktop effects for more speed.
GW ran flawlessly until this past weekend I had to format and start over. When I performed the same steps in the same order, all I could see were the torch flames in the login screen. That is why I made the comment it seems to be a coin toss each time.
Back on XP until next round of updates and maybe GW will work by then and I will be sure to not reinstall Ubuntu after that
:lolflag:

---

### Post by sinaen on 2008-09-09
Well what happend to my x was that everything was a jigsaw puzzle, it was paralell lines with scrambled graphics, like rectangles with various gw and various desktop images and nothing worked exept the mouse. 

very annoying, and i think its the similar in windows. i begin to think that it is a hardware mailfunction that does this to me that makes me not able to run GW.... Pain In The *** i say... i wish i could run GW on a game console instead :(

---

### Post by inclinetobelieve on 2008-09-22
[For Guild Wars Cheats, ](http://www.exploitsrus.com/gw.html) [Guild Wars Dupes, ](http://www.exploitsrus.com/gw/dupes.html) [Guild Wars Bots, ](http://www.exploitsrus.com/gw/bots.html) [and Guild Wars Guides click here](http://www.exploitsrus.com/gw/guides.html)

---

### Post by Torgas Prim on 2008-09-26
Ok back on Ubuntu permanently :KS

I forgot to add the -dx8 -noshaders switches 8-[

---

### Post by Naiki Muliaina on 2008-09-26
GW works fine with ATI from Wine 1.1.4 and 1.1.5. No messing about needed on the radeon hd2400 and x1950.

---

### Post by zoomy942 on 2008-10-07
so, i am so close to GW working.  I must be missing something though

here is what it looks like.

---

### Post by Naiki Muliaina on 2008-10-08
Which version of Wine are you using?

---

### Post by WTF_Shelley on 2008-10-08
Ive finaly got Gw to work woot! (had to replace my ati with a cheap nvidia)  It works at a good speed, one problem though the smoke affects have a weird outline and some distant buildings and mountain tops are just black squares until i get closer to them.


any ideas.

---

### Post by zoomy942 on 2008-10-08
> **Naiki Muliaina said:**
> Which version of Wine are you using?


thanks for the reply!

i am using version 1.1.5, the latest, from their website.

man - if we get this working i owe you lulnch for a month

---

### Post by sinaen on 2008-10-10
> **zoomy942 said:**
> so, i am so close to GW working.  I must be missing something though

here is what it looks like.

It is exactly how it looks for me but i have it fullscreen.... :(

---

### Post by om1 on 2008-10-12
have you installed the latest drivers for your cards?

---

### Post by sinaen on 2008-10-12
Well this time i have that. but i havent yet restarted my computer and tried them :)

---

### Post by sinaen on 2008-10-13
got guildwars to play but the faces are not visible entirely and when i came back from being out when the game loaded files the computer had crashed... :(

---

### Post by rasmus91 on 2008-10-20
Hi 

I also seem to have a problem, my GW crashes when it have just displayed the loading screen, the loading screen fades, then nothing happens. same for NWN2...

I've recently been told that play on linux works well, so im just going to try it. but do you have any ideas on what to do for wine to solve this problem, i think Ubuntu updated my graphic driver yesterday.

My card is: Mobile Intel(R) GMA 4500 MHD the card it self has 128 MB of ram, and should be able to draw 1415 MB from the system, i have 4 gb of ram so it should be all right.

i run 64 bit Ubuntu

Wine version... i think its 1.00 but im not sure at all... just going to update this post when i've found out.

Do you have any ideas for whats wrong?

---

### Post by sinaen on 2008-10-20
Rasmus 91 have you checked if you have direct rendering when you have run the program glxinfo ?

i had but my program still crashed. so i dont know what it is
and i do have the latest wine-version ... :(

---

### Post by rasmus91 on 2008-10-20
:s doesn't sound good... glxinfo... sorry but where to find it?

I think this is kinda strange, because in a older version of wine in ubuntu 7.10 i got GW working, just by installing it...

---

### Post by Shaythong on 2008-10-20
I got Guild Wars to work fine in Wine 1.1.6.

---

### Post by rasmus91 on 2008-10-20
hmm.... if i go to: "system/administration/hardware drivers" should it then show any, or are those "special" drivers for anything?

---

### Post by sinaen on 2008-10-21
glxinfo is something you put in  a terminal. :)

---

### Post by sinaen on 2008-10-25
well you got it to work?

i got my game to work and play with but i was only in for a while...
are there a Linux guild?

---

### Post by ironstorm on 2009-02-14
For those who have had the "Guild Wars: Music Plays, No Game Window" problem, see my post here...  
[http://ubuntuforums.org/showthread.php?t=498069&page=2#post6732983](http://ubuntuforums.org/showthread.php?t=498069&page=2#post6732983)

I'd be interested to know if people still have problems with that running it as an Emulated Desktop app

---

### Post by rasmus91 on 2009-03-14
> well you got it to work?

i got my game to work and play with but i was only in for a while...
are there a Linux guild?

Sorry for not writing on this thread for a long time.

No, Wine opens a window now, i see the cursor on a black screen. then the screen gives a couple of flashes, and goes to ubuntu login screen. :(

I have updated to 9.04 alpha and the graphic driver for GMA 4500 is far better in this version. But the computer still does the same thing. I don't really know what to do.

I've tried Wine, PlayOnLinux, but nothing seems to work... Haven't got the big help lately.

Does anyone have a suggestion?

btw glxgears gives me more than 1100+ fps by now (got 250 before) and this is my output of glxinfo:
```
rasmus@rasmus-Dell-E6400:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20090114
OpenGL version string: 1.4 (2.1 Mesa 7.3)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATIX_texture_env_combine3, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

36 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x94 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x95 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x96 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x97 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x98 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x99 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x9a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9b 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x9e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x9f 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa0 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa1 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa2 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xa3 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xa4 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa5 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa6 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa7 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xa8 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xa9 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xaa 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xab 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xac 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xad 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xae 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xaf 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb0 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xb1 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb2 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xb3 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6f 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None

36 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x74  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x75  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x76  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x77  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x78  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7c  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7d  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7e  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7f  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x80  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x81  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x82  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x83  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x84  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x85  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x86  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x87  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x88  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x89  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8a  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8b  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x8e  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x8f  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x90  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x91  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x92  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x93  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

rasmus@rasmus-Dell-E6400:~$ 

```

---

### Post by aphirst on 2009-05-05
I am led to believe that if you follow the instructions detailed on [this page](http://www.guildwarsguru.com/forum/showthread.php?t=10323347), you can run Guild Wars at a playable rate with minimal instability on the recent line of Intel GMA chips.

---

### Post by Torgas Prim on 2009-06-13
Have any others experienced GW having to repair the dat file every time you start GW? Eversince last month, I cannot get GW to load without that 20 minute process.
I had assumed it was because I was running it from an ntfs drive, so I installed windows, loaded my GW and it was fine. Defragged the drive. Moved a copy to my ubuntu Wine folder and tried launching from there but it still happens.

Any suggestions?

---

### Post by nowhere@cox.net on 2009-06-13
I had this happening on my Windows box and a quick reinstall from the DVD fixed it. It seems that the download never completely fixed the corrupted files so it redownloaded each time.  The corruption on my system came from a bad ram stick causing my system to crash four or five times in a row before I figured out which component was bad...



By the way, note to all: The latest builds from WineHQ repos breaks GW. I uninstalled and installed from the ubuntu Jaunty repo and it works fine. It's version 1.0.1 that's working...

---

### Post by Torgas Prim on 2009-06-26
Found out the issue. Wine 1.1.24 is the culprit and has moved GW to the Garbage section of the appdb because of this latest update.
Reverting to an earlier version..I chose 1.1, has resolved it.
I hope they fix it soon at WineHQ

---

### Post by kailkitsune on 2009-09-07
i entered every thing and know i have a small Q; ive been sitting here for about 20min, how long should this take?
*edit*
ok it finally stopped....... and now in worse off than before ill try and find a different root around this.

---

