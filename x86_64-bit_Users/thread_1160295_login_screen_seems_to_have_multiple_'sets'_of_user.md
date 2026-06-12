---
title: "login screen seems to have multiple 'sets' of users randomly"
date: 2009-05-15
forum: x86 64-bit Users
---

### Post by lmellor on 2009-05-15
It's an odd one but I'll try to describe it to the best of my ability...

I created a new user called 'guest', gave it a password, allowed it to be displayed on the login screen and gave it a picture (Mr. T).

Upon rebooting I noticed that the new account was not there, and so I logged in as myself again, this time I created the same user with the same credentials but decided to use a different picture as I couldn't find the original one I'd used.

After a further reboot low and behold, Mr. T came back...

It seems that now I have 2 sets of users with the same names, just different pictures and totally different settings once logged in (compiz for one example, network settings for another).

90% of the time it logs in with what I've now called the Mr. T login screen, but every 9 or 10 times it loads the 'rogue set' of users.

Has anyone got any idea what's happening at all?

I am running 9.04 AMD64 currently though this has been upgraded from 8.10 and 8.04 respectively (8.04 was a fresh installation).

Thanks in advance.

Luke.

---

### Post by lmellor on 2009-05-16
Upon further tinkering I've found myself remarkably more confused, it would seem that if I let the countdown on the grub menu go through then I get the desired login screen, if however I simply hit enter then I get the rogue set of users.

I guess that for now I can simply cut down the timer in grub though it seems a bit of a sham, also I'm concerned that using that method would result in catastrophe when a new kernel is released.

Thanks in advance, I do hope that someone has some sort of idea what's happening.

:confused:

---

