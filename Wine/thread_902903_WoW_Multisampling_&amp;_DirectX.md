---
title: "WoW: Multisampling &amp; DirectX"
date: 2008-08-27
forum: Wine
---

### Post by pheebs on 2008-08-27
Hey guys!

Finally got my new shiny 22 inch monitor, 300 gig laptop HD, and most importantly: Wow working in ubuntu!

My main question is about a little problem i'm having with changing the multi sampling option in the video settings. There's a few options available, but every time i change it, it reverts to the default '1x' (all the other settings can save and work perfectly cranked to the max).

I've done some googling and have only found a few dead ends:

The only 'solution' i've found tells me to run wow in direct x mode and then save the settings, except for some reason when i do so in the terminal i get a memory read error and the game crashes.

Is this the correct path to take?

Also do i need to enable anti aliasing in my nVidia Xserver config, and if so what is the correct setting?

Keep in mind that while i have some previous experience w/ ubuntu, i'm still very nubbish with commands/permissions etc. :)

I have a GeForce 8600M GT in a dell insprion 1520 laptop.

Any help is greatly appreciated!

---

### Post by Mahinva on 2008-08-27
The only workaround I can think of would be to manually change the anti-aliasing value in your config.wtf file.

[_WoWWiki_](http://www.wowwiki.com/Config.wtf_defaults) shows that there are 2 values that configure anti-aliasing - "gxMultisampleQuality" and "gxMultisample".

In looking at my own config.wtf, I have the following: SET gxMultisampleQuality "0.000000" and so I'd suggest that you fool around with that value, keeping in mind what it was by default in case you need to revert to it again.

Another thing to look into is using the addon called "Apply To Forehead" found here: [http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html) I can't say much about it though, as I have not needed to use the addon.

I hope this helps. :)

---

### Post by pheebs on 2008-08-27
Thank you for the prompt response.

I tried changing the value in the config file to "2.000000", but after logging in and exiting the config file changed back to 1.000000 .  In addition i tried changing my refresh rate which was set to a default 50 for some reason with the WoW ingame gui to one of the presets, strangely this value stayed in the config while the multisample was reset.  However when i tried to input a custom value into the wtf file, it was reset.

My monitor lists: 'H:65KHZ V:60KHZ' as the rates, and all of the presets are above 70, so i'm a little stumped in that category as well.

Update: I tried overriding the settings with Xserver.  It worked, but even just 2x makes the game unplayable.  Arrg, so close!

Also i have noticed that the ingame multisampling options are considerably limited compared to when i was playing on windows. I remember there being over ten options in the menu, now there are only 4.

---

### Post by Mahinva on 2008-08-28
Darn it. :(

As far as refresh rates go, my monitor is to refresh at 60Hz, however WoW lists 62-67Hz so in that respect, I'm in the same situation as you. I have yet to figure this out so I just leave the refresh rate as it is by default.

I don't have any other ideas as far as anti-aliasing goes; have you tried the Apply to Forehead addon?

Multisampling options ingame can be more diverse because the options include a combination of color depth, color bit and then the multisample rate. I have 8 options, but if I try to toggle mine, the game locks up. The 6 missing multisampling options could be unnecessary; I have some 16 bit options that I never used (even when on XP) because my display ran better on 24 bit. Hopefully that is the case with your missing options.

However, as my computer was never able to smoothly run the game on high settings (even when I had XP), I tend to keep my multisampling at x1. So, I'm afraid I can't really offer more insight. Hopefully someone else will be able to help you further.

---

### Post by Extreme Coder on 2008-08-28
WoW crashes with Wine when trying to use Multisampling in OpenGL. So far, it only worked for me in Cedega, using D3D.

---

