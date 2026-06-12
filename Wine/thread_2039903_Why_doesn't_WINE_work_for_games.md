---
title: "Why doesn't WINE work for games?"
date: 2012-08-09
forum: Wine
---

### Post by michelebachmann on 2012-08-09
I hear the reason why some people don't convert to linux is because they can't install big games like The Sims. Why doesn't Wine work for them?

---

### Post by johnathansmith on 2012-08-09
Some games works under the WINE.

Checkout this site: [http://appdb.winehq.org/](http://appdb.winehq.org/).

Reason why games don't work under ubuntu, is missing libraries.

---

### Post by linktopower on 2012-08-09
The reason that Wine is not perfect, and it has its faults. sometimes things will run sometime they won't. so thats why most people want to stay with their windows for compatibly sake. 
Heck I'm stil using Windows, My Linux Hard drive is used for mainly learning Linux.

---

### Post by michelebachmann on 2012-08-09
> **linktopower said:**
> The reason that Wine is not perfect, and it has its faults. sometimes things will run sometime they won't. so thats why most people want to stay with their windows for compatibly sake. 
Heck I'm stil using Windows, My Linux Hard drive is used for mainly learning Linux.

Since WINE is so important, is it the most worked on by developers out of all the apps?

---

### Post by linktopower on 2012-08-09
> **michelebachmann said:**
> Since WINE is so important, is it the most worked on by developers out of all the apps?

I don't have for an answer for that I really, I'm still new to the whole Linux screen.

---

### Post by whatthefunk on 2012-08-09
> **michelebachmann said:**
> Since WINE is so important, is it the most worked on by developers out of all the apps?

Wine really isnt that important.  Personally, I use native Linux apps for everything.  I only run games in Wine, which I could live without.  People who really need to run Windows specific programs usually dual boot.

---

### Post by johnathansmith on 2012-08-09
> **whatthefunk said:**
> Wine really isnt that important.  Personally, I use native Linux apps for everything.  I only run games in Wine, which I could live without.  People who really need to run Windows specific programs usually dual boot.

That is true. Best way to deal with lack of programs on Linux that can't be replaced.

---

### Post by Mopar1973Man on 2012-08-09
Like I just managed to fire up Guild Wars on Ubuntu and WINE without any problems. But that's one of they many that may or may not function with WINE.

---

### Post by vexorian on 2012-08-09
I have been using this thing for years, and the only win apps I ran under ubuntu with WINE were games. 

Overtime I played games like warcraft III, freedom force, gta san andreas and Starcraft 2 in it. Each game is a whole story, and workarounds might be needed. But my success rate with WINE is not bad at all. 

Casually the sims is one of the games that seem to have issues with WINE. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=8696](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8696)

But most of the time, WINE support is less of an issue than video card drivers support. Before daring to run a heavy weight game in WINE, you really need to make sure your video card drivers are good.

There is a lot of development in WINE. One issue is that microsoft has never released any documention about how to implement their APIs (probably because they don't want that to ever happen). Some games and apps might rely (maybe accidentally) on very specific implementation details of the APIs that can't be discovered until someone runs the game with WINE.  And of course, we can't expect WINE developers to buy and test each game in existence, so they have to rely on us to report bugs...

Incidentally, the other day I had to use MatLab and it also ran fine on WINE.

To be honest, knowing really how it works (That they basically had to reverse engineer windows' guts) I am just impressed that WINE can run at least *some* games and apps.

> That is true. Best way to deal with lack of programs on Linux that can't be replaced. When the program isn't heavy on graphics or RAM, then it is more practical to use virtualBox to run these apps that can't be replaced and don't run fine in WINE.

Edit: My recommendation is to use appdb.winehq.org, and try the games and apps that are either in the Platinum or Gold lists. For example, just found out that although "The sims" has plenty of issues, ["The sims 3" is actually platinum](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664). When an app is in the platinum list, it should run quite well in your machine provided you have the video card drivers... Winehq also includes instructions to tweak your wine configuration and work around possible bugs with the app.

---

### Post by Toz on 2012-08-09
Moved to Wine forum.

---

### Post by Mark Phelps on 2012-08-10
> **michelebachmann said:**
> Since WINE is so important, is it the most worked on by developers out of all the apps?

Wine is not developed by Canonical; instead, it is developed by CodeWeavers -- who are always working on improving it.

As to "so important" -- that is a very subjective opinion.  I used it for a while, found it would not run current MS Windows apps, and quit using it.

---

