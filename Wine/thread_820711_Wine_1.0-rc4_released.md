---
title: "Wine 1.0-rc4 released"
date: 2008-06-06
forum: Wine
---

### Post by cogadh on 2008-06-06
With only 11 bugs remaining for the final 1.0 release!
[http://www.winehq.org/?announce=latest](http://www.winehq.org/?announce=latest)
[http://bugs.winehq.org/buglist.cgi?bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&product=Wine&target_milestone=1.0.0&order=bugs.bug_severity](http://bugs.winehq.org/buglist.cgi?bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&product=Wine&target_milestone=1.0.0&order=bugs.bug_severity)

---

### Post by 4th guy on 2008-06-06
*jig*

---

### Post by Sleaka J on 2008-06-06
Yeah, only 11 bugs because they've deferred at least one that I know of to 1.2.0.

Defer bugs and make it look like you've got bigger progress than you really have.

---

### Post by happyhamster on 2008-06-07
> **Sleaka J said:**
> Yeah, only 11 bugs because they've deferred at least one that I know of to 1.2.0.

Defer bugs and make it look like you've got bigger progress than you really have.
Err, no. Wine's progress is too fast for testers to keep pace as it is. Deferring bugs is just being kind :).... Or perhaps it's just a rational decision to delay some bugs from being addressed, because wine 1.0 is going to be released some time soon, and solving those bugs will take too much time, or pose too great a risk of regressions, etc. 

Seems pretty reasonable to me, but I also know that, regrettably, anything kind or reasonable will be treated with mistrust and cynicism by some people nonetheless.

It's easiest to assume the worst I guess.

---

### Post by OpposingForce on 2008-06-07
Is it just me or is steam still having incorrect cursor position?  I just upgraded this morning and restarted GNOME, wine says in the about tab that its rc4.

---

### Post by heatblazer on 2008-06-07
The RC is great. There are, indeed, a lot of fixes :) Great job!

---

### Post by sdowney717 on 2008-06-07
I will be impressed when it runs Coastal Explorer with the menus showing.
[http://rosepointnav.com/CoastalExplorer/Trial/default.htm](http://rosepointnav.com/CoastalExplorer/Trial/default.htm)

---

### Post by Methuselah on 2008-06-08
I find it hard to complain about anything the wine team does.
It is an absolutely amazing volunteer effort.

---

### Post by Sleaka J on 2008-06-08
Found a second bug they deferred to 1.2.0.

Battle.net hosting for Warcraft 3 players.
[http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787)

Steam friends was the first one I knew of that they deferred.
[http://bugs.winehq.org/show_bug.cgi?id=9771](http://bugs.winehq.org/show_bug.cgi?id=9771)

---

### Post by cogadh on 2008-06-08
What's wrong with deferring a few bugs? Its not like we will have to wait 15 years for 1.2, like we had to wait for 1.0.

---

### Post by marine63 on 2008-06-08
starcraft battle.net still not fixed T_T

---

### Post by vexorian on 2008-06-08
They should really get at least all regressions fixed before retail 1.0, bugs are one thing but regressions are something quite lame to include in a release.

Anyway, regarding real bugs, well, there's nothing we can do or complaint about, 1.0 is meant for those useless apps like Office or photoshop, it won't care about our games :(

---

### Post by Sleaka J on 2008-06-09
> **cogadh said:**
> What's wrong with deferring a few bugs? Its not like we will have to wait 15 years for 1.2, like we had to wait for 1.0.

Because you don't win over users by openly advertising "We only have these bugs to fix by 1.0.0" on your website and then deferring them, instead of trying to fix them.

"Oh well, that's going to take too long. Better put it off."

They're obviously more interested in getting 1.0.0 out and I expect that kind of behaviour from a bad commercial developer (EA for example, look at Kane's Wrath).

Frankly, I wouldn't care if they got to 1.0rc999, just as long as they fixed what they said they were going to fix by 1.0.0

---

### Post by MemoryDump on 2008-06-09
I'd be happy if they'd end up supporting pulse.. but it seems they have their mind set on other stuff right now... stupid bugs.. :(

---

### Post by YokoZar on 2008-06-09
> **vexorian said:**
> They should really get at least all regressions fixed before retail 1.0, bugs are one thing but regressions are something quite lame to include in a release.
Exactly.  The point of the release is to produce a version of Wine that's 100% regression free.  Every non-regression bug at this point is being deferred; otherwise, we'd never make a release, since every single app that doesn't work perfectly is a bug of some sort.

> Anyway, regarding real bugs, well, there's nothing we can do or complaint about, 1.0 is meant for those useless apps like Office or photoshop, it won't care about our games :(This isn't quite true.  The four applications targeted for 1.0 (Photoshop and the Office 2003 viewer programs) weren't games, but *many* games have worked in the past and 1.0 won't release until every gaming regression found is fixed.  So, implicitly, any game that worked before is effectively a targeted application since 1.0 won't come out otherwise.

---

### Post by vexorian on 2008-06-09
I recognize many games will work in 1.0 if the problems affecting them are a regression, just saying that unlike Photoshop bugs, game bugs won't be considered show stoppers unless they are a regression.

---

### Post by YokoZar on 2008-06-09
> **vexorian said:**
> I recognize many games will work in 1.0 if the problems affecting them are a regression, just saying that unlike Photoshop bugs, game bugs won't be considered show stoppers unless they are a regression.
Right.  But, to be fair, there really weren't any showstopper bugs other than regressions going into this release anyway - Photoshop CS2 and the office apps were pretty much working a couple of months ago.

Now, it is reasonable to complain that a lot of the Wine developers were paying more attention to Photoshop and the Office apps than popular games, but keep in mind that every single paid Wine developer works for Codeweavers, and as of yet Crossover Games is only a small portion of their business compared to office apps.

---

### Post by RaleTheBlade on 2008-06-09
Well whatever the case, its an awesome effort regardless. I cant wait to see what Wine can do in the future! The road is wide open :)

As for right now, Wine plays Roller Coaster Tycoon 2 and Age of Empires fine, and thats enough for me, haha.

---

### Post by M4rotku on 2008-06-09
I am extremely confused (per usual).  Will wine upgrade itself or do we have to download the newest version and reinstall all of our games.  I just got my games installed and I don't want to go through that painful process again.  If that is the case, then I just won't upgrade.

Is there a way to upgrade without reinstalling everything?

---

### Post by cogadh on 2008-06-09
You can upgrade Wine without having to reinstall everything. If you want the latest version, you need to either download the source code and compile it yourself, or use the [WineHQ repository](http://www.winehq.org/site/download-deb) to get a precompiled package. Once you have installed the new version, just run "wineboot -u" in a terminal to update your existing Wine directory with any changes from the new version then continue to use it as you always have.

---

