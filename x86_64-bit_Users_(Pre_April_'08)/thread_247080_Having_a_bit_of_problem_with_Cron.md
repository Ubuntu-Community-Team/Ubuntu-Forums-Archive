---
title: "Having a bit of problem with Cron"
date: 2006-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by subpar on 2006-08-30
...and I hope I'm not just noobin out.

Anyways, I am trying to set up a crontab entry for an alarm clock that'll go off every morning at 9:30, Monday-Friday, and cron is giving me a pretty rough time.

I tried removing it and reinstalling it to no avail, and when I try to set up the cron, this is what I get:

```
subpar@Gargamel:/var/run$ cron 30 9 * * 1-5 /home/subpar/bin/alarm.sh
cron: can't open or create /var/run/crond.pid: Permission denied

```

If I try to do it with sudo, this is what I get:

```
subpar@Gargamel:/var/run$ sudo cron 30 9 * * 1-5 /home/subpar/bin/alarm.sh
cron: can't lock /var/run/crond.pid, otherpid may be 4508: Resource temporarily unavailable
```

Any help is appreciated!

---

### Post by jrib on 2006-08-30
Use ```
crontab -e
``` to edit your crontab file.  AFAIK, you can't just pass cron arguments like you were trying.

---

### Post by subpar on 2006-08-30
Ahh, thanks. I was just noobing out then.

---

