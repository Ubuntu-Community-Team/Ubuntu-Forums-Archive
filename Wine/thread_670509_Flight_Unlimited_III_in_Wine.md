---
title: "Flight Unlimited III in Wine"
date: 2008-01-17
forum: Wine
---

### Post by wheelhorse2347 on 2008-01-17
Hello,

I need help with a program I'm trying to run in wine.  I just installed flight unlimited III in wine, and it all seemed to work well...until I tried to open it.  I click to open it, i get the pinwheel and then nothing happens.  No error message or anything.  Does anyone have any idea on what might be wrong?

---

### Post by sickpuppet on 2008-03-27
Hi Wheelhorse2347 - 

Getting a program installed under Wine is a very different kettle of fish from getting it to run - especially old games designed for DOS or Win95/98.

I suggest running the game from a command prompt - that way you'll get to see any error messages Wine is producing. Try this:

$ wine /path/to/flight/unlimited.EXE

I had a look in the Wine AppDB for any references to "Flight Unlimited" - There are no results at all for the search "[Flight Unlimited]("http://appdb.winehq.org/search_results.php?cx=013271970634691685804%3Abc-56dvxydi&cof=FORID%3A11&q=%22flight+unlimited%22&sa=Search#203")"

Take a look at the WineHQ website ([http://www.winehq.com](http://www.winehq.com)) to see what they have to say about running old Windows games in Wine. (I haven't researched this yet.)

I suggest you try the free download of VMWare Server, and assuming you have a legitimate copy of Windows 95 or Windows 98, you could try installing Flight Unlimited III on that. I guess you'd need a pretty beefy box though, to get decent gameplay.

I found your post because I I'm thinking of installing Flight Unlimited (Version 1) on my Ubuntu setup and was looking for other people's experiences with running it under Wine or VMWare.

I'll let you know how I get on!

Regards
Ben

---

### Post by anthonyJC on 2008-04-11
Just browsing and thought I might chip in, since I've got version 2. Just tried it and version two seems to have the same problem. You run it from command line and the installer exists without any error codes or any response. You get the splash screen and then it ends after first file copy. (Flight Unlimited II) <- put that there for the search engine.

---

### Post by sickpuppet on 2008-04-11
Hi anthonyJC - thanks for pitching in! It's good to see that there are a few folks out there still playing this classic sim series.

First the good news: I've tried Flight Unlimited I on dosemu - it doesn't work. I've tried it on dosbox, and it works a treat!

The bad news is that I haven't tried Flight Unlimited II or III yet. I own both, so I'll try them over the next few days and keep you posted on progress.

regards
Ben

---

