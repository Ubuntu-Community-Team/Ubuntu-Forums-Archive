---
title: "Question about Davka Platinum 6 (Hebrew Word Processing software)"
date: 2008-04-16
forum: Wine
---

### Post by mnfiddledragon on 2008-04-16
Hi, 

I'm writing on behalf of a coworker who is interested in seeing if such support exists. His wife uses Davka Platinum 6 in Windows, and is looking to see if it's  possible to use it in linux via wine/CrossOver/Cedega.

Thanks!
Liz

---

### Post by happyhamster on 2008-04-16
I would say: just try it out :) 

- The application database has this entry:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4359](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4359)

- Which is pretty encouraging taking into account the very old age of that report  (current wine version = 0.9.59). So, chance is that things run more smoothly now.  Also: some, if not all font-related problems in that report will likely go away after installing the windows truetype corefonts:

sudo apt-get install msttcorefonts

- And a few other fonts can be installed using the winetricks script. See this page:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Good luck, and keep us informed.

---

### Post by mnfiddledragon on 2008-04-16
Thanks! I'll send this info on to him!

I've also contacted Davka to see if I can get a review copy of the software to see if I can see how it works under the most recent version of wine and update that review. We'll see how it goes :)

---

### Post by BroadArrow on 2010-01-24
Any recent reports on how well Davka Writer runs on Ubuntu?

---

### Post by gps-au on 2010-11-17
very interesting thread, If I can get davka installed and working under wine on lucid I'll report.

its probably that last program keeping me using windows !!

---

