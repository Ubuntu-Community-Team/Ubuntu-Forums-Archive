---
title: "Team Fortress 2 Crash"
date: 2008-10-28
forum: Wine
---

### Post by Genji on 2008-10-28
Hi all,

I have recently converted from WinXP Pro to Ubuntu 8.04 after reading up on improvements made to wine (I have dabbled with Linux often in the past, several distros, but I kind of grew attached to Ubuntu 6.10. Gaming kept me on WinXP though).

Installation of Ubuntu, wine, steam and TF2 was flawless. I read up on the graphics issues and sorted all my problems out. Or so I thought.

I can boot TF2 up as normal, look through server lists as normal, and connect as normal. I get the game statistics and the usual load bars, but at the end of all these everything goes wrong.

The "Retrieving Server Info" load bar is fine, as is the "Sending Client Info" but as soon as the Client Info bar is full and I'd expect to enter the game, TF2 crashes and just shuts itself down.

Some Clarification on what my setup proces was etc:
I installed 8.04 from the liveCD.
I installed major updates
I installed the propriety graphics drivers for my graphics card
I made sure Desktop Effects were off.
I installed Steam
I installed TF2
I copied my WinXP WoW install via my secondary HDD to the programfiles in wine
WoW works 100% perfectly. No glitches in sound or graphics, pulls about 30 - 60 fps. No difference from WinXP at all.
Steam works perfectly (although for some reason friends chat is invisible, even after installing the tahoma font, but that doesn't matter to me)
TF2 loads perfectly, menu's work, resolution is ok, sound works, graphics work, server lists work. Just crashes when I'd normally enter a server.
Oh, I found a thread here that someones TF2 crashed cause of the Steam Community, my problem persists even after making sure Steam Community is off.

System Setup:
ASRock 4CORE-DUAL motherboard
Intel Celeron 3,3Ghz Processor
Sapphire ATI Radeon HD 2900 GT 256MB Graphicscard
Twin Corsair DDR2 512MB RAM (Dual Channel)
Sound Blaster Creative Audigy SoundCard
Ubuntu 8.04 (Compiz is installed, but Desktop Effects are OFF when gaming)
Wine (Whatever the current version of today is)

I haven't changed anything else so far as I am aware, I'd gladly paste in the Terminal Output code for you but the Terminal doesn't recognize spaces in the TF2 folder (folder is named "team fortress 2" in the usr steamapps folder) and changing the folder name to get round this problem so I can boot the hl2.exe file from the terminal gives me an error. If anyone knows a workaround for this, I&#314;l galdy follow it and paste in the Terminal Output tomorrow.

Any other questions or info needed I&#314;l gladly provide.

Thanks in advance,
Ben

**EDIT:** Ok, been reading up and checking other peoples experiences with crashes, just trying stuff out.
It seems that adding -dxlevel 81 to the launch options of TF2 within Steam allows me to join servers. Things run ok-ish but I have what I can only describe as black/dark mirror boxes round my health and top left. fps is okish but choppy, especially when other people are in my field of view. I take it this means that my problem is graphicscard/driver related, and judging from what has been said in other threads, there&#347; not much I can do about it but wait for ATI or switch back to Nvidea (I'd rather not switch to Nvidea, but hey.. I dislike windows more than Nvidea).

If indeed this is the core of my problem, then I guess there's not much else that can be done about it. However, any input is welcome.
I&#314;l try and upload a screenshot as that'll give a better picture of whats going on.

**2nd EDIT:**
Ok - screenshot added.
[[IMG]http://img247.imageshack.us/img247/7862/screenshotvu2.th.png[/IMG]](http://img247.imageshack.us/my.php?image=screenshotvu2.png)[[IMG]http://img247.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Genji on 2008-10-28
[SOLVED]

Ok, I must remember the golden rule of any troubleshooting: KISS

Keep
It
Simple
Stupid

Removed the -dxlevel 81 from the launch options, set TF2 resolution to 1440xwhatever it is instead of 1680x1050 :p

---

