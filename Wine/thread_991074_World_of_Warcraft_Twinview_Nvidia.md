---
title: "World of Warcraft Twinview Nvidia"
date: 2008-11-23
forum: Wine
---

### Post by btallas on 2008-11-23
Running Ubuntu 8.10 64 bit.  Video card is a new GTX 260 core 216.  Got the restricted drivers setup.  Running 2 lcd monitors, one 19" 4:3 that runs 1280x1024 and one 24" 16:10 that runs 1920x1200 (this is the primary panel).  Have twinview setup to extend the desktop to the 19" panel.  Everything runs fine on the desktop.  Install wine (1.1.9), download World of Warcraft and install it, everything goes smooth.  Run the game and it launches in the 24" panel but it launches in 3200x1200 and there is no option to change resolution.  It looks like it's running my entire extended desktop on my one 24" panel.  Any way to get WoW to run on the one panel at the correct 1920x1200 resolution?

I was just messing around in the configure wine panel and noticed a setting for emulating a virtual desktop.  I set that to emulate a 1920x1200 desktop and WoW works great in that but the only issue is the game will only run in 1920x1200 (which is great) but the virtual desktop is prohibiting from seeing the entire top and bottom area (which is fairly game breaking considering you can't use any of your abilities).  Is there anyway to make the virtual desktop run full screen?

Funny thing about this is I was running an ATI 3870 before buying this new nVidia card.  The ATI card ran this dual monitor setup fine, no issues whatsoever.  The games I ran weren't extremely fast or anything but there was no dual monitor issue.  Only reason I went with nVidia was because it is generally understood that their linux driver is superior.  I'm no longer entirely sure that is true.

---

### Post by btallas on 2008-11-23
After messing around with virtual desktop, I just unchecked it and went back into WoW and it's working great.  Under video options it still says it's in 3200x1200 but it's actually playing in 1920x1200.  Checked out the Config.wtf file and confirmed the display is 1920x1200.  Guess whatever is set in Config.wtf overrides anything in the video options in game.  Either way, it's working great.  Now if I can only get Ventrilo to work with OSS, I'll be pretty much done with windows.

---

### Post by Phil Urich on 2008-11-25
Out of curiosity, how did you have your dual display set up with the ATI card before?  I've only had Nvidia cards for my multiple-monitor setups, but my next computer is almost inevitably going to be using an AMD/ATI card.  Is it a proprietary extension like TwinView? (which is seriously flawed, but I'll admit I have waaaaay too much experience with by now).  Or does Xinerama support having multiple screens at different resolutions?  Or were you just having multiple X displays? (ie. you wouldn't be able to have windows spanning across).

---

### Post by btallas on 2008-11-25
Honestly, it just worked out of the box when I installed the restricted ATI driver.  All I had to do was enable the other monitor and tell it where it was located (right of, left of).  After that, any game or app I used just "worked".

---

