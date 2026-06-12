---
title: "How long does your wine stand?"
date: 2008-05-07
forum: Wine
---

### Post by jreis on 2008-05-07
Hello all Ubunturs:

This is my problem:

I'm preparing a low budget, fast delivery and snap/easy development platform to stand at the least 6 months with out rebooting. So i was thinking on Ubuntu+Wine+<myflashapp>.exe solution.

So my question is how much time does your Ubuntu+Wine+<app>.exe stand with out crashing or with out you getting bored and quit.

Does anyone already tried something like this?

ps - I'm also going to assemble a machine with this specs and put it at test. But it would be good to know the limits!
ps2 - And will put the results of the tests also! :popcorn:

---

### Post by cogadh on 2008-05-07
When you say "myflashapp.exe" do you mean that you intend to develop the app using Flash? If so, Wine isn't necessary, Flash works natively in Linux. If you are not developing in Flash, I would ask, why are you trying to develop a Windows executable with the intention of running it in Linux through Wine? Why not skip a step (and a load of hassle) and just develop a Linux native app?

---

### Post by jreis on 2008-05-07
I know that flash is natively supported in linux, but all solutions that i have tried are not satisfatory:

*gnash: the *.swf work well, but it it is too slow
*swfdec: the *.swf could not access to local files (the path is relative to the player)
*adobe flash player 9 under Firefox 2: Also it is slow, but much better than with gnash. The alpha was not very well supported. After fully loaded, the animations are not fluid enough

The only one that worked satisfatory, in the primary teste was wine+myflashapp.exe. But does it keep on working, after 1 day and 6 months after?

---

### Post by cogadh on 2008-05-07
AFAIK, Wine will continue to work as long as your app is running. I've never left anything running for days in Wine, but I have run games for 6+ hours with no problems at all. Wine is just a compatibility layer, so its stability is totally dependent on the stability of your system and the application you are running with it. I would suggest you try it out in a test environment, just to confirm.

---

