---
title: "Slow, Choppy Gameplay In Steam Games"
date: 2008-05-04
forum: Wine
---

### Post by Patriot1776 on 2008-05-04
I managed to fix my sound problem, but now I have a bigger problem.  Using Wine 0.9.59 and 0.9.60, graphics are very choppy, almost slide-show like when playing Steam games.  The only non-Steam game I have installed is Dawn of War: Dark Crusade and it still runs fine even after upgrading to Hardy.  Have switched back to wine 0.9.59.

Graphics card is an nVidia GeForce 7300 with 256 MB of video memory.  Processor is a Pentium D @ 3.4 GHz, system memory is 2 GB.  Just upgraded to Hardy Heron about a week or so ago.  Tried running Steam with with -directx81 trick I think,still nothing, graphics are still choppy.  Only way I get decent framerates are by running in 640x480, smallest size available.

---

### Post by Trance56k on 2008-05-04
I have the same problem but with TF2. My specs are AMDx2 2.8GHZ,
2GB ram, 8600GT.

---

### Post by Patriot1776 on 2008-05-04
Main game I've been trying to play so far is Portal.

---

### Post by smrdelj on 2008-05-04
Hello. Excuse me for asking something out of topic, but I have problems running Steam and Cs 1.6 and perhaps yo have already dealed with something similar and solved it.
Steam doesn't allow me to install Cs. Did you come with something like that?

Thanks, here's my thread just in case you know anything: [http://ubuntuforums.org/showthread.php?t=777484](http://ubuntuforums.org/showthread.php?t=777484)

Bye

---

### Post by Patriot1776 on 2008-05-05
No, not really.  I've given up on Wine for running the Steam games.  I've still got a Windows partition so I freed up some space on it and installed all the Steam games from The Orange Box onto the Windows partition to ensure they work right rather than keep struggling with Wine.

I know, sounds like I quit too early and I'm a wimp because of it, but I was getting tired of waiting to see if the $50 I spent on The Orange Box was really worth it.

---

### Post by Trance56k on 2008-05-05
No I did not get that problem as well. I could get TF2 to install but it ran with poor FPS.

---

### Post by Melcar on 2008-05-05
People have been reporting very poor performance with Source games.  Basically, if you have anything lower than a 88xx or HD29xx card you're screwed.  Wine may not be an emulator, but it still has a rather big resource overhead.  I just use it to run non accelerated programs and my old 2D games.  I don't even bother trying to run 3D games anymore due to poor performance and graphical glitches.

---

### Post by Patriot1776 on 2008-05-05
I wonder then why Dawn of War: Dark Crusade runs so well.  You can zoom in awfully darn close to the individual soldiers and units with it and not really worry about slowdowns while running it in Wine, even after upgrading to Hardy.  You got any idea why?

EDIT - If the Source games were running bad, it's probably a good thing then that I couldn't get Silent Hunter 4 to run in Wine either.  Wide open spaces with it with models floating round, I probably would have been slide show city no matter what I did if I got it to run in Wine.

---

### Post by Melcar on 2008-05-05
> **Patriot1776 said:**
> I wonder then why Dawn of War: Dark Crusade runs so well.  You can zoom in awfully darn close to the individual soldiers and units with it and not really worry about slowdowns while running it in Wine, even after upgrading to Hardy.  You got any idea why?

EDIT - If the Source games were running bad, it's probably a good thing then that I couldn't get Silent Hunter 4 to run in Wine either.  Wide open spaces with it with models floating round, I probably would have been slide show city no matter what I did if I got it to run in Wine.


It depends on the game.  Games that have really good opengl hooks run really well.

---

### Post by Trance56k on 2008-05-05
I agree it does depend on the game. When I play WoW on Linux I can not tell difference between me running it on Windows or running it Wine.

---

### Post by DeSombra on 2008-05-10
I too had the same problem!  Made me crazy because I luv TF2 and now Hardy broke it!  I removed, I reinstalled, I wiped, I reloaded, etc. and so forth.  I was this close to waving a white flag and create a windows partition when Alas!  Thank to the great Google Gods I found the answer.  Twas not Hardy which broke my game.  Twas not Steam.  Nay, it was WINE!  The latest update of Wine rendered TF2 unplayable with horrible frame rates (and whats so sad, I STILL tried playing it, who's an addict?) Hardy was release with version .58 or .59...get rid of it!  Find and install version 0.9.46.  Now my TF2 is flying once more!  Why does the new version not work with TF2?  Don't know.  It might be something simple.  It might be something complicated.  Until I find the answer, .46 is the version to have.  In the meanwhile Hardy tells me everyday, hey, there's a new version we'd like you to have.  And I say "Hardy wants me to update (wine) and I say no, no, nooo...

---

### Post by Patriot1776 on 2008-05-10
Tell me what you had to do to backport, PLEASE.  Take me STEP BY STEP through it!

---

