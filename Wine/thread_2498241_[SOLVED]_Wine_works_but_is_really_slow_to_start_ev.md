---
title: "[SOLVED] Wine works but is really slow to start even on SSD(?)"
date: 2024-06-05
forum: Wine
---

### Post by 909mjolnir on 2024-06-05
I have a computer that's about a year old and I got Linux on it finally and Wine is on it too.  
Is Wine really this slow lately?  Over the years I've used Wine and it was never too slow.  
But lately, I'm almost about to give up right before each program loads.  Is this slowness normal?  

I have a high-speed SSD, so this seems surprising.  I'm using wine-staging.  

What can you tell me?

UPDATE:  Upgrading my RAM seemed to fix the probem.   SOLVED,

---

### Post by nicolasdentremont on 2024-06-05
I haven't noticed any slowness here. I've been using Wine Stable and Development.

---

### Post by 909mjolnir on 2024-06-06
Yeah, you wouldn't have noticed slowness on your own computer.  Each computer is like it's own fingerprint or snowflake.  No two are alike.  
But anyways, I found some info about this all of a sudden:  [https://www.reddit.com/r/linux_gaming/comments/mt8uh8/reducing_wine_startup_time/?rdt=57594](https://www.reddit.com/r/linux_gaming/comments/mt8uh8/reducing_wine_startup_time/?rdt=57594)

I remember this was a problem with Ubuntu Studio having hundreds to thousands of fonts instead of maybe 6 fonts.  
I gotta get in there and manually delete them.

---

### Post by 909mjolnir on 2024-06-08
OK, wine is still slow, but I found the "wineserver -p" command and added it to my Session startup list.  
Also, I set up a Session startup to run Appetizer or winecfg at startup.  After that, wine is a little faster.  
I can't tell which fonts are needed or not, so I can't delete them.  So I can't do that.  

But my system is at least running.  
I turned off some other extras (forgot what they were already).

---

### Post by Tadaen_Sylvermane on 2024-06-11
I run Battle.net via Bottles frontend for wine. It takes a fairly long time (relative to native programs) to load the Battle.net client and then whatever game. Once it's up though it runs perfectly, arguably better performance than Windows ever gave me. I haven't figured out why it takes so long to load initially. It does bug me but not a major problem.

---

### Post by 909mjolnir on 2024-07-08
Thanks Tadaen_Sylvermane.  
For the time being, I decided to try and find more Linux equivalents instead of pushing WINE.  
It's been working out better that way.  But I do like some Windows freeware classics.  The Linux freewares are good too.  

UPDATE:  I upgraded my RAM and that seemed to help too.

---

