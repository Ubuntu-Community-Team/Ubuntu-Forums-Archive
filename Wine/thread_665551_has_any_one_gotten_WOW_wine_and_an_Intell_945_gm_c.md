---
title: "has any one gotten WOW wine and an Intell 945 gm card to work?"
date: 2008-01-12
forum: Wine
---

### Post by -gabe-noob- on 2008-01-12
Hey guys, i've downloaded WoW thru wine once before but it didn't work quite nicely but that was a while ago so i'm wondering with the new versions of Wine that have come, has any one gotten WoW to run in Opengl with an Intell 945 graphics chip? (I can play Alien arena and Nexuiz and I assume those are opengl so why dosen't wow work?

---

### Post by mikekchar on 2008-02-26
Yes, I have.  But it's not all good news.

First, I upgraded to Hardy (which I don't actually advise doing just yet).  Then I upgraded to wine 0.9.56 (since 0.9.55 is borked in Hardy -- good reason not to upgrade :) ).  Then I switched to the intel driver in the xorg.conf file and then it works.  

Except some of the texture maps are wrong (which I think could probably be fixed by tweaking the xorg.conf file).  And I'm only getting 15-20 fps in Darnassus at 800x600 and *everything* turned off.

You can get the game to run using the normal driver on Gutsy using d3d.  In fact it works perfectly.  But you only get 10-15 fps...

So if anyone knows how to get this game working (in any way) at greater than 25 fps *please* respond!!!

---

