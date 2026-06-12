---
title: "How to Alt-Tab in Warcraft III using Wine"
date: 2008-06-18
forum: Wine
---

### Post by Tekmo on 2008-06-18
I created an account with Ubuntu forums JUST to post this message because this seriously was the only thing that kept me from using Linux full time.  I had a lot of problems with this and couldn't find a solution anywhere (including on these forums) and I can't register with the Wine application database right now due to some scripting error on their site, so I thought I would start by posting it here.

First off, let me just explain that the only thing I figured out was Alt-Tabbing.  The movies still don't work, but that was not an issue for me.

To be able to alt-tab out you run warcraft with the opengl and window flag:

**wine /path/to/war3.exe -opengl -window**

...and then when the window shows up, you just maximize it.

That's it!  You can pan the view using the screen edges just like in full-screen mode, but it still is a (big) window that you can minimize and tab through just like other windows.  I actually consider this setup superior to the one I had in Windows XP because I can browse the web and chat in the foreground while still being able to view Warcraft in the background, whereas in windows I had to have Banlist open to be able to monitor Warcraft while I was tabbed out (which I was usually doing while waiting for games to fill up or waiting on clanmates in our clan channel).

The only flaw is that Warcraft appears choppy only while it is in the background, but foreground applications are still fine.  My computer has a good graphics card, but other people may get poor performance results even if it is in the foreground because it is being windowed after all.

It took me so long to figure the maximize part out.  So here are a few things I had tried out before that did not work out or I considered inferior solutions:

**wine /path/to/war3.exe**

Warcraft works (besides the known wine problems with videos), but I can't alt-tab out.  If you try it just takes you back to the Warcraft window.

**wine /path/to/war3.exe -opengl**

I can alt-tab out under an older version of wine (0.9.x, something like that) and only if Warcraft is the same resolution as my desktop.  I was not happy with this solution because my preferred desktop resolution (1680x1050) was not the same as my preferred Warcraft resolution (1400x1050).  That and it required an old version of wine.

**wine /path/to/war3.exe -window [-opengl] without maximizing**

This seemed to be the most promising solution until I found out I couldn't scroll using the screen edges because it was in a window.  Using winecfg's directx option to lock the cursor to the window did absolutely nothing.  Same for using an emulated desktop with or without window: absolutely nothing.

**wine /path/to/war3.exe -window with maximizing**

DirectX couldn't handle it.  It works fine until you tab out and tab back in, upon which it messes up.

**wine /path/to/war3.exe -opengl on a different workspace and switch between workspaces**

It opens correctly, but when you switch to another workspace and back it just disappears completely.  You can only close it from system monitor.


I hope that helps and did not duplicate something somebody else already posted, but I seriously had a hard time finding this solution anywhere.

---

### Post by KuriKai on 2008-06-19
the crashing on different workspaces is fixed in the latest wine I beleive

---

### Post by davidw89 on 2008-08-11
> **Tekmo said:**
> I created an account with Ubuntu forums JUST to post this message because this seriously was the only thing that kept me from using Linux full time.  I had a lot of problems with this and couldn't find a solution anywhere (including on these forums) and I can't register with the Wine application database right now due to some scripting error on their site, so I thought I would start by posting it here.

First off, let me just explain that the only thing I figured out was Alt-Tabbing.  The movies still don't work, but that was not an issue for me.

To be able to alt-tab out you run warcraft with the opengl and window flag:

**wine /path/to/war3.exe -opengl -window**

...and then when the window shows up, you just maximize it.

That's it!  You can pan the view using the screen edges just like in full-screen mode, but it still is a (big) window that you can minimize and tab through just like other windows.  I actually consider this setup superior to the one I had in Windows XP because I can browse the web and chat in the foreground while still being able to view Warcraft in the background, whereas in windows I had to have Banlist open to be able to monitor Warcraft while I was tabbed out (which I was usually doing while waiting for games to fill up or waiting on clanmates in our clan channel).

The only flaw is that Warcraft appears choppy only while it is in the background, but foreground applications are still fine.  My computer has a good graphics card, but other people may get poor performance results even if it is in the foreground because it is being windowed after all.

