---
title: "Steam games utterly broken in Wine (multiple versions)"
date: 2007-10-18
forum: Wine
---

### Post by aoanla on 2007-10-18
So, I know that Wine has had problems for the last couple of versions with running Steam/Source games, but it seems that people mostly manage to get /some/ version of Wine to work.

I'm just trying to play Half-Life 2 (well, I'd like to be able to play other games - I'd /like/ to be able to buy The Orange Box and actually expect to be able to play the games in it...), but so far I have failed utterly to get the thing to launch.

I have an ATI X1950 Pro, and am currently running the 8.41.7 fglrx driver, which appears to provide actual functional hardware acceleration (and glxinfo reports direct rendering, which is good). I am not stupid enough to try getting Compiz to work with fglrx, so there's no 3d accelerated desktop. 

I'm running the 64bit Feisty, and am using the budgetdedicated repository for AMD64 builds of wine.

I have tried the following versions of Wine: 0.9.47, 0.9.46, 0.9.43, 0.9.38 (this last, some time ago, and with an older fglrx version).
I can get Steam to launch in all of them (and I installed Half-Life 2 in 0.9.38, so the installer was fine), but as soon as I try to launch HL2, either from the commandline, or via the Steam GUI, the Steam process either crashes (in 0.9.43), or "launches" nothing at all (the screen resolution changes, but after that, I am returned to the desktop, with no harddisk activity at all - nothing happens, even after 10 to 15 minutes of waiting).

I've tried dxlevel at 81, 80 and 90, disabling and enabling pixel and vertex shaders, both the ALSA and OSS audio drivers (and with the hardware acceleration at both "Full" and "Emulated"). 
I've tried deleting the ClientRegistry blob, which doesn't seem to make much difference.
I've tried disabling the Steam Community In-Game.

Nothing works.

Please, someone tell me they have more ideas about what to try?

---

### Post by aoanla on 2007-10-18
Hrm.

Trying wine 0.9.41, I can get Half-life 2 to run... only for it to crash after about 5 minutes of play (consistently) with the error:

wine: Unhandled page fault on write access to 0x00000022 at address 0xd388a37 (thread 0045), starting debugger...
Unhandled exception: page fault on write access to 0x00000022 in 32-bit code (0x0d388a37).

(and then a full register dump)

This is not a /massive/ improvement over not being able to play the game at all...

Wine 0.9.42 has basically the same behaviour, but lasts for about 10 minutes, rather than 5. This is still not optimal.

---

### Post by aoanla on 2007-10-19
*bumped just in case anyone actually has any ideas that I've not tried*

Is it worth going back as far as the pre-0.9.40 versions of wine? I seem to remember that people have the best success with 0.9.41 or so, which doesn't seem to be stable for me.

(In case people are thinking: oh, well it's the graphics card, I should note that WoW works perfectly well under wine on this machine.)

---

### Post by aoanla on 2007-10-20
More information:

Portal works (with large areas of the left-hand side of the screen black, for some reason) with 0.9.42, but crashes on loading the first level (without wine errors) if I try to change any of the video settings.
In 0.9.46 and 0.9.47, steam crashes on trying to load it in the first place, as with HL2.

If someone has any suggestions (I know that 0.9.47 is considered dodgy for Source games at present), then feel free to comment.


On a related note: all Orange Box games, other than Peggle Extreme, tell me that my video drivers are out of date when trying to run them from Steam. Is this a problem that everyone has? (Even 0.9.47 does this, before it crashes.)

---

### Post by Alex Carroll on 2007-10-20
Hi, I've been having countless problems with CounterStrike and other games, but I've just tried the 0.9.41 Wine release and it worked. I, like you, am on the 64-bit version, using an ATi X1800XL. I, however, used Envy to install my video drivers.

---

