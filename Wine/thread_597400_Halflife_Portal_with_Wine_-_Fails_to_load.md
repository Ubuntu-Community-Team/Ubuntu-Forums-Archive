---
title: "Halflife Portal with Wine - Fails to load"
date: 2007-10-30
forum: Wine
---

### Post by donovanh on 2007-10-30
Hey all..

I'm trying to get the Orange box games to work under a relatively fresh install of Ubuntu 7.1. I've got Steam installed and the game Portal is ready to go.

However when I launch the game, it loads for a few seconds and then the window vanishes from the taskbar before anything appears on the screen.

I had a feeling it may have something to do with compiz, but I've not been able to find how to disable compiz and test it.

I tried this: [http://ubuntuforums.org/showthread.php?t=176636](http://ubuntuforums.org/showthread.php?t=176636)

But I'm stuck as to how to use the nonXgl command with a Steam game running under wine.

Any suggestions appreciated!

Don

---

### Post by Sockerdrickan on 2007-10-30
Try different dxlevel commands like -dxlevel 80

---

### Post by Doctoxic on 2007-10-30
try adding this (or amending the entry you already have) to the end of your xorg.conf file (need a restart i think

Section "Extensions"
	Option "Composite" "disable"
	EndSection

you didn't say if its just portal thats not working or HL2 as well

doc

---

### Post by donovanh on 2007-10-30
Thanks for the replies.

I've tried various commands including -dxlevel, -windowed, -novid etc but without luck.

Regarding the xorg.conf change.. I've just tried that but it doesn't seem to have changed much.

I had HL1 running fine earlier, but haven't installed HL2.

If it is related to X, is there any way to temporarily switch off the conflicting process?

---

### Post by donovanh on 2007-10-30
Still trying.. I've updated wine to 0.9.47.

I'm getting a lot of messages in the terminal when trying to run Steam.exe through wine.. could this be a cause of the issue?

> err: dsound: DSOUND_MixOne Fatal error. Under/Overflow? primary_done=27996, mixpos=26034/73728 (26034/73728 ), primary_mixpos=1372, writepos=6144, mixlen=8116
err: dsound: DSOUND_MixOne Fatal error. Under/Overflow? primary_done=27996, mixpos=26034/73728 (26034/73728 ), primary_mixpos=1372, writepos=6144, mixlen=8268


---

### Post by aoanla on 2007-10-30
Well, firstly, you *don't* want wine 0.9.47 - that has a regression in it which seems to cause Source engine games, like Portal, to crash for many people.
Apparently this is somewhat fixed in 0.9.48, which you might want to try once the package is generated (sometime soon). Otherwise, try using 0.9.42, which seems to be stable for everyone.

One thing you might try is setting the hl2.exe in the Portal game directory to be run in Windows 98 mode using winecfg. That also seems to help stability.

---

### Post by donovanh on 2007-10-31
aoanla - Thank you for the tips. I've updated to wine 0.9.48, and set the hl.exe to run as Windows 98.

It's so close! The game's blurred background appears, but gives an error stating that DirectX 8 is needed to run the game. This is even though it's being launched with -dxlevel 80, and again with -dxlevel90.

Further, if I try a second time to launch the game, I get a registry error that states that another process is active. Aside from rebooting, is there a way to restart wine fully?

Many thanks for your continued help,

Don

---

### Post by aoanla on 2007-10-31
For the second problem (Steam complaining about the registry being in use), it is often sufficient to close and rerun Steam (you may need to do this twice, for some reason). 

For the first, I'm not sure what's going wrong. If I run Portal with -dxlevel 70 then it complains at me about the DirectX version, but I've never had your issue...
Although it's probably not the issue, I assume you're not getting any errors from wine any more? And other games with 3d acceleration are working fine?
(What happens with HL2? What version of DirectX does it think you're running, if you go into the video options menu?)

---

### Post by donovanh on 2007-10-31
I'm installing HL2 now to see if that's any different..

The error that seems to be showing up most in the terminal is this:

```
err:d3d:IWineD3DDeviceImpl_SetRenderTarget (0x145ac8) : Only 1 render targets are supported.

```

I'll let you know what HL2 says. Cheers again for the help.

Edit: It seems to believe I have DirectX 6.14.0.0.

The framerate is very very slow.. posssibly because of comvis? But at least HL2 runs :)

---

### Post by escobar_ on 2007-10-31
Try disabling compiz: System -> Preferences -> Desktop Effects

and then running HL2.

---

### Post by donovanh on 2007-11-01
After a clean install of Ubuntu, I've managed to get HL2 working an recognising the -dxlevel 81 launch command.

I've been running it after using "metacity --replace &" to switch off the compiz, but the framerate is still absolutely dire.

My graphic card isn't very powerful (Radeon Mobility X200), but under windows it is playable enough. It's like the graphic card isn't handling the graphics but relying on the processor instead (the textures are nasty, and framerate is close to 1 per second).

---

### Post by escobar_ on 2007-11-02
Umm, your graphic card sure is underpowered. I have the same card on my laptop and couldn't even run HL2 properly on windows.

---

### Post by donovanh on 2007-11-02
Thanks for the reply Escobar.

However I'd disagree about the capabilities. I played and completed halflife 2 and portal in windows. Sure, there were scenes that juddered a bit, but the majority was absolutely fine. There is a huge difference between the graphic performance on windows and on linux.. which is fair enough I guess.. I'll use Ubuntu for most stuff and boot into windows when I want to game.

---

### Post by drcranium on 2007-11-02
Sorry. Disregard.

---

