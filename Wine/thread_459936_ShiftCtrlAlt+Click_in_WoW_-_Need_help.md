---
title: "Shift/Ctrl/Alt+Click in WoW - Need help"
date: 2007-05-31
forum: Wine
---

### Post by DonPeppe on 2007-05-31
Hi All
I'm not sure this is the right place for this question, since it's HW related, but only happens on WoW.

I'm a linux newbie and I'm loving it so far.  I was able to install WoW (the only game I play at the moment) and I'm very pleased with the performance I get out of my box now.  However, I have a little hic-cup I can't find a solution yet.

I have a number of add-ons to the game to modify my UI.  Some of them require that I "Shift/Ctrl/Alt-Click" on something to make a particular action.  In particular the ace2 addon "Postal", lets you auto send an item by alt-clicking on it from your inventory for example.

The problem I have is that shift/ctrl/alt+click/rightclick doesn't work.  Only in WoW though.  If I try shift-click or ctrl- click on my gnome environment it does work as expected.  I have a MS Intellimouse explorer 5 button mouse, and all 5 buttons work fine in WoW  and out (having had to hack the xorg.conf file of course to make sure ubuntu recognizes the 2 extra buttons).

I have checked around for similar problems/solutions but I haven't seen anyone experiencing this problem.  How can I get around this issue?

---

### Post by DonPeppe on 2007-06-01
Shameless Bump.

I noticed that ctrl and shift do work.  Only alt+click seems to be bugged...  Any ideas?

---

### Post by hikaricore on 2007-06-01
If I remember correctly under gnome I needed to comment this line out in my Xorg.conf:

 > Option         "XkbOptions" "lv3:ralt_switch"

like so:

> # Option         "XkbOptions" "lv3:ralt_switch"

I could be wrong as I havn't used gnome or played WoW for awhile.

You can also check your keyboard settings under preferences in gnome for alt options.

Good luck,

--Aaron

---

### Post by yosser on 2007-06-01
> **DonPeppe said:**
> Shameless Bump.

I noticed that ctrl and shift do work.  Only alt+click seems to be bugged...  Any ideas?


I noticed this in Diablo 2 in Wine.

Makes it really annoying to pick up loot that drops.

How to fix?

---

### Post by yosser on 2007-06-01
> **yosser said:**
> I noticed this in Diablo 2 in Wine.

Makes it really annoying to pick up loot that drops.

How to fix?


Just as a heads up, to allow alt/shift + click in wine run programs, go to graphics tab in winecfg, then deselect the "allow the window manager to control the windows" option.

good to go. :)

---

### Post by DonPeppe on 2007-06-04
> **yosser said:**
> Just as a heads up, to allow alt/shift + click in wine run programs, go to graphics tab in winecfg, then deselect the "allow the window manager to control the windows" option.

good to go. :)


If I do this, I'm unable to type my password to log into the game.  Instead, a small text box appear at the bottom right corner of my screen with the characters I type.

> **hikaricore said:**
> If I remember correctly under gnome I needed to comment this line out in my Xorg.conf:

--Aaron

That line does not exist in my xorg.conf file

---

### Post by DonPeppe on 2007-06-12
Another Shameless bump to this

The game is playable and very enjoyable in Ubuntu, but I would really like to get the alt key to work on it, since many add-ons use it to relocate bars and widgets in the screen in conjunction to a click or right-click.

I tried to launch the game and log in to it, then changing the winecfg file as suggested before, but when I do that the game crashes badly (Ubuntu requires a hard reset).

Any other idea/tweak/hack I can try to get Alt-click to work with WoW?

---

### Post by DonPeppe on 2007-06-24
Any ideas?

---

### Post by m3741 on 2007-07-10
Sorry,  don't have a solution but I have the same issue and am looking into it.

---

### Post by m3741 on 2007-07-10
Got it! I would like to say that I figured it out but I got the solution from [http://ubuntuforums.org/showthread.php?t=351238]("http://ubuntuforums.org/showthread.php?t=351238").

If you go to System -> Preferences -> Windows then change the movement key to Super or something and you'll be good to go. Enjoy!

---

### Post by gpw797 on 2008-06-01
I have tried all of the above (and a few other things) and no luck here. Pretty sure I had it working correct before compiz was added,,, any other ideas for Heron users?

---

### Post by Sarmacid on 2008-06-07
The way I got shift+click to work again is disabling compiz

System -> Preferences -> Appearance

And select none in the visual effects tab.

A friend of mine said he downgraded his wine(No idea to what version) and now works for him too.

---

### Post by jmilest on 2008-07-11
That did it.  Thanks!

---

### Post by wylfing on 2008-10-25
I just wanted to add that my wife was having the same problem. She was unable to Control-Click to preview items, and unable to Shift-Right Click to socket, etc.

Disabling compiz before running WoW fixed the problem.

---

