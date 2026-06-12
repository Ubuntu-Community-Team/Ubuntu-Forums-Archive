---
title: "64bit flash (sort-of)"
date: 2005-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by punkass on 2005-05-13
Well I thought I would just drop a small note to anyone still trying to do battle with true 64bit Flash on amd64.

I am running hoary, but just updated my sources list to breezy, and found an updated version of libswfdec 0.3.4 and swf-player, and installed it, then reverted my sources list back to hoary.

It updated a few other packages as well, but I have seen no issues (YET).

the player works for about 40% of flash, it seems to have issue with flash with lots of actionscripting..so games etc dont really work, but plain old flash style movies etc seem ok, even the sound is good.

*But please note you are on your own if you try this, as its mixing hoary and breezy so its probably not the smartest thing to do.

---

### Post by poofyhairguy on 2005-05-13
Yet another reason (besides the fact that it offers no pratical speed increases) that people should use 32 bit mode....

---

### Post by punkass on 2005-05-13
[QUOTE=poofyhairguy]Yet another reason (besides the fact that it offers no pratical speed increases) that people should use 32 bit mode....[/QUOTE]

Actually when I first installed 64bit hoary on my new amd64 I found it to be quite a bit snappier.

Where as the 32bit xp install (dual boot) I noticed no real difference.

---

### Post by Terracotta on 2005-05-13
[QUOTE=poofyhairguy]Yet another reason (besides the fact that it offers no pratical speed increases) that people should use 32 bit mode....[/QUOTE]

Euhm, that's why I noticed that the 64bit version reacted faster than the 32 bit version? it also loads faster when logging in. There's an increase, but the 64 processor's are just that fast that the 32 bit version is speedy as well, though a bit slower. :-P

---

### Post by Crad on 2005-05-13
[QUOTE=poofyhairguy]Yet another reason (besides the fact that it offers no pratical speed increases) that people should use 32 bit mode....[/QUOTE]
 Doesn't it make sense for 64 bit users to actively use the 64 bit version so that problems get ironed out before 64 bit systems become mainstream?  The price of an Athlon 64 and Mobo are getting to the point that it's directly competing with Intel 32 bit processors, yet provide a wider memory bus and thus faster processing.  Seems silly to push people to not running the amd64 base when there are easy fixes to the common problems.

My only problem right now is running 32 bit apps in a chroot is more difficult because you have to manually edit the menu to get them to work.  I am thinking on how to make that process easier.

---

### Post by monchichi on 2005-05-14
hmm,

i find i get **much** better performance with 64 for really cpu-intensive tasks. i've never seen programs compile so fast. wanna race? compile ardour-cvs and time it, and we'll compare notes.  O:) 

and to stay on topic and not turn this into a pissing contest:

when i need to view a flash page, i just use a 32-bit opera binary. works perfectly (after a tiny bit of library tweaking). other than flash and a couple of codecs, what are you missing?

who's afraid of the big bad bleeding edge?

---