It took me so long to figure the maximize part out.  So here are a few things I had tried out before that did not work out or I considered inferior solutions:

**wine /path/to/war3.exe**

Warcraft works (besides the known wine problems with videos), but I can't alt-tab out.  If you try it just takes you back to the Warcraft window.

**wine /path/to/war3.exe -opengl**

I can alt-tab out under an older version of wine (0.9.x, something like that) and only if Warcraft is the same resolution as my desktop.  I was not happy with this solution because my preferred desktop resolution (1680x1050) was not the same as my preferred Warcraft resolution (1400x1050).  That and it required an old version of wine.

**wine /path/to/war3.exe -window [-opengl] without maximizing**

This seemed to be the most promising solution until I found out I couldn't scroll using the screen edges because it was in a window.  Using winecfg's directx option to lock the cursor to the window did absolutely nothing.  Same for using an emulated desktop with or without window: absolutely nothing.

**wine /path/to/war3.exe -window with maximizing**

DirectX couldn't handle it.  It works fine until you tab out and tab back in, upon which it messes up.

**wine /path/to/war3.exe -opengl on a different workspace and switch between workspaces**

It opens correctly, but when you switch to another workspace and back it just disappears completely.  You can only close it from system monitor.


I hope that helps and did not duplicate something somebody else already posted, but I seriously had a hard time finding this solution anywhere.

When i open Warcraft 3 in full screen mode and i switch workstation with compiz..you know switching cubes..i can't get back into Warcraft III?

---

### Post by Ecna on 2008-08-30
Thanks! This was really helpful, but I have a way to take it one step further.

If you don't emulate a virtual desktop, you can use Compiz to force the game to run full screen. This gets rid of the window borders and menu bars, which means it's a lot easier to scroll in the game.

Go to System->Preferences->Advanced Desktop Effects Settings enable Window Rules, and put class=Wine in the fullscreen bar.

UPDATE: Use this instead of class=Wine: 
> title=^Warcraft III$
And it will only fullscreen War3 and not all wine apps.

---

### Post by Ng Oon-Ee on 2008-09-01
Hey, thanks so much for the useful research. Used some of what's here together with my own trial-and-error to write [this guide]("http://ubuntuforums.org/showthread.php?p=5703907#post5703907"), if anyone wants a complete solution, with proper scrolling and all.

---

### Post by k1ngb0b0 on 2008-09-19
> **Ecna said:**
> Thanks! This was really helpful, but I have a way to take it one step further.

If you don't emulate a virtual desktop, you can use Compiz to force the game to run full screen. This gets rid of the window borders and menu bars, which means it's a lot easier to scroll in the game.

Go to System->Preferences->Advanced Desktop Effects Settings enable Window Rules, and put class=Wine in the fullscreen bar.

UPDATE: Use this instead of class=Wine: 

And it will only fullscreen War3 and not all wine apps.

This FINALLY fixed my problem and had it working just like I wanted.

Can I buy you a cookie?

---

### Post by eagzor on 2008-10-24
I works much better but with one last issue, i use kde4 and i can scroll all sides except the down side, there is a "line" there which you have to keep your mouse cursor or else it won't sroll.
EDIT:
After reading the linked post, it seems enabling virtual desktop in winecfg and running WC3 without -window fixes it

---

### Post by raajheshkannaa on 2008-12-01
Thanks! This was really helpful, but I have a way to take it one step further.

If you don't emulate a virtual desktop, you can use Compiz to force the game to run full screen. This gets rid of the window borders and menu bars, which means it's a lot easier to scroll in the game.

Go to System->Preferences->Advanced Desktop Effects Settings enable Window Rules, and put class=Wine in the fullscreen bar.

UPDATE: Use this instead of class=Wine:
Quote:
title=^Warcraft III$
And it will only fullscreen War3 and not all wine apps.

Hey thanks a lot ECNA , yu saved my day , damn happy :))

---

### Post by hotweiss on 2009-01-07
> **raajheshkannaa said:**
> Thanks! This was really helpful, but I have a way to take it one step further.

If you don't emulate a virtual desktop, you can use Compiz to force the game to run full screen. This gets rid of the window borders and menu bars, which means it's a lot easier to scroll in the game.

