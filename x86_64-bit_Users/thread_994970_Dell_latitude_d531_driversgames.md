---
title: "Dell latitude d531 drivers/games"
date: 2008-11-27
forum: x86 64-bit Users
---

### Post by epic93 on 2008-11-27
Hi I am installing ubuntu 8.10 64 bit on a dell latitude d531 .

It has a radeon x1270 which ati doesnt seem to host the drivers for, and it has a conexant type 2 modem. 

I was also wondering if there are any games out there for 64 bit linux.

---

### Post by cariboo on 2008-11-27
Not sure about the video drivers, but to see if your mode is supported, in a Applications-->Accessories-->Terminal type:

```
sudo wvdial
```

This will check to see if your modem is available.

As for games check Applications-->Add/Remove Programs-->Games.

Jim

---

### Post by Stunts on 2008-11-29
I also don't know about your graphics card support, but there must be a list somewhere. But if you can get compiz-fusion working on your instalation you _probably_ can get games working decently.
As for game availability, you also have some commercial titles available for linux (64 and 32). You can find a relatively complete list (both commercial and oss) in the 'Ubunu gamers arena' link in the main forum page.
Don't forget that you can also run many windows games on Ubuntu under wine. You can check on [http://winehq.com](http://winehq.com) under the AppDb for a compatibility list. Even recent games such as Fallout3 can be made run under wine (in this case with some caveats, but also some benefits relatively to the windows).
Good luck!

---

### Post by baryah on 2009-05-25
Ubuntu 8.10 works great on D531 but for one thing. the fglrx drivers provided from Ubuntu repositories are OK, but with compiz on video, Google earth, second life etc flickers. these work fine when desktop effects are turned off. With the 9.2 and 9.3 versions of the drivers downloaded from the ati website, the problem of flickering goes BUT another one creeps into. The screen is skewed. almost 6-7 cm of the right end of the screen is displayed on the left. But taking a screenshot of the desktop returns a correct (unskewed) desktop. The mouse pointer works as if there is no skew, i.e. it points to a point which corresponds to the point if there was no skew...hope you got it ... dont know   how to get my screen ok....

---

