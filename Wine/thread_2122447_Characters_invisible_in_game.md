---
title: "Characters invisible in game"
date: 2013-03-05
forum: Wine
---

### Post by watermelonfreak on 2013-03-05
Hi!
So I've heard about this problem a few times on other games, but I can't seem to find a way around it!
I got this game called "Tomb Raider: Reborn" (came out today or something) and when I played it, the characters weren't there. You could tell they were meant to be because there were shadows on the ground. 
The interactive objects around the place were invisible too. 
A big, blocky splotch also appears on the right-hand corner of the screen , as well as bad graphics at certain places. I know this can be fixed somehow since it disappeared for a fraction of a second, but came back.
Does anyone know what the problem(s) could be? Should I install something or change a code?
I'll answer questions and show pictures if asked, in case I wasn't very specific. 
Cheers!

---

### Post by Shadowstripe on 2013-03-05
I was checking here to see if anyone had got the game running and randomly checked your post, would be more helpfull if you put tomb raider in the topic title :)

I couldn't even get past the title screen (flickering)

are you using nvidia or ati ?

---

### Post by watermelonfreak on 2013-03-05
> **Shadowstripe said:**
> I was checking here to see if anyone had got the game running and randomly checked your post, would be more helpfull if you put tomb raider in the topic title :)

I couldn't even get past the title screen (flickering)

are you using nvidia or ati ?

Im using ati
i think you need a few things from wine tricks, like directX9 and it's dlls, .NET frameworks etc. I'm not sure, I downloaded a lot of Windows dlls off wine tricks.
But still, idk what to do. I know this happens on other games as well.

---

### Post by Shadowstripe on 2013-03-05
may not do anything but have you tried *winetricks glsl*=*disable* ? (this worked in the past with at least 1 other game)

as for the title screen flickering I tried it on a wine install with all the windows stuff installed and another fresh with nothing (not even directx) both run the same.

(nvidia)

---

### Post by watermelonfreak on 2013-03-06
> **Shadowstripe said:**
> may not do anything but have you tried *winetricks glsl*=*disable* ? (this worked in the past with at least 1 other game)

as for the title screen flickering I tried it on a wine install with all the windows stuff installed and another fresh with nothing (not even directx) both run the same.

(nvidia)

I tried it, but it didn't even let the game play. Well, it full screened and attempted to run, but it was just black and wouldn't do anything else.  :/ thanks anyway

---

### Post by Asatru9 on 2013-03-06
I've got some questions for you.  1)Which version of Ubuntu are you using?  2)Which version of WINE are you using?  Once we get those answered we hopefully can assist you.

---

### Post by Shadowstripe on 2013-03-06
op or ? I will post mine anyway in hopes someone can help (although I don't hold out much hope)

I'm using wine 1.4.1 and xubuntu 12.04 using the 310.14 driver.

there's (at time of writing) only 1 report on the wine app db ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=14996](http://appdb.winehq.org/objectManager.php?sClass=application&iId=14996))

seems he has the same problem as me but with wine 1.5.25


edit : pulled from the chat over there ....

also adding StrictDrawOrdering (wiki.winehq.org/UsefulRegistryKeys) supposed to reduce the flickering some

---

### Post by Shadowstripe on 2013-03-06
changing that last registry settings makes it almost playable for me

only a few minor problems

1 keyboard / mouse input do not work (workaround by using a gamepad but it does not detect second analogue stick meaning qtes that require left/right presses fail)

2 not sure what changed it but now for some reason now the xubuntu menu is always visible at the top

---

### Post by watermelonfreak on 2013-03-06
> **Asatru9 said:**
> I've got some questions for you.  1)Which version of Ubuntu are you using?  2)Which version of WINE are you using?  Once we get those answered we hopefully can assist you.

Alright, I have Ubuntu 12.04 and wine version 1.5.25 :3

---

### Post by Shadowstripe on 2013-03-06
> **watermelonfreak said:**
> Alright, I have Ubuntu 12.04 and wine version 1.5.25 :3

  the guys on appdb.winehq.org said they had to downgrade to wine-1.5.9 and the other wine 1.5.17 to get it working

Im going to try upgrade mine, not sure if its best to upgrade from the repositories on the site or to do it manually from source ? (would it make much difference?)

---

### Post by watermelonfreak on 2013-03-07
> **Shadowstripe said:**
> the guys on appdb.winehq.org said they had to downgrade to wine-1.5.9 and the other wine 1.5.17 to get it working

Im going to try upgrade mine, not sure if its best to upgrade from the repositories on the site or to do it manually from source ? (would it make much difference?)

Great! I'll do the same as you then :p 
I think theyre basically the same. Try either one I guess XD

---

