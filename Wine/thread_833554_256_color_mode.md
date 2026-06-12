---
title: "256 color mode?"
date: 2008-06-18
forum: Wine
---

### Post by Super TWiT on 2008-06-18
There is an application that I want to run in wine, however it requires 256 colors. I have tried the guide [here]("http://wiki.winehq.org/256ColorsWorkarounds"), but it doesn't seem to work. Is there any way I can run this application in 256 colors?

---

### Post by cogadh on 2008-06-19
Some 256 color apps just won't work, even if you try the workarounds they have on that page. You might try adding 8BPP color support to your xorg.conf, but I've never really had that work for me before (could have been the app I was running, though).

What application are you trying to run?

---

### Post by Super TWiT on 2008-06-19
It was an old Scrabble game I had around.  I never really got to try it out because I never even got any of the workarounds to go that far.  One started to, but I was running as root, and running an X session as root gave me a security warning which talked me out of that option.

---

