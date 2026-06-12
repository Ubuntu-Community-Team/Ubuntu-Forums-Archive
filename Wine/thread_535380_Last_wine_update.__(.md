---
title: "Last wine update.  :("
date: 2007-08-26
forum: Wine
---

### Post by Kaldir on 2007-08-26
I just did the wine update, and when I went to play WoW the sound was all messed up, so I went to quit WoW, and then wow froze.  So I got out of it changed the sound under winecfg and the sound works fine now, but still when I quit wow frezzes up, but the music still plays, any suggestions?

---

### Post by Drezliok on 2007-08-26
My sounds was fine but it's freezing on me too.

---

### Post by Mogurijin on 2007-08-26
Well, I remember other people reporting problems with WoW (I don't remember what problems exactly though) and I had problems with Fable. So I would recommend uninstalling WINE, going to [winehq]("http://www.winehq.com"), and downloading .9.43. Then, if your using the winehq repository, go to sofware sources and uncheck the winehq ones for now so you don't get a bunch of update me messages :D.

---

### Post by cogadh on 2007-08-26
Rather than removing the Wine repositories, just open Synaptic, search for Wine, click on Package > Force Version..., then pick the currently installed version. That way you won't get prompted to update, but if you want to, you still can.

---

### Post by Nehvrook on 2007-08-26
Yeah. I had a wierd login problem that was fixed by updating the WTF folder. But I'm still crashing when I try to quit. It's not so bad though you can just alt-tab and kill the console running WoW. Not the ideal way but better than nothing untill the next update fixes it.

---

### Post by marcw on 2007-08-26
I believe the crashing or freezing when quitting is a result of the latest release - 0.9.44.  I already filed bug 9479 at winehq.org.  The immediate remedy is to use a prior version.  I'm sticking with 0.9.43 for now.

---

### Post by chuckyp on 2007-08-26
What I don't understand is if the old version of wine was working why did you bother updating?

If it aint broke don't fix it.

---

### Post by hikaricore on 2007-08-26
> **chuckyp said:**
> What I don't understand is if the old version of wine was working why did you bother updating?

If it aint broke don't fix it.

Not everyone uses WINE just to play WoW.
Updates in WINE have bug fixes that affect many programs for the better.

A WoW regression is no reason to say people shouldn't update their version of WINE.

---

### Post by cogadh on 2007-08-26
Not to mention, nearly all of the updates to Wine relate directly to DirectX, sound and general gaming performance. I have found with each successive update since 0.9.35 that games I already use through Wine run better and with each update, more games start working.

---

### Post by marcw on 2007-08-26
> **chuckyp said:**
> What I don't understand is if the old version of wine was working why did you bother updating?
If it aint broke don't fix it.

I'm sure we're all pleased to learn that you are one of those that are philosophically opposed to updating except in the most dire of circumstances.  Most of us aren't.  When we see our update-notifier flashing away we assume that there is a good reason for updating: security, patches, etc.  Then there are those of us who experiment.  We like to be on the cutting edge knowing full well what we are getting ourselves into.  And then there are those of us who are helping with development - if people didn't report bugs there wouldn't be much progress, would there?

In my case, I use several programs that depend on Wine.  The previous version broke another app I use (yes, there's a bug report on it) and I was most anxious to see if this latest version not only fixed my earlier issue but didn't break anything else.  It did and it did.

---

