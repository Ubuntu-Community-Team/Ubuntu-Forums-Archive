---
title: "Is it no longer possible to play games in Wine?"
date: 2012-01-06
forum: Wine
---

### Post by beingthehero on 2012-01-06
I used to be able to play Hidden and Dangerous and Warcraft 2 perfectly in Wine, but suddenly they've started to mess up badly. 
[IMG]http://i228.photobucket.com/albums/ee35/beingthehero/Screenshot-1-8.png?t=1325900667[/IMG]

When I try to play Warcraft II, it simply causes the computer to crash. Same thing for Call of Duty 2. Call of Duty and Battlefield 1942 won't even install, even though all of these games are said to be compatible with Wine. I've tried going back to previous versions of Wine, and they all still did the same thing. Any help?

---

### Post by Basher101 on 2012-01-06
think back - did you do anything before it stopped working? (e.g. changing settings, updates, installing programs etc) if so could you think of something that could have messed it up?

this is the way i track down things if they worked and suddenly stop to do so.

---

### Post by oldos2er on 2012-01-07
Thread moved to Wine.

---

### Post by beingthehero on 2012-01-07
I can't remember if any specific update would have caused this. I use the update manager all the time, so I really can't pinpoint any specific program that would have caused everything to malfunction on a scale like this. The only games that work are some of the default, minor ones, like solitaire. Even GBA emulators no longer work properly.

---

### Post by tersogar on 2012-01-07
Did you add wine ppa?

---

### Post by cwwilson721 on 2012-01-07
Sounds like you borked your wine folder.

Did you do the silly thing, and install EVERYTHING in ~/.wine ? Almost guaranteed to screw it up.

I install ALL wine programs into different folders (i.e. '.wine-wow' for WoW, '.wine-office' for office, and 'wine-D3D' for stuff that needs D3D to run. Keep 'em separate, and you narrow down the causes of issues. "env WINEPREFIX=" is your best friend.

By the look of your screenshot, it looks like a video issue anyway.

---

