---
title: "[SOLVED] WoW entire system crash but only after 2nd try"
date: 2008-06-20
forum: Wine
---

### Post by jasontu on 2008-06-20
- Wine Version: 1.0
- Sorry no terminal output I can get to because this thing c-c-crashes my system
- Configeration:
Windows XP
No library overrides
ALSA Sound, emulated driver
Registry tweak found here
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

Also running ApplyToForehead Add-On

System
CPU: Intel Pentium 4 540
MB: Intel 945GCM-S2C
Video Card: Axel nVidia 6600 512mb running on EnvyNg drivers, but had same issue with official drivers as well

I have an odd issue with running World of Warcraft through Wine.  Everything works perfectly well the first time I start the game.  I mean it is no difference between how well it runs on Linux versus Windows.

When I begin start the game after exiting or shutting down, it will completely freeze if I touch any of the buttons on the login screen.

There is a work-around I discovered for this which is to completely delete my config.wtf and copy and paste a version I wrote at the beginning.  The only difference I can see between the two config.wtf files are these lines:

> SET gxRefresh "59"
SET Sound_VoiceChatInputDriverIndex "1"
SET Sound_VoiceChatOutputDriverIndex "1"
SET Sound_OutputDriverIndex "1"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET showPartyDebuffs "0"

I have no clue what freaks out the machine about these.  When it crashes no amount of ctrl-alt-backspace or anything that I know of will break it out of the freeze.  I simply have to do a hard reboot.

Please share any tips you may have.

Thank you!

---

### Post by Faud on 2008-06-20
I wonder if it's your screen refresh rate messing with your monitor....59 doesn't look like a "right" number. I would go to 
```

nvidia-settings

```
and see what the refresh rate is and put that number in as your first thing to try

---

### Post by jasontu on 2008-06-21
I noticed that too.  There is no 59 Hz refresh rate for my monitor so I have no idea where WoW got that from.  After setting both to 60 however it still causes the same crash.  In fact, I have the exact same text in my Config.wtf as I do in my backup Config.wtf and it will cause the same crash.  The only way I can fix it is to delete the original Config.wtf and move the backup into the WTF folder.  Even moving the backup Config.wtf into WTF folder and asking Ubuntu to "replace" the file doesn't work.

Bizarre huh?

---

### Post by jasontu on 2008-06-21
Solution / Work-around found!

[http://ubuntuforums.org/showthread.php?t=836254](http://ubuntuforums.org/showthread.php?t=836254)

I just made an executable that automatically deletes my Config.wtf and replaces it with a back-up Config.wtf every time I launch WoW.  It seems to make WoW happy.

Just remember that you'll lose any configurations you make in game.  Any configurations you want to make permanent have to be done textually and in the back-up Config.wtf rather than the Config.wtf in the WTF folder.

Thanks all!

---

