---
title: "The 2008 upgrade of Ubuntu 7.10 Gutsy Gibbon how to upgrade it?"
date: 2007-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2007-12-30
Will Ubuntu 7.10 will be upgradeable to 2008 through System Administration Update-Manager?
If not how can I upgraded it once the new version is released?

---

### Post by John.Michael.Kane on 2007-12-30
> **Lukasz Tarkowski said:**
> Will Ubuntu 7.10 will be upgradeable to 2008 through System Administration Update-Manager?
If not how can I upgraded it once the new version is released?

I'm taking it your are talking about upgrading to 8.04 hardy from 7.10. If this is indeed the case. The current method of doing this is the pass the below command from your terminal.

```
update-manager -d
```

After which the update manager will pop up stating New distribution release '8.04' is available.

---

### Post by Lukasz Tarkowski on 2007-12-30
I have Gutsy Gibbon 7.10 and I would like to know if I can upgraded to the newest version that will come up in 2009 _New release in year 2009_ Of Ubuntu Gutsy Giboon
_Cause this version of Ubuntu Gutsy Gibbon is supported till 2009_

---

### Post by jken146 on 2007-12-30
If you upgrade to a new release, you will no longer have Gutsy Gibbon.  8.04 will be Hardy Heron and 8.10 will be some other animal.  You can keep Gutsy for as long as you like (just don't upgrade) and you'll continue to get security updates and bug fixes until 2009.

I do a clean install every 6 months.

---

### Post by stmiller on 2007-12-31
Don't "upgrade" to the development version. Nothing will work right, unless you want to help file bugs. Hardy is still early alpha...

Gutsy is the most current version, and is continually updated with security updates and patches as needed. Just issuing
```

sudo apt-get update

sudo apt-get upgrade

```
will have your system up to date.

FYI Ubuntu makes a new release every [six months]("https://wiki.ubuntu.com/HardyReleaseSchedule"). Standard releases have 18 months of updates. The LTS releases have an extended support time.

---

### Post by Lukasz Tarkowski on 2008-01-05
Thnx :) that solves it :)
Sry for not replying to long

---

