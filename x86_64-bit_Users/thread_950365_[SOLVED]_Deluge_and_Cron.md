---
title: "[SOLVED] Deluge and Cron"
date: 2008-10-17
forum: x86 64-bit Users
---

### Post by mick316 on 2008-10-17
Hi Guys - I have been using deluge and crontab for some time now with great success, until I upgraded deluge to the latest version. Now the command does not work and I have to use Ktorrent so that I can make the most of my off peak downloads.

My Crontab is as: 04 01 * * * export DISPLAY=:0 && Deluge

Any help would be greatly appreciated.

---

### Post by mvoncken on 2008-10-17
Are you using deluge 1.0?

[http://dev.deluge-torrent.org/wiki/Faq#HowdoIstartthedaemon](http://dev.deluge-torrent.org/wiki/Faq#HowdoIstartthedaemon)

---

### Post by mick316 on 2008-10-17
Yes, I am using 1.02 now, and this problem started with version 1.

---

### Post by mvoncken on 2008-10-17
Did you read the faq I linked?

deluge 1.x has a daemon
You would start the daemon from cron, not the gtk-ui.

---

### Post by mick316 on 2008-10-18
Yes I did read the post and it did not make much sense to me (still  a newbie at this stuff). So that means I can't run the GUI from Cron. 
Thanks if that is the case then I will stick with Ktorrent.

---

