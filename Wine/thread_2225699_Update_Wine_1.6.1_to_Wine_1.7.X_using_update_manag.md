---
title: "Update Wine 1.6.1 to Wine 1.7.X using update manager"
date: 2014-05-22
forum: Wine
---

### Post by Martin_McGlensey on 2014-05-22
I want to update Wine 1.6.1 to 1.7.x. I installed 1.6 because it was the stable release. Now I've been advised to upgrade. The original install was done via apt-get. From the Wine PPA repository. apt-get install wine1.6. Noticed that the update updated a component of Wine but the version was still 1.6.1. What is the best way to do the update?  Should I install 1.7 over 1.6 (apt-get install wine1.7)? I've got apps working under wine so I do not want to lose them. This is all new to me so have patience. All replies are appreciated.

BTW I'm running Ubuntu 12.04 LTS.

Thanks

---

### Post by adec2 on 2014-05-25
I am guessing you need to do a "sudo apt-get remove wine1.6" then a "sudo apt-get install wine1.7" if you have the wine ppa installed?

---

