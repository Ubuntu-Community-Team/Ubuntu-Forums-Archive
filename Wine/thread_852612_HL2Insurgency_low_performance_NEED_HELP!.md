---
title: "HL2/Insurgency low performance NEED HELP!"
date: 2008-07-07
forum: Wine
---

### Post by v3t1t4s on 2008-07-07
Hey all

First of I'm a new ubuntu/linux user, loving it so far, except the games part =)  and thats why i'm here

So I've been trying to get insurgency(a source mod btw) up and running in Hardy, installed wine 1.1.0, steam, nvidia driver 173.14.05. and all is well, wine seems a little laggy, but i'm assuming thats just wine. In game is another story.  Intro is horribly laggy, takes 30 seconds to get through it.  Then the main menu is fine, then very low fps

In Windows i get 30+fps with these settings
1280x1024 x4 x4 hdr off colour correction off everything else high

Under Wine I get 10, maybe 15-20 if i lower any combination of those. Question is whY??

hardware is xp3500  500gb 7200.11  ecs rs482-m mobo  1gig ram and  8800gts 512 vid card, so even if wine is a bit slower, shouldn't be that much.  Others have had success with other hl2 mods such as css and dods.  So I've been reading forums all over for more then a day now, and nothing, no luck with anything I've come across, whether they solved their problem or not, I swear I've tried everything!! but i know i haven't :)
What I've tried so far

for ubuntu
tried different vid drivers
disabled compiz

wine
tried different os under wine
tried pixel shaders on/off in winecfg

added WINEDEBUG"-all" in my steam launcher ( env WINEPREFIX="/home/veritas/.wine" WINEDEBUG="-all" wine "C:\Program Files\Steam\Steam.exe" )

steam
changed insrugency launcher with -gl -directx 81 -heapsize 512000

in insurgency 
lowered res, models, texture, hdr, cc, filtering, aa

so, either I missed something, or I such a newb its something really obvious, I followed guides to install everything, tried to follow stuff with steam/wine/games orientation

Any suggestions would be great, whether obvious or technical.  I know there more out there with this problem, lets get a fix!

---

### Post by piousp on 2008-07-08
Maybe you are missing some dlls?

---

