---
title: "ATI+Wine=Games don't start"
date: 2007-12-18
forum: Wine
---

### Post by quadomatic on 2007-12-18
For some reason, none of the games I've tried with Catalyst 7.11 and WINE have been able to start. I've tried Half-Life 2: The Orange Box games and Max Payne 2. Both of them result in the game changing the screen resolution, and then not loading up ('cept in The Orange Box the VALVe Intro Video still plays).

Any ideas how to fix this?

---

### Post by aoanla on 2007-12-19
I had the same problem. Unfortunately, I only managed to fix it by getting an nVidia card...

(It appears that this is mostly ATI's fault, not Wine's.)

You, on the other hand, might get luckier. Things to try include:

Using winecfg, set hl2.exe to Windows 98 compatibility mode.

In Steam (this is just for Orange Box games), use the Properties button for each game to set the Launch options as:

-dxlevel 80 -heapsize XXXX

where XXXX is half your system ram in kilobytes - so, 524288 for 1/2 a Gig (if you have 1 Gig ram total).

Also, make sure you have the newest version of Wine - 0.9.51
If that doesn't work, consider downgrading to Wine 0.9.44 or so - there's a sweet spot around 0.9.43 to 0.9.45 (so try all three in sequence), where ATI cards seem to work better than with the newer versions of Wine. 
You'll get worse performance, but you may, at least, be able to play.

Also, remember that that current ATI drivers have a massive memory leak in them for last and current generation cards. This will cause your game to crash after about 20 minutes to an hour's play.

---

### Post by quadomatic on 2007-12-19
> **aoanla said:**
> 
Also, remember that that current ATI drivers have a massive memory leak in them for last and current generation cards. This will cause your game to crash after about 20 minutes to an hour's play.

Is this even in the latest drivers? I was able to play Enemy Territory Quake Wars demo for a while with high settings and no issues.

---

### Post by quadomatic on 2007-12-19
Huh...turns out you may be right about that memory leak.

I finally tried Enemy Territory Quake Wars under the drivers I recently updated to, and the game starts running like a slide show. Also, Doom 3 runs, but then the textures that load are very low quality, and the game goes pretty slow.

These were running natively btw.

I'm not sure what's up with all this.

---

### Post by aoanla on 2007-12-20
On the Phoronix forums, the memory leak (and the fact that it wasn't fixed for the latest driver) were the biggest topic of discussion for about two weeks around the Catalyst release, so yeah...

Have you had any luck with getting any of those tweaks to work with Steam?

---