Go to System->Preferences->Advanced Desktop Effects Settings enable Window Rules, and put class=Wine in the fullscreen bar.

UPDATE: Use this instead of class=Wine:
Quote:
title=^Warcraft III$
And it will only fullscreen War3 and not all wine apps.

Hey thanks a lot ECNA , yu saved my day , damn happy :))

Thanks for the tip! You wouldn't know how to make it fully maximize at the bottom, would you:

[[IMG]http://img211.imageshack.us/img211/9795/bottomre1.png[/IMG]](http://imageshack.us)
[[IMG]http://img211.imageshack.us/img211/bottomre1.png/1/w800.png[/IMG]](http://g.imageshack.us/img211/bottomre1.png/1/)

---

### Post by hotweiss on 2009-01-09
> **hotweiss said:**
> Thanks for the tip! You wouldn't know how to make it fully maximize at the bottom, would you:

[[IMG]http://img211.imageshack.us/img211/9795/bottomre1.png[/IMG]](http://imageshack.us)
[[IMG]http://img211.imageshack.us/img211/bottomre1.png/1/w800.png[/IMG]](http://g.imageshack.us/img211/bottomre1.png/1/)

Problem fixed. I enabled virtual desktop and disabled all of the desktop integration features; plus I removed the -window extension.

---

### Post by webchannel on 2010-05-31
> **hotweiss said:**
> Problem fixed. I enabled virtual desktop and disabled all of the desktop integration features; plus I removed the -window extension.

still problem on the lower part of the screen, mouse have some problem below the sreen...

---

### Post by Wandang on 2010-07-17
thx it worked for me.

summary: go to wine config, disable window-control features. enable virtual desktop, set to ur preferred value. then set ur desktop to that resolution.

get compiz -> windowrules -> fullscreen "title=^Warcraft III$"

start game with command "wine path/game -opengl

switching to the resolution b4 gaming is ok for me. at least i can alttab now since my mic doesnt work and i want to answer some icq messeges and stuff like that ;)

---

### Post by Beholder87 on 2010-09-01
This worked fine with me also. Now that virtual desktop is enabled in wine, I can ALT+TAB Warcraft III without problems, however **every** wine program opens in the virtual desktop now, which is really annoying for me because I have some programs that I wish I could see in the taskbar (which always went to taskbar before virtual desktop was enabled), but now they show up only on Wine Desktop. **Is there a way to configure wine to create the virtual desktop for only when warcraft is started?**

Thanks

---

### Post by tonkbert on 2011-05-04
Hello there!

I'm just wondering if you guys are experiencing any sort of issues on Ubuntu 11.04 (Unity interface) in combination with Warcraft 3.
I tried so many tweaks - still I cannot alt-tab out of WC3. Either you cannot regain control of the game's UI or it just shuts down on its own.


Would appreciate any help!!

-tonkbert

---

### Post by minimoo on 2013-05-02
I find a trick to this problem.

**First we need to change wine configuration:**
1. Open "Configure Wine".
2. Open "Graphics" tab.
3. Check "Emulate a Virtual Desktop".
4. Set the resolution according to your fullscreen resolution. (e.g: 1366x768)

**To play it with alt+tab enable:**
1. Change you workspace by pressing CTRL+ALT+RIGHT ARROW
2. Open "Warcraft III".
3. Press CTRL+ALT+LEFT ARROW to go back to previous workspace.
4. To resume your Warcraft III, press CTRL+ALT+RIGHT ARROW again.

And that's it.

Hope it's helpful.

---

### Post by minimoo on 2013-05-02
**Edit**

To set "Emulate a Virtual Desktop" for Warcraft 3 only, use this step:
1. Open "Configure Wine" (winecfg)
2. Navigate to "Application" tab, click "Add new application".
3. Browse for Warcraft 3 exe file, and select it. (e.g: warcraft3.exe)
4. Navigate to "Graphics" tab.
5. Check "Emulate a Virtual Desktop".
6. Set the resolution according to your fullscreen resolution. (e.g: 1366x768)
7. OK.

That's it, and enjoy!

---

### Post by oldos2er on 2013-05-04
Old thread closed.

---

