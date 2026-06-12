---
title: "New Wine is slow"
date: 2008-02-21
forum: Wine
---

### Post by UK-Wobbie on 2008-02-21
I had Wine 0.9.46 installed and ever game was working OK,
But i got some new games what did not work in 0.9.46, So i installed the new ones in 0.9.55 to see if the games will work and some of them did work, Working nice.
But then when i coming to play on some of my old games! Some of them are slow playing :(

So what do you say is best? Wine 0.9.46 or Wine 0.9.55
I like to know why that some games work in the old Wine and some games work in the new Wine? But all the games are not the same :confused:

---

### Post by nille on 2008-02-21
Recently Phoronix (great place, btw!) published a benchmark of 11 different versions of Wine and, as you can tell from the article, there's a "huge" loss in performance between 0.9.48 and 0.9.49 in some of the tests. But keep in mind that this is probably caused by new features and additional support for something, rather than a sudden increase of crappy code ;)
[http://www.phoronix.com/vr.php?view=11861](http://www.phoronix.com/vr.php?view=11861)

---

### Post by UK-Wobbie on 2008-02-21
> **nille said:**
> Recently Phoronix (great place, btw!) published a benchmark of 11 different versions of Wine and, as you can tell from the article, there's a "huge" loss in performance between 0.9.48 and 0.9.49 in some of the tests. But keep in mind that this is probably caused by new features and additional support for something, rather than a sudden increase of crappy code ;)
[http://www.phoronix.com/vr.php?view=11861](http://www.phoronix.com/vr.php?view=11861)

What is the best Wine version then what do you say?

---

### Post by EXCiD3 on 2008-02-21
thats interesting...i took a look at those benchmarks and there is a dramatic difference between 0.9.48 and 0.9.49. 

UK-Wobbie, you may want to try out 0.9.48 to get the best performance with the most features. I would recommend using the latest version however it looks like everything version 0.9.49+ are going to give you these lower framerates.

---

### Post by shad0w_walker on 2008-02-21
There is no 'best' version of wine, the best is whatever happens to work for you the best. It's a program still under incredibly heavy development. If you have problems with the new version go back to the older version.

---

### Post by UK-Wobbie on 2008-02-21
> **shad0w_walker said:**
> There is no 'best' version of wine, the best is whatever happens to work for you the best. It's a program still under incredibly heavy development. If you have problems with the new version go back to the older version.

The thing what i do not get is!
Old games work in the old Wine versions and some of the new games work in the new Wine versions, So why not work on the old version with the same features and then add the new features in that version? Or is that what they are doing :confused:

Is it something to do with Direct X?
As i seen the New Wine as got Direct X 9 in it, Is that right?

I better of going down some versions lol like what you all are saying :) 
Thanks

---

### Post by nille on 2008-02-21
I shall put it like this: if it works good for you, and you don't feel like you lack some features, you should stick with an older version.

If you need some feature only supported by a newer version you should use that one (or perhaps re-evaluate the need for that software).

What I'm trying to say is: there is no "best" version of Wine, only different versions with different features and properties. Some work great for certain applications, and some work better for other.

I think 0.9.46 is a pretty good (that is: stable and fast) release, but I'm not sure. As I said: pick the one that works best for you!

---

### Post by Ferrat on 2008-02-21
The reason 0.9.48 has better marks than 0.9.49+ is simple. 
The code for much of the DirectX stuff had a big make over, a lot of functions that didn't work before is now supported, so the results from before 0.9.49 isn't really real since they "cheat" by not doing everything they should and skipping much. 

As for preformance in games, true you might get better FPS if the game uses some of the stuff added in 0.9.49 but then you actually get something you didn't before and if it doesn't you really shouldn't see that much difference :)

As for best version... 
Well over all it's generally the last release but after that it depends alot on the app/game since some games don't use some stuff and might actually benefit from wine just ignoring some code while others just plain don't work with that same version because it needs it and so on.

---

### Post by UK-Wobbie on 2008-02-21
> **Ferrat said:**
> The reason 0.9.48 has better marks than 0.9.49+ is simple. 
The code for much of the DirectX stuff had a big make over, a lot of functions that didn't work before is now supported, so the results from before 0.9.49 isn't really real since they "cheat" by not doing everything they should and skipping much. 

As for preformance in games, true you might get better FPS if the game uses some of the stuff added in 0.9.49 but then you actually get something you didn't before and if it doesn't you really shouldn't see that much difference :)

As for best version... 
Well over all it's generally the last release but after that it depends alot on the app/game since some games don't use some stuff and might actually benefit from wine just ignoring some code while others just plain don't work with that same version because it needs it and so on.

I see lol 
Thanks for telling me all this :)

---

