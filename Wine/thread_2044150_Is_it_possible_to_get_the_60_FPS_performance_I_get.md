---
title: "Is it possible to get the 60 FPS performance I get in Windows?"
date: 2012-08-18
forum: Wine
---

### Post by Koviko on 2012-08-18
I used to use a GeForce 560 Ti for World of Warcraft in Windows and got framerates of about 60 FPS when doing anything other than large-scale content (raiding and battlegrounds). When moving over to Ubuntu + Wine, I'd get framerates of about 20-25 in places that I used to get 60 (such as Stormwind). I upgraded to a GeForce 670 (2GB instead of the 560 1GB), loaded up WoW, and am still getting about the same performance, maybe slightly higher (more constantly 30, but never much higher in Stormwind).

Are there optimizations that I should be making? Is this a CPU problem (Intel i5 quad-core 3.1GHz)?

*Note that this performance is in OpenGL with the highest settings OpenGL allows (not particularly high). I also use a lot of addons, but Auctioneer is always profiled to be the most CPU intensive, even though all it does is add data to the tooltips.*

---

### Post by BuffaloX on 2012-08-21
If you are running Unity you may double your framerate by swtching to Unity 2D.

---

### Post by Tweak42 on 2012-08-24
I run Wow and I'm pretty sure the problem is dual core support as described here:

[http://bugs.winehq.org/show_bug.cgi?id=11674](http://bugs.winehq.org/show_bug.cgi?id=11674)

It's a real pain but I have managed to compile wine with the suggested rGL patch and it makes a huge performance difference.  It however is a hack and tends to break when a) Nvidia updates their driver, b) new wine version releases, c) blizzard releases an update.

I made a rough guide how to compile wine with the patch but it's a bit out of date.
[http://ubuntuforums.org/showpost.php?p=11677311&postcount=12](http://ubuntuforums.org/showpost.php?p=11677311&postcount=12)

Starting with 12.04 compling 32 bit wine on 64 bit Ubuntu became a mess and I haven't figure out a simple way to do it yet.

---

