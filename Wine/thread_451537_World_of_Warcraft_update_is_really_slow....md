---
title: "World of Warcraft update is really slow..."
date: 2007-05-22
forum: Wine
---

### Post by Pikestaff on 2007-05-22
So I finally gave in to the pressure and started playing World of Warcraft a few weeks ago... :p

I'm enjoying it so far, and running it in Wine is giving me absolutely no problems other than the sound (very) occasionally acting up.  Overall it runs very smoothly and it's as though I'm running it natively in Windows, which makes me quite happy.

Today, though, I'm trying to apply the newest updates and the download just seems to be horrendously slow.  Initially installing the game and all the updates for the very first time was slow too, but certainly not this slow.  I've been downloading for over an hour now and I've only managed to download about 31 of the 276 MB.  Furthermore, the downloader tells me "You appear to be behind a firewall", but I don't think I set up a firewall.

So my question is, is there something I can do to speed up the download, or a setting somewhere that will speed it up?  Or is this normal and something I'll have to get used to?  I'm new to WoW so I don't know, maybe the downloads are always this slow :p  I'm using Kubuntu Dapper, in case that matters.

---

### Post by Stormweaver on 2007-05-22
Are you behind a Router by chance?

---

### Post by Pikestaff on 2007-05-22
I am yeah, I get wireless internet through a router.

---

### Post by lordhebe on 2007-05-22
It's not a wine problem that's for sure. I have many friends who play wow on windows and their downloads are just as slow as mine. Anyways following this part of the guide may help: [https://help.ubuntu.com/community/WorldofWarcraft#head-ffdb6e1abf69e93f2ee1bad73a59c4fc17a295db]("https://help.ubuntu.com/community/WorldofWarcraft#head-ffdb6e1abf69e93f2ee1bad73a59c4fc17a295db")

(Scroll down a little and you should find it)

---

### Post by Stormweaver on 2007-05-22
You will need to set up Port Forwarding on the Router according to your Router's instructions for the following Ports.

3724

and 

6881 - 6999


These are the ports used by Blizz to get the updates to you both from Blizz Direct and the Shared User Resources.  Once forwarded, restart and the Download should come as fast as their are users to share it.

---

### Post by Pikestaff on 2007-05-22
Awesome, I'll check out the guide and try that thing with the router, thanks!

---

### Post by Sammi on 2007-05-22
> **Pikestaff said:**
> Furthermore, the downloader tells me "You appear to be behind a firewall", but I don't think I set up a firewall.
Some routers use a firewall by default while others don't. Most use [NAT]("http://en.wikipedia.org/wiki/Network_address_translation") though, which essentially produces very similar results.

Anyway just do what the others told you. The info in the community howto is also great (I did not write that part myself).

---

### Post by lakersforce on 2007-05-22
I have not firewall and use no router and my Blizzard update is extremely slow.

---

### Post by Sammi on 2007-05-22
> **lakersforce said:**
> I have not firewall and use no router and my Blizzard update is extremely slow.
Then what kind of connection do you have?

---

### Post by GiantRobot on 2007-05-22
In general I find that the WoW updater is very slow.  I don't have a router or use a firewall and it is still absolutely horrible.

It's not really a big deal as the updates aren't very large, usually no bigger than ~50mb, bar a few of the major ones.

---

### Post by Tellisk on 2007-05-22
I just use Mirror sites. They're listed in the support section of worldofwarcraft.com. 2.1 downloaded in about a half hour. (Blizzard downloader sucks for me as well, always has)

---

### Post by lakersforce on 2007-05-23
> **Sammi said:**
> Then what kind of connection do you have?

2mbit/512kbit. The provider always delivers the promised speeds (actually, most of the time it is faster).

---

### Post by Sammi on 2007-05-23
> **lakersforce said:**
> 2mbit/512kbit. The provider always delivers the promised speeds (actually, most of the time it is faster).
I asked what *kind *not *speed*...

If it's broadband then it's usually ADSL or cable. Personally I have ADSL, and I know nothing about cable.

---

### Post by ShadowFlar3 on 2007-05-27
I find Blizzard Downloader the worst thing on earth. It has no way of limiting speeds so on DSL connection it is usual to have the downloader use up all the uploading bandwidth which effectively blocks your download bandwidth almost entirely and on top of that you can't surf the web or do anything that requires an interenet connection.

Surely you could fix your firewall / router settings but I suggest using patch mirror sites for direct downloading:
[http://www.wowwiki.com/Patch_mirrors](http://www.wowwiki.com/Patch_mirrors)

---

### Post by cryogenics on 2009-01-25
I configured my router to let my ip from the ip info to be the DMZ and it's still way waaaay slow.. I have a 10 meg connection and i get 28k-63k but consistant 38k download speed with a 64k upload. on a 465 meg download...
 at this rate the first update will take me (3-4-5) hours give or take

Another thing i noticed right out of the box was =
This . Installed through cadega that went to crap
Installed through wine 1.1.13 and got sound and everything so far except one minor weird thing.... If you try and run the game from scratch while running a higher then a 1024x768 your gonna get wacky errors and crashing
if you for the game to quit aka right click kill/close it and double click and don't change the Rez then bang it works updater everything so far ,but who knows I haven't gotten past the update yet LOL.

Yes the torrent thing is slow the more people that are on it the faster it
gets :) the more it moves along the faster it will get. after typing this i'm now at 2-3 hours or less.
:popcorn:
Ubuntu 8.10 Ibex / All updates applied etc..
;)

hrmm it's been a hour or 2 and I'm still at 2 hours WTF.

rainmanp7 ...................

This is almost like one of those days when
You would download from a 12.2? 14.4-28k-56k DialUp Modem!
............................................

---

