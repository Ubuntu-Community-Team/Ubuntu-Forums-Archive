---
title: "Weird cron..."
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by purefan on 2008-11-09
Hello there,

Ive been monitoring my system logs before updating to 8.10 (currently on 8.04) and found a funny cron job which cant find where its coming from, its on the screenshot.

I have checked the anacrontab file and heres what it reads:
```

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

```

The weird cron is ran every hour after boot up and cant find any for my user or root:
```

purefan@laptop-ub-64:/etc/cron.hourly$ crontab -l
no crontab for purefan
purefan@laptop-ub-64:/etc/cron.hourly$ sudo crontab -l
[sudo] password for purefan: 
no crontab for root

```

as far as I know this cron isnt really affecting my system but found it troubling not knowing how to disable it or why is it a php related thing...

So, anyone knows how to disable this cron or am I mistaken here and its not a cron or what?

Thanks!

---

### Post by jklslvch on 2008-11-09
yeah i dont kno much about ubuntu but isnt that for the update manager to refresh every hour to check for updates or is that another one?

---

### Post by purefan on 2008-11-10
I really dont know, but find that one and the one before the marked line troubling, why should the system be calling a php library? doesnt make sense to me...

---

