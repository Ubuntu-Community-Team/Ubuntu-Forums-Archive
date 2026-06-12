---
title: "Broodwar under WINE?"
date: 2008-01-18
forum: Wine
---

### Post by Syndacate on 2008-01-18
Does anybody have the latest version of starcraft broodwars (1.15.2 I believe) running on WINE version 0.9.53 ?

I'm getting no sound, with any driver selection, but I'm getting sound fine in max payne and more closely related to SC: Diablo II.  

The sound ran fine the first time (through the cinematics thing), but then brood war got all funny and went black so I hit <ctrl><alt><F2> but "startx" failed because it was already running (??) - so I restarted from the command prompt, and then when I tried starcraft again, it works, but no sound.

Furthermore, it won't connect to EAST battle.net and of course battle.net isn't displaying worth of crap.  It connected fine to Europe, but East failed (??) - though I don't really care what server I play on, but b.net itself is all black - I was able to use shortcut keys to make a game and it played fine (crashed when I quit b.net though).

Seems to be a lot of problems here but the general consensus about BW on WINE is that it works 100%...

Can anybody lend a hand?

EDIT:
PS:  The reason given when it won't connect to battle.net is "unable to detect application version, please install the latest ... "

---

### Post by tatrefthekiller on 2008-01-18
To restart X, you should use :

/etc/init.d/gdm restart

You could try to kill wine with :
killall wine
or killall wineserver

You can see all processes by typing :
ps -aux

Try to kill wine and/or Starcraft related processes.

You should  be able to go to X again (ctrl-alt-F7) and see the errors through wine output.

It seems that you get a screen problem, when resolution changes after cinematic...

---

### Post by Syndacate on 2008-01-18
> **tatrefthekiller said:**
> To restart X, you should use :

/etc/init.d/gdm restart

You could try to kill wine with :
killall wine
or killall wineserver

You can see all processes by typing :
ps -aux

Try to kill wine and/or Starcraft related processes.

You should  be able to go to X again (ctrl-alt-F7) and see the errors through wine output.

It seems that you get a screen problem, when resolution changes after cinematic...

It was working 100% until it crashed during that cinematic.  Though I'm not sure how the game play was as that's obviously the first time it's turned on.

EDIT:
PS:  The two main problems still are:
- No sound (though I have sound on the splash screen)
- It doesn't recognize version when I try to connect to b.net

---

### Post by menancito on 2008-01-19
I know it may sound cliche, but do you have compiz enabled. If yes go to the 'none' visual effect setting and try it anew. I haven't actually tried it myself, but here's what wine HQ's got to say about it:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=149")

---

### Post by Syndacate on 2008-01-21
You mean turn them all off?

I don't have a "none" setting in the compiz setup.

---

### Post by Syndacate on 2008-01-25
Update:

If you know your way around the game menus you can make multi-player work.  For player enter screens you just have to move the mouse around to get the black spots out of the way.  If it sticks when changing screens - click the mouse button (try to make sure you're not on a button), that'll change the screens, b.net profiles are kinda hard (impossible) to read, and the channel menu is very hard to see as well.

I got the sound working in it by using a different sound card.  Which is weird if you take into account the fact that it works fine with EVERYTHING else.

Recommendation:  Make real good friends with the game make menu and the channel menu - and learn the shortcut keys (friends, create, join, channel, etc.).

Haven't gotten worked out yet:  The mouse has a slight delay on it making for a really crappy game play experience :(.

---

