---
title: "ATTN: 64 bit IVTV card owners."
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ShadowRage on 2006-08-28
I set up an apt repo for those of you, like me, have an ivtv based tv card with mpeg encoding. (hauppauge cards, etc) with the latest bleeding edge version of xawtv (CVS pull as of 2006 08 16) There *should* be dvb support, but I hear it's a bit buggy, I dont have a dvb card so I cant test it.

WARNING: This is unofficial, largely untested, may contain bugs, nuts, and may have been in the vicinity of peanuts. Also, it is not my fault if radioactive fluid pours out from your computer case, or it grows appendages and makes sweet love to your mother.

In other words, use at your own risk. However, I'm fine and I can watch TV.

What use is this? simple, each time you want to watch TV, you dont have to use hacks to watch it with mplayer, or VLC, or have to install mythtv.

It works great with my Hauppauge PVR-150.

This was also my first time building a dpkg, so bear with me.

The repository can be added in /etc/apt/sources.list as follows:

```

deb http://dev.acidchat.net/apt dapper main
deb-src http://dev.acidchat.net/apt dapper main

```


Enjoy.

---

