---
title: "[SOLVED] Will Line Rider 2 Run under Wine?"
date: 2008-10-18
forum: Wine
---

### Post by Hyper Tails on 2008-10-18
Hi i Run Ubuntu 8.04 hardy heron (soon be 8.10 interpid ibex when released)

and I love line rider and i use to play it on the internet on [www.linerider.com](www.linerider.com) and when i heard about Line Rider 2 came out i was exicted

So before i buy the game i want to know.
will it run under wine?

please reply thank you.

---

### Post by Hyper Tails on 2008-10-19
........................................................................

---

### Post by Hyper Tails on 2008-10-19
nobody knows?

---

### Post by Hyper Tails on 2008-10-19
anybody??

---

### Post by Tim0miT on 2008-10-20
if its a .exe it might do, if its in a web window then it deff will as it is not OS dependant...:guitar:

---

### Post by StealThisAlias on 2008-10-20
I'm working on getting it running under Wine or Cedega, I'll post back with results later tonight :)

---

### Post by Hyper Tails on 2008-10-20
Okay sounds good I can't wait for the results :D

---

### Post by StealThisAlias on 2008-10-20
To be honest mate I wouldn't hold your breath, I ain't a Ubuntu Guru! Not having much luck yet, but I'm actively trying, I simply refuse to boot into my XP drive purely for this damn game! :)

So far... Wine: Gets the "opening" thing, but crashes out without any errors... Cedega does nothing at all.. I wonder if it has any dependencies such as Flash player or something..

Bit of an update for you, I haven't had any luck tonight... Between trying to install .NET 2.0 and messing on DeviantART, I've decided that the best thing to try is (sadly) sticking XP onto VirtualBox and see if that will run it, which I shall try tomorrow night once I find an XP disk that actually works >.<

---

### Post by Hyper Tails on 2008-10-21
so your saying that Line rider 2 unbound will not work in wine?

---

### Post by StealThisAlias on 2008-10-21
Good news for you mate - got it working!

Dead simple... The shortcut created when you install Line Rider 2 points to LR2Loader.exe. By changing this to point directly to LineRider2.exe, you can get it working! It seems to run a bit slower than it does on my Windows partition, but with better hardware it may well work a lot faster.

I'll try it out in Cedega too next!

EDIT

Update... Reason why LR2Loader.exe won't work is because its some kind of stupid splash screen, of what form I don't know, but I do know that Wine is not capable of displaying it properly.

---

### Post by Hyper Tails on 2008-10-21
okay good thanks I'l tell my mom and dad the news.

thanks so much mate ;)

---

### Post by StealThisAlias on 2008-10-21
You're welcome ^^ Working on speeding it up now, even on my home PC it still lags when he sets off riding....

---

