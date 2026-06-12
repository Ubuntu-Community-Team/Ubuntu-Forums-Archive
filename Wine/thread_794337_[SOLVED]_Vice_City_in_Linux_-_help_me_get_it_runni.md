---
title: "[SOLVED] Vice City in Linux - help me get it running better!"
date: 2008-05-14
forum: Wine
---

### Post by BigSilly on 2008-05-14
Please!

I've held on to my beloved copy of Vice City even though I've not used Windows for over a year. I suppose I just hoped that one day it would be playable in Ubuntu. I decided today to try WINE again today. I'd tried to use it a few months ago and had no luck, but to my surprise and astonishment, it installed and started to play. Excellent!

However, it's not completely perfect. I set the screen resolution in game to my native 1024x768, and noticed that it didn't quite fill the screen as it should. I didn't mind this, but on exiting the game it had had the effect of shrinking my desktop to the same size. I had to logout and back in again in order to reset the screen.

Also, and I couldn't figure this out, but Tommy Vercetti was constantly running. It didn't matter how I set the controls I couldn't stop him running, though I did notice that the joypad seemed to confuse him further still.

Has anyone here any experience of fixing these issues? Please let me know how you did it. I have to say though, I got a kick out of seeing Vice City on Linux so well. Really caught me by surprise.

Thanks all. :)

EDIT: Hikaricore, I never noticed the sticky above. Please move to the correct forum, and accept my apologies.

---

### Post by cogadh on 2008-05-14
Have you tried the troubleshooting steps on the game's AppDB page?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3050](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3050)

---

### Post by DoktorSeven on 2008-05-14
I too would love a perfect GTA:VC in Linux, though we're getting closer!

First, good news: the "running forward" bug has been fixed in Wine 1.0rc1 (has to do with Wine's joystick/gamepad configuration).   

I get a crash back to desktop in several games (not just Wine games), so I have a keyboard shortcut that runs this:

```
xrandr -s 1 && xrandr -s 0
```

to reset the resolution to my preferred one (two xrandr calls because sometimes just setting it as 0 doesn't work -- also, if it doesn't set it to your correct resolution, look at what **xrandr** by itself outputs in a terminal to see which number you need to use in the last call).  Sometimes the mouse gets locked as well, and I find that I have to just rerun a game that fullscreens/captures the mouse and then exit it normally to get that back.

The only things left in VC are the very slow and choppy cutscenes (which I can do without) and texture problems on cars that causes quite a bit of slowdown in the game (it's an unimplemented FIXME in Wine that tries to render a special effect for the car textures in software and doesn't work too well).

I have confidence that these will get worked out eventually though, but the fact that they did fix the "run forward" bug made VC actually playable for me for the first time in Wine.

---

### Post by BigSilly on 2008-05-15
Thanks for your replies people. I never thought to check out WINE's database, but I will do. 

Please excuse my n00bness with WINE DoktorSeven, but at what point would I be inputting that command you recommended? Before or after I attempt to play the game? I presume you are recommending this command instead of logging out and back in again, would that be right? 

Overall though, considering it's a Windows game I was amazed that it ran at all. I'll hope then that in the future the WINE team will be able to make this game completely playable on Linux. It's a cast iron classic.

I'll keep my eye out for WINE rc1. Thanks again. :)

---

### Post by cogadh on 2008-05-15
RC1 is already out, but it is only available in pre-packaged form for Hardy. You can get it by following the instructions here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by DoktorSeven on 2008-05-15
> **BigSilly said:**
> 
Please excuse my n00bness with WINE DoktorSeven, but at what point would I be inputting that command you recommended? Before or after I attempt to play the game? I presume you are recommending this command instead of logging out and back in again, would that be right? 


It's a command to run after your desktop has been shrunk down to a different size when the game exits.

---

### Post by BigSilly on 2008-06-20
Anyone using the new WINE version 1? Unbelievably, Vice City is absolutely perfect in it. I am totally thrilled. :D Pad works and everything! It still messes up the desktop resolution when you quit it, but otherwise it's absolutely bang on. Boy have I missed Vice!

I'm off for a quick play. I can't believe Vice City is running on Ubuntu!

:guitar:

---

### Post by cogadh on 2008-06-20
Holy crap! They even fixed those weird reflection problems on the cars! Another game off the list of apps that keep me tied to Windows!

---

### Post by BigSilly on 2008-06-20
> **cogadh said:**
> Holy crap! They even fixed those weird reflection problems on the cars! Another game off the list of apps that keep me tied to Windows!

Fantastic isn't it? :D

I couldn't figure out how to make a keyboard shortcut, but I created a little executable file with DoktorSeven's script above, so now I can just double click it when I exit the game to restore my resolution. 

Totally thrilled!

---

### Post by cogadh on 2008-06-20
I don't seem to have that resolution problem, but I run the game at the same resolution as my desktop. The only issue I have is the refresh rate gets reset to 60Hz, when I normally keep it at 85Hz. I think there might be a way around that by editing VC's settings file though.

---

### Post by BigSilly on 2008-06-27
> **cogadh said:**
> I don't seem to have that resolution problem, but I run the game at the same resolution as my desktop. The only issue I have is the refresh rate gets reset to 60Hz, when I normally keep it at 85Hz. I think there might be a way around that by editing VC's settings file though.

I fixed my resolution/refresh rate issue by unticking the option to "allow the window manager to control the windows" in the WINE graphics configuration, and also setting it to "emulate a virtual desktop" at my proper resolution. It seems to have done the trick! \\:D/ 

Seriously, I am absolutely stoked that this runs so beautifully in Linux. The last time I had XP installed, I had all sorts of issues with Vice. I couldn't get any sound, and it was choppy as hell. Can you believe a Windows game runs better on Linux? Hehehe! 

I know it's an old game, but it's a real personal fave of mine. Having been an eighties child, it really hit the spot for me. For me it has an atmosphere that none of the other GTA's quite got a hang of. 

My heartfelt thanks to the WINE devs for making this a reality. ThankyouThankyouThankyouThankyouThankyou! You're the best. I doff my guitar to you.

:guitar:

---

