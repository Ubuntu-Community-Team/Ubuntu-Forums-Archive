---
title: "crontab -e weirdness; help ???"
date: 2007-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by outsider2222 on 2007-11-24
hi; I'm a 12 year user of linux, but new to Ubuntu ...

I tried to do a crontab -e, but the system does not allow me ( bob ) to do so, even though  i placed myself in /etc/cron.allow:

$ crontab -e
You (bob) are not allowed to use this program (crontab)
See crontab(1) for more information

$ more /etc/cron.allow
bob

i have tried rebootting and everything that i can think of , whats the deal ????

---

### Post by dcstar on 2007-11-24
> **outsider2222 said:**
> hi; I'm a 12 year user of linux, but new to Ubuntu ...

I tried to do a crontab -e, but the system does not allow me ( bob ) to do so, even though  i placed myself in /etc/cron.allow:

$ crontab -e
You (bob) are not allowed to use this program (crontab)
See crontab(1) for more information

$ more /etc/cron.allow
bob

i have tried rebootting and everything that i can think of , whats the deal ????

Does your user account have administration rights?

---

### Post by outsider2222 on 2007-11-24
according to the "user & groups" pull down menu", the user bob has: "administer the system" rights .....

---

### Post by outsider2222 on 2007-11-24
actually it just started working (what the heck ...:lolflag:) , i was testing to see if i could get another user to be acceptable to crontab -e, it worked for that user; i went back and it worked for "bob" .. this was just after i added the other user to cron.allow ...[COLOR="Red"] almost as if crontab didn't read the cron.allow file for several hours the first time ??????[/COLOR]

---

